---
title: "Realtek RTL8187 card won't work"
date: 2008-08-31
forum: Networking &amp; Wireless
---

### Post by brahle on 2008-08-31
Hi! 
I just got a new laptop and installed new Ubuntu using Wubi yesterday evening. I used wireless without a problem on both Windows Vista and XP. However, it doesn't work at all in Linux. OS doesn't seem to recognise wireless card at all. I have Linux kernel version 2.6.24-19-generic, and my wireless network card is RTL8187b. 
I tried to follow steps from various forums and even tried downloading and compiling drivers myself. They, however, report errors and thus I cannot use them. 
Can somebody help me, please? 
PS I am relatively new to Linux, so please don't be to technical... :)

---

### Post by The Dork Lord on 2008-08-31
Hi there, having the same problem myself, I found [http://ubuntuforums.org/showthread.php?t=792092](http://ubuntuforums.org/showthread.php?t=792092) very handy. The only snag I've found is that WEP isn't very well supported.

---

### Post by brahle on 2008-08-31
Well, it doesn't work for me :(. I did all the steps from 1. to 5. (i just modified PID to suit my card), but all later steps cause problems. Network Settings do not allow me to add a wireless connection. So I try to use wifi-radar, which won't work either.

---

### Post by sauronsmatrix on 2008-08-31
Hey there, I have a tutorial on ndiswrapper. You can try it out, except on the driver step, replace the driver with your step. Just be sure to click on the "wireless" section. Let me know if it helps!

[http://avindra.com/?landing=hpubuntu#wireless](http://avindra.com/?landing=hpubuntu#wireless)

---

### Post by brahle on 2008-08-31
@sauronsmatrix: No, it doesn't help me. But thanks for the effort!

I forgot to add this detail:
This is what I get when I run 'lsusb':
```
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0bda:8189 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 0402:5606 ALi Corp. 
Bus 001 Device 001: ID 0000:0000
```
And this is what I get when I run 'lspci':
```
00:00.0 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. P4M900 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. P4M900 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. P4M900 PCI to PCI Bridge Controller (rev 80)
00:03.0 PCI bridge: VIA Technologies, Inc. P4M900 PCI to PCI Bridge Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M G (rev a1)
05:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
06:04.0 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller
06:04.1 SD Host controller: ENE Technology Inc ENE PCI SmartMedia / xD Card Reader Controller
06:04.3 FLASH memory: ENE Technology Inc ENE PCI Secure Digital / MMC Card Reader Controller
```

---

