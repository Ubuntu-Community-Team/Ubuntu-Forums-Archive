---
title: "IPTABLES - Webmin - Interface Alias"
date: 2015-10-23
forum: Networking &amp; Wireless
---

### Post by victor67 on 2015-10-23
Hello Ubuntu Forums,

I'm having a hard time configuring my IPTABLES to do something specific. First I'd like to say that I am using webmin to make some tasks easier when... I know that all this does is sometimes confuse things. 

I have a server with 2 network cards. The first card is my WAN card which is /dev/em1. In my /etc/network/interfaces, I have my entries as follows:

```

# WAN network interface
auto em1
iface em1 inet static
    address aaa.bbb.ccc.103
    netmask 255.255.255.240
    network aaa.bbb.ccc.96
    broadcast aaa.bbb.ccc.111
    gateway aaa.bbb.ccc.97
    dns-nameservers 10.255.1.1 aaa.bbb.ccc.61 8.8.8.8
    dns-domain 10.255.1.1
    post-up iptables-restore < /etc/iptables.up.rules
    # dns-* options are implemented by the resolvconf package, if installed

auto em1
iface em1 inet static
        address aaa.bbb.ccc.107
        netmask 255.255.255.240

# LAN network interface
auto p255p1
iface p255p1 inet static
    address 10.255.1.1
    netmask 255.255.0.0
    network 10.255.0.0
    broadcast 10.255.255.255


```

So as you can tell I have 2 IP's. **aaa.bbb.ccc.103** and [B]aaa.bbb.ccc.107
[/B]
So what I want is when ever someone hits aaa.bbb.ccc.107:3001 ... id like it to go to 10.0.0.231:3001

How do I go about doing this?

---

### Post by victor67 on 2015-10-24
Now keep in mind that I don't need to do this via webmin. I only mention it because it's part of the installation I'm working with. I simply want to know who to port forward with a specific public ip to a machine in my network.

---

### Post by Doug S on 2015-10-24
Hi victor67,

And welcome to Ubuntu forums.

What you want to do with your iptables rule set is easy, however we would need to see your current rule set to know where to insert your port forward stuff.

Now, the bigger issue here is that your interfaces file makes no sense at all, at least not to me. You have two address assigned to em1 and you are not on any sub-net that includes 10.0.0.231.

Anyway, to do what you want (once your interfaces file is sorted out), and assuming default policies of ACCEPT in your rule set and assuming tcp only.

Make sure forwarding enabled. (as root):```
echo "1" > /proc/sys/net/ipv4/ip_forward
```Do the port forward:```
sudo iptables -t nat -A PREROUTING -p tcp -i em1 --dport 3001 -j DNAT --to 10.0.0.231:3001
```or```
sudo iptables -t nat -A PREROUTING -p tcp -d aaa.bbb.ccc.107 --dport 3001 -j DNAT --to 10.0.0.231:3001
```

EDIT: If your iptables rule set doesn't already have it, you will need to provide a return path for the port forwarding:```
$sudo iptables -t nat -A POSTROUTING -o em1 -j SNAT --to aaa.bbb.ccc.107
```Note, your existing rule set might be using MASQUERADE instead of SNAT.

---

### Post by victor67 on 2015-10-24
I actually managed to get the above going. 

I am still having one problem. I had to remove connection states of ESTABLISHED and RELATED in order to accomplish the forwarding of traffic to the machine in the network. I would like to keep this in my FORWARD chain to strengthen the firewall. 

Here is my current iptables -vnL outputs and rules. (I have masked my IP address)

```
$ sudo iptables -vnLChain INPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
   64 15065 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
  995 84655 ACCEPT     all  --  p255p1 *       0.0.0.0/0            0.0.0.0/0           
  117  9628 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           
  300 39219 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:22
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:8000
   33  2364 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:10000
  378  102K ACCEPT     all  --  em1    *       0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
   64  5858 LOGGING    all  --  em1    *       0.0.0.0/0            0.0.0.0/0           


Chain FORWARD (policy DROP 2 packets, 96 bytes)
 pkts bytes target     prot opt in     out     source               destination         
55847   11M ACCEPT     all  --  p255p1 em1     0.0.0.0/0            0.0.0.0/0           
60455  177M ACCEPT     all  --  em1    p255p1  0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED


Chain OUTPUT (policy ACCEPT 2309 packets, 507K bytes)
 pkts bytes target     prot opt in     out     source               destination         


Chain LOGGING (1 references)
 pkts bytes target     prot opt in     out     source               destination         
   64  5858 LOG        all  --  em1    *       0.0.0.0/0            0.0.0.0/0            limit: avg 5/sec burst 10 LOG flags 0 level 4
   64  5858 DROP       all  --  em1    *       0.0.0.0/0            0.0.0.0/0           






$ sudo iptables -t nat -vnL
Chain PREROUTING (policy ACCEPT 2640 packets, 213K bytes)
 pkts bytes target     prot opt in     out     source               destination         
    2    96 DNAT       tcp  --  em1    *       0.0.0.0/0            MY_PUB_IP        tcp dpt:8000 to:10.255.50.75:8000


Chain INPUT (policy ACCEPT 1112 packets, 83884 bytes)
 pkts bytes target     prot opt in     out     source               destination         


