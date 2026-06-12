---
title: "Chilli-Coova client use Squid Transparent Proxy"
date: 2015-02-15
forum: Networking &amp; Wireless
---

### Post by rani2 on 2015-02-15
Help me,,,
I have Ubuntu Server 12.04 with CoovaChilli
My CoovaChilli work and My Squid work good too (Squid work well for non hotspot client)

I googling and found this for my chilli configuration
```
##Allow transparent proxy (wiboon 1/2)
iptables -A INPUT -p tcp -m tcp --dport 3128 --syn -j ACCEPT

##Allow transparent proxy (wiboon 2/2)

iptables -t nat -A PREROUTING -i tun0 -p tcp -m tcp --dport 3128 --syn -j DROP
iptables -t nat -A PREROUTING -i tun0 -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 3128
```

my Chilli create tun0 under eth1 interface,
but ```
iptables -t nat -A PREROUTING -i tun0 -p tcp -m tcp --dport 3128 --syn -j DROP
``` not work
can you help me routing client hotspot to use proxy transparent?

---

### Post by SeijiSensei on 2015-02-15
That rule just blocks people from using the proxy directly.  I don't know what you mean by it "doesn't work," though I'd just drop it from the ruleset.  I suppose it's intended to keep people outside your network from using the proxy, but the better solution for that is to bind Squid to the localhost interface:
```
http_port 127.0.0.1:3128 transparent
```
That lets the REDIRECT rule send packets to the local port 3128 but makes the port invisible to anyone else.

---

### Post by rani2 on 2015-02-16
Thanks SeijiSensei

After add 
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination
DROP       all  --  0.0.0.0/0            0.0.0.0/0
ACCEPT     icmp --  0.0.0.0/0            172.20.2.1
ACCEPT     udp  --  0.0.0.0/0            172.20.2.1           udp dpt:53
ACCEPT     udp  --  0.0.0.0/0            172.20.2.1           udp dpts:67:68
ACCEPT     udp  --  0.0.0.0/0            255.255.255.255      udp dpts:67:68
ACCEPT     tcp  --  0.0.0.0/0            172.20.2.1           tcp dpt:4990
ACCEPT     tcp  --  0.0.0.0/0            172.20.2.1           tcp dpt:3990
DROP       all  --  0.0.0.0/0            172.20.2.1
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:3128 flags:0x17/0x02

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
DROP       all  --  0.0.0.0/0            0.0.0.0/0
TCPMSS     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp flags:0x06/0x02 TCPMSS clamp to PMTU
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0
DROP       all  --  0.0.0.0/0            0.0.0.0/0
DROP       all  --  0.0.0.0/0            0.0.0.0/0

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```
what should I do? remove function DROP from chilli? but It will make chilli not running properly
or should I add iptables rule to chilli before it DROP?


sorry for bad english

---

### Post by rani2 on 2015-02-16
I'm sorry SeijiSensei , , ,

My Squid 3.3 didn't accept transparent type or intercept type
I left my proxy 
```
http_port 3128
```
and it will work transparent, if I add transparent or intercept or tproxy, squid3 won't work,
squid3 will block everything

Thanks for your advance SeijiSensei

---

### Post by SeijiSensei on 2015-02-16
I'm running a Squid cache on a client's gateway.  We have "http_port 3128 transparent".  This machine has eth0 pointing to the Internet and eth1 pointing to the internal network.  All the machines in the building have this box as their default gateway.  The iptables ruleset includes:
```

/sbin/iptables -A PREROUTING -s local.ip.network.address/mask -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 3128
/sbin/iptables -A POSTROUTING -o eth0 -j SNAT --to-source ip.addr.of.eth0

```
with the appropriate IP addresses. That's all we've needed to run Squid as a transparent proxy.  Outbound traffic to any other ports except 80 is handled by the POSTROUTING rule which "masquerades" all that traffic as coming from the IP address assigned to eth0.  Traffic for port 80 on remote servers is intercepted and pushed through the local port 3128.

We also had to enable net.ipv4.ip_forward in /etc/sysctl.conf to let all the traffic not handled by Squid be passed across the interfaces.  On a Squid-only box you don't actually need to enable forwarding since Squid receives the request on the local interface then generates its own separate HTTP request on the Internet-facing one.

I don't know how your systems are configured, but that should give you a starting point.  We're using Squid 3.1.10 on CentOS 6.5, but I've tested the same configuration on Squid 3.3 and 3.4 built from source.

---

### Post by rani2 on 2015-02-23
Thank You SeijiSensei
all work well now ^_^

---

### Post by SeijiSensei on 2015-02-23
Glad to hear it!  Go up to the "Thread Tools" link at the top of the thread and mark this thread SOLVED.

---

