---
title: "Ubuntu crashes when connecting to wifi"
date: 2007-02-18
forum: Networking &amp; Wireless
---

### Post by spewperb on 2007-02-18
Hi everyone, I have just installed my wireless network adapter (Netgear WPN111) using ndiswrapper. Everything seemed to be alright however when I went to configure it in network settings to connect to the network it crashes ubuntu. I get a complete screen lockup and have to do a hard reboot to get it running again. 

Any ideas anyone?

---

### Post by NJD on 2007-03-19
I have this EXACT problem, any takers on this one?

---

### Post by gavfranc on 2007-05-01
I'm also having problems Thinkpad T23 working with Wireless card Dlink G650M under edgy seemlessly. However under Feisty, major problems. Firstly only operated at 46% strength, then stopped working altogether. System started to crash when connecting to network. I did fresh install and removed ndiswrapper and installed latest 1.43. This also crashes when doing modprobe ndiswrapper. Only once did it connect and then crashed as soon as Gnome Network Manager was attempting to connect to network. Soon going back to Edgy, very disappointed as thought "at last a proper replacement for windows"

---

### Post by termdex on 2007-10-25
Here's my "same problem" story:

Just upgraded from 7.04 via Package Manager (no disc).
I have a Dlink DWA-642 pcmcia card that worked on 7.04 via ndiswrapper.
But after upgrade, when ndiswrapper attempts to init card the whole system locks hard.
The system dualboots with XP with which the card still works.
madwifi doesn't seem to recognize this chipset, yet.
Using the latest NDIS driver from Dlink doesn't help.

Card info: Dlink DWA-642
PN: BWA642NA..A1
HW ver: A1
FW ver: 1.01

---

### Post by sefs on 2007-10-25
If your card is rt73 based and you are using rt73 based drivers with WPA/WPA2 enabled, you may be out of luck.  So are you using an rt73 based card?

Either way try connecting to the router with

1) No securtiy

and then

2) with wep

3) and finally with wpa/wpa2

and see at which point you get the lockup

---

