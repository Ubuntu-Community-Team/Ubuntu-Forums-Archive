---
title: "Problem installing touchpad driver on ubuntu 10.10"
date: 2011-02-12
forum: New to Ubuntu
---

### Post by thepetesimpson on 2011-02-12
Completely new to Linux. Installed ubuntu 10.10 on a second-hand gericom ego laptop. The previous OS (XP) was screwed so I have no evidence yet that the touchpad works nor indeed that it is synaptics.

Installed Synaptics Touchpad driver for X.Org server.
Installed ksynaptics package 0.2.4-2ubuntu2.

System>preferences>mouse has no touchpad tab. Applications>Other>Touchpad shows touchpad enabled and also "Synaptics Driver vers 0.14.4 is needed for this program to work. In case of malfunction check your Xorg.log"

The log shows no mention of a touchpad. Nor does /proc/bus/input/devices and /etc/X11/xorg.conf does not exist. synclient -l says "can't find synaptics properties"

Any help would be greatly appreciated.

---

### Post by thepetesimpson on 2011-02-14
OK maybe I should narrow things down. How can I tell if ubuntu can see touchpad installed?

---

### Post by 311005901 on 2011-02-14
Can you copy and paste the terminal output of "lspci" and "lsusb" into the forum's code format? Someone may be able to help you with that information.

---

### Post by thepetesimpson on 2011-02-14
"pete@pete-Ego:~$ lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 21)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 21)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
02:04.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
02:04.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 04)
02:09.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
pete@pete-Ego:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0204:6025 Chipsbank Microelectronics Co., Ltd CBM2080 Flash drive controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
pete@pete-Ego:~$ "

---

