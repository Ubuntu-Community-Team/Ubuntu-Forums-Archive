---
title: "Driver installed, still no wireless --help"
date: 2007-01-18
forum: Networking &amp; Wireless
---

### Post by Helgeland on 2007-01-18
Ok, using ndiswrapper i installed the RT61.inf driver from the cd, and copied all .sys, .bin, and .inf files to /home/drivers/ from the Drivers/xp2k folder on the disk.  on edgy eft btw.
```
:~$ ndiswrapper -l
Installed drivers:
rt61            driver installed, hardware present 
```

heres lspci
```
:~$ lspci
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 Network controller: RaLink RT2561/RT61 802.11g PCI
01:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
05:00.0 VGA compatible controller: nVidia Corporation Unknown device 0295 (rev a1)

```

here are the contents of /etc/network/interfaces

```
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp
```

i go into system/admin/networking and enable wlan0 wireless and get no connection to the internet. in windows my card works fine so its not a hardware issue.
can anybody help me??

---

### Post by Helgeland on 2007-01-18
heres ifconfig -a
```
:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:16:E6:88:97:A1  
          inet addr:192.168.2.100  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::216:e6ff:fe88:97a1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5341 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5004 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5270653 (5.0 MiB)  TX bytes:705875 (689.3 KiB)
          Interrupt:217 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:16:E6:39:AE:95  
          inet6 addr: fe80::216:e6ff:fe39:ae95/64 Scope:Link
          UP RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:107 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:36936 (36.0 KiB)
          Base address:0xd000 

wmaster0  Link encap:UNSPEC  HWaddr 00-16-E6-39-AE-95-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0xd000 


```

---

### Post by Helgeland on 2007-01-18
and dmesg | grep eth
```
:~$ dmesg | grep eth
[17179579.020000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.54.
[17179579.276000] forcedeth: using HIGHDMA
[17179579.800000] eth0: forcedeth.c: subsystem: 01458:e000 bound to 0000:00:0a.0
[17179601.392000] eth0: no IPv6 routers present
[17179823.860000] eth0: no IPv6 routers present
[17180386.788000] eth0: no IPv6 routers present

```

---

### Post by Helgeland on 2007-01-18
sudo ifup eth0

```
~$ sudo ifup eth0
ifup: interface eth0 already configured

```

---

### Post by Helgeland on 2007-01-18
also eth0 doesnt show up in "networking" i think i lied in my first post, i have  
```

wireless connection (wmaster0)
not configured
wireless connection (wlan0)
not configured
Wired connection
address: DHCP
Modem connection
not configured

```

---

### Post by Helgeland on 2007-01-18
dmesg registers
```
[17179599.500000] Bluetooth: HCI device and connection manager initialized
[17179599.500000] Bluetooth: HCI socket layer initialized
[17179599.516000] Bluetooth: L2CAP ver 2.8
[17179599.516000] Bluetooth: L2CAP socket layer initialized
[17179599.544000] Bluetooth: RFCOMM socket layer initialized
[17179599.544000] Bluetooth: RFCOMM TTY layer initialized
[17179599.544000] Bluetooth: RFCOMM ver 1.7
[17179601.392000] eth0: no IPv6 routers present
[17179601.832000] wlan0: no IPv6 routers present
[17179823.860000] eth0: no IPv6 routers present
[17180386.788000] eth0: no IPv6 routers present
[17184435.744000] eth0: no IPv6 routers present
[17184761.024000] eth0: no IPv6 routers present

```

---

### Post by dmizer on 2007-01-18
eth0 is your wired network card, and wlan0 is your wireless card.

you cannot have two cards online at the same time, so you'll have to disable your wired network card before you can go online with your wireless.
```
sudo ifdown eth0
```

also, do you have wep/wpa enabled?

now, this won't fix your problem.  we need to disable ipv6, because i think it's causing you some problems, so do the following to disable ipv6:
```
sudo su
echo "blacklist ipv6" > /etc/modprobe.d/blacklist
exit
```
reboot.

either disable your eth0 card as indicated above, or disconnect the ethernet cable completely.  then post the output of the following command:
```
sudo iwlist wlan0 scan
```

we'll have to add your wlan card to your /etc/network/interfaces file with the correct information.

---

### Post by Helgeland on 2007-01-18
will do, thanks alot btw br0!!

---

### Post by Helgeland on 2007-01-18
um... slight problem?
```

:~$ sudo iwlist wlan0 scan
Password:
wlan0     Interface doesn't support scanning : Network is down

```

---

### Post by Helgeland on 2007-01-18
"network is down"... it all works fine in windows ... 54mb/s actually lol holy shist. is there anything i can do in windows to find out anything that i need to get ubuntu working?
and how do i find out if i have wep/wpa enabled? <-- prob. stupid ? but i'm sick of searching for my own damn answers... i just wanna ask questions... its so much easier lol, and less of a  headache.

---

### Post by Helgeland on 2007-01-18
*bump* sorry... i need to get this figured out though... can anybody help me?

---

### Post by Helgeland on 2007-01-18
```

:~$ sudo lshw -C network
Password:
  *-network DISABLED      
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 7
       bus info: pci@01:07.0
       logical name: wmaster0
       version: 00
       serial: 00:16:e6:39:ae:95
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical wireless ethernet physical
       configuration: broadcast=yes driver=rt61pci driverversion=CVS firmware=.bin link=yes multicast=yes wireless=IEEE 802.11g
       resources: iomemory:f3000000-f3007fff irq:66
  *-network
       description: IEEE1394 interface
       physical id: 1
       logical name: eth1
       serial: 00:16:e6:00:00:bb
       capabilities: ieee1394 physical
       configuration: broadcast=yes driver=eth1394 multicast=yes

```

---

### Post by Helgeland on 2007-01-18
*bump*
```

:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:16:e6:39:ae:95
Sending on   LPF/wlan0/00:16:e6:39:ae:95
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


```

---

### Post by Helgeland on 2007-01-18
i'm going to keep posting every hour till i get a responce damn*t lol.... i'm gona kill something... i've installed network-manager ... and it doesnt detect my wireless network, nor do i have the option to add another wireless connection....

---

### Post by mips on 2007-01-19
Do you have WEP or WPA enabled on your AP ? If yes then disable it for now, first you just want to establish connectivity.

1. Open **System->Administration->Networking** in the menu. 
 2. Click "Properties" 
 3. Enter your wireless access point's ESSID


Try DHCP again or try a static config and see if you can ping the AP or your router.


references:
[http://www.ubuntuforums.org/showthread.php?t=92142](http://www.ubuntuforums.org/showthread.php?t=92142)
[https://help.ubuntu.com/community/WifiDocs/RalinkRT2500Old](https://help.ubuntu.com/community/WifiDocs/RalinkRT2500Old)

---

### Post by dmizer on 2007-01-21
here's a good howto for your card.  ralink has linux drivers for your adapter:
[http://www.ubuntuforums.org/showthread.php?t=132980](http://www.ubuntuforums.org/showthread.php?t=132980)
and
[http://www.ubuntuforums.org/showthread.php?t=296822&highlight=RaLink+RT2561](http://www.ubuntuforums.org/showthread.php?t=296822&highlight=RaLink+RT2561)

in other words, uninstall your ndiswrapper configuration, and use the above directions instead.

---

