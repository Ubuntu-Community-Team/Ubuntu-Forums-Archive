---
title: "Questions about installing wifi drivers for NetGear WNDA3100v2 802.11abgn"
date: 2014-09-16
forum: Networking &amp; Wireless
---

### Post by Hastur_The_Unspeak on 2014-09-16
Hello ubuntu forums. I have a few questions in regards for installing the wifi drivers for the NetGear WNDA3100v2 802.11abgn, a usb wifi card. My first and foremost is if I can run ethernet and wifi together, and freely toggle between them. My second is if installing said wifi driver will impair the performance of my computer in any way, shape, or form.  

 

 Now, all trivial questions aside, I would like to know how to actually /install/ the driver, and what driver to use, as all guides I have seen have either addressed internal wifi cards, different cards/drivers than mine, or have asked questions about post-installation. Here is the output of the script that was in the sticky thread.  
 ```


 ########## wireless info START ##########  
 

 Report from: 15 Sep 2014 13:18 EDT -0400  
 

 Booted last: 15 Sep 2014 12:58 EDT -0400  
 

 Script from: 15 Sep 2014 03:40 UTC +0000  
 

 ##### release #####  
 

 Distributor ID:	Ubuntu  
 Description:	Ubuntu 14.04.1 LTS  
 Release:	14.04  
 Codename:	trusty  
 

 ##### kernel #####  
 

 Linux 3.13.0-35-generic #62-Ubuntu SMP Fri Aug 15 01:58:42 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux  
 

 Parameters: ro, quiet, splash, vt.handoff=7  
 

 ##### desktop #####  
 

 Ubuntu  
 

 ##### lspci #####  
 

 02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)  
 	Subsystem: ASUSTeK Computer Inc. P8P67 and other motherboards [1043:8432]  
 	Kernel driver in use: r8169  
 

 ##### lsusb #####  
 

 Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 001 Device 005: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]  
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 003 Device 004: ID 047f:c010 Plantronics, Inc.  
 Bus 003 Device 003: ID 413c:2005 Dell Computer Corp. RT7D50 Keyboard  
 Bus 003 Device 002: ID 0461:4d64 Primax Electronics, Ltd  
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 

 ##### PCMCIA card info #####  
 

 ##### rfkill #####  
 

 ##### lsmod #####  
 

 wmi                    19177  0  
 

 ##### interfaces #####  
 

 auto lo  
 iface lo inet loopback  
 

 ##### ifconfig ##### 
 

 eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>   
           inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0  
           inet6 addr: 2605:a000:1210:33:987f:26c3:172d:7b8/64 Scope:Global  
           inet6 addr: 2605:a000:1210:33:3285:a9ff:fe43:e074/64 Scope:Global  
           inet6 addr: fe80::3285:a9ff:fe43:e074/64 Scope:Link  
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1  
           RX packets:13603 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:12562 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:9649167 (9.6 MB)  TX bytes:2033736 (2.0 MB)  
 

 ##### iwconfig ##### 
 

 eth0      no wireless extensions.  
 

 lo        no wireless extensions.  
 

 ##### route #####  
 

 Kernel IP routing table  
 Destination     Gateway         Genmask         Flags Metric Ref    Use Iface  
 0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0  
 192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0  
 

 ##### resolv.conf #####  
 

 nameserver 127.0.1.1 
 search neo.rr.com  
 

 ##### nm-tool #####  
 

 NetworkManager Tool  
 

 State: connected (global)  
 

 - Device: eth0  [Wired connection 1] -------------------------------------------  
   Type:              Wired  
   Driver:            r8169  
   State:             connected  
   Default:           yes  
   HW Address:        <MAC 'eth0' [IF]>  
 

   Capabilities:  
     Carrier Detect:  yes  
     Speed:           10 Mb/s  
 

   Wired Properties  
     Carrier:         on  
 

   IPv4 Settings:  
     Address:         192.168.1.103  
     Prefix:          24 (255.255.255.0)  
     Gateway:         192.168.1.1  
 

     DNS:             192.168.1.1  
 

   IPv6 Settings:  
     Address:         2605:a000:1210:33:987f:26c3:172d:7b8  
     Prefix:          64  
     Gateway:         fe80::cad7:19ff:fe2c:5123  
 

     Address:         2605:a000:1210:33:3285:a9ff:fe43:e074  
     Prefix:          64  
     Gateway:         fe80::cad7:19ff:fe2c:5123  
 

     Address:         fe80::3285:a9ff:fe43:e074  
     Prefix:          64  
     Gateway:         fe80::cad7:19ff:fe2c:5123  
 

     DNS:             2605:a000:1210:33:cad7:19ff:fe2c:5123  
 

 ##### NetworkManager.state #####  
 

 [main]  
 NetworkingEnabled=true 
 WirelessEnabled=true 
 WWANEnabled=true  
 WimaxEnabled=true  
 

 ##### NetworkManager.conf #####  
 

 [main]  
 plugins=ifupdown,keyfile,ofono 
 dns=dnsmasq  
 

 [ifupdown]  
 managed=false  
 

 ##### NetworkManager profiles #####  
 

 cat: /etc/NetworkManager/system-connections/*: No such file or directory  
 

 ##### iw reg get #####  
 

 Region: America/New_York (based on set timezone)  
 

 country 00:  
 	(2402 - 2472 @ 40), (6, 20)  
 	(2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN, NO-IBSS  
 	(2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS  
 	(5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN, NO-IBSS  
 	(5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS  
 	(5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS  
 

 ##### iwlist channels #####  
 

 eth0      no frequency information.  
 

 lo        no frequency information.  
 

 ##### iwlist scan #####  
 

 eth0      Interface doesn't support scanning.  
 

 lo        Interface doesn't support scanning.  
 

 ##### module infos #####  
 

 ##### module parameters #####  
 

 ##### /etc/modules #####  
 

 lp  
 rtc  
 

 ##### modprobe options #####  
 

 [/etc/modprobe.d/blacklist-ath_pci.conf] 
 blacklist ath_pci  
 

 [/etc/modprobe.d/blacklist.conf] 
 blacklist evbug  
 blacklist usbmouse  
 blacklist usbkbd  
 blacklist eepro100  
 blacklist de4x5  
 blacklist eth1394  
 blacklist snd_intel8x0m  
 blacklist snd_aw2  
 blacklist i2c_i801  
 blacklist prism54  
 blacklist bcm43xx  
 blacklist garmin_gps 
 blacklist asus_acpi  
 blacklist snd_pcsp  
 blacklist pcspkr  
 blacklist amd76x_edac  
 

 [/etc/modprobe.d/blacklist-rare-network.conf] 
 alias net-pf-3 off  
 alias net-pf-6 off  
 alias net-pf-9 off  
 alias net-pf-11 off  
 alias net-pf-12 off  
 alias net-pf-19 off  
 alias net-pf-21 off  
 alias net-pf-36 off  
 

 [/etc/modprobe.d/iwlwifi.conf] 
 remove iwlwifi \  
 (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \  
 && /sbin/modprobe -r mac80211  
 

 [/etc/modprobe.d/mlx4.conf] 
 softdep mlx4_core post: mlx4_en  
 

 ##### rc.local ##### 
 

 exit 0  
 

 ##### pm-utils ##### 
   
 ##### udev rules #####  
 

 [/etc/udev/rules.d/70-persistent-net.rules] 
 # PCI device 0x10ec:0x8168 (r8169)  
 SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"  
 

 ##### dmesg #####  
 

 ########## wireless info END ############
 
```
 As you can see under the lsusb tab, I have the card plugged in to no avail.  
 

 I would also like to know how to uninstall the drivers, should a situation occur in which I would have to. Thank you for taking the time to read, and hopefully answer my question.

