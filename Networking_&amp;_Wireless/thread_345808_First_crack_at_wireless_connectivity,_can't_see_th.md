---
title: "First crack at wireless connectivity, can't see the router"
date: 2007-01-24
forum: Networking &amp; Wireless
---

### Post by bnoll on 2007-01-24
So, I'm following this: [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide) and I get down to the Router Connection portion (4.3) of the Troubleshooting Steps, and this is where it all goes to hell.

When running iwconfig, the "Access point:" portion of the output says "Invalid".

So, I downloaded and installed wifi-radar, but when I run it, all I see rolling across the terminal is the message "eth1 Interface doesn't support scanning : No such device".

Where I basically stop being able to understand what that troubleshooting guide is telling me is where it says:

 If you can not connect to the router then try these.

   1. Change to an open signal (instead of wep or wpa). 


Can anyone give me any more advice on where to go next on this?

BTW... I have my laptop set up to dual boot to Windows XP or Ubuntu 6.10.  This wireless connection is detected automatically in XP, and connects fine.

TIA,

Bryan

---

### Post by spd106 on 2007-01-25
I'm afraid that help doc is just too long to be of any help at the moment.

Try checking that your card is supported, enter **sudo lshw -C network** at a terminal. If it says Broadcom then you should probably check out this page [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy)

You may end up needing ndiswrapper though.

---

