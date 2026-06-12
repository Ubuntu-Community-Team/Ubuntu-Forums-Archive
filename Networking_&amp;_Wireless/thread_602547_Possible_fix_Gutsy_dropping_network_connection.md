---
title: "Possible fix Gutsy dropping network connection"
date: 2007-11-04
forum: Networking &amp; Wireless
---

### Post by gb5uqx on 2007-11-04
RT61 wireless PCI dropping out every few minutes.

I have been using these settings for a week now with absolutely no 
problems at all. Previously I would loose connections several times 
an hour when surfing or downloading.

Check system/admin/networking tools
Network Device = Loopback device (lo)

Next, right click the panel and select the add to panel option.
Choose Network Monitor in the System & Hardware section and apply.
NB: this is important because the default network icon does not
provide the necessary options to complete the process.

Left click the new network icon and you will then see connection
properties and signal strength, which is probably '0'.
The connection name will be wlan0. 

Click the dropdown and change this value to loopback device (lo). 
The signal strength meter will disapear and an idle status will 
appear. Also the configure button will grey out. Close. You should 
not need to re-boot but no probs if you do.

You can safely remove the original network icon leaving the new one
which will now show surfing activity.

Can anyone else replicate these results?

---

### Post by brodiepearce on 2007-11-16
I'm at a loss.... How would adding a network monitor to the panel for the loopback device stop RT61 wireless from dropping out?

---

### Post by gb5uqx on 2007-11-18
> **brodiepearce said:**
> I'm at a loss.... How would adding a network monitor to the panel for the loopback device stop RT61 wireless from dropping out?

It doesn't.

Perhaps a quirk in my installation meant clicking the network icon in the panel displayed network settings instead of connection properties. However adding 
the networking icon using add to panel displays connection properties. By selection of loopback in the drop down in place of the default wlan0 and then applying it has stopped the connection dropping.

---

### Post by Blutack on 2007-11-18
I suspect the change is coincidental.  A bunch of kernel updates came in recently - it is more likely these are the source of your fix.  There are two kinds of network applet - NetworkManager puts one in the system tray, and this is what appears by default on an install.  You can also add a gnome panel applet which monitors network connections.  The two are very different.

---

