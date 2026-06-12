---
title: "laptop fan running nonstop and hang on shutdown"
date: 2010-09-20
forum: New to Ubuntu
---

### Post by The_Pirate_King on 2010-09-20
I've recently had a problem with Ubuntu 10.04 freezing while it's shutting down on my Toshiba Satellite A305D.  It does this weird thing where the screen slowly bleaches to white; it almost looks like some kindof effect or screensaver.  Very bizarre. 

In addition to that the fan has been running nonstop (it starts, doesn't know when to shut off), and it seems to be getting unreasonably hot in comparison to my windows boot. 

Here's the 'sensors' output: 

> acpitz-virtual-0
Adapter: Virtual device
temp1:       +51.0°C  (crit = +105.0°C)                  

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +43.0°C                                    
Core0 Temp:  +40.0°C                                    
Core1 Temp:  +41.0°C                                    
Core1 Temp:  +37.0°Clspci:> 00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Device 7914
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
04:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
05:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
05:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
05:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
05:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
05:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)


top: 
> joe@Harold:~$ top

top - 01:10:54 up  8:28,  2 users,  load average: 1.45, 0.78, 0.69
Tasks: 159 total,   1 running, 158 sleeping,   0 stopped,   0 zombie
Cpu(s):  5.7%us,  2.3%sy,  0.0%ni, 91.1%id,  0.3%wa,  0.2%hi,  0.3%si,  0.0%st
Mem:   2965416k total,  1715596k used,  1249820k free,   125448k buffers
Swap:  3148700k total,        0k used,  3148700k free,  1198696k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
17224 joe       20   0 46584  13m  10m S    5  0.5   0:00.64 gnome-terminal     
 1124 root      20   0 54700  27m 7876 S    4  0.9  26:35.76 Xorg               
 1261 joe       20   0  450m 127m  29m S    4  4.4  33:02.88 firefox-bin        
 1213 joe       20   0 70824  25m 9268 S    1  0.9   6:37.38 compiz             
  927 root      20   0 24500 6856 1924 S    1  0.2   1:47.66 wicd               
 1030 root      20   0 12912 7220 3520 S    1  0.2   0:33.36 wicd-monitor       
   26 root      20   0     0    0    0 S    0  0.0   0:02.94 ata/0              
  732 messageb  20   0  3324 1628  760 S    0  0.1   1:17.90 dbus-daemon        
  785 root      20   0     0    0    0 S    0  0.0   4:01.46 phy0               
 1208 joe       20   0  159m 9.8m 7672 S    0  0.3   0:13.88 gnome-settings-    
17242 joe       20   0  2548 1204  904 R    0  0.0   0:00.04 top                
    1 root      20   0  2808 1612 1164 S    0  0.1   0:00.63 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT   0     0    0    0 S    0  0.0   0:00.04 migration/0        
    4 root      20   0     0    0    0 S    0  0.0   0:00.19 ksoftirqd/0        
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    9 root      20   0     0    0    0 S    0  0.0   0:00.54 events/0           




---

### Post by utnubuuser on 2010-09-20
Hello - If you post the output of > lspci -l people can have a look at what hardware you're running.

Also, post the output of > topor at least have a look at it to see what's using CPU cycles.

You can also get a look at what processes are running on your machine through System>>Administration>>System Monitor.

---

### Post by The_Pirate_King on 2010-09-20
How would I copy top's output to the clipboard?

---

### Post by k33bz on 2010-09-20
after you run the cmd just highlight with your cursor, right click, copy, then paste here.

---

### Post by The_Pirate_King on 2010-09-20
Okay, done.  Should be all the info you need...

---

### Post by The_Pirate_King on 2010-09-24
I really can't use ubuntu until I know how to solve this issue...

---

