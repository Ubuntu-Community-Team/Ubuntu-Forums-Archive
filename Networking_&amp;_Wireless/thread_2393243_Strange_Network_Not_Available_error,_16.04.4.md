---
title: "Strange Network Not Available error, 16.04.4"
date: 2018-05-31
forum: Networking &amp; Wireless
---

### Post by JKyleOKC on 2018-05-31
I'm in the process, finally, of migrating my production system from 14.04.5 to 16.04.4, and have run into a strange problem. The production system itself has full WAN and LAN connectivity on both the old and the new versions (they are on separate hard drives, to be able to maintain continuity of my files). However the other box on my LAN is able to connect to both versions for local traffic, but gets a Network Not Available error when attempting to access the WAN through 16.04. I'm typing this, however, with the 14.04 version running on the production box and I am on the other one.

However, I can ping the production box from this one; pinging any WAN address works if production is running 14.04 but not if it's on 16.04. And so far as I can determine, the critical files such as "ip route" and "iptables" are essentially identical (only the interface names changed) for both versions on the production box.

I'm out of ideas for troubleshooting techniques. Suggestions?

---

### Post by TheFu on 2018-05-31
You lost me in the nebulous description.  Can you please dumb it down with specific hostnames, specific commands, and specific protocols?

I moved most of my 14.04 to 16.04 last Feb. Stuff I saw was:
*  An incompatible perl;  I use perlbrew on 1 system and the non-OS perl confused the upgrade process.  
* Then about a month ago, ssh decided to stop working on 1 system and needed a new config line added.   
* Web servers and DBs migrated pretty cleanly.
* I think resolvconf and systemd were minor things I had to handle too.  I still fight with both from time to time, but mainly on laptops, not servers.

What to the log files show?  Look at the client and server logs.

---

### Post by JKyleOKC on 2018-05-31
Neither of the two boxes shows any trace in /var/log/syslog of the attempts to ping the WAN gateway (an AT&T combination modem/router). I'll have to try to organize my details offline and post them in another reply. Resolvcong and systemd may well be the problem; the 14.04 box doesn't seem to have many of the systemd packages in place!

---

