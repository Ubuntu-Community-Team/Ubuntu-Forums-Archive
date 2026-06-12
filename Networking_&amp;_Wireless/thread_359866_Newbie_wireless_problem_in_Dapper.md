---
title: "Newbie wireless problem in Dapper"
date: 2007-02-12
forum: Networking &amp; Wireless
---

### Post by sammy.j on 2007-02-12
Hi guys, 

After playing about with ububtu (dapper) on the live CD I got the wireless to work after I disabled WEP. I love the OS so installed the full thing and it's great, but I can't get wireless internet to work properly any more. It will connect at first but its very slow, and the connection soon dies. I can get it to work again by disabling then enabling the wireless connection but that's obviously not ideal.

Heres what I get when I type lspci in console:

sam@sam-laptop:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller ( rev 03)
0000:00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4 -M) USB UHCI Controller #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4 -M) USB UHCI Controller #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4 -M) USB UHCI Controller #3 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EH CI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
0000:00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridg e (rev 01)
0000:00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller ( rev 01)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH 4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
0000:00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97  Modem Controller (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 Lf [Fir eGL 9000] (rev 01)
0000:02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5702X Gigabi t Ethernet (rev 02)
0000:02:01.0 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (re v 20)
0000:02:01.1 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (re v 20)
0000:02:03.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini  PCI Adapter (rev 04)

Its a Dell Latitude D600 Laptop, 512 Ram, 1.4 Ghz Centrino. I've still got XP partitioned on 20GB of the HD and Ubuntu on the other 20.

Any help would be very much appreciated.

---

### Post by sumgi on 2007-02-12
This is a good [guide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide").

Also tail your system logs

tail -f /var/log/messages

---

### Post by sammy.j on 2007-02-13
Awesome it works great now, had no problems all day. Thanks for guide.

---

