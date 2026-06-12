---
title: "Trouble getting Airlink 101 pci wireless card to work"
date: 2007-03-09
forum: Networking &amp; Wireless
---

### Post by zanyspydude on 2007-03-09
Hello there.  Thanks for helping (or reading :D)  I have an airlink 101 pci wireless card that i'm trying to connect to my home network.  It's not connecting, in fact I dont think linux is recognizing the card.  Sadly I have no idea where to go from here.  Would someone mind walking me through it?

some stuff that might be useful...
I'm using ubuntu 6.10
ifconfig output:
```
eth0      Link encap:Ethernet  HWaddr 00:11:11:41:C8:DA  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1432 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1432 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:112160 (109.5 KiB)  TX bytes:112160 (109.5 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:14:A5:31:26:A8  
          inet6 addr: fe80::214:a5ff:fe31:26a8/64 Scope:Link
          UP RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:52 errors:0 dropped:0 overruns:0 frame:0
          TX packets:183 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3824 (3.7 KiB)  TX bytes:52598 (51.3 KiB)
          Base address:0xa000 

wmaster0  Link encap:UNSPEC  HWaddr 00-14-A5-31-26-A8-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0xa000 


```

iwconfig output:
```
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

david@david-desktop:~/Desktop$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.437 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:"acjp"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          
sit0      no wireless extensions.

```

lspci output

```
00:00.0 Host bridge: Intel Corporation 915G/P/GV/GL/PL/910GL Express Memory Controller Hub
00:01.0 PCI bridge: Intel Corporation 915G/P/GV/GL/PL/910GL Express PCI Express Root Port
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2)
06:01.0 Network controller: RaLink RT2561/RT61 802.11g PCI
06:03.0 Multimedia video controller: Internext Compression Inc iTVC15 MPEG-2 Encoder (rev 01)
06:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)
06:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 01)

```

my network is wpa protected which i understand might be a problem, but i don't know how to correct....


Thanks again!

---

### Post by infol on 2007-03-09
HI!

Can you post the contents of the file /etc/networking/interfaces ?

---

### Post by zanyspydude on 2007-03-09
sorry for the delay

/etc/network/interfaces:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp


iface wlan0 inet dhcp
wireless-essid acjp
wireless-key s:k33p0ut


iface wmaster0 inet dhcp
wireless-essid acjp





```

---

### Post by whayong on 2007-03-09
This is your problem:

06:01.0 Network controller: RaLink RT2561/RT61 802.11g PCI\

My opinion stay away from Ralink.  I've got one, it's running, but not at a 100%

if you still want to use it, follow this how to:
[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61?highlight=%28WifiDocs%2FDriver%29](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61?highlight=%28WifiDocs%2FDriver%29)

Good luck!

---