### Post by JKyleOKC on 2018-05-31
Here are the details, probably much more than you want to see:```
On hostname=mehitabel (the production box/router, running 14.04.5):
  lsb-release:
    DISTRIB_ID=Ubuntu
    DISTRIB_RELEASE=14.04
    DISTRIB_CODENAME=trusty
    DISTRIB_DESCRIPTION="Ubuntu 14.04.5 LTS"
  ifconfig:
    eth0    Link encap:Ethernet  HWaddr 70:71:bc:c9:fa:f8  
            inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
            inet6 addr: fe80::7271:bcff:fec9:faf8/64 Scope:Link
            UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
            RX packets:5194 errors:0 dropped:0 overruns:0 frame:0
            TX packets:8213 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000 
            RX bytes:627784 (627.7 KB)  TX bytes:9429875 (9.4 MB)
  resolv.conf:
    nameserver 192.168.1.254
    search attlocal.net mylan

On hostname=mehitabel (the production box/router, running 16.04.4):
  lsb-release:
    DISTRIB_ID=Ubuntu
    DISTRIB_RELEASE=16.04
    DISTRIB_CODENAME=xenial
    DISTRIB_DESCRIPTION="Ubuntu 16.04.4 LTS"
  ifconfig:
    enp0s7  Link encap:Ethernet  HWaddr 70:71:bc:c9:fa:f8  
            inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
            inet6 addr: fe80::7271:bcff:fec9:faf8/64 Scope:Link
            UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
            RX packets:89 errors:0 dropped:0 overruns:0 frame:0
            TX packets:117 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000 
            RX bytes:10422 (10.4 KB)  TX bytes:13346 (13.3 KB)
  resolv.conf:
    nameserver 192.168.1.254
    search attlocal.net mylan

On hostname=xubuntu2 (the box that cannot connect to WAN when mehitabel uses 16.04):
  lsb-release:
    DISTRIB_ID=Ubuntu
    DISTRIB_RELEASE=16.04
    DISTRIB_CODENAME=xenial
    DISTRIB_DESCRIPTION="Ubuntu 16.04.4 LTS"
  ifconfig:
    enp4s0  Link encap:Ethernet  HWaddr e8:40:f2:d4:51:2d  
            inet addr:192.168.0.5  Bcast:192.168.255.255  Mask:255.255.0.0
            inet6 addr: fe80::ea40:f2ff:fed4:512d/64 Scope:Link
            UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
            RX packets:24379 errors:0 dropped:0 overruns:0 frame:0
            TX packets:20823 errors:0 dropped:0 overruns:0 carrier:1
            collisions:0 txqueuelen:1000 
            RX bytes:16195517 (16.1 MB)  TX bytes:2463962 (2.4 MB)
  resolv.conf:
    nameserver 192.168.0.2
  ping -c3 mehitabel (with 14.04.5):
    PING mehitabel (192.168.0.2) 56(84) bytes of data.
    64 bytes from mehitabel (192.168.0.2): icmp_seq=1 ttl=64 time=0.340 ms
    64 bytes from mehitabel (192.168.0.2): icmp_seq=2 ttl=64 time=0.229 ms
    64 bytes from mehitabel (192.168.0.2): icmp_seq=3 ttl=64 time=0.201 ms
  ping -c3 mehitabel (with 16.04.4):
    PING mehitabel (192.168.0.2) 56(84) bytes of data.
    64 bytes from mehitabel (192.168.0.2): icmp_seq=1 ttl=64 time=0.217 ms
    64 bytes from mehitabel (192.168.0.2): icmp_seq=2 ttl=64 time=0.214 ms
    64 bytes from mehitabel (192.168.0.2): icmp_seq=3 ttl=64 time=0.204 ms
  ping -c3 google.com (with 14.04.5):
    PING google.com (172.217.9.142) 56(84) bytes of data.
    64 bytes from dfw25s26-in-f14.1e100.net (172.217.9.142): icmp_seq=1 ttl=53 time=31.6 ms
    64 bytes from dfw25s26-in-f14.1e100.net (172.217.9.142): icmp_seq=2 ttl=53 time=30.4 ms
    64 bytes from dfw25s26-in-f14.1e100.net (172.217.9.142): icmp_seq=3 ttl=53 time=30.7 ms

    --- google.com ping statistics ---
    3 packets transmitted, 3 received, 0% packet loss, time 2003ms
    rtt min/avg/max/mdev = 30.496/30.952/31.618/0.481 ms
ping -c3 google.com (with 16.04.4):
    PING google.com (172.217.9.142) 56(84) bytes of data.

    --- google.com ping statistics ---
    3 packets transmitted, 0 received, 100% packet loss, time 2025ms

```The last 8 lines of this tell the story. I've not found any mention of the LAN interfaces in any of the log files, except for a couple of entries during the repeated boot processes. They indicated that all went well. It's a true  puzzle!

---

### Post by The Cog on 2018-05-31
It looks to me as though your "production box / router" only has one interface. Very odd.
Can we please see the output of these two commands on the router with both versions of OS, and from xubuntu2 (total 3 sets of output):
```
ip link
ip route
sudo iptables-save
```

---

### Post by TheFu on 2018-05-31
Ping the router by ip
Ping 8.8.8.8 by ip
Ping google.com

Depending on which of those has the failure will determine what the issue is.  **Looks like the DNS settings are wrong on 16.04.**  Is the internal DNS 192.168.0.x or 192.168.1.x?

When I say ping the router, I mean the AT&T box.

---

