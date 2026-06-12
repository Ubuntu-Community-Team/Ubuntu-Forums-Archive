---
title: "Unable to connect to the router"
date: 2008-07-16
forum: Networking &amp; Wireless
---

### Post by Lokz on 2008-07-16
I am running ubuntu-8.04.1-server-i386 on a old 662mhz with 128mb ram.

With the rj-45 ethernet cable plugged in the network card, it seems like I cannot connect to my router.

My router is a Apple Airport Extreme (b/g, not n).
I've tried the Ethernet WAN port on Automatic and 100mbps/integral duplex

Here is my network configuration
IP range: 10.0.1.x (max is .200)
Mask: 255.255.255.0
Gateway: 10.0.1.1
DHCP: 10.0.1.1
DNS: 10.0.1.1
(there is another computer, aside the ubuntu box on the server at 10.0.1.2)

The power light of my ethernet card is on, but the activity led isn't.

I've tried numerous things

ifconfig eth0 down
ifconfig eth0 10.0.1.9 netmask 255.255.255.0
route add default gw 10.0.1.1

vim /etc/resolv.conf
nameserver 10.0.1.1
:wq

ifconfig eth0 up
ping 10.0.1.1
PING 10.0.1.1 (10.0.1.1) 56(84) bytes of data.
unknown host destination

ping google.com
*after 4-5 secondes*
ping: unknown host google.com

dhclient eth0
Listening on LPF/eth0/[MAC_ADDR]
Sending on          "
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5 (then 10,21,11,8,6)
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

I've tried both a iface static and dhcp
/etc/network/interfaces
auto eth0
iface eth0 inet static
adress 10.0.1.9
netmask 255.255.255.0
network 10.0.1.0
broadcast 10.0.1.255
gateway 10.0.1.1
dns-nameservers 10.0.1.1
dns-search WORKGROUP

#I've also tried this (uncommented of course and not as the same time as the above
#auto eth0
#iface eth0 inet dhcp

/etc/resolv.conf
search WORKGROUP
nameserver 10.0.1.1

I've also tried
/etc/networks
G4NET 10.0.1

my /etc/host.conf looks like this
order hosts,bind
multi on

ifconfig shows
eth0 Link encap:Ethernet HWaddr 00:06:29:f7:62:07
     inet addr:10.0.1.9 Bcast:10.0.1.255 Mask:255.255.255.0
     UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueulen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:3 errors:0 dropped:0 overruns:0 frame:0
TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueulen:1000
RX bytes:264 (264.0 B) TX bytes:264 (264.0 B)

I've also tried pluging my modem directly in the ethernet card and it works just fine with dhclient (I get an ip and I can ping google.com)

Hope someone can help me or point me somewhere :)

---

### Post by Lokz on 2008-07-18
I've also tried to put my router in DMZ and to try connecting with my ubuntu box, no luck.

Any help? :(

---

### Post by Lokz on 2008-07-19
I will try installing ubuntu desktop instead and see if it works... Probably just a line of code I'm missing, oh well...

---

