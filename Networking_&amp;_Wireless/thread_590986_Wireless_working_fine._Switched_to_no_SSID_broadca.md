---
title: "Wireless working fine. Switched to no SSID broadcast and now I'm lost"
date: 2007-10-25
forum: Networking &amp; Wireless
---

### Post by RipRapRob on 2007-10-25
Kubuntu 7.10 (This version is awesome - Microsoft should be very afraid!)

I took my laptop to work, and tried connecting to our Wireless network.

Success! Even easier and faster than Windows. Yeah! :lolflag:

But...

Today the access-points SSID broadcast was turned off, and the password (ASCII) changed, and I I haven't been able to connect since :(

I've tried configuring manually, but as a result, the network icon in my System Tray doesn't display no form of wireless anymore.

I can still see my wlan0 in the KDE Control Module, where it is listed as Enabled, but showing a wrong IP Address (=169.254.6.204, it should be in the 192.168.x.x. range))

1) How do I connect to a WLAN not broadcasting SSID in Kubuntu 7.10?

2) How do I 'revert' to the default network settings in Kubuntu (like they were when I installed 7.10.

Any help appreciated

Sorry about spelling and grammatical errors: English is not my native language.

Thanks

/Rob

---

### Post by staticsage on 2007-10-25
There is a bug open on the issue of not being able to connect to a network without a broadcasted SSID:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/50214](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/50214)

A patch has been made, but it only fixed the issues for some people. I can try to help you with it based on what I read in the bug thread, but I'll need some more information.


What wireless chipset are you using?

Open a terminal and type ```
lspci -v
```
Your wireless card will be listed as either Ethernet controllers or Network controller. Please paste that part of the output here.

Also, did Ubuntu auto detect the drivers?


As for your second question, I'm not familiar with the KDE environment, so someone else will have to tell you how to properly restore your settings (which package should he dpkg-reconfigure?).

---

### Post by AlanB66 on 2008-03-26
Hi.

I'm having the same issue. After finally getting this ath_pci wireless working ... with a lot of pain ... I can connect only if my Linksys is in broadcast mode.

Here is my output to lspci -v:
[INDENT]03:00.0 Ethernet controller: Atheros Communications, Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Hewlett-Packard Company Unknown device 137a
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f6000000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>[/INDENT]

I've locked down my router with WEP and Restricted MAC Addresses, so it's not the end of the World if I must broadcast. I'd just rather not ;-)

Thanks!

p.s.: For reference, here is the hell I went thru to get ath_pci to work on my Compaq F750US (F700): [http://ubuntuforums.org/showthread.php?t=687833&page=4](http://ubuntuforums.org/showthread.php?t=687833&page=4)

---

