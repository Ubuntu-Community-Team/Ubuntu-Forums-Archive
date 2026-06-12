---
title: "Updates Fail"
date: 2011-07-23
forum: New to Ubuntu
---

### Post by spikoley on 2011-07-23
When I run updates I receive an error message.  It looks like a dependency problem, but I cannot figure out how to fix it.

Running *sudo apt-get install -f* brings the following error.

```

Reading package lists...
Building dependency tree...
Reading state information...
The following package was automatically installed and is no longer required:
  chromium-browser-inspector
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
7 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up chromium-browser (12.0.742.112~r90304-0ubuntu0.10.10.1) ...
update-alternatives: error: /var/lib/dpkg/alternatives/x-www-browser corrupt: unexpected end of file while trying to read master file
dpkg: error processing chromium-browser (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of chromium-browser-l10n:
 chromium-browser-l10n depends on chromium-browser (= 12.0.742.112~r90304-0ubuntu0.10.10.1); however:
  Package chromium-browser is not configured yet.
dpkg: error processing chromium-browser-l10n (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of chromium-browser-inspector:
 chromium-browser-inspector depends on chromium-browser; however:
  Package chromium-browser is not configured yet.
dpkg: error processing chromium-browser-inspector (--configure):
 dependency problems - leaving unconfigured
Setting up firefox (3.6.18+build2+nobinonly-0ubuntu0.10.10.2) ...
update-alternatives: error: /var/lib/dpkg/alternatives/x-www-browser corrupt: unexpected end of file while trying to read master file
dpkg: error processing firefox (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of firefox-gnome-support:
 firefox-gnome-support depends on firefox (= 3.6.18+build2+nobinonly-0ubuntu0.10.10.2); however:
  Package firefox is not configured yet.
dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-dbg:
 firefox-dbg depends on firefox (= 3.6.18+build2+nobinonly-0ubuntu0.10.10.2); however:
  Package firefox is not configured yet.
dpkg: error processing firefox-dbg (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-gnome-support-dbg:
 firefox-gnome-support-dbg depends on firefox-gnome-support (= 3.6.18+build2+nobinonly-0ubuntu0.10.10.2); however:
  Package firefox-gnome-support is not configured yet.
 firefox-gnome-support-dbg depends on firefox-dbg (= 3.6.18+build2+nobinonly-0ubuntu0.10.10.2); however:
  Package firefox-dbg is not configured yet.
dpkg: error processing firefox-gnome-support-dbg (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 chromium-browser
 chromium-browser-l10n
 chromium-browser-inspector
 firefox
 firefox-gnome-support
 firefox-dbg
 firefox-gnome-support-dbg

```

---

### Post by e79 on 2011-07-23
Try to fix dependencies with:

```
sudo apt-get -f install
```

---

### Post by spikoley on 2011-07-24
> **e79 said:**
> Try to fix dependencies with:

```
sudo apt-get -f install
```

The error I get in my first post if from running *sudo apt-get -f install*.

Any other ideas?

---

### Post by e79 on 2011-07-24
My bad, I probably missed it.

Can you then try to completely uninstall and purge confirguration file of Chromium and Firefox and install them again to see if it still occurs ? Backup Bookmarks/Favorites before doing so.

To purge packages:
```
sudo apt-get purge <Package Name>
```

---

### Post by Miljet on 2011-07-24
You might try going to /var/lib/dpkg/alternatives, change the name of x-www-browser to x-www-browser-backup, then try reinstalling chromium.

Your error message is telling you that file is corrupt.
```
 error: /var/lib/dpkg/alternatives/x-www-browser corrupt
```

---

