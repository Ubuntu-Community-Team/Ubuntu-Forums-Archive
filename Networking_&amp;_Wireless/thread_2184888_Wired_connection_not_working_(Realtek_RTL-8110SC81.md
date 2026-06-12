---
title: "Wired connection not working (Realtek RTL-8110SC/8169SC)"
date: 2013-10-31
forum: Networking &amp; Wireless
---

### Post by delirium-q on 2013-10-31
When I first installed, no wire connection was detected.  I have not been able to get it to work.

I've tried changing /etc/networking/interface to have eth0 and restarting with ifup and restarting the network-manager, both have not work.

I know the ethernet cable and card work since it works in the Windows partition.

Out for lspci:
```
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA Controller [IDE mode] (rev 02)
01:00.0 VGA compatible controller: NVIDIA Corporation GF104 [GeForce GTX 460] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GF104 High Definition Audio Controller (rev a1)
03:00.0 SATA controller: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 02)
03:00.1 IDE interface: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 02)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)
04:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)
04:02.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx]
04:03.0 Multimedia video controller: Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder
04:04.0 Network controller: Ralink corp. RT2561/RT61 802.11g PCI

```

/etc/networking/interfaces
```
# interfaces(5) file used by ifup(8) and ifdown(8)auto lo
iface lo inet loopback


auto eth0
iface eth0 inet dhcp


auto eth1
iface eth0 inet dhcp
```

sudo lshw -C network
```
  *-network:0                    description: Ethernet interface
       product: RTL-8110SC/8169SC Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 10
       serial: 00:50:8d:9f:f8:48
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:23 ioport:be00(size=256) memory:dffff000-dffff0ff memory:fdc00000-fdc1ffff
  *-network:1
       description: Ethernet interface
       product: RTL-8110SC/8169SC Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:04:01.0
       logical name: eth1
       version: 10
       serial: 00:50:8d:9f:f8:49
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:22 ioport:bc00(size=256) memory:dfffe000-dfffe0ff memory:fdc20000-fdc3ffff
  *-network:2
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: Ralink corp.
       physical id: 4
       bus info: pci@0000:04:04.0
       logical name: wlan0
       version: 00
       serial: 00:1f:1f:3b:35:6f
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci driverversion=3.11.0-12-generic firmware=0.8 ip=192.168.1.139 latency=64 link=yes multicast=yes wireless=IEEE 802.11bg
       resources: irq:23 memory:dfff0000-dfff7fff

```

---

### Post by Shrek01 on 2013-10-31
What does **ifconfig** say? Does it show both eth0 and eth1? Do they have an IP assigned? (inet adr:XXX.XXX.XXX.XXX)

Could be a DNS problem.  Can you **ping 8.8.8.8**?

What does **route** say?  Does it show the correct route to your router?

---

### Post by delirium-q on 2013-10-31
ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:50:8d:9f:f8:48            UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


eth1      Link encap:Ethernet  HWaddr 00:50:8d:9f:f8:49  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:919 errors:0 dropped:0 overruns:0 frame:0
          TX packets:919 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:84061 (84.0 KB)  TX bytes:84061 (84.0 KB)


wlan0     Link encap:Ethernet  HWaddr 00:1f:1f:3b:35:6f  
          inet addr:192.168.1.139  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:1fff:fe3b:356f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3555 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2169 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1195761 (1.1 MB)  TX bytes:373384 (373.3 KB)

```

Can't ping anything because I can't connect.  I did something last night so when I boot now, it takes forever to start network manager.

---

### Post by Shrek01 on 2013-10-31
It looks like DHCP isn't giving a flying duck.

Is your Windows networking on DHCP, or was it manually entered?  I'm thinking your router has DHCP dissabled and Windows has all the info needed filled manually: Internal IP, router IP, and DNS.  Can you check if DHCP is selected in Windows?

---

### Post by delirium-q on 2013-11-01
Windows is configured to automatic DHCP.

[http://i.imgur.com/tG4jQVx.png](http://i.imgur.com/tG4jQVx.png)

---

### Post by tgalati4 on 2013-11-02
Try rebooting the router and any modem connected to it.  Do it in order:  Modem (cable/DSL/satellite) then wait a few minutes, then the router.  Look through the boot up records for DHCP messages:

Post the output of:

```
grep DHCP /var/log/syslog.*
```

Delete or modify any personal information (like external IP addresses).

---

### Post by SeijiSensei on 2013-11-02
Let's just do a quick manual test.  Determine your network prefix, like 192.168.1, then plug the cable into eth0 and run the command:

```
sudo ifconfig 192.168.1.33 netmask 255.255.255.0
```

Choose a final number for this machine's address that you know is outside the range of existing machines.  On a "class-C" subnet like this, you can choose any number between 1 and 254.

Now run ifconfig by itself to insure that the card is configured.  Next try pinging the router.  Any luck?

---

### Post by delirium-q on 2013-11-02
Posting from Windows as now WiFi doesn't work in Kubuntu.  ifconfig shows that my wireless settings have been deleted and now only eth0 exist.  I think I did something that fscked the settings.

---

### Post by delirium-q on 2013-11-02
I give up, I'm going to virtualize Kubuntu when I need to boot into a Linux environment.

---