Chain OUTPUT (policy ACCEPT 581 packets, 46547 bytes)
 pkts bytes target     prot opt in     out     source               destination         


Chain POSTROUTING (policy ACCEPT 31 packets, 2017 bytes)
 pkts bytes target     prot opt in     out     source               destination         
 1965  158K MASQUERADE  all  --  *      em1     0.0.0.0/0            0.0.0.0/0           






#### my IPTABLES rules


# Generated by iptables-save v1.4.21 on Fri Oct  9 13:59:58 2015
*nat
:INPUT ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
:POSTROUTING ACCEPT [0:0]
:PREROUTING ACCEPT [0:0]
-A PREROUTING -p tcp -m tcp -d MY_PUB_IP -i em1 --dport 8000 -j DNAT --to-destination 10.255.50.75:8000
-A POSTROUTING -o em1 -j MASQUERADE
COMMIT
# Completed on Fri Oct  9 13:59:58 2015
# Generated by iptables-save v1.4.21 on Fri Oct  9 13:59:58 2015
*mangle
:PREROUTING ACCEPT [34:3197]
:INPUT ACCEPT [34:3197]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [31:7469]
:POSTROUTING ACCEPT [31:7469]
COMMIT
# Completed on Fri Oct  9 13:59:58 2015
# Generated by iptables-save v1.4.21 on Fri Oct  9 13:59:58 2015
*filter
:LOGGING - [0:0]
:OUTPUT ACCEPT [0:0]
:FORWARD DROP [0:0]
:INPUT DROP [0:0]
-A INPUT -i lo -j ACCEPT
-A INPUT -i p255p1 -j ACCEPT
-A INPUT -p icmp -j ACCEPT
-A INPUT -p tcp -m tcp --dport 22 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 8000 -j ACCEPT
-A LOGGING -m limit -i em1 --limit 5/second --limit-burst 10 -j LOG
-A LOGGING -i em1 -j DROP
-A INPUT -p tcp -m tcp --dport 10000 -j ACCEPT
-A FORWARD -i p255p1 -o em1 -j ACCEPT
-A INPUT -m state -i em1 --state ESTABLISHED,RELATED -j ACCEPT
-A FORWARD -m state -i em1 -o p255p1 --state ESTABLISHED,RELATED -j ACCEPT
-A INPUT -i em1 -j LOGGING
COMMIT
# Completed on Fri Oct  9 13:59:58 2015
```


How can I still allow connections from MY_PUB_IP and still maintain EST and REL states? With the above, I cannot access 10.255.50.75:8000

---

### Post by Doug S on 2015-10-24
You got it working with the interfaces file as you originally posted?

I am confused are you trying to forward port 8000 or port 3001? Or both?

Anyway, with a default policy of DROP on your FORWARD chain, you need to provide a path through it for the first port forward packet. Thereafter, they can follow the established/related rule.```
sudo iptables -A FORWARD -i em1 -o p255p1 -p tcp --dport 3001 -d 10.0.0.231 -m state --state NEW -j ACCEPT
```

---

### Post by victor67 on 2015-10-25
Here are my rules:

```
$ cat /etc/iptables.up.rules
# Generated by iptables-save v1.4.21 on Fri Oct  9 13:59:58 2015
*nat
:POSTROUTING ACCEPT [0:0]
:PREROUTING ACCEPT [0:0]
:INPUT ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
# Don't forget the forward chain!
-A PREROUTING -p tcp -m tcp -d MY_PUB_IP -i em1 --dport 3001 -j DNAT --to-destination 10.255.230.231:3001
-A POSTROUTING -o em1 -j MASQUERADE
COMMIT
# Completed on Fri Oct  9 13:59:58 2015
# Generated by iptables-save v1.4.21 on Fri Oct  9 13:59:58 2015
*mangle
:PREROUTING ACCEPT [34:3197]
:INPUT ACCEPT [34:3197]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [31:7469]
:POSTROUTING ACCEPT [31:7469]
COMMIT
# Completed on Fri Oct  9 13:59:58 2015
# Generated by iptables-save v1.4.21 on Fri Oct  9 13:59:58 2015
*filter
:OUTPUT ACCEPT [0:0]
:FORWARD DROP [0:0]
:INPUT DROP [0:0]
:LOGGING - [0:0]
-A INPUT -i lo -j ACCEPT
-A INPUT -i p255p1 -j ACCEPT
-A INPUT -p icmp -j ACCEPT
-A INPUT -p tcp -m tcp --dport 22 -j ACCEPT
-A LOGGING -m limit -i em1 --limit 5/second --limit-burst 10 -j LOG
-A LOGGING -i em1 -j DROP
-A INPUT -p tcp -m tcp --dport 10000 -j ACCEPT
-A FORWARD -p tcp -m tcp -i em1 -o p255p1 --dport 3001 -j ACCEPT
-A FORWARD -i p255p1 -o em1 -j ACCEPT
-A INPUT -m state -i em1 --state ESTABLISHED,RELATED -j ACCEPT
-A FORWARD -m state -i em1 -o p255p1 --state ESTABLISHED,RELATED -j ACCEPT
-A INPUT -i em1 -j LOGGING
COMMIT
# Completed on Fri Oct  9 13:59:58 2015
```

All seems to working..!now I can specify from any of my public facing IPs a specific machine and port on the network.

Next task is a site to site vpn.. thanks for the help!

---

