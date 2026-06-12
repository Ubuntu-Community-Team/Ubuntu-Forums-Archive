---
title: "Route only port 3389 to internal network with iptables"
date: 2016-10-12
forum: Networking &amp; Wireless
---

### Post by niglas2 on 2016-10-12
I have a virtual machine (guest) that I want to be able to connect with RDP (remote desktop) to from outside, but I want to disallow the guest to reach internet in any other way than the RDP connection from outside.

The Host machine have two networks (br0 to the internet & virbr0 internally 192.168.122.0/24). Where virbr0 is the guest's network (guest ip 192.168.122.45), and br0 is the host machine's connection to the internet.

I want to create iptables rules that achieve this. This is as far as I got:
```

sudo iptables -t nat -A PREROUTING ! -s 192.168.122.0/24 -p tcp --dport 3389 -j DNAT --to 192.168.122.45
sudo iptables -t nat -A PREROUTING ! -s 192.168.122.0/24 -p udp --dport 3389 -j DNAT --to 192.168.122.45

sudo iptables -t nat -A POSTROUTING -s 192.168.122.0/24 ! -d  192.168.122.0/24 -p tcp --sport 3389 -j MASQUERADE --to-ports 1024-65535
sudo iptables -t nat -A POSTROUTING -s 192.168.122.0/24 ! -d  192.168.122.0/24 -p udp --sport 3389 -j MASQUERADE --to-ports 1024-65535
```

Other filter rules are set to accept all:
```

sudo iptables -P INPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
sudo iptables -P OUTPUT ACCEPT

sudo iptables -t nat -P PREROUTING ACCEPT
sudo iptables -t nat -P INPUT ACCEPT
sudo iptables -t nat -P OUTPUT ACCEPT
sudo iptables -t nat -P POSTROUTING ACCEPT
```

IPv4 forward is on:
```

$ sysctl net.ipv4.ip_forward
net.ipv4.ip_forward = 1
```

Any suggestions for correct pre/postrouting-rules?

---

### Post by Fire_Chief on 2016-10-14
Hi niglas2,

Your rules are not doing anything because they are using the same subnet on both sides of the nat mapping (source and destination).

As I understand it, you have a host machine with a single network interface (br0) that is used for Internet access. Is this connected to a modem and what IP address does it have assigned? By the way, br0 is normally a reserved name for a bridge interface that acts as a dumb connector (no IP address assigned) between two network interfaces. This just seems odd as you have described it...however.

If the br0 interface has a public IP address from your Internet provider, then your rules need to accept traffic on that interface and forward it to the private interface virbr0.
```
sudo iptables -A FORWARD -i br0 -o virbr0 -p tcp --syn --dport 3389 -m conntrack --ctstate NEW -j ACCEPT
```
Then you allow related traffic from this initial connection to pass through properly.
```
sudo iptables -A FORWARD -i br0 -o virbr0 -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A FORWARD -i virbr0 -o br0 -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
```
Set the default policy on the FORWARD table to DROP
```
sudo iptables -P FORWARD DROP
```
Then you can do the pre and post routing rules. Note that RDP is a TCP only port need, no UDP communication takes place for that.
```
sudo iptables -t nat -A PREROUTING -i br0 -p tcp --dport 3389 -j DNAT --to-destination 192.168.122.45
sudo iptables -t nat -A POSTROUTING -o virbr0 -p tcp --dport 3389 -d 192.168.122.45 -j SNAT --to-source {insert IP address for virbr0}
```
If the virtual machine is already on the same network as your host machine (via the bridge) and can reach the Internet directly, then all of this is irrelevant and you would just configure the firewall on the VM to allow TCP/3389 traffic to it from anywhere.

Hope this helps!
-Fire Chief

---

### Post by niglas2 on 2016-10-16
Thanks a lot Fire_Chief.

These were the rules I ended up adding in order to make it work:

```

sudo iptables -A FORWARD -o virbr0 -p tcp ! --dport 3389 -j REJECT --reject-with icmp-port-unreachable
sudo iptables -A FORWARD -i virbr0 -p tcp ! --sport 3389 -j REJECT --reject-with icmp-port-unreachable

sudo iptables -t nat -A PREROUTING ! -s 192.168.122.0/24 -p tcp --dport 3389 -j DNAT --to 192.168.122.45
sudo iptables -t nat -A POSTROUTING -s 192.168.122.0/24 ! -d 192.168.122.0/24 -p tcp --sport 3389 -j MASQUERADE --to-ports 1024-65535

```

---

