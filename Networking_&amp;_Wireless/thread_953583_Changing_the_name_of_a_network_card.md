---
title: "Changing the name of a network card"
date: 2008-10-20
forum: Networking &amp; Wireless
---

### Post by Scormen on 2008-10-20
Hi all,

I have 3 network cards in my computer (a server for dhcp, firewall, network bonding, etc - 1 NIC is on the motherbord, the other 2 are PCI's). How can I know what card is eth0, eth1 or eth2?

With a brand new installation with Ubuntu 8.04 (server edition) I'm having also a strange problem. After the installation, the names of my network cards are "eth0", "eth1" and "eth1_rename". Is there a way to rename that card with name "eth1_rename"?

Thanks,
Kris

---

### Post by pedro_orange on 2008-10-20
This will tell you about your network cards:

```
sudo lshw -C network
```

I'm not sure if you can rename what the logical name of a NIC is, however it is theoretically possible. 
I found a link on google you might find useful:

[http://www.xenotime.net/linux/doc/network-interface-names.txt](http://www.xenotime.net/linux/doc/network-interface-names.txt)

---

### Post by Scormen on 2008-10-21
Hi!

Thanks for your answer.

I know lshw, but how do I now what "physical id" is the real peace of hardware in my server?

I'll gonna have a greater look at that document of your link, but the pahts for the program files are different, that file is quite not for Ubuntu/Debian ;) 

Someone else maybe?

Thanks again,
Kris

---

### Post by Scormen on 2008-10-22
Hi all,

I have found this howto: [How to change network interface names in Ubuntu (click)](http://www.jusupov.com/2008/07/23/how-to-change-network-interface-names-in-ubuntu/)

In the file **/etc/network/if-post-down.d/ifenslave** I have this:
```
# PCI device 0x10ec:0x8169 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:17:3f:9a:00:0e", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:0x8169 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:17:3f:9a:00:0e", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# PCI device 0x10ec:0x8139 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:10:dc:2d:9c:e7", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"

# PCI device 0x10ec:0x8169 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:17:3f:9b:f2:e9", ATTR{type}=="1", KERNEL=="eth*", NAME="eth3"
```

Now, the name of the last interface is "eth3". When I restart the server the name is "eth1_rename". When I restart again, it is again "eth3", and so on...

I am using network bonding with [ifenslave](packages.ubuntu.com/nl/hardy/ifenslave-2.6) ([info here](http://www.linuxhorizon.ro/bonding.html)) because it is a bussy line...

"eth0" and "eth3" are bonded to "bond0". Here is my **/etc/network/interfaces**:
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth2
iface eth2 inet static
   address 10.10.10.31
   gateway 10.10.10.4
   netmask 255.255.255.192

auto bond0
   iface bond0 inet static
   address 192.168.1.1
   netmask 255.255.255.0
   post-up ifenslave bond0 eth0 eth3
```


Here is my **lshw -C Network**:

```
root@router:/home/kris# lshw -C Network
  *-network:0             
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:17:3f:9a:00:0e
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full latency=64 link=yes maxlatency=64 mingnt=32 module=r8169 multicast=yes port=twisted pair slave=yes speed=100MB/s
  *-network:1 DISABLED
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth1_rename
       version: 10
       serial: 00:17:3f:9a:00:0e
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full latency=64 link=yes maxlatency=64 mingnt=32 module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network:2
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:02:06.0
       logical name: eth2
       version: 10
       serial: 00:10:dc:2d:9c:e7
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=10.10.10.31 latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: bond0
       serial: 00:17:3f:9a:00:0e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bonding driverversion=3.2.3 firmware=2 ip=192.168.1.1 master=yes multicast=yes
```

Does anybody have a idea or a solution?

Many thanks,
Kris

---

### Post by Scormen on 2008-10-25
Hi all,

I'm still having the same problem. Nobody a idea? ;) 

Many thanks,
Kris

---

### Post by Scormen on 2008-11-08
The very last bumpy ;)

---

