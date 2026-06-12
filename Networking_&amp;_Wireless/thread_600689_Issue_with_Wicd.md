---
title: "Issue with Wicd"
date: 2007-11-02
forum: Networking &amp; Wireless
---

### Post by grEnAlEins on 2007-11-02
I am running Ubuntu 7.10 with both Gnome and KDE.  Gnome network manager was causing shutdown issues for me.  After I hit shutdown, it would start terming and killing things, but could not do it eth1 (my wireless connection).  The KDE wireless manager did not have this issue for some reason.

One of my classmates is an avid Ubuntu user, and said he was having the same problem.  He resolved it by using Wicd.  He advised me to download and install it.  So I added the appropriate repository and installed it via synaptic.  I also followed the directions to get Wicd to start on boot, however it did not work in Gnome or KDE.  Below is what I did.

Gnome:
System > Preferences > Sessions
....Startup Programs > New > **Name:** Wicd  **Command:** /opt/wicd/tray.py  **Description:** Wicd network manager

KDE:
In Konsole, I entered " sudo ln -s /opt/wicd/tray.py ~/.kde/Autostart/tray.py "
------------------------------
Neither of these worked.  I can still connect by manually starting Wicd, but would really rather have it run on boot.  Does anyone have any ideas?  I followed the directions from [here]("http://wicd.sourceforge.net/download.php"), but they did not work for me.  Any help would be outstanding.

Thanks,

Nick

---

### Post by grEnAlEins on 2007-11-03
Nobody knows how to make Wicd work?

Does anybody know how I can get gnome/kde network managers back?  Like what the packages are called?

---

### Post by imdano on 2007-11-03
This might help you [http://wicd.sourceforge.net/phpbb/viewtopic.php?f=3&t=237](http://wicd.sourceforge.net/phpbb/viewtopic.php?f=3&t=237)

---

### Post by grEnAlEins on 2007-11-03
I just switched back to Gnome/KDE network manager...

---

### Post by patrickfromspain on 2007-11-03
try: ln -s /opt/wicd/tray.py ~/.kde/Autostart/

---

### Post by imdano on 2007-11-04
Using a symlink with KDE tends to cause problems with the icon not being displayed correctly.  It may end up getting fixed when 1.4 gets released, since we're reorganzing the code quite a bit, including the way we specify the paths for images.

---

### Post by grEnAlEins on 2007-11-04
> **imdano said:**
> Using a symlink with KDE tends to cause problems with the icon not being displayed correctly.  It may end up getting fixed when 1.4 gets released, since we're reorganzing the code quite a bit, including the way we specify the paths for images.

That is good to know.  Can you think of any reason why it would not start on boot in Gnome?  I added it to the list of startup programs but this did not make it start.

I went back to the stock network managers for now, although I did like the interface of Wicd.

Thanks,

Nick

---

### Post by imdano on 2007-11-04
The GNOME problem might be due to a bug in old versions (1.3.3 and earler, I think, or maybe 1.3.1).  I think that right now the version in the repo is affected.  If you ever decide to try wicd again you should get the newest testing version from the sourceforge site.

---

