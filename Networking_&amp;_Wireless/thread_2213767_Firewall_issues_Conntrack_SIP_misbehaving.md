---
title: "Firewall issues: Conntrack SIP misbehaving"
date: 2014-03-28
forum: Networking &amp; Wireless
---

### Post by sgofferj on 2014-03-28
Hi,

I'm running a pretty minimal Ubuntu server 12.04 LTS in a vbox as perimeter firewall. The host OS is Opensuse 12.3.

_**Bad UDP checksum with SIP nat module**_
Among others, I use the SIP conntrack and SIP nat modules and I have an Asterisk PBX in the LAN. Generally, all works perfectly. However, every once in a while, the asterisk loses connection with my SIP provider. When I tcpdump the traffic, I see that the SIP packets on the inside interface are ok but the SIP packets on the outside if have a bad UDP checksum. As of now, I have done some 35h of testing and could not determine a possible reason, nor how to fix it. If I kill the SIP nat module, the packets immediately are fine but - well - have the "wrong" address then. Nothing seems to help, not even rebooting the guest or even the host. It will stop on it's own after a highly variable time, ranging from minutes to several hours.

_**-m helper --helper sip doesn't work**_
I'm trying to tag the SIP RTP packets with 

  $IPTABLES -t mangle -A PREROUTING -m helper --helper sip -j TOS --set-tos 0x18

But that doesn't have any effect. The TOS of the packets doesn't change


Anybody any thoughts on that?

-S

---

### Post by sgofferj on 2014-04-02
Bump

---

