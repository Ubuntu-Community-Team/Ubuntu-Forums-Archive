---
title: "Iptables disables my printer"
date: 2014-07-05
forum: Networking &amp; Wireless
---

### Post by wmsopou on 2014-07-05
Hi All

With iptables disabled my network printer works like a charm but when enabled it stops working. 

my iptabls config allows incoming traffic from localhost and not must else:

-A INPUT -i lo -j ACCEPT
-A INPUT -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
-A INPUT -j DROP

I tried adding port 631 tcp,udp for CUPS but that made no change. I tried googling CUPS firewall settings and it appears everybody have issues but no answers.

I tried logging incoming traffic that is dropped by the firewall but the log doesnt make much sense to me. Could the printer be announcing itself over multicast (192.168.1.103 is the printer, 192.168.1.147 is the workstation running ubuntu 12.04)?

Jul  5 11:57:43 supernova kernel: [327419.206924] IPTables-Drop: IN=wlan0 OUT= MAC= SRC=192.168.1.103 DST=224.0.0.251 LEN=781 TOS=0x00 PREC=0x00 TTL=255 ID=54948 PROTO=UDP SPT=5353 DPT=5353 LEN=761 
Jul  5 11:57:58 supernova kernel: [327433.838317] IPTables-Drop: IN=virbr0 OUT= MAC= SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Jul  5 11:57:58 supernova kernel: [327434.128891] IPTables-Drop: IN=virbr0 OUT= MAC= SRC=192.168.122.1 DST=224.0.0.251 LEN=119 TOS=0x00 PREC=0x00 TTL=255 ID=48461 DF PROTO=UDP SPT=5353 DPT=5353 LEN=99 
Jul  5 11:57:58 supernova kernel: [327434.128939] IPTables-Drop: IN=lxcbr0 OUT= MAC= SRC=10.0.3.1 DST=224.0.0.251 LEN=119 TOS=0x00 PREC=0x00 TTL=255 ID=48462 DF PROTO=UDP SPT=5353 DPT=5353 LEN=99 
Jul  5 11:57:58 supernova kernel: [327434.129071] IPTables-Drop: IN=wlan0 OUT= MAC= SRC=192.168.1.147 DST=224.0.0.251 LEN=119 TOS=0x00 PREC=0x00 TTL=255 ID=48463 DF PROTO=UDP SPT=5353 DPT=5353 LEN=99 
Jul  5 11:57:58 supernova kernel: [327434.310617] IPTables-Drop: IN=wlan0 OUT= MAC= SRC=192.168.1.103 DST=224.0.0.251 LEN=781 TOS=0x00 PREC=0x00 TTL=255 ID=56484 PROTO=UDP SPT=5353 DPT=5353 LEN=761 
Jul  5 11:58:01 supernova kernel: [327437.199826] IPTables-Drop: IN=wlan0 OUT= MAC= SRC=192.168.1.103 DST=224.0.0.251 LEN=781 TOS=0x00 PREC=0x00 TTL=255 ID=56740 PROTO=UDP SPT=5353 DPT=5353 LEN=761 
Jul  5 11:58:13 supernova kernel: [327449.110470] IPTables-Drop: IN=virbr0 OUT= MAC= SRC=192.168.122.1 DST=224.0.0.251 LEN=119 TOS=0x00 PREC=0x00 TTL=255 ID=48470 DF PROTO=UDP SPT=5353 DPT=5353 LEN=99 
Jul  5 11:58:13 supernova kernel: [327449.110518] IPTables-Drop: IN=lxcbr0 OUT= MAC= SRC=10.0.3.1 DST=224.0.0.251 LEN=119 TOS=0x00 PREC=0x00 TTL=255 ID=48471 DF PROTO=UDP SPT=5353 DPT=5353 LEN=99 
Jul  5 11:58:13 supernova kernel: [327449.110650] IPTables-Drop: IN=wlan0 OUT= MAC= SRC=192.168.1.147 DST=224.0.0.251 LEN=119 TOS=0x00 PREC=0x00 TTL=255 ID=48472 DF PROTO=UDP SPT=5353 DPT=5353 LEN=99 
Jul  5 11:58:13 supernova kernel: [327449.172321] IPTables-Drop: IN=wlan0 OUT= MAC= SRC=192.168.1.103 DST=224.0.0.251 LEN=781 TOS=0x00 PREC=0x00 TTL=255 ID=56996 PROTO=UDP SPT=5353 DPT=5353 LEN=761 
Jul  5 11:58:16 supernova kernel: [327452.250070] IPTables-Drop: IN=wlan0 OUT= MAC= SRC=192.168.1.103 DST=224.0.0.251 LEN=781 TOS=0x00 PREC=0x00 TTL=255 ID=58276 PROTO=UDP SPT=5353 DPT=5353 LEN=761 
Jul  5 11:58:28 supernova kernel: [327464.094966] IPTables-Drop: IN=virbr0 OUT= MAC= SRC=192.168.122.1 DST=224.0.0.251 LEN=119 TOS=0x00 PREC=0x00 TTL=255 ID=48479 DF PROTO=UDP SPT=5353 DPT=5353 LEN=99 
Jul  5 11:58:28 supernova kernel: [327464.095015] IPTables-Drop: IN=lxcbr0 OUT= MAC= SRC=10.0.3.1 DST=224.0.0.251 LEN=119 TOS=0x00 PREC=0x00 TTL=255 ID=48480 DF PROTO=UDP SPT=5353 DPT=5353 LEN=99 
Jul  5 11:58:28 supernova kernel: [327464.095147] IPTables-Drop: IN=wlan0 OUT= MAC= SRC=192.168.1.147 DST=224.0.0.251 LEN=119 TOS=0x00 PREC=0x00 TTL=255 ID=48481 DF PROTO=UDP SPT=5353 DPT=5353 LEN=99 
Jul  5 11:58:28 supernova kernel: [327464.190026] IPTables-Drop: IN=wlan0 OUT= MAC= SRC=192.168.1.103 DST=224.0.0.251 LEN=781 TOS=0x00 PREC=0x00 TTL=255 ID=58532 PROTO=UDP SPT=5353 DPT=5353 LEN=761 
Jul  5 11:58:31 supernova kernel: [327467.155791] IPTables-Drop: IN=wlan0 OUT= MAC= SRC=192.168.1.103 DST=224.0.0.251 LEN=781 TOS=0x00 PREC=0x00 TTL=255 ID=58788 PROTO=UDP SPT=5353 DPT=5353 LEN=761

---

### Post by wmsopou on 2014-07-05
I opened muticast on port 5353 and the printer showed up right away.

-A INPUT -i lo -j ACCEPT
-A INPUT -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
**-A INPUT -d 224.0.0.251/32 -p udp --dport 5353 -j ACCEPT**
-A INPUT -j DROP

---

