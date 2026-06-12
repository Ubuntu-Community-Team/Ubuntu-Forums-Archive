---
title: "I can't set up a wireless network!"
date: 2008-06-26
forum: Networking &amp; Wireless
---

### Post by president rich on 2008-06-26
I just installed Ubuntu 8.04 on my Dell XPS 1530 that has a Dell Wireless 1395 802.11g Mini Card. My wireless router is a Linksys WRT54G.

Please help me enable wireless internet!

---

### Post by president rich on 2008-06-27
bump

---

### Post by president rich on 2008-06-28
bump

---

### Post by cwbar_1 on 2008-06-28
Post the results of lspci,  (Applications> Accessories> Terminal)

---

### Post by president rich on 2008-06-28
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1)
03:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)

---

### Post by cwbar_1 on 2008-06-28
Do you still have Vista or XP installed on this laptop?

---

### Post by president rich on 2008-06-28
> **cwbar_1 said:**
> Do you still have Vista or XP installed on this laptop?

Vista.

---

### Post by cwbar_1 on 2008-06-28
OK.  Go to the Dell website and download the XP driver package for your card.  You can then try to install the driver in Vista. (Don't worry, you're just using Vista to extract the files you need.  Vista should tell you, after it tries to install the drivers, that the installation failed.)  Pay attention to where Vista extracts the files.  Then go to that directory and copy the .inf & .sys files for your card.
Then follow these directions.
[http://ubuntuforums.org/showthread.php?t=843755](http://ubuntuforums.org/showthread.php?t=843755)

---

### Post by president rich on 2008-06-28
> **cwbar_1 said:**
> OK.  Go to the Dell website and download the XP driver package for your card.  You can then try to install the driver in Vista. (Don't worry, you're just using Vista to extract the files you need.  Vista should tell you, after it tries to install the drivers, that the installation failed.)  Pay attention to where Vista extracts the files.  Then go to that directory and copy the .inf & .sys files for your card.
Then follow these directions.
[http://ubuntuforums.org/showthread.php?t=843755](http://ubuntuforums.org/showthread.php?t=843755)

I will try this and post back results. Thank you.

---

### Post by president rich on 2008-06-28
> **cwbar_1 said:**
> OK.  Go to the Dell website and download the XP driver package for your card.  You can then try to install the driver in Vista. (Don't worry, you're just using Vista to extract the files you need.  Vista should tell you, after it tries to install the drivers, that the installation failed.)  Pay attention to where Vista extracts the files.  Then go to that directory and copy the .inf & .sys files for your card.
Then follow these directions.
[http://ubuntuforums.org/showthread.php?t=843755](http://ubuntuforums.org/showthread.php?t=843755)

Wicd tells me "no wireless networks found."
I'm worried I may have done something wrong.

---

### Post by bobyy on 2008-06-29
Post your $ifconfig and $ifconfig -a  output hereand we will see what is whrong :)

---

### Post by cwbar_1 on 2008-06-29
Post the results of ndiswrapper -l & iwconfig.

---

### Post by president rich on 2008-06-29
> **bobyy said:**
> Post your $ifconfig and $ifconfig -a  output hereand we will see what is whrong :)

ifconfig:
> 
eth0      Link encap:Ethernet  HWaddr 00:21:9b:cd:56:5b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

eth0:avahi Link encap:Ethernet  HWaddr 00:21:9b:cd:56:5b  
          inet addr:169.254.6.222  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4399 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4399 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:220534 (215.3 KB)  TX bytes:220534 (215.3 KB)

ifconfig -a:
> eth0      Link encap:Ethernet  HWaddr 00:21:9b:cd:56:5b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

eth0:avahi Link encap:Ethernet  HWaddr 00:21:9b:cd:56:5b  
          inet addr:169.254.6.222  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4399 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4399 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:220534 (215.3 KB)  TX bytes:220534 (215.3 KB)


---

### Post by president rich on 2008-06-29
> **cwbar_1 said:**
> Post the results of ndiswrapper -l & iwconfig.

ndiswrapper:
> bcmwl6 : driver installed
	device (14E4:4315) present (alternate driver: wl)


iwconfig:
> lo        no wireless extensions.

eth0      no wireless extensions.



---

### Post by bobyy on 2008-06-29
I think this thread will solve your BCN driver problem
 
[http://ubuntuforums.org/showthread.php?t=650729](http://ubuntuforums.org/showthread.php?t=650729)

regards

---

### Post by bravo331 on 2008-07-05
bobyy ur link appears to be broken!

---

