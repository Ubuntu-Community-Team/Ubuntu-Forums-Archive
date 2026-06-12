---
title: "Difficult iptables nut"
date: 2008-10-15
forum: Networking &amp; Wireless
---

### Post by Bo Mellberg on 2008-10-15
Hi all!

I'm trying to get my Bubba|Two up and going, and for this I need to get Port Forwarding to work. I've read nearly every IPTABLES article there is, including applicable chapters in Oscars excellent howto.

My network is as follows:

ADSL IN -> UBUNTU SERVER 8.04 LTS (as firewall and router) -> Gigabit Switch -> Bubba (on internal LAN)

Firewall = ext0 - 213.x.x.x, ext1 - 192.168.0.1
Bubba = ext1 - 192.168.0.85

My iptables.up.rules (which I mostly edit using webmin):

```
root@alex:~# more /etc/iptables.up.rules
######## Network Address Translation:

*nat
:OUTPUT ACCEPT [0:0]
:PREROUTING ACCEPT [0:0]
:POSTROUTING ACCEPT [0:0]
-A POSTROUTING -o eth0 -j SNAT --to-source 213.x.x.x
-A PREROUTING -p tcp -m tcp -d 213.x.x.x --dport 8080 -j DNAT --to-destination 192.168.0.85:80
COMMIT

######## Filtering:

*filter
:FORWARD ACCEPT [0:0]
:INPUT ACCEPT [0:0]
:LOGNDROP - [0:0]
:OUTPUT ACCEPT [0:0]
-A INPUT -p icmp -j ACCEPT
-A INPUT -i eth1 -j ACCEPT
-A INPUT -i lo -j ACCEPT
-A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
-A INPUT -p tcp -m tcp --dport 22 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 25 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 80 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 993 -j ACCEPT
-A INPUT -p udp -m udp -d 224.0.0.251 --dport 5353 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 5901 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 10000 -j ACCEPT
-A INPUT -p udp -m udp --dport 10000 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 49160:49300 -j ACCEPT
-A INPUT -p udp -m udp --dport 49160:49300 -j ACCEPT
-A INPUT -j LOGNDROP
-A FORWARD -j LOG  --log-prefix "FORWARD " --log-level 7
-A FORWARD -p tcp -d 192.168.0.85 -i eth0 --dport 80 -j ACCEPT
-A LOGNDROP -p tcp -m limit --limit 5/min -j LOG  --log-prefix "Denied TCP: " --log-level 7
-A LOGNDROP -p udp -m limit --limit 5/min -j LOG  --log-prefix "Denied UDP: " --log-level 7
-A LOGNDROP -p icmp -m limit --limit 5/min -j LOG  --log-prefix "Denied ICMP: " --log-level 7
-A LOGNDROP -j DROP
COMMIT

######## Mangle:

*mangle
:PREROUTING ACCEPT [1:366]
:INPUT ACCEPT [1:366]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [1:79]
:POSTROUTING ACCEPT [1:79]
COMMIT

```

As you can see in the forward chain, I log every forwarded packet, which result in these entries in syslog:

```
Oct 15 15:36:46 alex kernel: [399511.241182] FORWARD IN=eth0 OUT=eth1 SRC=85.235.y.y DST=192.168.0.85 LEN=52 TOS=0x00 PREC=0x00 TTL=116 ID=11506 DF PROTO=TCP SPT=7401 DPT=80 WINDOW=65535 RES=0x00 ACK URGP=0
Oct 15 15:36:48 alex kernel: [399513.010867] FORWARD IN=eth1 OUT=eth0 SRC=192.168.0.85 DST=85.235.y.y LEN=452 TOS=0x00 PREC=0x00 TTL=63 ID=25012 DF PROTO=TCP SPT=80 DPT=7401 WINDOW=6432 RES=0x00 ACK PSH URGP=0
```

Where 85.235.y.y is my ip at work.

As you can see from the log, the DNAT works, and sends the package to the internal 192.168.0.85 machine. The second line shows that the internal machine has also answered and is sending a packet out to my work computer, through the firewall.

BUT, I don't get any reply whatsoever. If I telnet to 213.x.x.x 8080 the cmd window goes blank, but no reply.

Please advice, If you have any hints...

/Bo

---

### Post by Bo Mellberg on 2008-10-15
no one?

---

