---
title: "2nd Network cards not recognized"
date: 2008-07-22
forum: Networking &amp; Wireless
---

### Post by airandfingers on 2008-07-22
Hi, I installed Ubuntu 8.04 on this computer, which has some sort of Intel processor and motherboard, with one ethernet card onboard. I am attempting to install a second onboard ethernet card, and set it up so that I can eventually send and receive traffic through both ports (actually from one to another, it's complicated).
I have tried the following cards:

Netgear FA311 ([http://www.netgear.com/Products/Adapters/WiredAdapters/FA311.aspx](http://www.netgear.com/Products/Adapters/WiredAdapters/FA311.aspx))

Linksys LNE100TX ([http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1115416833483&pagename=Linksys%2FCommon%2FVisitorWrapper](http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1115416833483&pagename=Linksys%2FCommon%2FVisitorWrapper))

3com SOHO100B-TX ([http://www.3com.com/products/en_US/detail.jsp?tab=features&pathtype=purchase&sku=3CSOHO100B-TX](http://www.3com.com/products/en_US/detail.jsp?tab=features&pathtype=purchase&sku=3CSOHO100B-TX))

I am simply plugging these into the PCI slot while the machine is off, then booting the computer and attempting to use the Internet. None work. The lscpci command shows only one ethernet card at a time (always the onboard card), and I have also tried these commands per some other forum posts. Sorry for pasting so many of them, I just want to provide as much information as possible.

user@machine:~$ more /etc/network/interfaces
auto lo
iface lo inet loopback

user@machine:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.19.36.0     *               255.255.252.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         172.19.39.254   0.0.0.0         UG    0      0        0 eth0

user@machine:~$ dmesg | grep eth
[   14.272362] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[   14.293080] Driver 'sd' needs updating - please use bus_type methods
[   14.293468]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   34.973530] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1747.103525] e1000: eth0: e1000_watchdog: NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX/TX
[ 1747.107650] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1772.955265] eth0: no IPv6 routers present
[ 1777.440702] e1000: eth0: e1000_watchdog: NIC Link is Down
[ 1829.314655] e1000: eth0: e1000_watchdog: NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX/TX
[ 1829.318415] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1843.726009] eth0: no IPv6 routers present

user@machine:~$ grep -R eth /etc/modprobe.d/*
/etc/modprobe.d/blacklist:blacklist eth1394

user@ machine:~$ sudo lshw -C network
[sudo] password for user: 
  *-network               
       description: Ethernet interface
       product: 82547EI Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 00
       serial: 00:0c:f1:86:97:a5
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI duplex=full firmware=N/A ip=172.19.36.43 latency=0 link=yes mingnt=255 module=e1000 multicast=yes port=twisted pair speed=1GB/s

user@machine:~$ sudo modprobe 3c59x
[no output]

user@machine:~$ cd /sys/bus/pci/drivers
user@machine:/sys/bus/pci/drivers$ find -name '0000:00:0b:0'
[no output]
user@machine:/sys/bus/pci/drivers$ find -name '0000:00:11:0'
[no output]

I'd appreciate any and all suggestions :)

---

### Post by tech0007 on 2008-07-22
It seems you have a busted PCI slot after trying several different cards. I use card from Realtek and it works fine.

---

### Post by airandfingers on 2008-07-22
I'm sorry, but I don't quite understand, is one of these three cards a Realtek? (I would assume it's the 3Com one).
I plugged the 3Com and Netgear cards into my top PCI slot, and my Linksys card into the second slot. I can try putting one card in each (there are three slots total) and seeing what happens, but I get the same result for two cards in two different slots..

I wound up putting all three cards into the computer, in the three PCI slots, and the output of the commands I tried is the same as above. Should I be looking at my motherboard instead of Ubuntu?

---

