---
title: "[SOLVED] No ipV4 interface/network/internet with wired"
date: 2008-09-17
forum: Networking &amp; Wireless
---

### Post by kbubuntu on 2008-09-17
I'm new to ubuntu so bear with me pls. Installed 8.04 last night using the alternate CD. The DHCP setup phase failed during the install so I had to try configuring it manually, without much luck.

Latest attempt was to switch from DHCP to static IP address. My router is set up to statically bind 192.168.1.100 to the MAC address of my NIC (Realtek RTL-8139/8139C/8139C+), so I set that up in /etc/network/interfaces, but still can't connect.

Looking at the ifconfig output for eth0 below, I don't see an IPv4 address for this interface, just an IPv6 address. I'm pretty sure, though, that ifconfig showed the expected IPv4 address 192.168.1.100 just after saving /etc/network/interfaces, but I still wasn't able to ping anything, including the router.

So, I'm all alone in my little black box. I've been through the forums but found nothing helpful so far except for tip on converting to static IP address.

Can anyone help?

```
kb@kb-ubuntu:~$ netstat -i
Kernel Interface table
Iface   MTU Met   RX-OK RX-ERR RX-DRP RX-OVR    TX-OK TX-ERR TX-DRP TX-OVR Flg
eth0       1500 0         0      0      0 0             0      0      0      0 BMRU
lo        16436 0      1521      0      0 0          1521      0      0      0 LRU
kb@kb-ubuntu:~$ /sbin/route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
kb@kb-ubuntu:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:02:06.0
       logical name: eth0
       version: 10
       serial: 00:0c:76:7e:c3:6a
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
kb@kb-ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0c:76:7e:c3:6a  
          inet6 addr: fe80::20c:76ff:fe7e:c36a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1521 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1521 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:80606 (78.7 KB)  TX bytes:80606 (78.7 KB)

```

---

### Post by Iowan on 2008-09-17
Post **/etc/network/interfaces** file.  I presume you've done **sudo /etc/init.d/networking restart** after edits.
I don't have Realtek cards, so I haven't paid much attention to the threads about drivers, issues, etc, - the RTL-8139 shows up in [this]("http://ubuntuforums.org/showthread.php?p=5809029#post5809029") post. A forum search might turn up more potential solutions.

---

### Post by kbubuntu on 2008-09-18
Thx Iowan. I did run .../networking restart but it failed SIGxxx not found or something. I restarted Ubuntu instead but no effect. Here is an updated listing, including /etc/network/interfaces.

```
kb@kb-ubuntu:~$ more /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
gateway 192.168.1.1

auto eth0
kb@kb-ubuntu:~$ netstat -i
Kernel Interface table
Iface   MTU Met   RX-OK RX-ERR RX-DRP RX-OVR    TX-OK TX-ERR TX-DRP TX-OVR Flg
eth0       1500 0         0      0      0 0             0      0      0      0 BMRU
lo        16436 0      1252      0      0 0          1252      0      0      0 LRU
kb@kb-ubuntu:~$ /sbin/route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0
kb@kb-ubuntu:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:02:06.0
       logical name: eth0
       version: 10
       serial: 00:0c:76:7e:c3:6a
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
kb@kb-ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0c:76:7e:c3:6a  
          inet6 addr: fe80::20c:76ff:fe7e:c36a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1521 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1521 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:80606 (78.7 KB)  TX bytes:80606 (78.7 KB)
```

---

### Post by kbubuntu on 2008-09-18
yay rockin now

it was windows -- i have a dual boot setup. windows shuts off the realtek card on shutdown and enables it on power up/boot. but ubuntu does not reenable on power up/boot. there is a post on gentoo relating to this -- i'll post the link here when i find it again.

the fix was simple:

- boot into windows
- open device manager (start->administration tools->computer manager->device manager)
- right-click network card from the device list and select properties
- click on advanced tab (i think its called advanced) in device properties
- select "wake up on lan after shutdown" and enable it
- shut windows down and boot ubuntu

then i undid my attempt to assign a static address in /etc/network/interfaces and restored dhcp

all the lights came on

yay

thx

---

### Post by Iowan on 2008-09-18
Really good news! Please DO post the link - and (if problem is solved), mark the thread [SOLVED] (under Thread Tools).

---

### Post by kbubuntu on 2008-09-19
here is the gentoo post that helped me...

   [http://gentoo-wiki.com/HARDWARE_RTL8168](http://gentoo-wiki.com/HARDWARE_RTL8168)

referenced in...

   [http://ubuntuforums.org/showthread.php?p=3278523](http://ubuntuforums.org/showthread.php?p=3278523)

---

