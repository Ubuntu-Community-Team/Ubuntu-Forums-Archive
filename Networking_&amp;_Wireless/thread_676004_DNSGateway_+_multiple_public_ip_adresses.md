---
title: "DNS/Gateway + multiple public ip adresses"
date: 2008-01-23
forum: Networking &amp; Wireless
---

### Post by Jahntje on 2008-01-23
Hi,
we're currently working on a project at school which involve making a so-called NOC center, with one surveillance network (192.168.2.0/24) and one honeypot network (212.20.204.0/64 - public ip addresses). Our main firewall (FW1) got 3 NICs.

[IMG]http://img512.imageshack.us/img512/3959/networkok9.jpg[/IMG]


Everything works perfectly when it comes to routing. All the honeypot servers can access the internet via FW1. Our problem is that we have a range of public ip's which we are going to use on the honeypot network, but they aren't "visible" on the outside of FW1. We can't ping them or anything. This probably means they can't be accessed by any potential hacker either, which kind of ruins its purpose. All the outside world can see is FW1.

I.e, you can ping 212.20.204.2 (eth0) and 212.20.204.3 (eth1), but you won't get any answer from 212.20.204.4 (unsecured ftp/web server)

FW1 is only there to sniff packets and have total control over everything that goes in and out, namely the IDS main server.

What we're wondering is how can we make all the servers in the honeypot network seem like they're not behind any firewall or gateway? Is this possible at all with our setup? If you try to access 212.20.204.4 in any way, it should seem like you interact directly with that server and not through FW1.





Our iptables script:
```
#!/bin/bash

#
#########################
# Firewall Firewall.noc #
#########################
#

#define LOG_EMERG       0       /* system is unusable */
#define LOG_ALERT       1       /* action must be taken immediately */
#define LOG_CRIT        2       /* critical conditions */
#define LOG_ERR         3       /* error conditions */
#define LOG_WARNING     4       /* warning conditions */
#define LOG_NOTICE      5       /* normal but significant condition */
#define LOG_INFO        6       /* informational */
#define LOG_DEBUG       7       /* debug-level messages */

ipt="iptables"
echo "Variabels set!"

modprobe iptable_nat
modprobe ipt_MASQUERADE
modprobe ipt_REJECT

echo 1 > /proc/sys/net/ipv4/ip_forward

#------------------------------------

$ipt -F
$ipt -F INPUT
$ipt -F OUTPUT
$ipt -F FORWARD
$ipt -t nat -F
echo "Flushing rules!"

#------------------------------------


$ipt -P INPUT ACCEPT
$ipt -P OUTPUT ACCEPT
$ipt -P FORWARD ACCEPT
echo "Setting policys!"

#------------------------------------

$ipt -A INPUT  -j LOG --log-level 4 --log-prefix "INPUT Dropped by firewall:"
$ipt -A OUTPUT -j LOG --log-level 4 --log-prefix "OUTPUT Dropped by firewall:"
echo "Logging set!"

#------------------------------------

$ipt -A FORWARD -i eth0 -o eth1 -m state --state ESTABLISHED,RELATED -j ACCEPT
$ipt -A FORWARD -i eth1 -o eth0 -j ACCEPT

$ipt -A FORWARD -i eth0 -o eth2 -m state --state ESTABLISHED,RELATED -j ACCEPT
$ipt -A FORWARD -i eth2 -o eth0 -j ACCEPT


#------------------------------------

$ipt -t nat -A POSTROUTING -o eth0 -j SNAT --to 212.20.204.2
$ipt -t nat -A POSTROUTING -o eth0 -j MASQUERADE

```

Any help is appreciated!

---

### Post by sqrt2 on 2008-01-24
There are a few things about your setup that look pretty strange to me. First of all, your default policies are all set to ACCEPT. This has contrary effects to what you write in your logs and also makes your firewall rules in the FORWARD chain completely ineffective because you don't REJECT or DROP anything there. Also, your internal network should be completely accessible from your insecure servers! (The only reason one can't connect now is that your ISP drops all the packets to private addresses.)

Since you do NAT for everything that goes out of your network, people will firstly not recognize that there is something like a router in place anyway. On the other hand, you have to take into account that somebody who breaks into your insecure servers will have total knowledge about what is going on. Any attempts to use FW1 as a router will be seen from the servers because they have to have a default gateway.

I think the most reasonable approach is to connect SW1 directly to the internet and use its monitor port to look at the traffic. Unless you have a Gigabit connection to the Internet (in which case I envy you)  there should be no problem with capturing all the traffic that is going through the switch.

You then of course will also have to configure FW2 to do all the the NAT work and secure your internal network against the Internet.

By the way, what software did you use to create the diagram? Looks nice. :)

---

