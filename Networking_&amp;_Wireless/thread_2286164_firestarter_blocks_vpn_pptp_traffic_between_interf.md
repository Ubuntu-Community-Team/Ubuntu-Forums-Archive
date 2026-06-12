---
title: "firestarter blocks vpn pptp traffic between interfaces, can't access server resources"
date: 2015-07-10
forum: Networking &amp; Wireless
---

### Post by neostead on 2015-07-10
Hi, i have following problem:

I have debian machine acting as firewall/router for my home network. There is also a PPTP server running on the same machine. I can successfully connect to VPN host, i can access other hosts in lan, but i can't access resources on pptp server, and that is a problem.

Machine has two interfaces:
eth0 (LAN) 192.168.2.200
eth1 (WAN) 192.168.1.21

PPTP configuration:
localip 192.168.3.150
remoteip 192.168.3.151-155

There is some iptables configuration in /etc/firestarter/user-pre

```
$IPT -A INPUT -p gre -j ACCEPT
$IPT -A OUTPUT -p gre -j ACCEPT
$IPT -t nat -A POSTROUTING -o eth0 -j MASQUERADE
$IPT --table nat --append POSTROUTING --out-interface ppp0 -j MASQUERADE
$IPT -I INPUT -s 192.168.3.0/24 -i ppp0 -j ACCEPT
$IPT --append FORWARD --in-interface eth0 -j ACCEPT

```

When i'm trying to ping vpn host from connected client (android phone), i can't get any response and i see in syslog following lines:
```
Jul 10 14:50:04 debian kernel: [ 9223.650659] Unknown OutputIN= OUT=ppp0 SRC=192.168.2.200 DST=192.168.3.151 LEN=84 TOS=0x00 PREC=0x00 TTL=64 ID=49856 PROTO=ICMP TYPE=0 CODE=0 ID=844 SEQ=15

```

It's weird for me, since i'm pinging from pptp client (192.168.3.151), shouldn't 192.168.3.151 be the SRC address ?

When i disable firestarter, i can access server resources.

Additional information:

```

$ sudo route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.20    0.0.0.0         UG    0      0        0 eth1
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.3.151   0.0.0.0         255.255.255.255 UH    0      0        0 ppp0

```

```

$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 90:2b:34:52:23:33  
          inet addr:192.168.2.200  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::922b:34ff:fe52:2333/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3114 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2854 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:454093 (443.4 KiB)  TX bytes:430483 (420.3 KiB)
          Interrupt:40 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr 00:0e:2e:cc:f2:3a  
          inet addr:192.168.1.21  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:2eff:fecc:f23a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:36001 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31875 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26136136 (24.9 MiB)  TX bytes:5251477 (5.0 MiB)
          Interrupt:20 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3293 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3293 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:531034 (518.5 KiB)  TX bytes:531034 (518.5 KiB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:192.168.3.150  P-t-P:192.168.3.151  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1396  Metric:1
          RX packets:219 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:15054 (14.7 KiB)  TX bytes:348 (348.0 B)

```

All i need is to access single service available on eth0 (LAN) interface. Maybe i need some hacky iptables forwards?

---

