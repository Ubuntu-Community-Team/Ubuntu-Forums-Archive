---
title: "Ubuntu bridge causes tcp retransmission and DUP ACK"
date: 2018-04-14
forum: Networking &amp; Wireless
---

### Post by michaeleino2 on 2018-04-14
When I do configure a network bridge on my Ubuntu server I got each  packet to be retransmitted and getting many duplicate ACKs... [URL="https://i.stack.imgur.com/OuNmQ.png"]as this wireshark image:

[IMG]https://i.stack.imgur.com/OuNmQ.png[/IMG]

[/URL]

  my bridge interface config is:
  ```
iface enp5s0 inet manual


auto br0
iface br0 inet static
      address 172.25.25.1
      netmask 255.255.255.0
      network 172.25.25.0
      gateway 172.25.25.251
      broadcast 172.25.25.255
      dns-nameservers 172.25.25.251
      bridge_ports enp5s0
      bridge_stp off
      bridge_fd 0
      bridge_maxwait 0

```  
Kernel: Linux 4.13.0-38-generic #43~16.04.1-Ubuntu x86_64 
OS: Ubuntu 16.04.4 LTS

  
my ethtool results:

  ```
ethtool enp5s0
Settings for enp5s0:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Speed: 1000Mb/s
    Duplex: Full
    Port: Twisted Pair
    PHYAD: 1
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: on
    Supports Wake-on: g
    Wake-on: g
    Link detected: yes

```  also I do set 
  ```
sysctl net.bridge.bridge-nf-call-iptables=0

```  Do I miss any thing? or is it a bug somewhere ? or there is a something messy!

  I have tried the hwe kernel 4.13 and the generic 4.4 tried to change the switch/cables .. all the same, just removing the bridge interface and add the ip directly solves the issue.

---

### Post by The Cog on 2018-04-14
Which interface are you tracing on? I wonder if you chose "any" and are simply capturing the same packet twice - once on br0 and again on enp5s0. Just a guess though.
EDIT:
As an afterthought, the only way to prove they are duplicates is to take a trace from outside the machine - run tcpdump or wireshark on the other PC to see if the duplicates are real.

---

### Post by michaeleino2 on 2018-04-14
thanks Cog for you response!
was it that easy? I weren't to think that this is just a wireshark marking... and was thinking it is an actual network error.. specially with the tcp-out-of-order packets that follows those retransmission!
[ATTACH=CONFIG]279295[/ATTACH]
when I capture the traffic for br0, enp5s0 separately it looks fine.

Many thanks :)

---

