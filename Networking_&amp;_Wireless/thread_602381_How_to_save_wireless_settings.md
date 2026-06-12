---
title: "How to save wireless settings"
date: 2007-11-04
forum: Networking &amp; Wireless
---

### Post by MrHyde on 2007-11-04
Hi,

I have finally got my wireless card to work under Gutsy Gibbon, but now I have having trouble saving the settings.  I have made changes in the /etc/networking/interfaces file to add the following lines

[PHP]
auto wlan0
iface wlan0 inet dhcp
wireless-essid Mittal
wireless-key FEFEFEFEFEFEFEFEFEFEFEFEF
wireless-channel 1
wireless-mode managed
[/PHP]

However, everytime I re-start my computer, the wireless card does not come up.  I have to run /etc/init.d/networking start everytime.  I believe it is due to the script not being enabled in any of the runlevels.  Am I right or is there something else I have missed.  Also, which runlevel should I add it to - 3 or 5. I am using the box for MythTV.

Thank you.
Vivek Mittal

---

### Post by Colbrac on 2007-12-04
Shouldn't you have 'auto wlan0' below the definition of the interface? I'm not sure but maybe that helps.

---

