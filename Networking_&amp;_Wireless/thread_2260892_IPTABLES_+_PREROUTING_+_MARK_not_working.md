---
title: "IPTABLES + PREROUTING + MARK not working"
date: 2015-01-15
forum: Networking &amp; Wireless
---

### Post by themedserv2 on 2015-01-15
Hi, I set up ip table bypass with mark and iptables on specifics ports.

It works fine on the ouput for let say port 80:
```
iptables -t mangle -A OUTPUT -p tcp --dport 80 -j MARK --set-mark 2
iptables --table nat --append POSTROUTING -o eth0 -j MASQUERADE
```

I put a rule with a custom table:
```
ip rule add fwmark 2 table 2
```

Everything works fine here. My table 2 is used when I connect from the inside to any website with port 80, my table main is bypassed and table 2 is used.
-----
When I want to bypass main table on incoming connection to 80 it doesn't work tho.
If I use a rule like this with sport or dport, and I also tried with 443:
```
sudo iptables -t mangle -A PREROUTING -p tcp --sport 80 -j MARK --set-mark 2 
or
sudo iptables -t mangle -A PREROUTING -p tcp --dport 80 -j MARK --set-mark 2 

```
main table is used :(...
All my rp_filter are set to 0 if check this:
```
sysctl -a | grep \\.rp_filter
```
All my forwarding are set to 1 if check this:
```
sysctl -a | grep \\.forwarding
```

I CAN acces my table 2 via this command. But then, all my connection are going in table 2.. I just want some ports to go in table 2. But with this:
```
ip rule add from 192.168.2.0/24 table 2
```
It works! but all my port are bypassing my table 1 and it is not what I want :(

Is there a command I missed or something to enable to Mark a packet on PREROUTING?

When i use tcpdump, i can see the connection trying to get in:
ethertype IPv4 (0x0800), length 66: xx.xxx.x.xx.**54052** > 192.168.2.xx.80: Flags [S], seq 1474137113, win 8192, options [mss 1460,nop,wscale 2,nop,nop,sackOK], length 0
Btw, what is this number: 54052

Thks please help on that!

---

### Post by themedserv2 on 2015-01-15
In other words, this works:
```
ip rule add from 192.168.2.0/24 table 2
```

But not this
```
ip rule add from all fwmark 2 lookup 2
# none of this works:
iptables -t mangle -A PREROUTING -j MARK --set-mark 2
iptables -t mangle -A INPUT -j MARK --set-mark 2
iptables -t nat -A INPUT -j MARK --set-mark 2
iptables -t nat -A PREROUTING -j MARK --set-mark 2

```

No mark is marked on the connection input NEVER..
BUT it works on the output
with this:
```
ip rule add from all fwmark 2 lookup 2
sudo iptables -t mangle -A OUTPUT -p tcp --dport 80 -j MARK --set-mark 2

# I Have no idea what this is doing but I need to make it work:
sudo iptables --table nat --append POSTROUTING -o eth0 -j MASQUERADE



```

---

### Post by Doug S on 2015-01-15
Hi and welcome to Ubuntu forums,

I am having trouble to understand what you are trying to do and why.

However, the answer to this question is simple enough:> **themedserv2 said:**
> When i use tcpdump, i can see the connection trying to get in:
ethertype IPv4 (0x0800), length 66: xx.xxx.x.xx.**54052** > 192.168.2.xx.80: Flags [S], seq 1474137113, win 8192, options [mss 1460,nop,wscale 2,nop,nop,sackOK], length 0
Btw, what is this number: 54052The computer at xx.xxx.x.xx is trying to access 192.168.2.xx port 80, and it is using its port 54052 to do so. This method of access is normal.

---

### Post by themedserv2 on 2015-01-15
Hi thanks for the response! I am glad to be part of the community!

Basically I am try to bypass my vpn on custom VPN ports. I want to access my server via my PUBLIC ISP address. But, when VPN is on, all my incoming connections are blocked. 

**table main** is My VPN
**table 2** is a normal connexion to the router via eth0.  something like: default via 192.168.0.1 dev eth0

So to do so I am trying to mark packets coming from specifics port via this iptables rule:

```
sudo iptables -t mangle -A PREROUTING -p tcp --sport 80 -j MARK --set-mark 2
ip rule add fwmark 2 table 2
```
But I can't get any packet to be marked in any of the PREROUTING / INPUT - MANGLE and NAT
I tried all of them without any port restriction:
```
iptables -t mangle -A PREROUTING -j MARK --set-mark 2
iptables -t mangle -A INPUT -j MARK --set-mark 2
iptables -t nat -A INPUT -j MARK --set-mark 2
iptables -t nat -A PREROUTING -j MARK --set-mark 2
```
And no packet get marked and pass to table 2.

if I use this tho:
```
ip rule add from 192.168.2.0/24 table 2
```
All my incoming connection are passing to the table 2. That is fine, but I want to do it per port.

Anyway I guess if I set all my incoming port to go to table 2 is not a big deal.. since VPN is usefull only on outgoing connections.

Does someone can tell me if it would be a problem to do so:
incoming -> no vpn
 outgoing connections -> vpn?

Thks!!!

---

### Post by themedserv2 on 2015-01-20
Found the solution, with a kernel > 3.16, had too enable kernel option like so:

```
sudo sysctl -w net.ipv4.tcp_fwmark_accept=1
```

Tutorial here:
[http://themediaserver.com/bypass-vpn-connections-specifics-ports-ubuntu-kodibuntu/](http://themediaserver.com/bypass-vpn-connections-specifics-ports-ubuntu-kodibuntu/)

Thks!

---

### Post by The Cog on 2015-01-20
Yikes!
Thank you really lots for posting the solution. That one was waiting to bite me big time, next time I upgrade. I would never have thought of that, and I use lots of tables and fwmarks.

---

