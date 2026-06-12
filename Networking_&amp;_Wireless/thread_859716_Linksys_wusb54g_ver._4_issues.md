---
title: "Linksys wusb54g ver. 4 issues"
date: 2008-07-14
forum: Networking &amp; Wireless
---

### Post by carlos_kennerley on 2008-07-14
Hi,

I have a problem with my Linksys wireless USB device (wusb54g ver. 4)with ubuntu 8.04.

Below is my config results:

My AP Wireless Channel is set to 2.

Network tools output:
Network device:	wlan0
Hardware address:	00:12:17:7d:0c:2b
IP address:	192.168.1.68
Netmask:	255.255.255.0
Broadcast:	192.168.1.255
Multicast:	Enabled
MTU:	1500
Link speed:	5.5 Mbps
State:	Active
Transmitted packets:	57
Transmission errors:	0
Received packets:	11
Reception errors:	0
Collisions:	0


Network device:	wmaster0
Hardware address:	not available
IP address:	not available
Netmask:	not available
Broadcast:	not available
Multicast:	not available
MTU:	not available
Link speed:	not available
State:	not available
Transmitted packets:	0
Transmission errors:	0
Received packets:	0
Reception errors:	0
Collisions:	0


When I press configure error = &#8220;The interface doesn't exist&#8221;


HOME:~$ iwconfig

lo        no wireless extensions.
eth1      no wireless extensions.
wmaster0  no wireless extensions.
wlan0     IEEE 802.11g  ESSID:"2WIRE208"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:1B:5B:2A:31:41   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

HOME:~$ ifconfig wlan0

wlan0     Link encap:Ethernet  HWaddr 00:12:17:7d:0c:2b  
          inet addr:192.168.1.68  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:17ff:fe7d:c2b/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1007 (1007.0 B)  TX bytes:8302 (8.1 KB)


HOME:~$ sudo ifdown wmaster0
ifdown: interface wmaster0 not configured

HOME:~$ sudo ifup wlan0
ifup: interface wlan0 already configured


HOME:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
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
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
02:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)

**Note: Looks like no device is listed but I am getting the correct info from my AP i.e. MAC Address. I also only have one wireless device and I don't know how to remove wmaster0**

---

### Post by carlos_kennerley on 2008-07-24
Any ideas anyone?

---

### Post by wraith42 on 2008-07-26
I'm in the same boat man. Been trying different drivers and methods for days now with no luck. I can connect to my router but I'm averaging about 40kbps when I get 1500kbps in windows xp easily. tried ndiswrapper, both installed through synaptic and manually compiled using the rt2500usb drivers from linksys. also tried the rt2570 drivers from serialmonkey compiled manually without ndiswrapper which also didnt work. I've reset the beacon interval to 10-20 instead of the default of 100 on the router and also tried setting the MTU on the router to 1400 instead of AUTO. nothing really seems to help. if you can figure it out, please let me know. hey are you able to connect to your router?

---

### Post by carlos_kennerley on 2008-07-27
I can not connect to the router via it's https config page or by ping but the wireless driver seems to pick up a DHCP IP address and get the SSID of my network, ?. So somethng is working. I think for me it is something to do with the "Master0" extra device.??

I am back to using XP at home until I can re-locate my router nearer to my PC to use a wired connection :(

---

