---
title: "iptables and port redirection to SQL Server"
date: 2007-05-02
forum: Networking &amp; Wireless
---

### Post by indiocolifa on 2007-05-02
I'm trying to setup netfilter and i've the following scenario:

Linux Box, Static IP 201.x.x.x on eth1 (connected to 256Kbps Link WAN)
                  Static IP 192.168.0.240 on eth0 (to LAN)

Windows 2000 Box, Static IP 192.168.0.2, connected to another WAN through router 192.168.0.1

This winbox runs SQL Server on port 1433.

What I'm trying to do it's to forward 1433 connections on the Linux Box with netfilter to the 192.168.0.1 SQL Server.

First, I enabled forwarding with:

[FONT="Fixedsys"]echo 1 > /proc/sys/net/ipv4/ip_forward[/FONT]

Tried the 'redir' utility to verify the connections:

[FONT="Fixedsys"]redir --lport 1433 --cport 1433 --caddr 192.168.0.2[/FONT]

This works perfect (I verified that a host 500km far away connected to the DB tables on 192.168.0.1 through REDIR daemon).

But I want to use NAT to forward requests. So, I've tried the following:

[FONT="Fixedsys"]iptables -F
iptables -t nat -F
iptables -Z[/FONT]

And now

[FONT="Fixedsys"]iptables -t nat -A PREROUTING -p tcp -i eth1 --dport 1433 -j DNAT --to-destination 192.168.0.2:1433[/FONT]

This does not work :( 

I'm a novice with the NAT question. Could this be related to not having a SNAT rule and/or the default routing of 192.168.0.1 which is present on 192.168.0.2 (SQL box) is interfering?

Thank you.

---