### Post by TheFu on 2015-07-10
FYI - [http://www.computerworld.com/article/2505117/cyberwarfare/tools-released-at-defcon-can-crack-widely-used-pptp-encryption-in-under-a-day.html](http://www.computerworld.com/article/2505117/cyberwarfare/tools-released-at-defcon-can-crack-widely-used-pptp-encryption-in-under-a-day.html)
PPTP has been hacked for years. MSFT doesn't use it anymore.

Is ipv4-forward enabled in sysctl.conf?

---

### Post by neostead on 2015-07-10
> **TheFu said:**
> FYI - [http://www.computerworld.com/article/2505117/cyberwarfare/tools-released-at-defcon-can-crack-widely-used-pptp-encryption-in-under-a-day.html](http://www.computerworld.com/article/2505117/cyberwarfare/tools-released-at-defcon-can-crack-widely-used-pptp-encryption-in-under-a-day.html)
PPTP has been hacked for years. MSFT doesn't use it anymore.

Is ipv4-forward enabled in sysctl.conf?

I'm aware of that this vpn isn't secure and i'll take that risk.
Forwarding is currently disabled, i don't need access to any internal host except vpn server itself.
Switching it on won't help, i tried that.

Could You help me understand syslog message?
I believe only rejected communication is logged, because pinging (from vpn client) other host that vpn server itself does work and no messages are logged. (However it's interesting, net.ipv4.ip_forward=0 but vpn client still can ping/access other hosts in LAN..)

---

### Post by Doug S on 2015-07-10
> **neostead said:**
> There is some iptables configuration in /etc/firestarter/user-pre

```
$IPT -A INPUT -p gre -j ACCEPT
$IPT -A OUTPUT -p gre -j ACCEPT
$IPT -t nat -A POSTROUTING -o eth0 -j MASQUERADE
$IPT --table nat --append POSTROUTING --out-interface ppp0 -j MASQUERADE
$IPT -I INPUT -s 192.168.3.0/24 -i ppp0 -j ACCEPT
$IPT --append FORWARD --in-interface eth0 -j ACCEPT

```I do not understand this line:```
$IPT -t nat -A POSTROUTING -o eth0 -j MASQUERADE
```And think it should be:```
$IPT -t nat -A POSTROUTING -o eth1 -j MASQUERADE
```I am saying that NAT should occur to your WAN and not your LAN.> **neostead said:**
> When i'm trying to ping vpn host from connected client (android phone), i can't get any response and i see in syslog following lines:
```
Jul 10 14:50:04 debian kernel: [ 9223.650659] Unknown OutputIN= OUT=ppp0 SRC=192.168.2.200 DST=192.168.3.151 LEN=84 TOS=0x00 PREC=0x00 TTL=64 ID=49856 PROTO=ICMP TYPE=0 CODE=0 ID=844 SEQ=15

```

It's weird for me, since i'm pinging from pptp client (192.168.3.151), shouldn't 192.168.3.151 be the SRC address ?It is the echo reply that is being logged, not the echo request. We would need to see the context of the iptables rules to know better.

Disclaimer: firestarter generated iptables rules sets are very difficult to read / follow. Note that firestarter is rarely used anymore.

---

### Post by neostead on 2015-07-10
> **Doug S said:**
> I do not understand this line:```
$IPT -t nat -A POSTROUTING -o eth0 -j MASQUERADE
```And think it should be:```
$IPT -t nat -A POSTROUTING -o eth1 -j MASQUERADE
```
I changed eth0 to eth1, (and restarted firestarter service), but it did not help.

My iptables rules are below:

```
# Generated by iptables-save v1.4.14 on Fri Jul 10 20:39:00 2015
*nat
:PREROUTING ACCEPT [44:4315]
:INPUT ACCEPT [7:704]
:OUTPUT ACCEPT [13:870]
:POSTROUTING ACCEPT [11:782]
-A PREROUTING -i eth1 -p tcp -m tcp --dport 10500:10599 -j DNAT --to-destination 192.168.2.105:10500-10599
-A PREROUTING -i eth1 -p udp -m udp --dport 10500:10599 -j DNAT --to-destination 192.168.2.105:10500-10599
-A POSTROUTING -o eth1 -j MASQUERADE
-A POSTROUTING -o ppp0 -j MASQUERADE
-A POSTROUTING -o eth1 -j MASQUERADE
COMMIT
# Completed on Fri Jul 10 20:39:00 2015
# Generated by iptables-save v1.4.14 on Fri Jul 10 20:39:00 2015
*mangle
:PREROUTING ACCEPT [18897:2544124]
:INPUT ACCEPT [8409:459265]
:FORWARD ACCEPT [10475:2083541]
:OUTPUT ACCEPT [6870:1379821]
:POSTROUTING ACCEPT [17331:3462553]
COMMIT
# Completed on Fri Jul 10 20:39:00 2015
# Generated by iptables-save v1.4.14 on Fri Jul 10 20:39:00 2015
*filter
:INPUT DROP [2:728]
:FORWARD DROP [0:0]
:OUTPUT DROP [8:352]
:INBOUND - [0:0]
:LOG_FILTER - [0:0]
:LSI - [0:0]
:LSO - [0:0]
:OUTBOUND - [0:0]
-A INPUT -s 192.168.3.0/24 -i ppp0 -j ACCEPT
-A INPUT -p gre -j ACCEPT
-A INPUT -i lo -j ACCEPT
-A INPUT -p icmp -m limit --limit 10/sec -j ACCEPT
-A INPUT -d 255.255.255.255/32 -i eth1 -j DROP
-A INPUT -d 192.168.1.255/32 -j DROP
-A INPUT -s 224.0.0.0/8 -j DROP
-A INPUT -d 224.0.0.0/8 -j DROP
-A INPUT -s 255.255.255.255/32 -j DROP
-A INPUT -d 0.0.0.0/32 -j DROP
-A INPUT -m state --state INVALID -j DROP
-A INPUT -f -m limit --limit 10/min -j LSI
-A INPUT -i eth1 -j INBOUND
-A INPUT -d 192.168.2.200/32 -i eth0 -j INBOUND
-A INPUT -d 192.168.1.21/32 -i eth0 -j INBOUND
-A INPUT -d 192.168.2.255/32 -i eth0 -j INBOUND
-A INPUT -j LOG_FILTER
-A INPUT -j LOG --log-prefix "Unknown Input" --log-level 6
-A FORWARD -i eth0 -j ACCEPT
-A FORWARD -p icmp -m limit --limit 10/sec -j ACCEPT
-A FORWARD -p tcp -m tcp --tcp-flags SYN,RST SYN -j TCPMSS --clamp-mss-to-pmtu
-A FORWARD -d 192.168.2.105/32 -i eth1 -p tcp -m tcp --dport 10500:10599 -j ACCEPT
-A FORWARD -d 192.168.2.105/32 -i eth1 -p udp -m udp --dport 10500:10599 -j ACCEPT
-A FORWARD -i eth0 -j OUTBOUND
-A FORWARD -d 192.168.2.0/24 -p tcp -m state --state RELATED,ESTABLISHED -j ACCEPT
-A FORWARD -d 192.168.2.0/24 -p udp -m state --state RELATED,ESTABLISHED -j ACCEPT
-A FORWARD -j LOG_FILTER
-A FORWARD -j LOG --log-prefix "Unknown Forward" --log-level 6
-A OUTPUT -p gre -j ACCEPT
-A OUTPUT -o lo -j ACCEPT
-A OUTPUT -s 224.0.0.0/8 -j DROP
-A OUTPUT -d 224.0.0.0/8 -j DROP
-A OUTPUT -s 255.255.255.255/32 -j DROP
-A OUTPUT -d 0.0.0.0/32 -j DROP
-A OUTPUT -m state --state INVALID -j DROP
-A OUTPUT -o eth1 -j OUTBOUND
-A OUTPUT -o eth0 -j OUTBOUND
-A OUTPUT -j LOG_FILTER
-A OUTPUT -j LOG --log-prefix "Unknown Output" --log-level 6
-A INBOUND -p tcp -m state --state RELATED,ESTABLISHED -j ACCEPT
-A INBOUND -p udp -m state --state RELATED,ESTABLISHED -j ACCEPT
-A INBOUND -s 192.168.2.0/24 -p tcp -m tcp --dport 111 -j ACCEPT
-A INBOUND -s 192.168.2.0/24 -p udp -m udp --dport 111 -j ACCEPT
-A INBOUND -s 192.168.2.0/24 -p tcp -m tcp --dport 2049 -j ACCEPT
-A INBOUND -s 192.168.2.0/24 -p udp -m udp --dport 2049 -j ACCEPT
-A INBOUND -s 192.168.2.0/24 -p tcp -m tcp --dport 137:139 -j ACCEPT
-A INBOUND -s 192.168.2.0/24 -p udp -m udp --dport 137:139 -j ACCEPT
-A INBOUND -s 192.168.2.0/24 -p tcp -m tcp --dport 445 -j ACCEPT
-A INBOUND -s 192.168.2.0/24 -p udp -m udp --dport 445 -j ACCEPT
-A INBOUND -p tcp -m tcp --dport 1723 -j ACCEPT
-A INBOUND -p udp -m udp --dport 1723 -j ACCEPT
-A INBOUND -p tcp -m tcp --dport 20022 -j ACCEPT
-A INBOUND -p udp -m udp --dport 20022 -j ACCEPT
-A INBOUND -p tcp -m tcp --dport 20021 -j ACCEPT
-A INBOUND -p udp -m udp --dport 20021 -j ACCEPT
-A INBOUND -p tcp -m tcp --dport 20080 -j ACCEPT
-A INBOUND -p udp -m udp --dport 20080 -j ACCEPT
-A INBOUND -p tcp -m tcp --dport 20061 -j ACCEPT
-A INBOUND -p udp -m udp --dport 20061 -j ACCEPT
-A INBOUND -p tcp -m tcp --dport 20050:20060 -j ACCEPT
-A INBOUND -p udp -m udp --dport 20050:20060 -j ACCEPT
-A INBOUND -p tcp -m tcp --dport 20013 -j ACCEPT
-A INBOUND -p udp -m udp --dport 20013 -j ACCEPT
-A INBOUND -s 192.168.2.0/24 -p tcp -m tcp --dport 10000 -j ACCEPT
-A INBOUND -s 192.168.2.0/24 -p udp -m udp --dport 10000 -j ACCEPT
-A INBOUND -s 192.168.2.0/24 -p tcp -m tcp --dport 67:68 -j ACCEPT
-A INBOUND -s 192.168.2.0/24 -p udp -m udp --dport 67:68 -j ACCEPT
-A INBOUND -s 192.168.2.0/24 -p tcp -m tcp --dport 53 -j ACCEPT
-A INBOUND -s 192.168.2.0/24 -p udp -m udp --dport 53 -j ACCEPT
-A INBOUND -s 192.168.2.0/24 -p tcp -m tcp --dport 6000:6015 -j ACCEPT
-A INBOUND -s 192.168.2.0/24 -p udp -m udp --dport 6000:6015 -j ACCEPT
-A INBOUND -s 192.168.2.0/24 -p tcp -m tcp --dport 80 -j ACCEPT
-A INBOUND -s 192.168.2.0/24 -p udp -m udp --dport 80 -j ACCEPT
-A INBOUND -s 192.168.2.0/24 -p tcp -m tcp --dport 443 -j ACCEPT
-A INBOUND -s 192.168.2.0/24 -p udp -m udp --dport 443 -j ACCEPT
-A INBOUND -s 192.168.2.0/24 -p tcp -m tcp --dport 36701:36706 -j ACCEPT
-A INBOUND -s 192.168.2.0/24 -p udp -m udp --dport 36701:36706 -j ACCEPT
-A INBOUND -p tcp -m tcp --dport 20031:20040 -j ACCEPT
-A INBOUND -p udp -m udp --dport 20031:20040 -j ACCEPT
-A INBOUND -s 192.168.2.0/24 -p tcp -m tcp --dport 9100 -j ACCEPT
-A INBOUND -s 192.168.2.0/24 -p udp -m udp --dport 9100 -j ACCEPT
-A INBOUND -s 192.168.2.0/24 -p tcp -m tcp --dport 3306 -j ACCEPT
-A INBOUND -s 192.168.2.0/24 -p udp -m udp --dport 3306 -j ACCEPT
-A INBOUND -s 192.168.2.0/24 -p tcp -m tcp --dport 4999 -j ACCEPT
-A INBOUND -s 192.168.2.0/24 -p udp -m udp --dport 4999 -j ACCEPT
-A INBOUND -s 192.168.3.0/24 -p tcp -m tcp --dport 20080 -j ACCEPT
-A INBOUND -s 192.168.3.0/24 -p udp -m udp --dport 20080 -j ACCEPT
-A INBOUND -j LSI
-A LSI -j LOG_FILTER
-A LSI -p tcp -m tcp --tcp-flags FIN,SYN,RST,ACK SYN -m limit --limit 1/sec -j LOG --log-prefix "Inbound " --log-level 6
-A LSI -p tcp -m tcp --tcp-flags FIN,SYN,RST,ACK SYN -j DROP
-A LSI -p tcp -m tcp --tcp-flags FIN,SYN,RST,ACK RST -m limit --limit 1/sec -j LOG --log-prefix "Inbound " --log-level 6
-A LSI -p tcp -m tcp --tcp-flags FIN,SYN,RST,ACK RST -j DROP
-A LSI -p icmp -m icmp --icmp-type 8 -m limit --limit 1/sec -j LOG --log-prefix "Inbound " --log-level 6
-A LSI -p icmp -m icmp --icmp-type 8 -j DROP
-A LSI -m limit --limit 5/sec -j LOG --log-prefix "Inbound " --log-level 6
-A LSI -j DROP
-A LSO -j LOG_FILTER
-A LSO -m limit --limit 5/sec -j LOG --log-prefix "Outbound " --log-level 6
-A LSO -j REJECT --reject-with icmp-port-unreachable
-A OUTBOUND -p icmp -j ACCEPT
-A OUTBOUND -p tcp -m state --state RELATED,ESTABLISHED -j ACCEPT
-A OUTBOUND -p udp -m state --state RELATED,ESTABLISHED -j ACCEPT
-A OUTBOUND -j ACCEPT
COMMIT
# Completed on Fri Jul 10 20:39:00 2015

```

---

### Post by Doug S on 2015-07-10
Your ping reply is being logged and then dropped because there isn't a path for it to get to the OUTBOUND chain. You might want to add a line from this:```
-A OUTPUT -o eth1 -j OUTBOUND
-A OUTPUT -o eth0 -j OUTBOUND
```to this:```
-A OUTPUT -o eth1 -j OUTBOUND
-A OUTPUT -o eth0 -j OUTBOUND
-A OUTPUT -o ppp0 -j OUTBOUND
```Edit: By the way, this:```
-A OUTBOUND -p icmp -j ACCEPT
-A OUTBOUND -p tcp -m state --state RELATED,ESTABLISHED -j ACCEPT
-A OUTBOUND -p udp -m state --state RELATED,ESTABLISHED -j ACCEPT
-A OUTBOUND -j ACCEPT
```can be simplified to:```
-A OUTBOUND -j ACCEPT
```

---

### Post by neostead on 2015-07-15
Hi,
I'm sorry it took this long to answer, but server's motherboard has hardware issues and i had to replace it.

Anyway, back to the topic.
if i manually add a rule:
```
# iptables -A OUTPUT -o ppp0 -j OUTBOUND
``` while ppp0 interface exists, i can ping my vpn server from vpn client. However, if i try to access web page accessible on port 20080, communication is blocked:

```
Jul 15 22:19:43 debian kernel: [ 2799.274377] Unknown InputIN=ppp0 OUT= MAC= SRC=192.168.3.151 DST=192.168.2.200 LEN=67 TOS=0x00 PREC=0x00 TTL=64 ID=15233 DF PROTO=UDP SPT=33580 DPT=53 LEN=47 
Jul 15 22:19:44 debian kernel: [ 2800.742980] Unknown InputIN=ppp0 OUT= MAC= SRC=192.168.3.151 DST=192.168.2.200 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=15923 DF PROTO=TCP SPT=43662 DPT=20080 WINDOW=13560 RES=0x00 SYN URGP=0 
Jul 15 22:19:44 debian kernel: [ 2800.745216] Unknown InputIN=ppp0 OUT= MAC= SRC=192.168.3.151 DST=192.168.2.200 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=59440 DF PROTO=TCP SPT=43663 DPT=20080 WINDOW=13560 RES=0x00 SYN URGP=0 
Jul 15 22:19:48 debian kernel: [ 2804.361814] Unknown InputIN=ppp0 OUT= MAC= SRC=192.168.3.151 DST=192.168.2.200 LEN=67 TOS=0x00 PREC=0x00 TTL=64 ID=16733 DF PROTO=UDP SPT=9360 DPT=53 LEN=47 
Jul 15 22:19:51 debian kernel: [ 2807.459183] Unknown InputIN=ppp0 OUT= MAC= SRC=192.168.3.151 DST=192.168.2.200 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=15924 DF PROTO=TCP SPT=43662 DPT=20080 WINDOW=13560 RES=0x00 SYN URGP=0 
Jul 15 22:19:51 debian kernel: [ 2807.468666] Unknown InputIN=ppp0 OUT= MAC= SRC=192.168.3.151 DST=192.168.2.200 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=59441 DF PROTO=TCP SPT=43663 DPT=20080 WINDOW=13560 RES=0x00 SYN URGP=0 
Jul 15 22:19:53 debian kernel: [ 2809.278312] Unknown InputIN=ppp0 OUT= MAC= SRC=192.168.3.151 DST=192.168.2.200 LEN=67 TOS=0x00 PREC=0x00 TTL=64 ID=17234 DF PROTO=UDP SPT=1977 DPT=53 LEN=47 
Jul 15 22:19:58 debian kernel: [ 2814.278386] Unknown InputIN=ppp0 OUT= MAC= SRC=192.168.3.151 DST=192.168.2.200 LEN=67 TOS=0x00 PREC=0x00 TTL=64 ID=16734 DF PROTO=UDP SPT=9360 DPT=53 LEN=47 
Jul 15 22:19:58 debian kernel: [ 2814.783651] Unknown InputIN=ppp0 OUT= MAC= SRC=192.168.3.151 DST=192.168.2.200 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=53200 DF PROTO=TCP SPT=54573 DPT=10000 WINDOW=13560 RES=0x00 SYN URGP=0 
Jul 15 22:19:58 debian kernel: [ 2814.790457] Unknown InputIN=ppp0 OUT= MAC= SRC=192.168.3.151 DST=192.168.2.200 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=8550 DF PROTO=TCP SPT=54574 DPT=10000 WINDOW=13560 RES=0x00 SYN URGP=0
```

What rules should i add now, and what exactly is being blocked?

I also have some extra questions:
Can i use wildcards in interface naming? (Won't next vpn client create ppp1 interface?)
If i manage to collect all missing iptables rules, can i place them in script being executed at ppp* interface creation to make sure it will apply?

---

### Post by Doug S on 2015-07-15
I do not know why you are getting those log entries. Clearly, this rule:```
-A INPUT -s 192.168.3.0/24 -i ppp0 -j ACCEPT
```should be providing an ACCEPT path before the "Unknown Input" log and DROP rule.

---

### Post by Doug S on 2015-07-15
> **neostead said:**
> I also have some extra questions:
Can i use wildcards in interface naming? (Won't next vpn client create ppp1 interface?)you could just not specify an interface and have everything go to the OUTBOUND chain at that point. But the OUTBOUND chain just ACCEPTs everything, so just delete it and set the default policy of the OUPUT chain to ACCEPT, and delete the log line.

---

### Post by neostead on 2015-07-20
Hi,
I have updated file /etc/firestarter/user-pre
```

$IPT -A INPUT -p gre -j ACCEPT
$IPT -A OUTPUT -p gre -j ACCEPT
$IPT -A OUTPUT -o ppp+ -j OUTBOUND
$IPT -A INPUT -i ppp+ -j ACCEPT

```

And it seems $IPT -A OUTPUT -o ppp+ -j OUTBOUND does not apply, i need to add it manually. But if i do, i can finally access server's resources.
Any idea how to fix that?

---