---

### Post by Bucky Ball on 2014-09-17
Welcome. Are you positive you need to install drivers for it? Plug it in and run:

```
sudo lshw -C network
```

... in a terminal. Post the output back here, please. ;)

---

### Post by Hastur_The_Unspeak on 2014-09-17
```

*-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 06
       serial: 30:85:a9:43:e0:74
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.1.103 latency=0 link=yes multicast=yes port=MII speed=10Mbit/s
       resources: irq

```

---

### Post by Bucky Ball on 2014-09-17
That is all? There is no output for 'Network Controller' under that? I guess not ...

If not it sees nothing with the dongle plugged in. Those particular dongles have always been problematic, I'm sorry to say, with Ubuntu. I'll keep digging. :-k

* Could you please open a terminal and provide us with the output of this:

lsusb

... with the dongle plugged in, of course.

---

### Post by Hastur_The_Unspeak on 2014-09-17
> **Bucky Ball said:**
> That is all? There is no output for 'Network Controller' under that? I guess not ...

If not it sees nothing with the dongle plugged in. Those particular dongles have always been problematic, I'm sorry to say, with Ubuntu. I'll keep digging. :-k

* Could you please open a terminal and provide us with the output of this:

lsusb

... with the dongle plugged in, of course.

```


Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 017: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 047f:c010 Plantronics, Inc. 
Bus 003 Device 003: ID 413c:2005 Dell Computer Corp. RT7D50 Keyboard
Bus 003 Device 002: ID 0461:4d64 Primax Electronics, Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
Yea I went through this a week ago when I was trying to fix this issue myself. The comp detects the usb dongle, that's not an issue. I can gurantee that it needs a driver of some kind, it's just a question of which one, how to install it, and what side effects it will bring on after install. 

If it's any help I picked up a driver that is /supposed/ to work with my dongle [https://dl.dropboxusercontent.com/u/249190490/2955302-Broadcom_bcm43xx_USB_32_64bit_v3.tar.gz](https://dl.dropboxusercontent.com/u/249190490/2955302-Broadcom_bcm43xx_USB_32_64bit_v3.tar.gz)

But again, I have no idea on how to install it or if it will even work.

---

