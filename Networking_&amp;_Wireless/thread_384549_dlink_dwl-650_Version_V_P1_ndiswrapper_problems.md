---
title: "dlink dwl-650 Version V P1 ndiswrapper problems"
date: 2007-03-14
forum: Networking &amp; Wireless
---

### Post by thesheff17 on 2007-03-14
alright have read a ton about installing this wireless card but I just can't seem to get it to work.

I have ndiswrapper all installed and everything working correctly.

I downloaded the newest drivers and installed the xp version and when I do ndiswrapper -l
netprism    driver present

and modprobe ndiswrapper works fine.

When I try to start up the network interface I get: ifup wlan0

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device 
wlan0: ERROR while getting interface flags: No such device 
Bind socket to interface: No such device
failed to bring up wlan0


I know I read that I should have this device on lspci but I am not sure why I don't see it.  Do I need to modprobe something else for this card.  I also have a dlink wired card that works fine which also does not list in the lspci when I put it in.  Maybe the module is already loaded?  Any help would be greatly appreciated.  Let me know if you need more information about the system.

Below is the log when I plug in the wireless card:
dmesg:

pccard: PCMCIA card inserted into slot 1
pcmcia: registering new device pcmcia1.0

---

### Post by tturrisi on 2007-03-14
You shouldn't need ndiswrapper for any dwl650 cards, all the chipsets that card ever came with are supported in linux.  Are you sure of the version # you stated above?

---

