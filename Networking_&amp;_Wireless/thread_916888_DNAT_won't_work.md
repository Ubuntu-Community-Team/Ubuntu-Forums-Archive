---
title: "DNAT won't work"
date: 2008-09-11
forum: Networking &amp; Wireless
---

### Post by tchainsaw on 2008-09-11
Hi all,

I'm having a pretty strange problem. My DNATs just doesn't work on Ubuntu Server 8.04. I'm used to Slackware Linux for firewalls and that is the first time I'm using a Ubuntu for this solution, actually I'm loving it, but this issue is killing me!

My configuration is the most simple ever:

LINK -> Ubuntu -> LAN

eth1 = net
eth0 = lan

In my Ubuntu I just have:

> 
echo "1" /proc/sys/net/ipv4/ip_forward

iptables -t filter -F
iptables -t nat -F
iptables -t mangle -F

iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT

iptables -t nat -A PREROUTING -i eth1 -d 200.x.x.1 -p tcp --dport 5900 -j DNAT --to 172.x.x.31
iptables -t nat -A POSTROUTING -s 172.x.x.0/24 -o eth1 -j MASQUERADE


And when I try to connect to the IP 200.x.x.1 at port 5900 it doesn't work... I've a several firewall running on Slack so I'm used to deal with FW, but this one is strange...

I believe I'm missing some ridiculous configuration at Ubuntu, as I'm not totally used to this OS for FW, and it is not allowing my FW to DNAT this connection...

ANY HELP will be great!!! =)

If need any further info, please, just ask.

Many thanks in advance!

---

### Post by tchainsaw on 2008-09-11
Hi all, 

Nevermid... I realized what was wrong... This link is far from me, I'm configuring it remotely and the dude that did the cables there did this:

Link -> Switch -> Ubuntu

And in this switch are all the computer that are in the LAN... 

Now I've:

Link -> Ubuntu

All working! ;)

---

