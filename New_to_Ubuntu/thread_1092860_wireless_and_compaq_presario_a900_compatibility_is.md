---
title: "wireless and compaq presario a900 compatibility issues"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by littlebanana on 2009-03-10
whenever I boot up into ubuntu I have to deactivate the hardware and reactivate before I can access my wireless network.
Here is the output of lspci:
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

So what I'm wondering is why this is happening and why I don't see madwifi in synaptic (I've been away for a bit)
Also, I remember reading recently about ath5k.  When I go to use wlanconfig or any other commands relating to the atheros chipset in the wireless card I don't even see the interface until I use airmon-ng (part of aircrack) when I do this command
airmon-ng stop wlan0
then I get something else concerning mon0
does anyone know of any workarounds for this? -Thanks

---

### Post by Newfoundlander on 2009-04-26
I have the same laptop and have been tried every wireless tip on this forum for the past year with no success.  NDISwrapper is the only thing that partly worked but it would randomly freeze up the laptop so I had to disable it.

---

### Post by lkraemer on 2009-04-29
banana,
You shouldn't have any problem getting the MadWifi software downloaded
and installed.  I have it working on my Comapq Presario CQ50-139NR.

There are guides for 8.04, 8.10 etc.

[http://madberry.org/](http://madberry.org/)
[http://madberry.org/2008/08/how-to-get-atheros-ar242x-wireless-to-work-2/](http://madberry.org/2008/08/how-to-get-atheros-ar242x-wireless-to-work-2/)

Update AR242x:
[http://ubuntuforums.org/showthread.php?t=1142199](http://ubuntuforums.org/showthread.php?t=1142199)

lkraemer

---

