---
title: "Broadcom card is present, but not totally..."
date: 2007-12-29
forum: Networking &amp; Wireless
---

### Post by ososxe on 2007-12-29
Hello everyone, and happy new year!
I have a big problem (for me) with the wifi on my Acer laptop. The card is a Broadcom 4318 and it does not work. It used to work with Xubuntu Gutsy, WPA even, until some weeks ago it stopped showing up, and since I had to format and reinstall this computer, I let it go until today. 
I did a clean install of Kubuntu Gutsy and the restricted drivers manager detects it and install the driver, and the card works right after: wireless led lit up, it appears under network manager, I can configure, it even gets an IP adress.... but is not connected to any wireless network, the Netwrok Manager's tray icon does not detect any wifi network. And after I reboot the laptop the wireless led does not lit and the Broadcom does not show up on the NEtwork Manager tray icon.
I tried to uninstall and reinstall the restricted drivers, same result.
I tried what is suggested on this how to:
[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)
And it does not work :( I tried WICD as suggested on that thread and same result..
This is what ifconfig tells me:
oso@acerlaptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:10:C3:E9
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fe10:c3e9/64 Scope:Link
          UP DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Metric:1
          RX packets:35726 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23586 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000
          RX bytes:45225259 (43.1 MB)  TX bytes:2453724 (2.3 MB)
          Interrupt:16 Base address:0x1800

lo        Link encap:Bucle local
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK CORRIENDO  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

The attached screenshot is what the restricted drivers manager shows up.

Any suggestions?
Thanks!

---

### Post by ososxe on 2007-12-29
This is the exist of my lscpi:

oso@acerlaptop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

---

### Post by ososxe on 2007-12-29
This is what I have on my /etc/network/interfaces

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0


iface eth1 inet dhcp

auto eth1

iface eth0 inet dhcp

auto eth0


Any suggestions¿?

---

### Post by ososxe on 2007-12-29
This is what it is on my /etc/modules

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
ndiswrapper

---

### Post by cdtech on 2007-12-30
This is the procedure I used to get my wifi to work. I have the Broadcom BCM94311MCG wlan mini-PCI. It works great now. I hope this helps you.

[[COLOR="DarkRed"].:: Broadcom setup ::.[/COLOR]]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29")

---

### Post by ososxe on 2008-01-05
Thanks, cdtech!
I follow your link to this other one: [BCM43xx on Feisty]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff") that it's simpler, but the cleaning up instructions on your link helped me to start with a fresh install, and now is working and I'm posting from my WPA encrypted network, thanks!!

---

### Post by cdtech on 2008-01-07
Awesome, glad you got it working.....

---

