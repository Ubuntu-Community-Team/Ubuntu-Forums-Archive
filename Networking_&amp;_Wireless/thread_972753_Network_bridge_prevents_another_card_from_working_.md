---
title: "Network bridge prevents another card from working + the solution."
date: 2008-11-06
forum: Networking &amp; Wireless
---

### Post by Bodwin on 2008-11-06
I reported this as a bug but I decided to post the same thing here if anyone should have the same problem as me.

[Background information]
OK, I have a computer with ubuntu 8.10 intrepid ibex distro. 
My kernel version is 2.6.27-7-generic.
 I have 3 ethernet cards.: eth0, eth1 and eth2. Eth0 and eth2 are in a bridge called br0 made with bridge-utils. Eth1 is connected to the internet through a ZTE ZXDSL 831 modem my ISP gave me. Here is my /etc/network/interfaces file for better understanding of the network setup:

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet manual

auto eth0
iface eth0 inet manual

auto br0
iface br0 inet static
   address 192.168.0.1
   netmask 255.255.255.0
   gateway 192.168.0.4
   network 192.168.0.0
   broadcast 192.168.0.255
   bridge_ports eth0 eth2
__________________________________
The version of bridge-utils is 1.4-3
__________________________________
Now I am not 100% sure about this but judging by the the way lspci command orders them I can say that:
eth0 is an: Intel Corporation 82810BA/BAM/CA/CAM Ethernet Controller
eth1 is a: Davicom Semiconductor, Inc. 21x4x Dec-Tulip compatible 10/100 Ethernet
eth2 is a: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+

[The problem]
Basically when I restart the network the dhcp assigns the right addresses to eth1 card but I have no ping to any external machine. The only thing I can ping is the modem.  Br0 works perfectly though. I found out that br0 actually prevents my card from working properly because if I delete it or take it down, eth1 works like a charm.

[My workaround]
What I noticed is that after a network restart if you take br0 down and then up both the bridge and eth1 work properly. So I made a script that is to be executed on startup containing these commands:
ifconfig br0 down
ifconfig br0 up

Good luck I hope this works for you as well as it works for me :)

---

### Post by Bodwin on 2008-11-06
Never mind I got it. Obviously I had to remove the gateway line at /etc/network/interfaces file for br0 because ubuntu tries to set 2 gateways. After removing it everything works properly. :lolflag:

---

