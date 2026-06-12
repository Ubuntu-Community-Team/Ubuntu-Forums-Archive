---
title: "[SOLVED] Install pci and remove usb"
date: 2007-07-16
forum: Networking &amp; Wireless
---

### Post by Mark_in_Hollywood on 2007-07-16
I had a Linksys WUSB11v4 USB wireless adapter on my desktop computer.

I now want to remove it and uninstall whatever drivers and/or other packages it used IF NECESSARY.

I then want to install a PCI D=link WDA2320.

What order of install and remove to fix this?

---

### Post by kevdog on 2007-07-16
What drivers does the new card require???  If it requires ndiswrapper then some changes may be needed, however if it doesnt -- you dont necessarily have to remove the old drivers.

---

### Post by Mark_in_Hollywood on 2007-07-16
This is the review from a cust. of circuit city. He is linux based:

 Works with Linux (Madwifi-ng)
Reviewer: Kevin from Saint Louis, MO on Tue Apr 24 10:58:44 EDT 2007
16 out of 31 found this review helpful

Bought it because it's supported on linux platforms. Works like a charm. Performance is OK. Reception will be no better than the 1320 (same antenna) but if it's pushing 2db more power then it can get to the AP better. 3db would be twice the power andgiven the +/- fudge factors on the ratings it really could be twice as powerful as a 1320 or no better at all. If you are having trouble with signal strength consider an external antenna over a new card. a 6di antenna is much better than a slightly morepowerful card. example: a 100 mw card upgraded to 200 mw card will not have the perfomance of the 100 mw card with a 6db gain antenna which has an effective radiated power of 400mw. It also helps eliminate reflected power by moving the antenna away from the PC case.

I can't tell you more than that the linuxquestions HCL doesn't have a word about it. Google-ing ubuntu and wda2320 (model #) brings nothing, too. Well lots of people selling the card, little or nothing about problems or troubleshooting

---

### Post by Mark_in_Hollywood on 2007-07-16
I also found:

WDA-2320 ¶
Chipset:	AR5212(802.11a/b/g)
URL:	[www.dlink.com](www.dlink.com)
Interface:	PCI
Antenna Connector:	SMA
Notes:	Successfully working with SuSE 10.1
Notes:	Successfully working with Gentoo 2.6.18-gentoo-r3
Notes:	Successfully working with Debian/Lenny using madwifi-hal-0.9.30.13-current.tar.gz.

Firmware Compatibility:
Hardware	Firmware	Status
A1	1.00	Works just fine
A2	1.00	No problems at all so far, painless setup with madwifi-0.9.2, wpa_supplicant-0.5.6

from: [http://madwifi.org/wiki/Compatibility/D-Link#WDA-2320](http://madwifi.org/wiki/Compatibility/D-Link#WDA-2320)

---

### Post by Mark_in_Hollywood on 2007-07-16
It would SEEM that this is a MadWIFI requirement device.

Where does that leave the ndiswrapper? Must it be accounted for? Removed?

I found the:

[http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)

A How-To for wireless noobs like me. Still, it talks about DHCP and I've seen that in the config of Gnome Wirelss-mgr., so I ask what needs doing if anybody has ever, ever done anything like this before?

---

### Post by kevdog on 2007-07-16
Madwifi in feisty is integrated, in earlier versions it is not (ie Dapper).  That means with just a few tweaks in feisy it will almost run out of the box.  In earlier version, the process of installing madwifi drivers are very similar to ndiswrapper.  Since either way do not require ndiswrapper, you really dont need to remove it.  I would only at a minimum remove the ndiswrapper line from /etc/modules to prevent it loading from startup.  Not that it would cause a problem, but why load a driver you dont need?

---

