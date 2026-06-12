---
title: "Enabling Wireless Network"
date: 2010-06-21
forum: New to Ubuntu
---

### Post by Captain Man on 2010-06-21
Hey everyone, a while back a friend told me about Linux and Ubuntu, got it, hated it, tried it again, liked it more, blah blah exposition blah PROBLEM! I can't get wireless to work on my Netbook with the Ubuntu 10.04 Netbook Remix 32 bit OS. (Note: This netbook also has Windows XP on it and wireless works fine there) I found a helpful link though, [http://ubuntuforums.org/showpost.php?p=5024425&postcount=1](http://ubuntuforums.org/showpost.php?p=5024425&postcount=1) and I went ahead and did everything in the list so you guys could help me out. Any help is appreciated!

1. I am trying to connect to the wireless router at my house, when I click the wireless button to connect to a network no networks appear.

2. These terminal commands got me the following outputs.

```
lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
05:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 154b:6545 PNY 
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 002: ID 5986:0241 Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

lshw -class network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:26:9e:0d:d3:82
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.102 firmware=sb v3.04 latency=0 multicast=yes
       resources: irq:27 memory:f0200000-f020ffff
  *-network
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:f0400000-f0403fff
  *-network DISABLED
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:26:82:43:e5:2c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
```3. Charter in the USA.

4. Version info
```
uname -a
Linux jackson-netbook 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux

lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.04 LTS
Release:    10.04
Codename:    lucid
```5. Yes, I can connect with an Ethernet cord, and also with wireless in Windows XP which is on the laptop as well.

6. I am on my desktop! Which I also recently put Ubuntu on!

7. Terminal Stuff
```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:9e:0d:d3:82  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5600 (5.6 KB)  TX bytes:5600 (5.6 KB)

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

ping -c 3 208.67.219.101
connect: Network is unreachable

ping -c 3 www.opendns.com
ping: unknown host www.opendns.com
```8. I use WEP encryption, I don't know what a "channel" is. and I can't find any networks, period.

9. Read that link and such, and I turned off the power management on the card and still no luck.

-------------------------------------

Thanks so much for reading all of that and helping me, everyone!

---

### Post by davidmohammed on 2010-06-21
Hi there,
  if you connect your netbook via the ethernet cable and then goto administrator - hardware drivers, does it give you a choice of drivers e.g. B43 or STA?  Choose B43 and choose to activate.  Reboot.

---