### Post by JKyleOKC on 2018-06-01
> **The Cog said:**
> It looks to me as though your "production box / router" only has one interface. Very odd.
Can we please see the output of these two commands on the router with both versions of OS, and from xubuntu2 (total 3 sets of output):
```
ip link
ip route
sudo iptables-save
```
Here's what you requested -- just to keep the thread's continuity. However I'm feeling quite stupid now. I had used /etc/sysctl.d on the 16.04 installaion to enable forwarding, but had failed to uncomment the same line in /etc/sysctl.cong -- and apparently the commented-out line disabled it! removing the comment character solved the problem and I am posting this from the "xubuntu2" box!

```

These are all from the "mehitabel" box, which actually has three network adaptersw but only two are actually being used; the third (eth2/enp1s10) is a spare.

ip link (on 14.04):
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth2: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN mode DEFAULT group default qlen 1000
    link/ether 00:a0:cc:db:f0:cf brd ff:ff:ff:ff:ff:ff
3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP mode DEFAULT group default qlen 1000
    link/ether 00:1b:21:59:6a:e3 brd ff:ff:ff:ff:ff:ff
4: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP mode DEFAULT group default qlen 1000
    link/ether 70:71:bc:c9:fa:f8 brd ff:ff:ff:ff:ff:ff

ip route (on 14.04):
default via 192.168.1.254 dev eth1 
192.168.0.0/24 dev eth0  scope link 

sudo iptables-save (on 14.04):
# Generated by iptables-save v1.4.21 on Thu May 31 22:51:36 2018
*nat
:PREROUTING ACCEPT [147:43022]
:INPUT ACCEPT [36:6831]
:OUTPUT ACCEPT [914:58081]
:POSTROUTING ACCEPT [37:2220]
-A PREROUTING -i eth1 -p tcp -m tcp --dport 80 -j DNAT --to-destination 192.168.0.4:80
-A POSTROUTING -o eth1 -j MASQUERADE
COMMIT
# Completed on Thu May 31 22:51:36 2018
# Generated by iptables-save v1.4.21 on Thu May 31 22:51:36 2018
*mangle
:PREROUTING ACCEPT [11428:4253821]
:INPUT ACCEPT [11376:4240988]
:FORWARD ACCEPT [28:2176]
:OUTPUT ACCEPT [11173:1633439]
:POSTROUTING ACCEPT [11201:1635615]
COMMIT
# Completed on Thu May 31 22:51:36 2018
# Generated by iptables-save v1.4.21 on Thu May 31 22:51:36 2018
*filter
:INPUT DROP [0:0]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [11060:1624806]
:LOG_DROP - [0:0]
:fail2ban-dovecot - [0:0]
:fail2ban-dovecotauth - [0:0]
:fail2ban-postfix - [0:0]
:fail2ban-proftpd - [0:0]
:fail2ban-sasl - [0:0]
:fail2ban-ssh - [0:0]
-A INPUT -p tcp -m multiport --dports 25,465,587,143,220,993,110,995 -j fail2ban-dovecotauth
-A INPUT -p tcp -m multiport --dports 25,465,587,143,220,993,110,995 -j fail2ban-dovecot
-A INPUT -p tcp -m multiport --dports 25,465,587,143,220,993,110,995 -j fail2ban-sasl
-A INPUT -p tcp -m multiport --dports 25,465,587 -j fail2ban-postfix
-A INPUT -p tcp -m multiport --dports 21,20,990,989 -j fail2ban-proftpd
-A INPUT -p tcp -m multiport --dports 22 -j fail2ban-ssh
-A INPUT -s 58.240.0.0/15 -j REJECT --reject-with icmp-host-prohibited
-A INPUT -s 202.104.0.0/16 -j REJECT --reject-with icmp-host-prohibited
-A INPUT -s 67.217.34.238/32 -j REJECT --reject-with icmp-host-prohibited
-A INPUT -p udp -m udp --dport 7100 -j REJECT --reject-with icmp-host-prohibited
-A INPUT -s 192.168.0.0/16 -j ACCEPT
-A INPUT -i lo -j ACCEPT
-A INPUT -i eth0 -p tcp -m tcp --dport 22 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 20:21 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 25 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 51200:51299 -j ACCEPT
-A INPUT -p icmp -j ACCEPT
-A INPUT -i eth0 -j ACCEPT
-A INPUT -i eth1 -m state --state RELATED,ESTABLISHED -j ACCEPT
-A INPUT -j LOG_DROP
-A FORWARD -i eth0 -j ACCEPT
-A FORWARD -i eth1 -o eth0 -m state --state RELATED,ESTABLISHED -j ACCEPT
-A FORWARD -i eth1 -p tcp -m tcp --dport 80 -j ACCEPT
-A FORWARD -j LOG_DROP
-A LOG_DROP -j LOG --log-prefix "[IPTABLES] : "
-A LOG_DROP -j REJECT --reject-with icmp-host-prohibited
-A fail2ban-dovecot -j RETURN
-A fail2ban-dovecotauth -j RETURN
-A fail2ban-postfix -j RETURN
-A fail2ban-proftpd -j RETURN
-A fail2ban-sasl -j RETURN
-A fail2ban-ssh -j RETURN
COMMIT
# Completed on Thu May 31 22:51:36 2018
 
ip link (on 16.04):
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: enp1s10: <BROADCAST,MULTICAST> mtu 1500 qdisc pfifo_fast state DOWN mode DEFAULT group default qlen 1000
    link/ether 00:a0:cc:db:f0:cf brd ff:ff:ff:ff:ff:ff
3: enp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP mode DEFAULT group default qlen 1000
    link/ether 00:1b:21:59:6a:e3 brd ff:ff:ff:ff:ff:ff
4: enp0s7: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP mode DEFAULT group default qlen 1000
    link/ether 70:71:bc:c9:fa:f8 brd ff:ff:ff:ff:ff:ff
 
ip route (on 16.04):
default via 192.168.1.254 dev enp3s0 
192.168.0.0/24 dev enp0s7  scope link 
 
sudo iptables-save (on 16.04):
# Generated by iptables-save v1.6.0 on Thu May 31 23:11:59 2018
*nat
:PREROUTING ACCEPT [12:2174]
:INPUT ACCEPT [4:216]
:OUTPUT ACCEPT [58:3550]
:POSTROUTING ACCEPT [32:1861]
-A POSTROUTING -o enp3s0 -j MASQUERADE
COMMIT
# Completed on Thu May 31 23:11:59 2018
# Generated by iptables-save v1.6.0 on Thu May 31 23:11:59 2018
*mangle
:PREROUTING ACCEPT [316:30430]
:INPUT ACCEPT [312:29698]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [337:30159]
:POSTROUTING ACCEPT [350:30888]
COMMIT
# Completed on Thu May 31 23:11:59 2018
# Generated by iptables-save v1.6.0 on Thu May 31 23:11:59 2018
*filter
:INPUT DROP [0:0]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [236:22298]
:LOG_DROP - [0:0]
:f2b-sshd - [0:0]
-A INPUT -p tcp -m multiport --dports 22 -j f2b-sshd
-A INPUT -s 58.240.0.0/15 -j REJECT --reject-with icmp-host-prohibited
-A INPUT -s 202.104.0.0/16 -j REJECT --reject-with icmp-host-prohibited
-A INPUT -s 67.217.34.238/32 -j REJECT --reject-with icmp-host-prohibited
-A INPUT -p udp -m udp --dport 7100 -j REJECT --reject-with icmp-host-prohibited
-A INPUT -s 192.168.1.254/32 -j ACCEPT
-A INPUT -s 192.168.0.0/24 -j ACCEPT
-A INPUT -i lo -j ACCEPT
-A INPUT -i enp0s7 -p tcp -m tcp --dport 22 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 20:21 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 25 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 51200:51299 -j ACCEPT
-A INPUT -p icmp -j ACCEPT
-A INPUT -i enp0s7 -j ACCEPT
-A INPUT -i enp3s0 -m state --state RELATED,ESTABLISHED -j ACCEPT
-A INPUT -j LOG_DROP
-A FORWARD -i enp0s7 -j ACCEPT
-A FORWARD -i enp3s0 -o enp0s7 -m state --state RELATED,ESTABLISHED -j ACCEPT
-A FORWARD -i enp3s0 -p tcp -m tcp --dport 80 -j ACCEPT
-A FORWARD -j LOG_DROP
-A LOG_DROP -j LOG --log-prefix "[IPTABLES] : "
-A LOG_DROP -j REJECT --reject-with icmp-host-prohibited
-A f2b-sshd -j RETURN
COMMIT
# Completed on Thu May 31 23:11:59 2018

```

