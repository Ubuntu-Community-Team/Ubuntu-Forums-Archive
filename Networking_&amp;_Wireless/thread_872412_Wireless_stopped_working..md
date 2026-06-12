---
title: "Wireless stopped working."
date: 2008-07-27
forum: Networking &amp; Wireless
---

### Post by robertkane on 2008-07-27
Several weeks ago I got a Belkin F5D7000 wireless card working. Occasionally, the network wouldn't work but I'd reboot and all would be fine. Today, however, the card just does not seem to be working.

Here's a summary of the system currently:

lspci reports the id of the wireless card.
ndiswrapper -l shows that the driver is present and device is installed
The configuration in /etc/network/interfaces still has the same config (including loading wpa_supplicant"
iwconfig shows information for wlan0
ifconfig shows information for wlan0 and wlan0:avahi

wlassistant reports that "Radio of your wireless card seems to be turned off using an external switch on your computer. You need to turn it on to be able to use wireless networks".


At this point I'm assuming that it may be hardware, but is there anything I can check on the configuration side of things?

---

### Post by falcon61102 on 2008-07-28
I know it sounds silly, but do you have one of those buttons on your computer that shuts the wireless off and you may have bumped it?

If not, have you tried checking out the BIOS, it may be possible that a BIOS setting changed and shut your wireless off.  I'd give a quick check through there.

---

### Post by evozniak on 2008-07-28
i heaving the same problem with wireless

---

### Post by robertkane on 2008-07-28
I don't have a power button on the card. Following advice I found in another thread I:

a) Used  "serviceconfig" to disable the avahi-daemon

b) Need to run "sudo /etc/init.d/networking restart"

---

### Post by falcon61102 on 2008-07-28
Did that work for you?

---

