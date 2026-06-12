---
title: "How can I create a simple Access Point?"
date: 2008-11-09
forum: Networking &amp; Wireless
---

### Post by tylermenezes on 2008-11-09
I have been trying for literally 6+ hours to get a wireless access point working. I've tried every tutorial I could find. I have a wireless access card, ath0, running in master mode, and a wired ethernet card eth1. I need to get the traffic from ath0 -> eth1 however possible. eth1 is connected to router which dynamically assigns it an IP via DHCP (always 192.168.0.50 if it makes a difference). (Technically there's also another router in-between them, but it's just acting as a layer 2 switch, not doing any sort of NAT or anything.)

This is an old laptop running as a server, and it only has room for two cards, both used now, so however this is done the machine still needs to be able to send its own traffic to eth1. The ideal way of doing this, I guess, is to have the PC just repeat traffic on both segments of the network. I have no idea how to do that or if it's even possible, so having it do some sort of NAT would work too.

The only really important thing is that connected devices on ath0 need to get the gateway, IP, DNS, etc. assigned dynamically. For whatever reason, all the tutorials I've tried have either failed to do the DHCP stuff, failed to actually transmit the traffic from one interface to the other, or failed at both. A lot of them don't even seem to make sense, switching from eth0 to eth1 for no reason, or changing from 192.168.1.0/24 to 10.0.0.0/24 suddenly.

Please tell me someone knows how to do this! It doesn't seem like it should be too hard, it's already running MadWifi, it's just the data transit now.

Eternally thankful,
Tyler Menezes

---

### Post by tylermenezes on 2008-11-11
I don't mean to bump this up (actually that's exactly what I mean to do, I guess) but doesn't anyone have *any* ideas?

---

### Post by deltaprime on 2008-11-11
im interested as well but no idea how to do that.... sorry

delta

---

### Post by Jayock on 2008-11-11
Did something similar a while back, on Fedora.

AFAIK, the wireless card can only connect to one computer, so it won't be a true access point.  This is what I did anyways, and is the limit as I understood it.

Essentially you set up both connections, and bridge the two.

---

### Post by pdc124 on 2008-11-27
ive done this in gentoo and am trying to get a friends' ubuntu laptop to do it - but why is it so difficult ????

steps ( in gentoo) 
active wired card  to get network connection 
configure wireless card 
eg
ifconfig wlan0 10.0.0.1
iwconfig wlan0 essid "mywireless" mode ad-hoc channel 6

start wireless card 

start dhcp server on wireless card 
/etc/init.d/dnsmasq start ( or dnsmasq -i wlan0 --dhcp-range 10.0.0.10,10.0.0.50 -d ) 
sort out IP tables with shorewall 

/etc/init./shorewall start 

and it works 

but i cant get further than trying to get the cards and dnsmasq configured.
 so ( in ubuntu desktop ) 

How do i bring both  cards down 
how do i restart just the wired 
how do  stop whatever it is that is preventing dnsmasq  listening on wlan0 ?

eg 
paul@paul-desktop:/etc/default$ sudo /etc/init.d/networking stop
 * Deconfiguring network interfaces...                                                                                                                                                [ OK ]
so why do the cards still appear as active ?

paul@paul-desktop:/etc/default$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0b:6a:08:b0:c5
          inet addr:192.168.0.204  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:6aff:fe08:b0c5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4346 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3862 errors:0 dropped:0 overruns:0 carrier:0
          collisions:1 txqueuelen:1000
          RX bytes:3024951 (2.8 MB)  TX bytes:537295 (524.7 KB)
          Interrupt:17 Base address:0xee00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:800 (800.0 B)  TX bytes:800 (800.0 B)

wlan1     Link encap:Ethernet  HWaddr 00:11:3b:13:d0:35
          inet addr:10.2.0.1  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::211:3bff:fe13:d035/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:4 overruns:0 frame:0
          TX packets:780 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:43462 (42.4 KB)

but if i then try and stop a card 

paul@paul-desktop:/etc/default$ sudo ifdown eth0
ifdown: interface eth0 not configured
paul@paul-desktop:/etc/default$                                          


so im stuck

---

### Post by pdc124 on 2008-11-28
i can configure a wireless card and see the network with another laptop. But i cant find  whatever the deafult process is that stops dnsmasq running and giving out IP addresses 

paul@paul-desktop:/etc/default$ sudo dnsmasq -i wlan1 -F 10.2.0.10,10.2.0.50 -d

dnsmasq: failed to bind DHCP server socket: Address already in use
paul@paul-desktop:/etc/default$ sudo netstat -ap | grep bootps
udp        0      0 *:bootps                *:*                                 4832/dnsmasq
paul@paul-desktop:/etc/default$ dnsmasq stop

so what is happening is that dnsmasq, once installed starts on boot.
so diabling it on startup and rebooting means I can start the DHCP server 

paul@paul-desktop:~$ sudo dnsmasq -i wlan1 -F 10.2.0.10,10.2.0.50 -d
dnsmasq: started, version 2.41 cachesize 150
dnsmasq: compile time options: IPv6 GNU-getopt no-ISC-leasefile DBus I18N TFTP
dnsmasq: DHCP, IP range 10.2.0.10 -- 10.2.0.100, lease time 12h
dnsmasq: DHCP, IP range 10.2.0.10 -- 10.2.0.50, lease time 1h
dnsmasq: reading /etc/resolv.conf
dnsmasq: using nameserver 192.168.0.254#53
dnsmasq: read /etc/hosts - 9 addresses
                             
With the laptop , i can see the new wireless network but when i try and  connect with my laptop it says NODHCP OFFERS
and nothing appears at the server side.

Ho hum

---

### Post by pdc124 on 2008-11-28
so i now thinkt he problem is to do with brinign up the wireless card . Ive installed wireshark andwhen i ty to connect with a client there is no traffic through the card.
paul@paul-desktop:/etc/default$ sudo ifconfig wlan1
wlan1     Link encap:Ethernet  HWaddr 00:11:3b:13:d0:35
          inet addr:10.2.0.1  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::211:3bff:fe13:d035/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:10 overruns:0 frame:0
          TX packets:6963 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:366696 (358.1 KB)


would indicate that the card is active.
 but when i do this 
paul@paul-desktop:/etc/default$ sudo ifdown wlan0
ifdown: interface wlan0 not configured
paul@paul-desktop:/etc/default$         

it thinks it isnt active 

when i do this 
paul@paul-desktop:/etc/default$ sudo ifconfig wlan1 down

wireshark tells me the card isnt active yet lsiting it ( without the -a ) shows it still is. 

paul@paul-desktop:/etc/default$ sudo ifconfig wlan1
wlan1     Link encap:Ethernet  HWaddr 00:11:3b:13:d0:35
          inet addr:10.2.0.1  Bcast:10.255.255.255  Mask:255.0.0.0
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:17 dropped:16 overruns:0 frame:0
          TX packets:6991 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:368068 (359.4 KB)

paul@paul-desktop:/etc/default$              


so can anyone explain this , and how I get an active wireless card that will receive DHCP requests ?

---

