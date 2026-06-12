---
title: "Wireless troubles for a brand new user"
date: 2006-07-30
forum: Networking &amp; Wireless
---

### Post by Rickshaw Driver on 2006-07-30
I took the time to install Ubuntu for the first time last night on my desktop.  I recently had a raid failure and after hearing my friend go on and on about how much he loved it, I decided to try.  I am having a bit of trouble getting the network to run on this clean install.  I have done some searching, but have not felt comfortable enough to know that the help given to another user would apply the same in my situation.  I don't want to screw anything up (even though a fresh install is a breeze so far) on the system.  The details are:

Wireless Card: Linksys WMP54G
Details in device manager (let me know if more is needed from the PCI or Advanced tab):
[INDENT]vendor: Broadcom Corporation
Device: BCM4318 (Airforce One 54g) 802.11g
Status: Status
Bus Type: PCI
Device Type: Unknown
Capabilities: Unknown[/INDENT]

Information in etc/network/interface file:
[INDENT]auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid myssidname
wireless-key mywirelesskey

autoeth2
iface eth2 inet dhcp

autoath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp[/INDENT]

Router: Linksys WRT54GL

As you can see I have WEP set for security at 128 bit encryption. I have gone into the bios and disabled the onboard card and gone into the graphic networking interface and enabled the wireless card.  When I enable it, it takes a good while and I still get no access.  Also, when I reboot after activating it, it defaults back to disabled. Any help to get this going would be greatly appreciated.

---

### Post by psycosmyth on 2006-07-30
Just a tip since I'm learning this...search the forums for that model, I have seen it pop up several times. I don't remember the solution though, sorry.

---

### Post by Rickshaw Driver on 2006-07-31
Thanks for the reply.  I have seen many of them, just am worried that I will screw something up.  Oh well, guess it won't hurt anything if I have to reinstall.  Can someone at least let me know if this walkthrough would be relevent to my system?

[http://www.ubuntuforums.org/showthread.php?t=201633](http://www.ubuntuforums.org/showthread.php?t=201633)

---

### Post by cheapos on 2006-07-31
i still can't get on wireless anyway, but try reading thru this.. it may help...

[http://ubuntuforums.org/showthread.php?t=185841](http://ubuntuforums.org/showthread.php?t=185841)

apparently my wireless card works juz fine... but my router dun??
:sad:

---

### Post by MarkSheely on 2006-07-31
For the BCM4318 cards, this is the method you want to use:

[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

It seems to work for most people.  You may end up having to do a fresh installation to "undo" the changes you have already made.

Good luck, let me know if you run into more problems.

--Mark
[email]marksheely@gmail.com[/email]

---

### Post by Rickshaw Driver on 2006-07-31
Thank you MarkSheely, I will try this when I get home and update to let you know how it goes.

---

