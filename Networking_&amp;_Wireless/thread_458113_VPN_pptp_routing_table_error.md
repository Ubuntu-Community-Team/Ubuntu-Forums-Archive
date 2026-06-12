---
title: "VPN pptp: routing table error"
date: 2007-05-29
forum: Networking &amp; Wireless
---

### Post by gioppopc on 2007-05-29
Hi all :D,
befor the VPN connection from my home to a factory network my Routing Table is:
Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use
Iface
192.168.10.0    *               255.255.255.0   U      0       0         0 ath0
link-local             *               255.255.0.0       U     1000  0         0 ath0
default         192.168.10.1    0.0.0.0            UG    0       0         0 ath0
where 192.168.10.1 is my home gateway (wireless ath0).

after the VPN connection my Routing Table is:
Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use
Iface
83.103.19.XXX  192.168.10.1    255.255.255.255       UGH  0      0        0 ath0
192.168.10.0    *                        255.255.255.0           U      0      0        0 ath0
link-local             *                        255.255.0.0              U     1000  0        0 ath0
default               *                        0.0.0.0                      U     0        0        0 ppp0
where 83.103.19.XXX is the VPN IP of the factory network.
After the VPN connection I can't ping the IP 83.103.19.XXX and I can't ping any factory network server.
How I can modify the Routing Table to use the IP 83.103.19.XXX like default gateway?
Why the default gateway has a ppp0 Use if I don't use a modem but only a wireless connection?
Which is the difference between Route and Ip Route commands?
Thanks. Gioppo

---

### Post by dre2004 on 2007-05-31
Are you using the network-manager-pptp on feisty?

I'm having a similar problem by where my PPTP VPN tunnel gets established fine but it doesnt automatically create the routes I specified in the config.

What is strange through is that it did create the routes fine once but then I could only access those networks that I defined in my PPTP connection settings.

For the time being I've just got a script which adds the other routes manually till I figure out how to fix this.

---

### Post by hazgod on 2007-06-28
Hi

I have just installed kubunto feisty and am having this issue. VPN is essential to my work so I need to get it fixed otherwise I'm going to have to go back to suse, which is crap. What routes do you need to add in to make it work correctly?

After I connect and do ifconfig I get a ppp0 connection. I can ping the ip address that my computer is given, but cannot ping anything else on the network.

My route table is as follows:

Kernel IP routeing table
Destination          Gateway              Genmask           Flags Metric Ref    Use Iface
192.168.250.10        *                  255.255.255.255    UH    0      0        0 ppp0
192.168.238.0          *                  255.255.255.0       U      0      0        0 eth0
default             192.168.238.254         0.0.0.0             UG    0      0        0 eth0

Ubunto is great and I don't want to use suse again because it's a pain. This is the only thing that doesn't work in Kubunto but it is important. Thanks in advance for the help!

---

### Post by twistedtwig on 2007-07-02
I am having a similar issue.  I can get (well it seems) the vpn to work connecting to windows 2003 vpn server.  But I can not ping anything on the network.

---

