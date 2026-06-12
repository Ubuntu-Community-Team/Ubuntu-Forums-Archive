---
title: "Ubuntu 7.04, Thinkpad X40 and Orinoco wireless problems"
date: 2007-09-15
forum: Networking &amp; Wireless
---

### Post by cruzton on 2007-09-15
I have a Thinkpad X40 and a Orinoco Gold PCMCIA card. On this combination of hardware the wireless worked:

 - under 6.06 (ok, but still hit and miss to get it going... but still usable)
 - under 6.10 (better, but still far from flawless)
 - under windows XP, just to see if it's the hardware (wireless worked flawlessly)
 - but under 7.04, mostly not at all

Under 7.04 the wireless, in about 1 in 100 reboots would work, but most of the time I get:

 - card is detected in dmesg
 - network manager shows that i have a wireless adapter, but never finds any wireless networks. manually entering wireless networks gets me nowhere

I've long searched the net, and tried blacklisting various drivers, all without any luck. I also read somewhere that the version 8 firmware of the card might be a problem. Any help on this would be very much appreciated.

Thanks!

ps Here is the kernel version and dmesg output of the card:

Lnux fireball 2.6.20-16-generic #2 SMP Fri Aug 31 00:55:27 UTC 2007 i686 GNU/Linux

[171809.428000] eth1: Hardware identity 0001:0004:0005:0000
[171809.428000] eth1: Station identity  001f:0001:0008:0048
[171809.428000] eth1: Firmware determined as Lucent/Agere 8.72
[171809.428000] eth1: Ad-hoc demo mode supported
[171809.428000] eth1: IEEE standard IBSS ad-hoc mode supported
[171809.428000] eth1: WEP supported, 104-bit key
[171809.428000] eth1: MAC address 00:02:2D:8F:06:C5
[171809.428000] eth1: Station name "HERMES I"
[171809.428000] eth1: ready
[171809.428000] eth1: orinoco_cs at 0.0, irq 3, io 0x3100-0x313f
[171809.592000] ADDRCONF(NETDEV_UP): eth1: link is not ready

---

### Post by cruzton on 2007-09-18
Oh, and the orinoco wireless seems to work flawlessly when I boot the 7.04 live cd. Ugh, so annoying.

---

### Post by Hans-Erik on 2007-10-05
I have the exact same problem on my Thinkpad T41. Wireless works on live CD but not when i installed it. Really frustrating!

---

### Post by Hans-Erik on 2007-10-07
Im just a beginner at linux but this worked for me.

I got it working by first copy the /wireless folder from the liveCD "installation" 

1. Boot up on livecd and copy the /wireless from /lib/modules/kernel/2.0.16../drivers/net/wireless (i think this is the path.. not sure because im not on that computer now) to USB memory or something.
2. Boot up real installation (no cd in cd/dvd-rom)
3. Remove the /lib/modules/kernel/2.0.16../drivers/net/wireless then reboot (no light on orinoco card now)

4. copy the /wireless dir from the USB-memory to the now removed wireless location in /lib/modules/kernel/2.0.16../drivers/net/

5. sudo modprobe orinoco_cs (and now it should work)

PS. I also blacklisted the hostap, hostap_pci and prism2_pci in my created modprobe.d/blacklist-orinoco file) I dont know if this is needed tho.

---

