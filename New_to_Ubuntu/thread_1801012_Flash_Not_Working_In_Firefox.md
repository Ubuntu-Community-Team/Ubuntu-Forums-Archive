---
title: "Flash Not Working In Firefox"
date: 2011-07-09
forum: New to Ubuntu
---

### Post by spikoley on 2011-07-09
Flash isn't working in Firefox, but it works in Chromium.  I did an update a few days ago and it broke flash for everything.  I was able to get it working with Chromium, but not Firefox.

When I run *sudo apt-get install -f* it gives me some errors which I believe are the root cause of the issue.

Any ideas?

```

sudo apt-get install -f
Reading package lists...
Building dependency tree...
Reading state information...
The following package was automatically installed and is no longer required:
  chromium-browser-inspector
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up chromium-browser (12.0.742.112~r90304-0ubuntu0.10.10.1) ...
update-alternatives: error: /var/lib/dpkg/alternatives/x-www-browser corrupt: line not terminated while trying to read priority
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
update-alternatives: error: /var/lib/dpkg/alternatives/x-www-browser corrupt: line not terminated while trying to read priority
dpkg: error processing firefox (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of firefox-gnome-support:
 firefox-gnome-support depends on firefox (= 3.6.18+build2+nobinonly-0ubuntu0.10.10.2); however:
  Package firefox is not configured yet.
dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 chromium-browser
 chromium-browser-l10n
 chromium-browser-inspector
 firefox
 firefox-gnome-support

```

```

sudo dpkg --configure -a
Setting up chromium-browser (12.0.742.112~r90304-0ubuntu0.10.10.1) ...
update-alternatives: error: /var/lib/dpkg/alternatives/x-www-browser corrupt: line not terminated while trying to read priority
dpkg: error processing chromium-browser (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of chromium-browser-inspector:
 chromium-browser-inspector depends on chromium-browser; however:
  Package chromium-browser is not configured yet.
dpkg: error processing chromium-browser-inspector (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of chromium-browser-l10n:
 chromium-browser-l10n depends on chromium-browser (= 12.0.742.112~r90304-0ubuntu0.10.10.1); however:
  Package chromium-browser is not configured yet.
dpkg: error processing chromium-browser-l10n (--configure):
 dependency problems - leaving unconfigured
Setting up firefox (3.6.18+build2+nobinonly-0ubuntu0.10.10.2) ...
update-alternatives: error: /var/lib/dpkg/alternatives/x-www-browser corrupt: line not terminated while trying to read priority
dpkg: error processing firefox (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of firefox-gnome-support:
 firefox-gnome-support depends on firefox (= 3.6.18+build2+nobinonly-0ubuntu0.10.10.2); however:
  Package firefox is not configured yet.
dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 chromium-browser
 chromium-browser-inspector
 chromium-browser-l10n
 firefox
 firefox-gnome-support

```

---

### Post by LowSky on 2011-07-09
there is a plugin for linux called flash-aid... give you the newest verion of flash and makes sure everything works

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

---

### Post by spikoley on 2011-07-09
> **LowSky said:**
> there is a plugin for linux called flash-aid... give you the newest verion of flash and makes sure everything works

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

Thanks!  Your the man.  

I can now view [http://www.youtube.com/watch?v=-bbQUDFkdsU]("http://www.youtube.com/watch?v=-bbQUDFkdsU").

---

