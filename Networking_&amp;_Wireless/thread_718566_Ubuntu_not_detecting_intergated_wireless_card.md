---
title: "Ubuntu not detecting intergated wireless card"
date: 2008-03-08
forum: Networking &amp; Wireless
---

### Post by krayziereysta on 2008-03-08
hello, im just having biggest trouble using ubuntu. Well apparantly it doesnt detect my wireless card because i doesnt detect my wireless network. so then i tried connectting through my LAN wired and still no connection. im not really concern about using the LAN connection, just the wireless connection. i tried for hours trying to mess with ndiswrapper and downloading xp drivers with no avail. i have an HP DV6226us laptop...if anyone can help...PLZ!!!

---

### Post by lswest on 2008-03-08
post the output of ```
lspci
lshw -C network
iwconfig
ifconfig
```
(make sure you enter the -C capitalized, it means something different from -c)

---

### Post by krayziereysta on 2008-03-08
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03) 
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) 
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03) 
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02) 
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) 
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) 
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02) 
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02) 
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02) 
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02) 
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) 
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02) 
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) 
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02) 
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02) 
02:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01) 
05:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller 
05:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19) 
05:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a) 
05:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05) 
05:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff) 
05:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02) 

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03) 
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) 
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03) 
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02) 
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) 
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) 
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02) 
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02) 
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02) 
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02) 
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) 
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02) 
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) 
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02) 
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02) 
02:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01) 
05:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller 
05:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19) 
05:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a) 
05:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05) 
05:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff) 
05:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02) 

lo        no wireless extensions. 

eth0      no wireless extensions. 

wmaster0  no wireless extensions. 

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

eth0      Link encap:Ethernet  HWaddr 00:16:36:e7:3b:73  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:2212 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:2212 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:110600 (108.0 KB)  TX bytes:110600 (108.0 KB)

---

### Post by lswest on 2008-03-09
Here are some basic instructions and the drivers that i used to get my BCM94311MCG wlan mini-PCI (rev 02) working.  no, if there is no driver for the card, the light won't turn on (sometimes even with a driver it doesn't work) and the card won't be listed.  Attached are the drivers i use to get my broadcom card working.  First off extract the drivers from the archive to a folder of your choice, then do this:
```

cd [path to driver files]
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -m
sudo modprobe ndiswrapper
gksudo gedit /etc/modules and add "ndiswrapper" (without the quotes) to the end of the file
sudo reboot
```

See if these instructions work for you

---

### Post by krayziereysta on 2008-03-09
Nope it didnt work...maybe it conflicted with my previous attempt to set it up? is there a way to start fresh? seems like we have the same kind wireless adapter, were you able to work it right away?

---

### Post by lswest on 2008-03-11
What is the output of ```
ndiswrapper -l
``` it'll show us what drivers are installed.

---

