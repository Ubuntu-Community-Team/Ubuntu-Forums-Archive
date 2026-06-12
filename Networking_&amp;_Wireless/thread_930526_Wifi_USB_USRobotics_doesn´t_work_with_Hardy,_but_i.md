---
title: "Wifi USB USRobotics doesn´t work with Hardy, but it does with Intrepid, please help"
date: 2008-09-26
forum: Networking &amp; Wireless
---

### Post by viper77 on 2008-09-26
Was anyone able to make this Wifi USB dongle work with Hardy?
I already tried everything on the sticky Broadcom thread but no luck.
It worked automatically on Intrepid but i had to go back to Hardy for the time being because of fglrx (Ati driver) that is not working yet.
If it worked with Intrepid i guess it should work with these workarounds on Hardy as well, if there's no way then i guess that ndiswrapper will be my only choice for the moment...

Chipset: 4320SKBG
Model: USRobotics WIfi MaxG USB adapter (USR5421)

[IMG]http://www.ciudadwireless.com/images/USR805421CW.jpg[/IMG]

uname -a: Linux ubuntu 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686 GNU/Linux

lspci -nn:
00:00.0 Host bridge [0600]: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] [1106:0305] (rev 03)
00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP] [1106:8305]
00:07.0 ISA bridge [0601]: VIA Technologies, Inc. VT82C686 [Apollo Super South] [1106:0686] (rev 40)
00:07.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 06)
00:07.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 1a)
00:07.3 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 1a)
00:07.4 Bridge [0680]: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] [1106:3057] (rev 40)
00:07.5 Multimedia audio controller [0401]: VIA Technologies, Inc. VT82C686 AC97 Audio Controller [1106:3058] (rev 50)
00:0e.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV350 AS [Radeon 9550] [1002:4153]
01:00.1 Display controller [0380]: ATI Technologies Inc RV350 AS [Radeon 9550] (Secondary) [1002:4173]

dpkg -l | grep linux-restricted:
ii linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45 Non-free Linux 2.6.24 modules on x86/x86_64
ii linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.50 Non-free Linux 2.6.24 modules on x86/x86_64
ii linux-restricted-modules-common 2.6.24.14-21.50 Non-free Linux 2.6.24 modules helper script
ii linux-restricted-modules-generic 2.6.24.21.23 Restricted Linux modules for generic kernels

lsusb: (just in case)
Bus 001 Device 002: ID 0baf:011b U.S. Robotics

Any help or feedback will be appreciated.
Thanks!
Sebastian

---

### Post by viper77 on 2008-09-29
Sorry but have to bump it... ](*,)

---

