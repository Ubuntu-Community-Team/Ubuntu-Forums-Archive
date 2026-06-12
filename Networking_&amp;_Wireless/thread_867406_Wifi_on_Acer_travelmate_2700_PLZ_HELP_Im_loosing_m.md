---
title: "Wifi on Acer travelmate 2700 PLZ HELP Im loosing my insanity!"
date: 2008-07-22
forum: Networking &amp; Wireless
---

### Post by zezito555 on 2008-07-22
Hi to all
i followed every post of this matter i found, and didnt made my wifi card work!!!
i installed ndiwrapper, used "ndiswrapper -i neti2220.inf" and when using "ndiswrapper -l" it shows "neti2220 : driver installed".
when i type "iwconfig", doesnt have the wifi card, only eth0!
this is lspci output:
00:00.0 Host bridge: ATI Technologies Inc Radeon 9100 IGP Host Bridge (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc Radeon 9100 IGP AGP Bridge
00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01)
00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01)
00:13.2 USB Controller: ATI Technologies Inc EHCI USB Controller (rev 01)
00:14.0 SMBus: ATI Technologies Inc SMBus (rev 1a)
00:14.1 IDE interface: ATI Technologies Inc Dual Channel Bus Master PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc Unknown device 434c
00:14.4 PCI bridge: ATI Technologies Inc IXP200 3COM 3C920B Ethernet Controller
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller (rev 01)
00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01)
01:05.0 VGA compatible controller: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]
02:02.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)

the ndiswrapper -l output:
neti2220 : driver installed
	device (17FE:2220) present

the iwconfig output:
lo        no wireless extensions.

eth0      no wireless extensions.


Its my 1st time attempt to migrate to linux, and i really wanted not to go back to winXP(those robbers!)

Plz help me guys!! Plz!
Thanks in advance!!

---

### Post by sputnikkk on 2008-07-22
What s the output from :

```
lshw -C network
```

Not sure if it will work for you, but my troubles for wireless networking were solved by Wicd application.  A replcement for the Ubunto 8.04 Network Manager application


[www.wicd.net](www.wicd.net)

[http://www.wicd.net/download.php](http://www.wicd.net/download.php)

---

### Post by calraith on 2008-07-22
[What would Jesus Google?](http://ubuntuforums.org/showthread.php?t=89476)

---

### Post by lmsm76 on 2011-01-20
Hi, could you solve your problem?
I'm currently trying to get my wireless working on my old TravelMate 2700
 
Any comments will be appreciated.
 
Thanks!

---

### Post by david-emm on 2011-01-25
Hi, I'm running meerkat gnome on a Acer Travelmate 2200 (2700 motherboard). You need to install ndiswrapper and ndisgtk - they are in the Synaptic package manager. If you also have WinXP on your harddisk open up ndisgtk (System-Administration-Windows Wireless Drivers) and Install New Driver. Search in your Windows directory for the 802BG directory, open it and select the neti2220.inf file. After a short pause you should see neti2220 Hardware present:Yes message come up. Network Manager should now see all of the wifi broadcasts in your immediate area including (hopefully) yours. Suggest you let your wifi router set the net address for you.

If you don't have a dual boot system you will need to copy the windows drivers into a directory on your linux system. I keep mine in my home folder as 80211BG. You can get the drivers from the Acer software download sites.

The drivers I downloaded have a full directory for with files for XP and W2k but you only need these three from the XP directory.
i2220ntx.cat
i2220ntx.sys
neti2220.inf

Don't use *nti* files only the *ntx* ones.
Hope this helps you.

---

