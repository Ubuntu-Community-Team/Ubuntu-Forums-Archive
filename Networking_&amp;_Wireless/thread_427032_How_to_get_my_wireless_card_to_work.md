---
title: "How to get my wireless card to work"
date: 2007-04-29
forum: Networking &amp; Wireless
---

### Post by KidA01 on 2007-04-29
hi, i was wondering if somebody could tell me what to do to get my wireless USB adapter to work with ubuntu distro. here's the info i believe you need:

auto wlan0
anthony@anthony-desktop:~$ cat /etc/network/interfaces
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


anthony@anthony-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:11:11:C3:D8:04  
          inet addr:192.168.1.138  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:11ff:fec3:d804/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3208 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2809 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3495540 (3.3 MiB)  TX bytes:404282 (394.8 KiB)

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

wlan0     Link encap:Ethernet  HWaddr 00:11:50:BC:A4:88  
          MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:14616 (14.2 KiB)
          Base address:0x8000 

wmaster0  Link encap:UNSPEC  HWaddr 00-11-50-BC-A4-88-00-80-00-00-00-00-00-00-00-00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0x8000 


anthony@anthony-desktop:~$ sudo lshw -C network
Password:
  *-usb DISABLED          
       description: Wireless interface
       product: Belkin 54g USB Network Adapter
       vendor: Belkin
       physical id: 1
       bus info: usb@4:1
       logical name: wmaster0
       version: 0.01
       serial: 00:11:50:bc:a4:88
       capabilities: usb-2.00 logical wireless
       configuration: broadcast=yes driver=rt73usb driverversion=CVS firmware=rt73usb->%s: Error - vendor requ4-1:1.0 link=yes maxpower=300mA multicast=yes speed=480.0MB/s wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@01:08.0
       logical name: eth0
       version: 02
       serial: 00:11:11:c3:d8:04
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=e100 driverversion=3.5.10-k2-NAPI duplex=full firmware=N/A ip=192.168.1.138 link=yes multicast=yes port=MII speed=100MB/s
       resources: iomemory:feaff000-feafffff ioport:ddc0-ddff irq:217
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:11:50:bc:a4:88
       capabilities: ethernet physical wireless
       configuration: multicast=yes wireless=IEEE 802.11g


anthony@anthony-desktop:~$ iwlist scanning
lo        Interface doesn't support scanning.

wmaster0  Failed to read scan data : Operation not supported

wlan0     No scan results
eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.


anthony@anthony-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:01.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 04)
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
anthony@anthony-desktop:~$ 


any info on where i go to get drivers etc is much appreciated

thanks

---

### Post by tturrisi on 2007-04-29
what's the exacvt model name & version # of the usb adapter?

---

### Post by KidA01 on 2007-04-29
It's a Belkin Wireless G USB Network Adapter. 802.11g 54mbps 2.4GHz

interface USB 1.0, 1.1, 2.0

network standards IEEE 802.11g, IEEE 802.11b

security 64-bit, 128-bit WEP encryption

i bought it around 8 months ago

i'm in the UK too (if that makes any difference)

that's all the information i can find on it i'm afraid

---

### Post by KidA01 on 2007-04-29
ah, i've found F5D7050uk written on the box in a few places

---

### Post by tturrisi on 2007-04-30
look on the box or the device to locate the exact version number.  Then we can determine the chipset inside the device, then determine what driver to use.  That adapter has 4-5 versions using 3 different chipsets = 3 different drivers.

---

### Post by KidA01 on 2007-04-30
ok, i just looked on the back of the actual adapter *makes note to get new brain* and here are all the numbers/IDs i could find:

model no. F5D7050
IC ID: 3623A-F5D7050B
FCC ID: K75-F5D7050B
FC Belkin F5D7050 (the FC is written in the style of a trademark/logo)
N10117
Z52B
Complies with RSS-210
P81976-D

the MAC address is written on the back too, do i need to post that?

thanks

---

### Post by tturrisi on 2007-04-30
There's nothing on the box or on the adapter that says versionX or vX, as in v2, v4, etc?  That adapeter was made using a Ralink chipset, a Broadcom chipset, a Prism chipset, an Airgo chipset or a Zydas chipset.  We would need to know the chipset...

---

### Post by KidA01 on 2007-04-30
i'm afraid i can't find any version number, or anything that even looks like a version number on the box, in the manual or on the adapter itself. does this mean i'm screwed?

---

### Post by randell6564 on 2007-04-30
> anthony@anthony-desktop:~$ sudo lshw -C network
Password:
  *-usb **DISABLED    **      
       description: Wireless interface
       product: Belkin 54g USB Network Adapter
       vendor: Belkin
       physical id: 1
       bus info: usb@4:1
       logical name: wmaster0
       version: 0.01
       serial: 00:11:50:bc:a4:88
       capabilities: usb-2.00 logical wireless
       configuration: broadcast=yes driver=rt73usb driverversion=CVS firmware=rt73usb->%s: Error - vendor requ4-1:1.0 link=yes maxpower=300mA multicast=yes speed=480.0MB/s wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@01:08.0
       logical name: eth0
       version: 02
       serial: 00:11:11:c3:d8:04
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=e100 driverversion=3.5.10-k2-NAPI duplex=full firmware=N/A ip=192.168.1.138 link=yes multicast=yes port=MII speed=100MB/s
       resources: iomemory:feaff000-feafffff ioport:ddc0-ddff irq:217
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:11:50:bc:a4:88
       capabilities: ethernet physical wireless
       configuration: multicast=yes wireless=IEEE 802.11g
I don't know.,I'm gonna go out on a limb here and say. ENABLE your wireless (Wlan0) device!
DISABLE your Eth0 first.  If that doesn't work then post your  /etc/network/interfaces.

---

### Post by Russel_Winder on 2008-02-08
According to the page at [http://www.belkin.com/uk/support/article/?lid=enu&pid=F5D7050uk&aid=6121&scid=0](http://www.belkin.com/uk/support/article/?lid=enu&pid=F5D7050uk&aid=6121&scid=0)
this device is Version 3xxx.  I am guessing that the NDIS wrapper can be used to employ the Windows driver.  The question is: is there a native driver for this device?

Unfortuately, [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin)
is missing any reference to this device.

---

