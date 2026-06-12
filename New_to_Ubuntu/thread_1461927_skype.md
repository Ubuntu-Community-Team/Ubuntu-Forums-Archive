---
title: "skype"
date: 2010-04-24
forum: New to Ubuntu
---

### Post by iamsolost on 2010-04-24
i was trying to install skype and its saying that i have to resolve these dependancies first....


skype:
  Depends: libgcc1 (>=1:4.3) but 1:4.2.4-1ubuntu4 is to be installed
 Depends: libqt4-dbus (>=4.4.3) but it is not installable
 Depends: libqt4-network (>=4.4.3) but it is not installable
 Depends: libqtcore4 (>=4.4.3) but it is not installable
 Depends: libqtgui4 (>=4.4.3) but it is not installable
  Depends: libstdc++6 (>=4.3) but 4.2.4-1ubuntu4 is to be installed


how do i fix these or what needs to be done to install skype successfully.

---

### Post by HermanAB on 2010-04-24
Howdy,

Get the 'static' version of Skype from their web site.  It doesn't have any dependencies.

---

### Post by ddecator on 2010-04-24
Otherwise, you can go into Synaptic and manually work out the dependencies. When you get that error, it means that the necessary dependencies conflict with packages already installed on your system. If you go in and manually try to install the necessary packages, then it will tell you what will need to be uninstalled. From there, you can decide whether it is worth uninstalling them, or if you would rather take HermanAB's advice and download from the site.

---

### Post by yetiman64 on 2010-04-25
+1 for HermanAB's suggestion.

I'm on 9.04 using the static version from the skype site (note the latest is a beta version though - be aware), but it works like a charm here & with no dependency problems on install.
Hope it works for you either way you go - its fantastic tech.
Cheers.

Also note if you're on amd64 platform you may have a hitch with setting an avatar (not a real important problem as such though).

---

