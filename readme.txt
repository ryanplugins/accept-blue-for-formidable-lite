=== RyanPay Card Payments with accept.blue for Formidable ===
Contributors: ryanplugins
Tags: formidable, payment, accept.blue, gateway, credit card
Requires at least: 6.0
Tested up to: 6.9
Requires PHP: 7.4
Stable tag: 1.0.1
License: GPL-2.0-or-later
License URI: https://www.gnu.org/licenses/gpl-2.0.html

Accept credit card payments through accept.blue directly inside your Formidable Forms.

== Description ==

**Secure Form Checkout** connects your Formidable Forms payment forms to the accept.blue payment processing platform. All card data is handled inside a secure accept.blue Hosted Tokenization iFrame — it never passes through your server, keeping your site PCI-compliant.

This is the **free Lite version**.

= What's Included in Lite =

* **Credit card payments** via accept.blue Hosted Tokenization iFrame — card data never touches your server
* **Test / Sandbox mode** — safely test payments with accept.blue sandbox credentials before going live
* **Test Connection** — verify your API credentials without leaving WordPress
* **Debug logging** — dedicated per-month log file with an in-admin log viewer, gated behind a settings toggle
* **3D Secure 2 (3DS2)** — optional EMV 3DS2 browser-based authentication per Form Action
* **Per-form API credential override** — run different forms against different accept.blue merchant accounts
* **Processing overlay** — animated spinner shown on form submit while payment processes
* **Minified assets** — production-ready JS and CSS; source files served automatically when WP_DEBUG is on


= Requirements =

* WordPress 6.0 or higher
* PHP 7.4 or higher
* Formidable Forms Pro (required for payment fields)
* An active accept.blue merchant account (sign up at https://accept.blue)

== Third-party Services ==

This plugin transmits payment data to accept.blue, a third-party payment processor. Card data is captured inside an accept.blue Hosted Tokenization iFrame and never passes through your server.

* accept.blue website: https://accept.blue


No card data is stored on your server. All sensitive payment data is handled exclusively by accept.blue's PCI-compliant infrastructure.

== Source code ==

The unminified source files for all JavaScript and CSS are included in the plugin's assets/ directory alongside the minified production files. No separate build step is required to review the source.

== Installation ==

1. Upload the plugin folder to /wp-content/plugins/ or install via Plugins > Add New > Upload Plugin.
2. Activate via Plugins > Installed Plugins.
3. Go to Formidable > Global Settings > Accept.Blue.
4. Enter your credentials:
   - API Key — from your accept.blue portal under API Keys
   - PIN — if your API key requires one (optional)
   - Hosted Tokenization Key — from accept.blue Settings > Hosted Tokenization
5. Click Save Changes and use the Test Connection button to confirm your credentials work.
6. Create or open a Formidable Form.
7. Drag the Accept.Blue Card field onto the form canvas.
8. Open Form Actions and add the Accept.Blue Payment action.
9. Set your amount and currency.
10. Click Update and publish your form.

== Frequently Asked Questions ==

= Does this store card numbers on my server? =

No. Card data is tokenised entirely within the accept.blue Hosted Tokenization iFrame. Your server only ever receives a short-lived nonce token. No card numbers, CVVs, or expiry dates are stored on your server or in your database.

= Can I use this in test/sandbox mode? =

Yes. Enable Test / Sandbox Mode in Formidable > Global Settings > Accept.Blue and use your accept.blue sandbox credentials. No real charges are made. Disable the setting and switch to live credentials when you are ready for production.

= What statuses does the plugin use? =

complete — charge captured and settled; auth — authorised but not yet captured; failed — charge declined or errored; voided — authorisation cancelled before capture; refunded — charge refunded in full or in part.

= Does debug logging store sensitive data? =

API request and response bodies are logged when debug logging is enabled. Card numbers are never present (they are handled by the accept.blue iFrame and never reach your server), but disable debug logging once you have finished troubleshooting.

No card data is stored on your server. All sensitive payment data is handled exclusively by accept.blue's PCI-compliant infrastructure.


== Changelog ==

= 1.0.1 =
* Fixed: Added nonce verification to settings save path in route() to prevent CSRF
* Fixed: Removed recurring, installment, and trial fields from prepare()/get_defaults() — recurring is not implemented in Lite and was dead code
* Fixed: Updated accept.blue Terms of Service and Privacy Policy URLs to correct paths (/legal/...)
* Fixed: Updated admin upsell notice and readme to accurately reflect which features are in Lite vs Pro
* Fixed: 3DS and per-form API credential override are fully functional in Lite — moved from Pro-only list to Lite feature list
* Fixed: Removed recurring-related JavaScript toggle code from admin panel (no recurring UI in Lite)
* Fixed: Removed screenshot reference to recurring payment settings panel (no such UI in Lite)

= 1.0.0 =
* Initial Lite release based on Pro v1.0.0
* Core credit card payments via accept.blue Hosted Tokenization iFrame (PCI-minimised)
* Debug logging with in-admin log viewer and Clear Log function
* 3D Secure 2 (3DS2) browser-based authentication per Form Action
* Per-form API credential override for multi-merchant support
* Licensing system fully removed
* All PHP identifiers prefixed with _lite (classes, functions, constants, options, hooks, DB tables)
* Plugin entry file renamed to formidable-acceptblue-lite.php
* All include files renamed to class-frm-ab-lite-*.php
