---
title: "How do I know whether iptables is currently running?"
date: 2006-10-16
forum: Networking &amp; Wireless
---

### Post by xp_newbie on 2006-10-16
Using Synaptic Pakcage Manager I can tell that iptables is installed.

But how do I know whether it is actually running?

I checked System|Administration|Services but it only lists a few (weird since I could swear that there are many more services running on my machine).

Thanks!
Alex

---

### Post by TheWizzard on 2006-10-16
check syslog

---

### Post by mips on 2006-10-16
Well the ip_tables module is built into the kernel so should run by default when you start up.

to check if the module is loaded you can do a **lsmod | grep ip**

**sudo iptables -L** will show you the current rule set that is running I believe.

---

### Post by xp_newbie on 2006-10-16
> **mips said:**
> to check if the module is loaded you can do a **lsmod | grep ip**

I just did that and here is what I get:

> ipv6                  286976  20 
ipw3945               132348  1 
ieee80211              38952  1 ipw3945


Which one is iptables?

> **mips said:**
> 
**sudo iptables -L** will show you the current rule set that is running I believe.

I did that too and here is what I received:
> Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         


What does this mean?

Thanks,
Alex

---

### Post by mips on 2006-10-16
Is that all you get ? Does not look like the module is loaded.

Mine looks like this:
```
mips@obelix:~$ lsmod | grep ip
ipt_TCPMSS              4928  1
ipt_limit               2944  8
ip_nat_irc              3072  0
ip_nat_ftp              3840  0
iptable_nat             8580  1
iptable_mangle          3328  0
ipt_LOG                 7616  8
ipt_MASQUERADE          4160  1
ip_nat                 20972  4 ip_nat_irc,ip_nat_ftp,iptable_nat,ipt_MASQUERADE
ipt_TOS                 2880  0
ipt_REJECT              6592  1
ip_conntrack_irc        7280  1 ip_nat_irc
ip_conntrack_ftp        8560  1 ip_nat_ftp
ipt_state               2304  8
ip_conntrack           54488  8 ip_nat_irc,ip_nat_ftp,iptable_nat,ipt_MASQUERADE,ip_nat,ip_conntrack_irc,ip_conntrack_ftp,ipt_state
nfnetlink               7192  2 ip_nat,ip_conntrack
iptable_filter          3392  1
ip_tables              24000  10 ipt_TCPMSS,ipt_limit,iptable_nat,iptable_mangle,ipt_LOG,ipt_MASQUERADE,ipt_TOS,ipt_REJECT,ipt_state,iptable_filter
mips@obelix:~$
```

```
mips@obelix:~$ sudo iptables -L
Password:
Chain INBOUND (4 references)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED
LSI        all  --  anywhere             anywhere

Chain INPUT (policy DROP)
target     prot opt source               destination
ACCEPT     tcp  --  10.0.0.2             anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN
ACCEPT     udp  --  10.0.0.2             anywhere
ACCEPT     all  --  anywhere             anywhere
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5
DROP       all  --  anywhere             255.255.255.255
DROP       all  --  anywhere             10.255.255.255
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8
DROP       all  --  255.255.255.255      anywhere
DROP       all  --  anywhere             0.0.0.0
DROP       all  --  anywhere             anywhere            state INVALID
LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5
INBOUND    all  --  anywhere             anywhere
INBOUND    all  --  anywhere             192.168.0.1
INBOUND    all  --  anywhere             10.0.0.10
INBOUND    all  --  anywhere             192.168.0.255
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input'

Chain FORWARD (policy DROP)
target     prot opt source               destination
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5
TCPMSS     tcp  --  anywhere             anywhere            tcp flags:SYN,RST/SYN TCPMSS clamp to PMTU
OUTBOUND   all  --  anywhere             anywhere
ACCEPT     tcp  --  anywhere             192.168.0.0/24      state RELATED,ESTABLISHED
ACCEPT     udp  --  anywhere             192.168.0.0/24      state RELATED,ESTABLISHED
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward'

Chain LOG_FILTER (5 references)
target     prot opt source               destination

Chain LSI (2 references)
target     prot opt source               destination
LOG_FILTER  all  --  anywhere             anywhere
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       icmp --  anywhere             anywhere            icmp echo-request
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound '
DROP       all  --  anywhere             anywhere

Chain LSO (0 references)
target     prot opt source               destination
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound '
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable

Chain OUTBOUND (3 references)
target     prot opt source               destination
ACCEPT     icmp --  anywhere             anywhere
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     all  --  anywhere             anywhere

Chain OUTPUT (policy DROP)
target     prot opt source               destination
ACCEPT     tcp  --  10.0.0.10            10.0.0.2            tcp dpt:domain
ACCEPT     udp  --  10.0.0.10            10.0.0.2            udp dpt:domain
ACCEPT     all  --  anywhere             anywhere
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8
DROP       all  --  255.255.255.255      anywhere
DROP       all  --  anywhere             0.0.0.0
DROP       all  --  anywhere             anywhere            state INVALID
OUTBOUND   all  --  anywhere             anywhere
OUTBOUND   all  --  anywhere             anywhere
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output'
mips@obelix:~$ 
```

---

### Post by xp_newbie on 2006-10-16
Yes, that is all I get, and that is why I suspected that iptables is not running on my Ubuntu installation for some reason (is this how it is supposted to be out-of-the-box?)

What do I need to do to run it?

Thanks,
Alex

---

### Post by TheWizzard on 2006-10-16
there exist several gui tools to edit iptables. 
the most widely used (as far as i know) is firestarter. very easy to configure. 
the one i use is guarddog. this one is very restrictive, though. it allows nothing unless you give explicit permission for a protocol. 
both should be in your repo's.

---

### Post by xp_newbie on 2006-10-16
> **TheWizzard said:**
> there exist several gui tools to edit iptables.
Do they also **start** iptables? :???: 
If not, how do I start iptables?

> **TheWizzard said:**
> the one i use is guarddog. this one is very restrictive, though. it allows nothing unless you give explicit permission for a protocol.

Isn't this actually a feature of iptables itself?
If so, firestarter should be able to do that [too]("http://groups.google.com/group/alt.os.linux.mandrake/browse_frm/thread/bb6de7ad5679dddf/e87d24b078bed65f?tvc=1&q=firestarter+vs.+guardog&hl=en#e87d24b078bed65f"), right?

Thanks,
Alex

---

### Post by TheWizzard on 2006-10-17
> Do they also start iptables?
yes, you can enable and disable iptables from here.

> Isn't this actually a feature of iptables itself?

iptables does this, but firestarter makes generic, more relaxed default rules.

---

