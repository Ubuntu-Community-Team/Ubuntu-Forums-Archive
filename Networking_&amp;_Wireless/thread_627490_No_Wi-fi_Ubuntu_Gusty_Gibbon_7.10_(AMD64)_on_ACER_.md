---
title: "No Wi-fi Ubuntu Gusty Gibbon 7.10 (AMD64) on ACER Aspire 4310"
date: 2007-11-30
forum: Networking &amp; Wireless
---

### Post by barlaventoexpert on 2007-11-30
Yesterday I installed Ubuntu Gusty Gibbon 7.10 (AMD64) on my new ACER Aspire 4310.

Everything seems to working sweetly to date with the exception of....**WIFI**

I have now spent 5 to 6 hours googling, ubuntu foruming, etc etc, reconfiguring via terminal etc, and cannot for the life of me get the wifi up and running, despite the many excellent posts I've read.

The laptop hardware config is as follows:

Processor: Intel Celeron M processor 530
Memory: 1 GB DDR2

Wifi: BCM94311MCG wlan mini-PCI

I am running a network with wifi router/access point with WPA-PSK - TKIP operational.

The machine worked fine when Vista was installed, but I want Gutsy Gibbon as I have only worked with Ubuntu for the past 3 years and have no intention to returning to Windoze. However, I need the wifi active for both home and roaming.  My partner also has a laptop with XP installed and its wifi is operating fine.

Using the downloaded windows driver config applet, I have the machine showing that the bcmwl5 windows driver is installed and the hardware is recognised. Additionally, the wifi light to the left of the keyboard is lit showing orange.

Running ifconfig -a shows:

eth0      Link encap:Ethernet  HWaddr 00:16:D3:E4:15:75  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d3ff:fee4:1575/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4583 (4.4 KB)  TX bytes:6409 (6.2 KB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:1C:26:78:B3:0F  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Memory:d8000000-d8004000 

eth1:avah Link encap:Ethernet  HWaddr 00:1C:26:78:B3:0F  
          inet addr:169.254.4.232  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Memory:d8000000-d8004000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0 is the ethernet cable link which is working fine.

However,from the above, it can be seen that eth1 (the wifi card) is generating a local IP address only.

I have set the card to both automatic DHCP and static IP settings with no result.

Running lspci gives:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
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
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
0a:06.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
0a:06.2 Generic system peripheral [0805]: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
0a:06.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)

interfaces shows:

auto lo
iface lo inet loopback


iface eth1 inet dhcp

wpa-ap-scan 1
wpa-pairwise TKIP
wpa-group TKIP
wpa-psk 0df5efde925965b78dab2dca8dbf6d5a17a3f1a82b149653a18e6d915df4e83d
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid C54BRS4A

iface eth0 inet dhcp

auto eth0

auto eth1

I would appreciate any assistance anyone can provide to help me get this working as I urgently need the machine operational.

---

