---
title: "TL-WN620G Drivers"
date: 2008-01-10
forum: Networking &amp; Wireless
---

### Post by Salazar420 on 2008-01-10
Does anyone know of any easier or other method of attaining and installing the drivers for this card? I've attempted to follow this tutorial: [https://help.ubuntu.com/community/WifiDocs/Device/TP-Link_TL-WN620G_(ndiswrapper)]("https://help.ubuntu.com/community/WifiDocs/Device/TP-Link_TL-WN620G_(ndiswrapper)") but didn't get it to work properly. I am, however, using Ubuntu 7.10 Gutsy, whereas the tutorial is based on Dapper. 'lsusb' reveals that the device is present:> xenouser@XeNoToP:~$ lsusb
Bus 004 Device 002: ID 0cf3:0002 Atheros Communications, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000   as you can see; however, 'ndiswrapper -l shows that the device is not detected: > athfmwdl : driver installed
        device (0CF3:0002) present
tl-wn620g : driver installed
 This does, fortunately, show that I've successfully managed to install the drivers. The actual card is in, yet it only blinks red for a split second when I first insert the card. After that, there is no activity on the indicator-light. Could someone help me out with this? Has anybody had more luck than myself? I bought the card because it appears to be quality, and I'd rather not have to run windows xp on my desktop in order to put it to use. Don't do it for me; do it for the masses

---

### Post by driftingprogrammer on 2008-02-23
I have a 64 bit AMD processor and Ubuntu 7.10.

I download ndiswrapper from sourceforgenet as suggested by people (instead of using the apt-get), I downloaded the stable version 1.52
- install ndiswrapper

i download the latest drivers for the TP-Link usb wifi modem and follow the steps
- install the driver using ndiswrapper -i

now i am able to view my drivers (net553 and athfmwdl installed in that order but listed in the opposite order) on firing ndiswrapper -l and they are mapped to the device id also printed on firing command lsusb

now i type modprobe ndiswrapper

on firing iwconfig i do not see wifi0 instead i see

> lo        no wireless extensions.

eth0      no wireless extensions.

In the logs i see an error - 


> ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
Feb 24 00:51:10 curtain kernel: [ 8569.780266] ndiswrapper (load_sys_files:210): couldn't prepare driver 'net5523'
Feb 24 00:51:10 curtain loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver net5523 
Feb 24 00:51:10 curtain kernel: [ 8569.781424] ndiswrapper (load_wrap_driver:112): couldn't load driver net5523; check system log for messages from 'loadndisdriver'
Feb 24 00:51:10 curtain kernel: [ 8569.781586] usbcore: registered new interface driver ndiswrapper

But there is no saperate 64 bit driver available for this device so what is the solution. Please help i have spent the entire day on this and have tried everything i could get my hands on.
The output on giving command lspci is - 
> 
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51G [GeForce 6100] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)


tia.

---

### Post by bagong on 2008-02-23
hi there, i'm xubuntu user and i use tl-wn650g and it use atheros chip too.. but i don't use ndiswrapper as the driver, i use madwifi driver and it work fine since a year ago (i'm a new linux user so i try many linux distro and currently i use xubuntu 7.10 and the driver from madwifi always works ) you can try that if you want.. you can use synaptic and search for madwifi driver or you can download the source code at [www.madwifi.org](www.madwifi.org).   i hope that help..

---

### Post by driftingprogrammer on 2008-02-23
My device connects through USB and not PCMCIA so on madwifi.org there is no driver for my device i chacked there was 1 available for 610, 630, 650 but nor 620 :(

---

### Post by pienose on 2008-03-09
I have the same exacatlly the same problem as salazar...is there any way to get this thing to work? I have also tryed installing the program that come with the stick through wine but that did not help...

---

### Post by driftingprogrammer on 2008-03-10
actually i faced the same problem woth 32 bit ubuntu also...problem seems to persist :(

---

### Post by pienose on 2008-03-10
hellow? is ther any solution to this! I really don't want to go back to shitty old windows :(

---

### Post by driftingprogrammer on 2008-03-10
no there is no solution i spent 2 days and have decided to throw the device and buy a wireless bridge.

---

### Post by pienose on 2008-03-12
oh well, i guess it's by by 'buntu...

---

### Post by driftingprogrammer on 2008-03-12
You should seriously think about throwing the devise, it is no good and by something that comes with linux support

---

### Post by pienose on 2008-03-13
I'm afraid that's not a choise. I didn't buy it, my dad did and he dosn't really get linux...

---

