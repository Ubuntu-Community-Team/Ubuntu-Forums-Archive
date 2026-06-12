---
title: "Cannot connect to internet over wired connection - please help (eth0:avahi problem?)"
date: 2008-07-10
forum: Networking &amp; Wireless
---

### Post by BB2008 on 2008-07-10
Hi All:

I am a newbie to ubuntu, have used linux mildly but this is the first time I am planning on using linux as my *only* platform on a new build. I installed ubuntu 8.04 on my fresh built desktop machine. My problem is that I cannot connect to the internet over a wired connection. 

**This is what I have tried so far:**

To begin, I went to System -> Administration -> Network and configured the "Wired Connection". I set the "Connection Settings" "Configuration" to "Automatic Configuration (DHCP)". After that, I rebooted and then fired up mozilla, that did not work. 

I then did a ifconfig and saw that while eth0 has no IP address, there is a "eth0:avahi" entry that has an IP address. I googled and found this article: [http://omingo.zorngrid.com/](http://omingo.zorngrid.com/). i tried the process laid out here, and that too did not work.

And that brings me to you guys :-). I have copy pasted below output from ifconfig, iwconfig and lspci - my PCI wireless card is also not working but that is for another day!

**ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:1f:d0:5a:0b:e1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:8292065968 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:254 Base address:0x2000 

eth0:avahi Link encap:Ethernet  HWaddr 00:1f:d0:5a:0b:e1  
          inet addr:169.254.7.95  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:254 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:112492 (109.8 KB)  TX bytes:112492 (109.8 KB)



**iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.


**lspci**
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:07.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
03:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

---

### Post by superprash2003 on 2008-07-11
have you tried static ip instead of DHCP?

---

### Post by BB2008 on 2008-07-11
Thanx for looking at my post, and no, I have not tried static IP. So should I assign a static IP to the eth0 interface?

---

### Post by pxwpxw on 2008-07-11
BB2008

Is your router configured to provide dhcp?

---

### Post by superprash2003 on 2008-07-11
yes eth0 interface

---

