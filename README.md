# Sho MultiReseller

Sho MultiReseller is an alpha/master reseller plugin for cPanel/WHM. It adds Super Alpha, Alpha and Master reseller tiers on one WHM server, with pooled disk, bandwidth and account limits.

This repository holds documentation only. The plugin is commercial software, licensed by ShoHost. It is not a hosting plan, and it is not made or endorsed by cPanel.

## Features

Verified on the [product page](https://shohost.com/sho-multireseller):

- Five-tier tree on one WHM server: Super Alpha, Alpha, Master, WHM reseller and cPanel, with rolled-up usage
- Super Alpha sits above Alpha branches (optional, for more than one top-level brand on the same server). Alpha owns Masters, WHM resellers and cPanel accounts. Master owns WHM resellers and cPanel accounts
- Pooled disk, bandwidth and account limits, with oversell controls you set on the subtree. Quota overruns through root WHM or direct API calls are blocked
- ACL templates: the Sho MultiReseller default ACL, or a custom list, when promoting resellers or via packages
- Package editor extension so a WHM package can carry a default tier, limits and ACL
- Watchdog automation for auto-suspend, package sync, usage rebuild and quota notification emails on a schedule
- Account scanner and hierarchy repair when accounts are created or moved outside the plugin UI
- Legacy marker import for an existing multi-reseller tree, plus hook cutover and registry reconcile
- Remote reseller transfer into the correct parent pool, with parent quotas checked before each pull
- Subtree backups of a reseller's accounts, with a choice of pool on restore
- Live server load (CPU/RAM) plus rolled-up disk and bandwidth
- WHM hooks on account create, modify, remove, suspend, unsuspend and package change
- Installs as a WHM AppConfig plugin, with a CGI management UI and background maintenance jobs

## Requirements

Sho MultiReseller is the cPanel/WHM edition only. It does not support DirectAdmin.

- cPanel/WHM 11.110 or newer
- Root access on your own cPanel/WHM server (not a reseller hosting plan)
- Python core and SQLite WAL
- Outbound HTTPS to ShoHost for install, updates and licence checks
- For remote transfers, network access from your server to the source servers
- One licence per production WHM server IP

Check the cPanel version as root:

```bash
/usr/local/cpanel/cpanel -V
```

Anything at 11.110 or newer is fine.

## Install

Run this command as root on the WHM server (over SSH, or in WHM → Server Configuration → Terminal):

```bash
curl -fsSL https://files.shodns.in/sho-multireseller/install | bash
```

Trial: run without a license key first. Licensed: add your key from the [ShoHost license store](https://license.shohost.com/index.php?rp=/store/sho-multireseller) when prompted.

The installer registers the plugin with WHM as an AppConfig plugin, adds the package editor extension and sets up background maintenance jobs. In WHM, open **Plugins → Sho MultiReseller**, or type “Sho” in the WHM search box.

## Licence and pricing

Licensed by ShoHost. From $2/mo, $19.20/yr or $100 lifetime per server, with a 15-day free trial and a 7-day refund on eligible orders.

One licence per production WHM server IP covers Super Alpha, Alpha, Master and WHM reseller tiers. The licence includes updates, install scripts and licence verification.

Order or start from the [ShoHost license store](https://license.shohost.com/index.php?rp=/store/sho-multireseller). See the [refund policy](https://shohost.com/refund-policy) for refund terms.

## Using with WHMCS

Sho MultiReseller works through WHMCS's standard cPanel/WHM module. It does not ship a separate WHMCS module.

Set the tier (WHM Reseller, Master, Alpha or Super Alpha) under Sho MultiReseller Privileges on a WHM package. When WHMCS creates an account on that package, the account gets that tier, and WHMCS reseller setup is picked up too.

If you sell through WHMCS, run one test order end to end during the trial.

## Moving an existing reseller tree

You can move an existing multi-reseller tree onto Sho MultiReseller on the same WHM server: install (a 15-day free trial is available), import the legacy multi-reseller markers, then use the account scanner, hook cutover and registry reconcile. Plan a short maintenance window after large moves while usage rebuilds, and back up first.

## Version

Current stable release: **1.2.18**, released 22 November 2026.

Version, release date and release note: [https://files.shodns.in/sho-multireseller/version.json](https://files.shodns.in/sho-multireseller/version.json). The installer fetches the current stable release from that host. Updates are included with every licence, including lifetime. See [CHANGELOG.md](CHANGELOG.md).

## Support

- Email: [support@shohost.com](mailto:support@shohost.com)
- WhatsApp: +91 94880 91432
- Hours: 9 AM–12 midnight IST

## Links

- Product page: [https://shohost.com/sho-multireseller](https://shohost.com/sho-multireseller)
- Store: [https://license.shohost.com/index.php?rp=/store/sho-multireseller](https://license.shohost.com/index.php?rp=/store/sho-multireseller)
- Guide: [Alpha vs Master vs Super Alpha reseller](https://blog.shohost.com/alpha-vs-master-vs-super-alpha-reseller/)
- Current version: [version.json](https://files.shodns.in/sho-multireseller/version.json)

## FAQ

### What is an alpha reseller plugin for cPanel/WHM?

WHM on its own has one reseller layer. An alpha reseller plugin such as Sho MultiReseller adds Super Alpha, Alpha and Master tiers above it on the same WHM server, with pooled disk, bandwidth and account limits for each branch. See [Alpha vs Master vs Super Alpha reseller](https://blog.shohost.com/alpha-vs-master-vs-super-alpha-reseller/).

### How do I create an alpha reseller in WHM?

WHM supports only one reseller layer, so you need a plugin. Install Sho MultiReseller as root, open **Plugins → Sho MultiReseller → Alpha**, then create or promote the account and set its maximum Masters, WHM resellers, cPanel accounts, disk and bandwidth pool, and ACL.

### Does it work with WHMCS?

Yes, through WHMCS's standard cPanel/WHM server module. Set the Sho tier on a WHM package under Sho MultiReseller Privileges; accounts WHMCS creates on that package get that tier. There is no separate Sho MultiReseller WHMCS module.

### Does it support DirectAdmin?

No. Sho MultiReseller is the cPanel/WHM edition only and needs cPanel/WHM 11.110 or newer with root access.

### Is there a trial?

Yes. You can run Sho MultiReseller for 15 days on your WHM server without a licence key. After purchase, eligible orders have a 7-day refund.

---

Licensed by ShoHost.
