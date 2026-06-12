---
title: "Con't connect to internet"
date: 2006-08-03
forum: Networking &amp; Wireless
---

### Post by The Shadow on 2006-08-03
I have an HP dv8000 Turion64 laptop with a realteck RTL8139 PCI Fast Ethernet card. I seem to have a connection to my router, but i can't get access to the internet.

ifconfig results are:

etho Link encap:Ethernet HWaddr 00:0f:B0:BD:72:6E
      init addr:192.168.1.104 Bcast:192.168.1.225 Mask: 255.255.255.0
      inet6 addr: fe80:20f:b0ff:febd:726e/64 Scope:link
       UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
      RX packets:355 errors:0 dropped:1407 overruns:0 frame:0
      TX packets:231 errors:0 dropped:0 overruns:0 carriers:0
      collisions:0 txqueuelen:1000
      RX bytes:62614  (61.1 KiB)  TX bytes:17743 (17.3 KiB)
      Interrupt:153 Base address: 0xa400

sudo ethtool results are:

Settings for eth0:
    Support ports: [ TP MII ]
     Supported link modes: 10baseT/ha;f 10baseT/full
                            100baseT/Half 100baseT/full
     Advertised auto-negotiation: Yes
      speed: 100Mb/s
     Duplex: Full
     Port: MII
     PHYAD: 32
     Transceiver: internal
      Auto-negotiation: on
     Supports Wake-on: pumbg
     wake-on: d
     Current messge level:0x00000007 (7)
     Link detected: yes

cat /etc/network/interfaces results are:

auto eth0
iface eth0 inet dhcp

auto eth1 
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


I re-booted my machine and now the network icon showes i am connected with eth0. it even showes a proper network address. But I still can not access the internet. I can't find anything about what sort of prototcols i might need to add or how to install them, but is it possible i don't have the TCP/IP protocol?

---

### Post by hasimir44 on 2006-08-03
you have tcp/ip installed (that's how you got an ip address..) 

try to ping google from inside of a terminal: 

ping [www.google.com](www.google.com)

(use control-C to stop the ping)

if you get replies from google, then you're connected to the internet. if you don't get replies, then try this: 

ping 66.102.7.104   (a google ip..)

if you get replies from pinging the ip address, but not the name [www.google.com](www.google.com) then you're connected, but you don't have name resolution (dns..) 

if neither give replies, then check your router's web based configuration and see if it says something like:

status: connected

good luck

---

### Post by The Shadow on 2006-08-04
Still no joy:confused: 

Ping [www.google.com](www.google.com) results in:
 no response


Ping 66.102.7.104 results in:

     Ping 66.102.7.104
     from 192.168.1.103 icmp_seq=2 Destination Host Unreachable
     66.102.7.104 ping statistics 22 packets transmitted, 0 received +15 error, 100% packet loss

any suggestions?

---

