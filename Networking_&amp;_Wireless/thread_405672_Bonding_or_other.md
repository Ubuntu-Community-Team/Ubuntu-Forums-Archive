---
title: "Bonding or other ???"
date: 2007-04-10
forum: Networking &amp; Wireless
---

### Post by Peque on 2007-04-10
Hey Forum. 

I have an installed server with LAMP on it.
At the office where it's placed there's redundant network. and have setup Nagios for survalient services.
The problem is the following. 

The host and services are comming up and down constantly all the time. I cannot find anything in the logfiles about this problem. 

I have setup Bonding with the 2 NIC - but when I ping the machine I get the following result: 
pbj@CAN1:~$ ping -c 100 192.168.1.20
PING 192.168.1.20 (192.168.1.20) 56(84) bytes of data.
64 bytes from 192.168.1.20: icmp_seq=1 ttl=64 time=2.50 ms
64 bytes from 192.168.1.20: icmp_seq=1 ttl=64 time=2.51 ms (DUP!)
64 bytes from 192.168.1.20: icmp_seq=2 ttl=64 time=0.094 ms
64 bytes from 192.168.1.20: icmp_seq=2 ttl=64 time=0.098 ms (DUP!)
64 bytes from 192.168.1.20: icmp_seq=3 ttl=64 time=0.093 ms
64 bytes from 192.168.1.20: icmp_seq=3 ttl=64 time=0.097 ms (DUP!)
64 bytes from 192.168.1.20: icmp_seq=4 ttl=64 time=0.093 ms
64 bytes from 192.168.1.20: icmp_seq=4 ttl=64 time=0.096 ms (DUP!)

It seems  like the netcards are dublicated ??? 
I have the following setup : 
# cat /etc/modprobe.d/bond0
options bonding mode=1 miimon=100

# cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
mousedev
psmouse
bonding

# cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.


# NIC Bonding interfaces
auto bond0
iface bond0 inet static
        address         192.168.1.20
        netmask         255.255.255.0
        gateway         192.168.1.1
        broadcast       192.168.1.255
#       dns-nameservers 192.168.1.2

up ifenslave bond0 eth0 eth1
down ifenslave -d bond0 eth0 eth1

Is there somewhere somethings that I have missed - The result I want is a failover solution so if the one are failing the other one takes over??? 
The server: 
Dell 1950 Poweredge
Ubuntu Edgy
0000:05:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5721 Gigabit Ethernet PCI Express (rev 11)
0000:06:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5721 Gigabit Ethernet PCI Express (rev 11)


Have someone a good idea of the solution for this problem???  Caurse I have 2other machines running on the network without any problems?? 

Thanks 
PBJ

---

