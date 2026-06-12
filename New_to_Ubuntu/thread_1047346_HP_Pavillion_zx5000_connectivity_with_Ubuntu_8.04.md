---
title: "HP Pavillion zx5000 connectivity with Ubuntu 8.04"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by FalconMtn on 2009-01-22
I’m pleased to say that I have the Hardy Heron (8.04) up and running on my wife’s old HP Pavillion zx 5000 laptop. Install was a breeze; however I’ve encountered a problem with network connectivity: the machine will not connect to the local wireless network or via wired Ethernet connection. I’m not particular regarding the type of connection; I’d be satisfied with either. The primary purpose of this machine will be web browsing, music, occasional office-suite applications, but more than anything an opportunity to learn more about a Linux-based OS. Instead of doing something smart like testing Ubuntu before installing it, I just dove in head first and installed 8.10 wiping the previous version of XP right off the machine. I’ve reverted to 8.04 since the initial install of 8.10. Here’s response to the “help me help you questions:”

[B]1. How were you trying to get online? e.g. dial-up, USB-wired ADSL modem, ethernet-wired ADSL modem, ethernet-wired ADSL modem-router, wireless router / modem-router, 3G-mobile internet etc.
[/B]
A: Wireless Router (with Ethernet out). In simple speak: I have a Net Gear wireless router, which works fine for on other devices both wirelessly and when plugged in via Ethernet cable. 

**2. What hardware are you using? The brand & model number (perhaps with a link to an online manual) for your adapters, modems, routers etc. You can generally identify external components from their labelling, and internal components from within an Operating System already installed (e.g. Windows or Ubuntu).**

A:
Router: Netgear 54g Wireless Router WGR
Network Controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03) 


Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

daniel@FalconMtnLaptop:~$ sudo lshw -C network 
[sudo] password for daniel:  
  *-network:0              
       description: Network controller 
       product: BCM4306 802.11b/g Wireless LAN Controller 
       vendor: Broadcom Corporation 
       physical id: 2 
       bus info: pci@0000:02:02.0 
       version: 03 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master 
       configuration: driver=b43-pci-bridge latency=64 module=ssb 
  *-network:1 
       description: Ethernet interface 
       product: RTL-8139/8139C/8139C+ 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 3 
       bus info: pci@0000:02:03.0 
       logical name: eth0 
       version: 10 
       serial: 00:02:3f:6a:85:0f 
       size: 100MB/s 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=128 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s 
  *-network DISABLED 
       description: Wireless interface 
       physical id: 2 
       logical name: wlan0 
       serial: 00:90:4b:4b:cc:c8 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g 
daniel@FalconMtnLaptop:~$  

**3. Who is your Internet Service Provider (and in which country)?**

A: Comcast Cable, USA


**4. Which version of Ubuntu are you using? e.g. Ubuntu 8.04, Xubuntu 7.10 etc.**


A: 8.04, but have tried 7.10 and 8.10. Initially, I installed 8.10 on 1/19/09 with a recent download of 8.10. I had read that 8.10 may damage some network cards, could this be the problem with the Ethernet connection?

[B]
5. Can you get online with any other method? e.g. if you have a wifi problem, can you connect with ethernet?[/B]

A: That’s the problem, I can’t get online with wifi or Ethernet. I just want to get one of the two to work. Both wifi and Ethernet work on this network when tested with other computers.

**6. How are you getting online to post on this forum?**

A: With another laptop, running XP.

**7. Include the output from the following commands from Terminal (all case sensitive). They help identify your hardware, so provide further detail to potential helpers. If necessary, just copy and paste the text into a text file and upload from a different computer.**

_Lspci_

daniel@FalconMtnLaptop:~$ lspci 
00:00.0 Host bridge: ATI Technologies Inc Radeon 9100 IGP Host Bridge (rev 02) 
00:01.0 PCI bridge: ATI Technologies Inc Radeon 9100 IGP AGP Bridge 
00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01) 
00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01) 
00:14.0 SMBus: ATI Technologies Inc SMBus (rev 16) 
00:14.1 IDE interface: ATI Technologies Inc Dual Channel Bus Master PCI IDE Controller 
00:14.3 ISA bridge: ATI Technologies Inc Unknown device 434c 
00:14.4 PCI bridge: ATI Technologies Inc IXP200 3COM 3C920B Ethernet Controller 
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller 
00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01) 
01:05.0 VGA compatible controller: ATI Technologies Inc M9+ 5C61 [Radeon Mobility 9200 (AGP)] (rev 01) 
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link) 
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03) 
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10) 
02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01) 
02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01) 
02:04.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01) 
02:07.0 USB Controller: NEC Corporation USB (rev 43) 
02:07.1 USB Controller: NEC Corporation USB (rev 43) 
02:07.2 USB Controller: NEC Corporation USB 2.0 (rev 04) 

