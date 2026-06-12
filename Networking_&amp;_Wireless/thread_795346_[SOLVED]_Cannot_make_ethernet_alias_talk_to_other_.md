---
title: "[SOLVED] Cannot make ethernet alias talk to other networks"
date: 2008-05-15
forum: Networking &amp; Wireless
---

### Post by jefframsey on 2008-05-15
I have tried this so many different ways and I cannot make it work.

I am new to Ubuntu, but not new to Linux. Been using linux for 10+ years now. A few different flavors.

This is on a clean install of Ubuntu 8.04 server.

My eth0 interface is 65.174.242.10, and it works fine.

My alias (eth0:0) is 65.174.242.8 and it can talk to all nodes on it's subnet, but cannot talk through the gateway to any node on another network.

Here is my current /etc/network/interfaces file:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 65.174.242.10
        netmask 255.255.255.240
        network 65.174.242.0
        broadcast 65.174.242.15
        gateway 65.174.242.5
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 65.174.242.10
        dns-search tmifp.com

auto eth0:0
iface eth0:0 inet static
        address 65.174.242.8
        netmask 255.255.255.240

#post-up ifconfig eth0:0 inet 65.174.242.8 netmask 255.255.255.240 gateway 65.174.242.5 up
#pre-down ifconfig eth0:0 down

#|---EOF---|

I also have tried it via the post-up/pre-down method. I have tried it manually from the command line via "ifconfig eth0:0 inet 65.174.242.8 netmask 255.255.255.240". I have tried it with all, one, or some of broadcast/network/gateway options specified, via either method, and still nothing.

My routing table looks like this:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
localnet        *               255.255.255.240 U     0      0        0 eth0
default         fw1.tmifp.com   0.0.0.0         UG    100    0        0 eth0


Am I missing something? Is there some manual routing or interface configuration that I am overlooking? It should work on the command line via ifconfig without any other info, correct?

EDIT: I removed all references to eth0:0 from /etc/networks/interfaces and rebooted the machine. I then typed in the following as root:

ifconfig eth0:0 65.174.242.8 netmask 255.255.255.240

Then I typed ifconfig and got:

eth0      Link encap:Ethernet  HWaddr 00:02:e3:22:8d:d4  
          inet addr:65.174.242.10  Bcast:65.174.242.15  Mask:255.255.255.240
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24895 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25318 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3440862 (3.2 MB)  TX bytes:3623910 (3.4 MB)
          Interrupt:5 Base address:0xe000 

eth0:0    Link encap:Ethernet  HWaddr 00:02:e3:22:8d:d4  
          inet addr:65.174.242.8  Bcast:65.174.242.15  Mask:255.255.255.240
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:5 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:55 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7319 (7.1 KB)  TX bytes:7319 (7.1 KB)


And still, I get the same response.

My routing table is the same as above. I should not have a static route in the table for the alias, should I?

---

### Post by jefframsey on 2008-05-20
My router was not flushing the arp table properly. There was an outdated arp table entry in my router that was pointing the alias' IP to a different MAC ID.

Problem is solved.

---

