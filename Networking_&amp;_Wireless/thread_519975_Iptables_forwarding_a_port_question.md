---
title: "Iptables forwarding a port question?"
date: 2007-08-07
forum: Networking &amp; Wireless
---

### Post by mbiwpeoyc on 2007-08-07
I've got ubuntu server up and running and iptables/dhcp going with the help of this forum and a few friends. Now the question I have that's stumping my friends and isn't really covered at least with the current setup I have that's working.

Here's the current config

```
 170K   14M ACCEPT     0    --  lo     any     anywhere             anywhere
21103 2097K ACCEPT     0    --  eth0   any     anywhere             anywhere            state RELATED,ESTABLISHED
 2567  395K ACCEPT     0    --  eth1   any     172.27.68.0/24       anywhere
 1368 82068 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:ssh

Chain FORWARD (policy ACCEPT 29 packets, 2389 bytes)
 pkts bytes target     prot opt in     out     source               destination
 471K  273M ACCEPT     0    --  eth0   eth1    anywhere             anywhere            state RELATED,ESTABLISHED
 454K   37M ACCEPT     0    --  eth1   eth0    anywhere             anywhere

Chain OUTPUT (policy ACCEPT 112K packets, 11M bytes)
 pkts bytes target     prot opt in     out     source               destination
85271 7164K ACCEPT     0    --  any    lo      anywhere             anywhere
```

and my nat

```
Chain PREROUTING (policy ACCEPT 14052 packets, 1344K bytes)
 pkts bytes target     prot opt in     out     source               destination
56554   22M ACCEPT     0    --  eth0   any     anywhere             anywhere

Chain POSTROUTING (policy ACCEPT 1297 packets, 107K bytes)
 pkts bytes target     prot opt in     out     source               destination
10301  768K MASQUERADE  0    --  any    eth0    anywhere             anywhere

Chain OUTPUT (policy ACCEPT 1302 packets, 111K bytes)
 pkts bytes target     prot opt in     out     source               destination
```

we've added forward rules to prerouting and input, and forward and everything adn it still isn't opening a hole. So either a) I setup the rules wrong or b) I'm just not forwarding stuff properly.

eth0 = internet/comcast modem
eth1 = internal LAN

If I setup the rules wrong initially, someone please tell me what I did wrong and how to get traffic from eth1 to eth0 and back again. Or how I'm forwarding improperly :)

---

### Post by noob12 on 2007-08-08
Have you got forwarding enabled at the IP level?  This will tell you.

```

sudo sysctl -a 2>&1 | grep ip | grep forward

```

**man 7 ip**

---

### Post by Vola on 2007-08-08
please check the routing table, the ip forward is off by default:

```

route -n 
```

if you use a file for configure iptables at start time just add this:

```

echo "1" > /proc/sys/net/ipv4/ip_forward

```

---

### Post by noob12 on 2007-08-08
Or edit /etc/sysctl.conf

---

### Post by mbiwpeoyc on 2007-08-08
Here's the output
```

sudo sysctl -a 2>&1 | grep ip | grep forward

net.ipv6.conf.eth1.forwarding = 0
net.ipv6.conf.default.forwarding = 0
net.ipv6.conf.all.forwarding = 0
net.ipv6.conf.eth0.forwarding = 0
net.ipv6.conf.lo.forwarding = 0
net.ipv4.conf.eth1.mc_forwarding = 0
net.ipv4.conf.eth1.forwarding = 1
net.ipv4.conf.eth0.mc_forwarding = 0
net.ipv4.conf.eth0.forwarding = 1
net.ipv4.conf.lo.mc_forwarding = 0
net.ipv4.conf.lo.forwarding = 1
net.ipv4.conf.default.mc_forwarding = 0
net.ipv4.conf.default.forwarding = 1
net.ipv4.conf.all.mc_forwarding = 0
net.ipv4.conf.all.forwarding = 1
net.ipv4.ip_forward = 1

```

I did do the echo of 1 to ipv4 forward.

and I don't use ipv6 at all

---

### Post by noob12 on 2007-08-10
Sorry.  Lost this thread.  I didn't spot anything obvious.   Check your route table (as suggested by the other poster as well).  I'd suggest using the non-terminal LOG target to see what rules are being traversed.  Since your default policies are ACCEPT on every chain (except INPUT, which you didn't show and I presume is DENY), the only possible sources of problems are your INPUT chain and the MASQUERADE rule.

---

### Post by mbiwpeoyc on 2007-08-10
Actually I just fixed the problem last night.

$IPTABLES -A FORWARD -i $EXTIF -o $INTIF -m state --state ESTABLISHED,RELATED -j ACCEPT

$IPTABLES -A FORWARD -i $INTIF -o $EXTIF -j ACCEPT

$IPTABLES -t nat -A POSTROUTING -o $EXTIF -j MASQUERADE

That's what I was missing...got it working.

---

