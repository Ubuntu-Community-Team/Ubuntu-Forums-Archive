---
title: "looking for help getting wireless to work w/ ndiswrapper"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by sandsean on 2009-11-02
hey all.  i'm very new to linux.  currently trying to get wireless working, but have been running into problems.  i installed ndiswrapper using the tutorial in the first post of this thread [http://ubuntuforums.org/showthread.php?t=340689](http://ubuntuforums.org/showthread.php?t=340689)  

wireless card is recognized, but it can't find or connect to my network.  any and all advice / handholding would be welcome!

here's some info:

lspci

```
00:00.0 Host bridge: Intel Corporation 82850 850 (Tehama) Chipset Host Bridge (MCH) (rev 04)
00:01.0 PCI bridge: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 04)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 04)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 04)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation NV25 [GeForce4 Ti 4200] (rev a3)
02:07.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
02:08.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
02:09.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
02:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```sudo lshw -class network

```
  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 7
       bus info: pci@0000:02:07.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: a
       bus info: pci@0000:02:0a.0
       logical name: eth0
       version: 10
       serial: 00:c0:a8:82:8b:52
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0c:41:5e:f4:e8
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
```uname -a

```
Linux samuel-desktop 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux
```lsb_release -a

```
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 8.04.1
Release:    8.04
Codename:    hardy
```ifconfig

```
eth0      Link encap:Ethernet  HWaddr 00:c0:a8:82:8b:52  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xe800 
```iwconfig

```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"linksys"  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```route -n

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
```ping -c 4 192.168.1.1

```
connect: Network is unreachable
```

---

### Post by coolbrook on 2009-11-02
> Description:    Ubuntu 8.04.1

Can you connect your computer to your router by an ethernet cable to get online?

I suggest you give that a try and run update manager to get 8.04.3, disconnect from the wired connection and try wireless again.  If that fails, take a look at newer solutions here.  

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Hardy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Hardy)

[http://ubuntuforums.org/showthread.php?t=1134787](http://ubuntuforums.org/showthread.php?t=1134787)

The second is for Jaunty but perhaps it will work for Hardy's most recent update as well.

---

