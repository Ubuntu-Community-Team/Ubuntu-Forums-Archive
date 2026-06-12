---
title: "Is this behavior a kernel bug? 14.04 x86: Unable to activate (2nd) USB WiFi adapter"
date: 2014-05-22
forum: Networking &amp; Wireless
---

### Post by odoll on 2014-05-22
Hi,

is this a bug? A friend of mine has an old (Germany) Medion MD 8386 XL (special MSI MS-7091 Board) tower PC [1]. Since WXP gets no further fixes he wanted to give Linux - in this case Ubuntu - a try :-)

So he installed wither 12.04 and 14.04 onto it, but he couldn't get the build-in Wifi Ralink RT2500 USB activated [2] as the system always claimed it would have been deactivated by a hardware button.

However as this is an 802.11g only he used a 2nd 802.11n attached to one of the USB ports on the rear.

But though the 2nd devices should be usable (output of rfkill list looked similar to):

0: phy0: Wireless LAN
Soft blocked: no
Hard blocked: yes

1: phy1: Wireless LAN
Soft blocked: no
Hard blocked: no

both devices were grayed out and couldn't be actived.

The ultimate suolution was to unplug the "internal" device from USB port JUSB2 on the board.

After this the 2nd "external" device become availabe and could be used.

I'd have thought that even one device is (hard) blocked it should be possible to acitvate/use the other!?

Is this a bug, that if one device is blocked, it also blocks all others (of the same kind)?

If so, what's the best place to get that issue addressed?

[1]
[http://www.pcwelt.de/produkte/Technische-Daten-und-Testergebnisse-283848.html](http://www.pcwelt.de/produkte/Technische-Daten-und-Testergebnisse-283848.html)
[2] [http://forum.ubuntuusers.de/topic/wlan-medion-md8386/](http://forum.ubuntuusers.de/topic/wlan-medion-md8386/)

---

### Post by praseodym on 2014-05-22
Have you tried the wrapper?

[http://forum.ubuntuusers.de/topic/w-lan-karte-rt-2500-usb-funktioniert-nicht/2/#post-3664457](http://forum.ubuntuusers.de/topic/w-lan-karte-rt-2500-usb-funktioniert-nicht/2/#post-3664457)

---

### Post by praseodym on 2014-05-22
Or this one (also 64bit inside)

[http://forum.ubuntuusers.de/topic/wlan-unter-ubuntu-10-10-deaktiviert/2/#post-2779387](http://forum.ubuntuusers.de/topic/wlan-unter-ubuntu-10-10-deaktiviert/2/#post-2779387)

---

### Post by odoll on 2014-05-23
Thx, yes, we tried this, however this was not my point. My issue is, that the 2nd Wifi USB-Stick couldn't be used though reported as

1: phy1: Wireless LAN
Soft blocked: **[COLOR=#008000]no[/COLOR]**
Hard blocked: **[COLOR=#008000]no[/COLOR]**

unless we unplugged the 1st, which was in the state

0: phy0: Wireless LAN
Soft blocked: **[COLOR=#008000]no[/COLOR]**
Hard blocked: [COLOR=#ff0000]**yes**[/COLOR]

After the 1st was physically removed the 2nd worked like a charm out of the box without to have to install any (alternative) drivers.

---

### Post by praseodym on 2014-05-23
From today there is a patched version of acerhk available:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget media.cdn.ubuntu-de.org/forum/attachments/07/20/6674857-acerhk-0.5.6_dkms.tar.gz
sudo tar xvf 6674857-acerhk-0.5.6_dkms.tar.gz -C /usr/src
sudo dkms add -m acerhk -v 0.5.6
sudo dkms build -m acerhk -v 0.5.6
sudo dkms install -m acerhk -v 0.5.6 

```

---