---

### Post by JKyleOKC on 2018-06-01
> **TheFu said:**
> Ping the router by ip
Ping 8.8.8.8 by ip
Ping google.com

Depending on which of those has the failure will determine what the issue is.  **Looks like the DNS settings are wrong on 16.04.**  Is the internal DNS 192.168.0.x or 192.168.1.x?

When I say ping the router, I mean the AT&T box.Actually there are separate subnets. 192.168.0.x is my LAN and 192.168.1.x is the connection to the 
AT&T box. I've set the netfilter on "xubuntu2" to 255.255.0.0 to allow it to access both with only one adapter. The "mehitabel" box serves as my LAN router and has separate adapters for each subnet.

However it was one of those very simple errors: I failed to note that /etc/sysctl.conf overrides things set by /etc/sysctl.d/* files and thus wound up with forwarding being disabled on the production box! Thanks to all for the quick responses, which steered me toward the solution!

EDIT: Actually the DNS settings are correct -- I maintain a local DNS server for my LAN, on the mehitable box. However I use the AT&T box's DNS links there and only the xubuntu2 box uses the local DNS. This is all a carryover from the days 10 years ago when my LAN had seven physical boxes and a dozen VMs, all active at the same time in my very small home office. It's now downsized to just the two boxes described in this thread, but I've stayed with the system design that has worked so well through the years.

---

### Post by The Cog on 2018-06-01
Glad you got it sorted. And I don't have to wade through the firewall rules. 
I remembered ip forwarding after I went to bed last night <Doh!>

---

### Post by JKyleOKC on 2019-01-03
> **The Cog said:**
> Glad you got it sorted. And I don't have to wade through the firewall rules. 
I remembered ip forwarding after I went to bed last night <Doh!>

And although the original problem got solved, Murphy's Law struck me again. On December 3, I stepped into my home office to discover that a leaking hot water heater was in the process of flooding the room! I quickly shut down the computers and began moving everything to a dry area. This meant disconnecting all wiring. We eventually moved everything out and stripped the soggy carpet and pad, right down to the slab. Took a full week to dry out the room. The computers remained off line until this week, when I got them back into the room and began putting things back together.

Both power up properly, and show no indications of any damage (neither got wet, thank goodness). I'm posting this via Mehitabel. However for some reason I seem to have no connection between Mehitabel and Xubuntu2. Attempting to ping Mehitabel from Xubuntu 2 results in a couple of hundred thousand bytes being transmitted from its sole network adapter, but no responses received. Mehitabel's logs show no bytes received or sent over the 192.168.0.2 interface, though ifconfig reported the interface as up and running. Between the two, my EZXS88W siwtch's lights indicate it's hearing from both ends, but the topmost green light blinks -- which I never saw before. Any ideas what it means? Is it time to replace the switch?

EDIT:  As usual, the cause was totally simple. In my rush to get things going, I had forgotten to pug the network cable into the adapter at the Mehitabel end, and misinterpreted the display on the switch. Plugged the cable in, and all now works as expected!

---

