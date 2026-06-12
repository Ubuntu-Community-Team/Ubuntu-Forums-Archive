---
title: "Ubuntu 10.04.1 help needed please!"
date: 2010-12-04
forum: New to Ubuntu
---

### Post by geminimoon66 on 2010-12-04
I'll try to keep this short.  Burned Ubuntu 10.04 a week ago to DVD and installed it flawlessly on 2 laptops.
Couple of days ago went to install it on old desktop(Compaq EVO D510 SFF) and realized it only had CD player. So burned newest version Ubuntu 10.04.1 to CD and it installed just fine.  Problems are:

-No panel bars at top or bottom after boot up. For that I tried this: 
[B][I]gconftool - -recursive-unset /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-panel[/I][/B]
It worked, but only until I rebooted again, so I am lost here now.[LEFT]

-No wireless internet connection.  My Wireless card is a Zyxel G-302 and I have the Windows drivers but don't understand how to install them.


-No sound.


I think that's everything that's not working.  I have read lots of threads and stuff on the wireless problem and the no panel bars, but not found a fix.  I have seen a lot of requests for other info so I have included results from lspci and iwconfig below.  



Let me know if more info is needed and I will post as soon as I can!  Thanks in advance for any help with these issues!!!!!

[/LEFT]
asn2010@asn2010-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82815 Chipset Graphics Controller (CGC) (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 02)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC '97 Audio Controller (rev 02)
02:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 01)
02:0a.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
---------------------------------------
asn2010@asn2010-desktop:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

[LEFT]

Thanks again folks!!
[/LEFT]

---

### Post by conradin on 2010-12-05
I've got stuff like that and typically its been some issue with the cd. While you can mess with it and probably get it to work eventually, I would recommend doing another fresh install with a fresh download of the OS, and checking the MD5 / using the "check this disk for errors" before installing next time.

---

