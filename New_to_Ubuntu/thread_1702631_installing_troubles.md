---
title: "installing troubles"
date: 2011-03-08
forum: New to Ubuntu
---

### Post by josephmills on 2011-03-08
So A friend asked me to install ubnutu on his computer. I accepted but am having some troubles installing. I think that I might have a bad cd. On the other hand I have used that cd a couple of times and it has worked out just fine. But when I put the cd into my friends computer I can run it as a live cd but when trying to install I get a error at the end of the installation. saying that my cd/dvd drive might be dirty or that the cd image is broken.  I cleaners t o computer out head to toe and cleaned the lens on the disk drive. tried to re-install with the same cd and got the same error. so then I burned a new   image tp a cd (ubuntu 10.10 desktop). and got the same error, and now am out I of cd's   the md5sum was good on the disk so I know that it is a good disk. I then thought that it could be a hardware issue so I tryed to install a different operating system(bt4 r2) and it worked out of the box. ZHere are some spec about this machine       
(code)
 lspci  00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge 00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge 00:08.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03) 00:0a.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03) 00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80) 00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) 00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) 00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) 00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) 00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) 00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) 00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) 00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South] 00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60) 00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80) 00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78) 01:00.0 VGA compatible controller: VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] (rev 01)  (/code)    (code)   cat /proc/cpuinfo processor       : 0 vendor_id       : AuthenticAMD cpu family      : 6 model           : 10 model name      : AMD Athlon(tm) XP 3200+ stepping        : 0 cpu MHz         : 2200.515 cache size      : 512 KB fdiv_bug        : no hlt_bug         : no f00f_bug        : no coma_bug        : no fpu             : yes fpu_exception   : yes cpuid level     : 1 wp              : yes flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up bogomips        : 4402.40 clflush size    : 32 cache_alignment : 32 address sizes   : 34 bits physical, 32 bits virtual power management: ts  
(/code)   
(code)    
free -m              total       used       free     shared    buffers     cached Mem:           688        346        341          0         14        154 -/+ buffers/cache:        178        510 Swap:         2015          0       2015  
(/code)    
I should also add that my friends BIOs can not run via usb  thanks for taking the time to read this.

---

### Post by mastablasta on 2011-03-08
is the install unsuccesfull after the message? 
 
is Wubi install possible?
 
Is it possible to bring your own DVD drive? Did you check the cables on the drive that they are attached ok and also that the cables are ok. kind of had a similar issue with HDD. turned out it was bad SATA cables.

---

### Post by josephmills on 2011-03-08
> **mastablasta said:**
> is the install unsuccesfull after the message? 
 

Yes, It is unsuccesfull every time.



> 
is Wubi install possible?
 looking into to that,Thanks no this will not work as I deleted the windoz partition during the install of ubuntu  

> 
Is it possible to bring your own DVD drive? Did you check the cables on the drive that they are attached ok and also that the cables are ok. kind of had a similar issue with HDD. turned out it was bad SATA cables.[/QUOTE]


Sorry to hear about your cables but mine are fine. I did a full voltage diagnostics  and  the power is there. I also tries to put the dvd drive into a different computer and it worked great.

---