_lsusb_

daniel@FalconMtnLaptop:~$ lspci 
00:00.0 Host bridge: ATI Technologies Inc Radeon 9100 IGP Host Bridge (rev 02) 
00:01.0 PCI bridge: ATI Technologies Inc Radeon 9100 IGP AGP Bridge 
00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01) 
00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01) 
00:14.0 SMBus: ATI Technologies Inc SMBus (rev 16) 
00:14.1 IDE interface: ATI Technologies Inc Dual Channel Bus Master PCI IDE Controller 
00:14.3 ISA bridge: ATI Technologies Inc Unknown device 434c 
00:14.4 PCI bridge: ATI Technologies Inc IXP200 3COM 3C920B Ethernet Controller 
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller 
00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01) 
01:05.0 VGA compatible controller: ATI Technologies Inc M9+ 5C61 [Radeon Mobility 9200 (AGP)] (rev 01) 
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link) 
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03) 
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10) 
02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01) 
02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01) 
02:04.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01) 
02:07.0 USB Controller: NEC Corporation USB (rev 43) 
02:07.1 USB Controller: NEC Corporation USB (rev 43) 
02:07.2 USB Controller: NEC Corporation USB 2.0 (rev 04) 
[U]
lshw -class network[/U]

daniel@FalconMtnLaptop:~$ lshw -class network 
WARNING: you should run this program as super-user. 
  *-network:0              
       description: Network controller 
       product: BCM4306 802.11b/g Wireless LAN Controller 
       vendor: Broadcom Corporation 
       physical id: 2 
       bus info: pci@0000:02:02.0 
       version: 03 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master 
       configuration: driver=b43-pci-bridge latency=64 module=ssb 
  *-network:1 
       description: Ethernet interface 
       product: RTL-8139/8139C/8139C+ 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 3 
       bus info: pci@0000:02:03.0 
       logical name: eth0 
       version: 10 
       serial: 00:02:3f:6a:85:0f 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=128 maxlatency=64 mingnt=32 module=8139too multicast=yes 
  *-network DISABLED 
       description: Wireless interface 
       physical id: 3 
       logical name: wlan0 
       serial: 00:90:4b:4b:cc:c8 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g 
daniel@FalconMtnLaptop:~$  

**8. Do you dual-boot with Windows? If yes - read this:**


A: No, don’t dual boot

With the information above, I am hoping to get some trouble-shooting suggestions. My experience with Ubuntu and Linux pretty much zero, but I can follow directions well. Advice please? Thanks in advance!

---

### Post by mikewhatever on 2009-01-22
Do you get an IP when the computer is connected to the router by cable? Can you post the output of <ifconfig>?

---

### Post by FalconMtn on 2009-01-22
Thank you very much for the response. Looks like I'm getting an IP address, but maybe you can confirm. Here's the results of ifconfig:

ubuntu@ubuntu:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:02:3f:6a:85:0f   
          inet6 addr: fe80::202:3fff:fe6a:850f/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:2 dropped:0 overruns:0 frame:0 
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:5607 (5.4 KB) 
          Interrupt:18 Base address:0xa000  
 
eth0:avahi Link encap:Ethernet  HWaddr 00:02:3f:6a:85:0f   
          inet addr:169.254.4.30  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          Interrupt:18 Base address:0xa000  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:4454 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:4454 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:223316 (218.0 KB)  TX bytes:223316 (218.0 KB) 
 
ubuntu@ubuntu:~$

---

### Post by mikewhatever on 2009-01-22
Yes, you do get an IP, although it doesn't seem to be from the router. Do you, by any chance, have two network cards? Any idea why there are two ethernet interfaces?

---

### Post by FalconMtn on 2009-01-23
The HP lives on a docking station because the power adapter no longer gives juice through the normal ac plug-in spot on the laptop. Therefore, there are two ethernet ports, one on the docking station, and on on the laptop. I had the ethernet plugged in to the laptop; switched the ethernet cord to the docking station and presto: live. But...I did learn a little along the way, which was the objective of the ubuntu exercise in the first place. Thanks!

---

