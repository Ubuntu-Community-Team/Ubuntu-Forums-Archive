---
title: "Lost wireless after update."
date: 2008-12-16
forum: New to Ubuntu
---

### Post by optimusmedia on 2008-12-16
Today after an update, I lost wireless connection (having to work off a lan connection).  

I'm using Ubuntu 8.10. 
2.6.27-9-generic i686

Here's what updated/upgraded followed by ifconfig, and iwconfig results:

Commit Log for Tue Dec 16 09:11:43 2008

Upgraded the following packages:
bind9-host (1:9.5.0.dfsg.P2-1ubuntu2) to 1:9.5.0.dfsg.P2-1ubuntu3
console-setup (1.25ubuntu3) to 1.25ubuntu4
dnsutils (1:9.5.0.dfsg.P2-1ubuntu2) to 1:9.5.0.dfsg.P2-1ubuntu3
gnome-power-manager (2.24.0-0ubuntu8) to 2.24.0-0ubuntu8.1
jockey-common (0.5~beta3-0ubuntu6) to 0.5~beta3-0ubuntu6.1
jockey-gtk (0.5~beta3-0ubuntu6) to 0.5~beta3-0ubuntu6.1
libbind9-40 (1:9.5.0.dfsg.P2-1ubuntu2) to 1:9.5.0.dfsg.P2-1ubuntu3
libdns43 (1:9.5.0.dfsg.P2-1ubuntu2) to 1:9.5.0.dfsg.P2-1ubuntu3
libisc44 (1:9.5.0.dfsg.P2-1ubuntu2) to 1:9.5.0.dfsg.P2-1ubuntu3
libisccc40 (1:9.5.0.dfsg.P2-1ubuntu2) to 1:9.5.0.dfsg.P2-1ubuntu3
libisccfg40 (1:9.5.0.dfsg.P2-1ubuntu2) to 1:9.5.0.dfsg.P2-1ubuntu3
liblwres40 (1:9.5.0.dfsg.P2-1ubuntu2) to 1:9.5.0.dfsg.P2-1ubuntu3
libnm-glib0 (0.7~~svn20081018t105859-0ubuntu1) to 0.7~~svn20081018t105859-0ubuntu1.8.10.1
libnm-util0 (0.7~~svn20081018t105859-0ubuntu1) to 0.7~~svn20081018t105859-0ubuntu1.8.10.1
libpulse-browse0 (0.9.10-2ubuntu9) to 0.9.10-2ubuntu9.1
libpulse0 (0.9.10-2ubuntu9) to 0.9.10-2ubuntu9.1
libpulsecore5 (0.9.10-2ubuntu9) to 0.9.10-2ubuntu9.1
libshout3 (2.2.2-4) to 2.2.2-4ubuntu1
libx11-6 (2:1.1.5-2ubuntu1) to 2:1.1.5-2ubuntu1.1
libx11-data (2:1.1.5-2ubuntu1) to 2:1.1.5-2ubuntu1.1
libx11-xcb1 (2:1.1.5-2ubuntu1) to 2:1.1.5-2ubuntu1.1
network-manager (0.7~~svn20081018t105859-0ubuntu1) to 0.7~~svn20081018t105859-0ubuntu1.8.10.1
network-manager-gnome (0.7~~svn20081020t000444-0ubuntu1) to 0.7~~svn20081020t000444-0ubuntu1.8.10.1
ppp (2.4.4rel-10ubuntu2) to 2.4.4rel-10ubuntu2.8.10.1
pulseaudio-esound-compat (0.9.10-2ubuntu9) to 0.9.10-2ubuntu9.1
pulseaudio-module-gconf (0.9.10-2ubuntu9) to 0.9.10-2ubuntu9.1
pulseaudio-module-hal (0.9.10-2ubuntu9) to 0.9.10-2ubuntu9.1
system-cleaner (1.10.4-0ubuntu1) to 1.10.4-0ubuntu2
system-cleaner-gtk (1.10.4-0ubuntu1) to 1.10.4-0ubuntu2
ubufox (0.6-0ubuntu1) to 0.6-0ubuntu1.8.10.1
xkb-data (1.3-2ubuntu4.2) to 1.3-2ubuntu4.4


ifconfig results: 
eth0      Link encap:Ethernet  HWaddr 00:16:36:f0:ef:06  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fef0:ef06/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27690 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22715 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26066163 (26.0 MB)  TX bytes:3675022 (3.6 MB)
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:29878 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29878 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1292713 (1.2 MB)  TX bytes:1292713 (1.2 MB)

 iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
pan0      no wireless extensions.


Thank you in advance for any help.

---

### Post by Nxion on 2008-12-16
What is the wireless card you have?

---

### Post by optimusmedia on 2008-12-16
> **Nxion said:**
> What is the wireless card you have?

If I remember right it was a Broadcom 4310

But nothing's showing via a "lspci" command: 

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
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

---

### Post by optimusmedia on 2008-12-17
Next morning bump. 

Should I try the networking forum?

---

### Post by ohzopants on 2008-12-17
I lose wireless on my laptop after every kernel update.  I have to manually recompile the driver every time.

It doesn't appear that you updated your kernel, so this might not be related.

---

### Post by optimusmedia on 2008-12-17
> **ohzopants said:**
> I lose wireless on my laptop after every kernel update.  I have to manually recompile the driver every time.

It doesn't appear that you updated your kernel, so this might not be related.

I rebooted into 2.6.27-7 generic and that didn't help either.
Got a link where I can learn how to recompile?

---

### Post by ohzopants on 2008-12-17
My particular wifi chipset (Atheros AR5007EG) requires the HAL branch of madwifi, or ndiswrapper, but I've had better results with madwifi.

[http://madwifi-project.org/wiki/news/20080829/new-hal-release-for-atheros-hardware](http://madwifi-project.org/wiki/news/20080829/new-hal-release-for-atheros-hardware)

---

