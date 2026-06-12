---
title: "Netgear WNDA3100v2 not working"
date: 2014-12-21
forum: Networking &amp; Wireless
---

### Post by trevis2 on 2014-12-21
I have read about a thousand threads about this and just cannot get my wireless network working to save my life.  I have been close, getting it connected to wifi, but it dropped and connected slow.  So, I tried to fix that, and now I am back to basically where I started with wlan0 missing.  I have a driver installed with ndiswrapper.  Here's some details from my system:

```
$ lsusb
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 19ff:0238 Dynex 
Bus 003 Device 003: ID 1a2c:0023 China Resource Semico Co., Ltd 
Bus 003 Device 002: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hu

```

```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr b8:97:5a:6a:c1:fb  
          inet addr:192.168.137.230  Bcast:192.168.137.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7882 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6208 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1418183 (1.4 MB)  TX bytes:577927 (577.9 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2204 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2204 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:438212 (438.2 KB)  TX bytes:438212 (438.2 KB)

```

I get no output from rfkill list.

```
$ sudo lshw -c network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 07
       serial: b8:97:5a:6a:c1:fb
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.137.230 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:41 ioport:e000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
```

Please let me know if there's other info I can provide.  I am connected to my router through an ethernet connection to my laptop.  This has been the biggest headache I have ever had in my pc troubleshooting career.  I have spent nearly 3 days now troubleshooting this issue.  Thanks so much!

---

### Post by chili555 on 2014-12-21
Three days, huh?? As you can see by my details and a few hundred forum posts on the matter, I have been struggling with this device for nearly a decade. What does this tell us?```
sudo modprobe ndiswrapper
ndiswrapper -l
```Does the log hold any clues?```
dmesg | grep ndis
```As far as I know, these are the currently preferred drivers: [http://ubuntuforums.org/showthread.php?t=1964173](http://ubuntuforums.org/showthread.php?t=1964173)

I have learned three things about this device over the years: 

* Whether it works or not ... *EVER* ... depends on the specific kernel version, ndiswrapper version, phase of the moon and luck. 
* Getting it to work using the crutch ndiswrapper and a creaky old XP driver is a miracle that it works at all, much less fast.
* Sometimes it is pragmatic to invest US$10-15 in a fully supported device and be happy than to exchange 40-50 posts with old Chili and suffer.

I am happy to help in any event. I always hope I discover a trick or fix that makes these devices work and makes me a hero.

---

### Post by trevis2 on 2014-12-21
Do you have any suggestions for good cards?  This PC is going to be a media server, so internet speed counts.  Unfortunately, the PC is going to be too far away from the router for Ethernet.

---

### Post by chili555 on 2014-12-21
Please see: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

[http://www.htpcbeginner.com/linux-compatible-usb-wireless-adapters-2012/](http://www.htpcbeginner.com/linux-compatible-usb-wireless-adapters-2012/)

[http://arstechnica.com/civis/viewtopic.php?t=1237279](http://arstechnica.com/civis/viewtopic.php?t=1237279)

[http://ubuntuforums.org/showthread.php?t=2233349](http://ubuntuforums.org/showthread.php?t=2233349)

---

### Post by jeremy31 on 2014-12-21
Maybe even something like the Cisco RE1000 [http://support.linksys.com/en-us/support/rangeexpanders/RE1000](http://support.linksys.com/en-us/support/rangeexpanders/RE1000)

---

### Post by trevis2 on 2014-12-21
I solved it, but only by getting a WiFi extender.  I plug into its one Ethernet port, and away I go.  This will also help some devices that I use upstairs to have internet.  Thanks for all the help!

---

