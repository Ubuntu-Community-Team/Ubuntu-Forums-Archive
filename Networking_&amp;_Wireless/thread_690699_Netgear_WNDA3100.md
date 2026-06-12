---
title: "Netgear WNDA3100"
date: 2008-02-07
forum: Networking &amp; Wireless
---

### Post by jwmcgee1 on 2008-02-07
Has anyone had any luck getting the Netgear WNDA3100 USB adapter?  My system doesn't even know it has anything attached to the USB port.

I am running Ubuntu 7.10.

---

### Post by DataKnutten on 2008-04-30
I'm thinking of buying this adapter but I cannot find any info about drivers for Linux.

I think your system "knows" it but you don't have a driver that supports it. I saw your post here:
[http://ubuntuforums.org/showthread.php?t=690796](http://ubuntuforums.org/showthread.php?t=690796)
where I can see that your "lsusb" reports:
"Bus 005 Device 004: ID 0846:9010 NetGear, Inc."

I search Google on "0846:9010" and found this:
[http://listing.driveragent.com/usb/0846/9010](http://listing.driveragent.com/usb/0846/9010)
where it says its based on a Atheros chipset.
The INF-file [http://driveragent.com/archive/15863/2-1-1](http://driveragent.com/archive/15863/2-1-1) give some hints too. Here you can see that the chipset is the Atheros AR9170 and should support Linux:
[http://www.atheros.com/pt/AR9001U.htm](http://www.atheros.com/pt/AR9001U.htm)
This chipset is also in the following products:
D-Link DWA-160 Xtreme N Duo USB Adapter(rev.A)
Atheros 11n Wireless Network Adapter
ZCOM NB 802.11n ABG Wireless LAN USB Adapter(UB82)

You might try help here:
[https://help.ubuntu.com/community/Wi...eShootingGuide](https://help.ubuntu.com/community/Wi...eShootingGuide)

Mor driver info on this, anyone?

---

### Post by viper19 on 2008-06-11
Haven't tried on Ubuntu, but I got the WNDA3100 to work on my Debian system without much trouble.  I'm running 2.6.23 and built ndiswrapper-1.53 from sources.  I installed the drivers from the CD on an XP machine, copied them over and loaded them into ndiswrapper.

Here's the start of the .inf file, which happened to be named oem15.inf on my system:

;+-----------------------------------------------------------------------+
;| Device name    : Atheros USB 802.11n Wireless LAN card.               |
;| Platform       : Microsoft Windows 98 / Me / 2000 / XP                |
;| Host interface : USB 

The drivers are: wnda31.sys, wsimd.sys, and arusb_xp.sys.

Here's some dmesg output:

usb 2-1: new high speed USB device using ehci_hcd and address 4
usb 2-1: configuration #1 chosen from 1 choice
ndiswrapper version 1.53 loaded (smp=no, preempt=no)
usb 2-1: reset high speed USB device using ehci_hcd and address 4
ndiswrapper: driver oem15 (,01/17/2008,3.0.0.95) loaded
wlan0: ethernet device 00:1e:2a:d9:eb:80 using NDIS driver: oem15, version: 0x40700, NDIS version: 0x501, vendor: 'Atheros OTUS Wireless Network Adapter', 0846:9010.F.conf
wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
usbcore: registered new interface driver ndiswrapper

I'm using it with a 802.11g wap and wpa-psk.  I briefly ran into what seems to be a common problem with the wap's dns cache returning 1.0.0.0, so I manually removed that entry from etc/resolv.conf.  After that it has been smooth sailing.

Hope that helps.

---

### Post by Al-Saeed on 2008-07-09
Has anyone got this working? I'm really stuck trying to get this to work. Does anyone know how? Thanks.

Kind regards

---

### Post by mr. juicy on 2008-07-10
I'm having trouble myself.  I was able to find the .inf file after some work.  Mine was called oem40.inf.  I copied it, along with the driver files listed by viper19 into a directory, and tried to install it with ndiswraper.  It gave me an error, saying that it was an invalid driver.

Next, I tried running the driver installer under wine to see what came out, and there was a different .inf file called arusb_xp.inf.  I copied it to the same directory as the others and tried that as an install, but i got the same error.  I don't really know how to proceed from here.  Any tips?

---

### Post by Al-Saeed on 2008-07-10
Where are did you find the .inf file? The only one I can see is the one in the CD called autorun.inf but that's useless.

Kind regards

---

### Post by mr. juicy on 2008-07-10
well, I haven't gotten it to work yet, but as for the .inf file--after you run the windows installer one is created in the windows\inf\ directory.  Windows creates them starting with oem1.inf and on up.  the other guy had oem15.inf, and mine was oem40.inf.  I found it by using the search tool in Ubuntu, and set as the parameters *.inf, and a secondary parameter "file contains wnda31.sys", which I got from the driver info screen in windows device manager.

The second .inf I found with wine, because there was only one .inf in the windows\inf folder.

---

### Post by Al-Saeed on 2008-07-10
oh, I see. Thanks.

---

