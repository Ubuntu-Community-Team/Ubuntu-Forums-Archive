---
title: "iptables confusion -I vs -A"
date: 2007-03-09
forum: Networking &amp; Wireless
---

### Post by Lars Noodén on 2007-03-09
I'm getting a behavior I can't figure out with iptables.  I used to use it a lot, but seem to have forgotten something.  I'm using kernel 2.6.17-10-powerpc #2 Fri Oct 13 16:37:41 on edgy.

The rules below here ought to let all packets through.  But they do not.  Now if I start changing the **-A**'s to **-I**'s, then packets get through.

What's up with that?

[INDENT]iptables -P INPUT   DROP;
iptables -P OUTPUT  DROP;
iptables -P FORWARD DROP;

iptables -N INFILTER
iptables -N OUTFILTER

iptables -A INPUT     -j INFILTER
iptables -A OUTPUT    -j OUTFILTER

iptables -A INFILTER  -j ACCEPT
iptables -A OUTFILTER -j ACCEPT[/INDENT]

Here is the list of the filters  as seen from *iptables.*  The bold number is not what I would expect.  I would expect 127.0.0.1.

[INDENT]Setting filter rules for **127.0.1.1**

Chain INPUT (policy DROP)
target     prot opt source               destination
INFILTER   all  --  anywhere             anywhere

Chain FORWARD (policy DROP)
target     prot opt source               destination

Chain OUTPUT (policy DROP)
target     prot opt source               destination
OUTFILTER  all  --  anywhere             anywhere

Chain INFILTER (1 references)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere

Chain OUTFILTER (1 references)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
[/INDENT]

Below is the output from *ifconfig*.  Only two network interfaces.

[INDENT]eth1      Link encap:Ethernet  HWaddr 00:11:24:74:97:BC
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:24ff:fe74:97bc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:172511 errors:0 dropped:0 overruns:0 frame:0
          TX packets:122124 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:253475133 (241.7 MiB)  TX bytes:12270260 (11.7 MiB)
          Interrupt:41 Base address:0x6000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)[/INDENT]

---

### Post by koenn on 2007-03-09
-A is append, and -I is insert so your choice influences the order of the rules, and the order is important because the first match will be applied. 
Maybe you should review your iptables statements from that perspective (and read man iptables for details)

---

