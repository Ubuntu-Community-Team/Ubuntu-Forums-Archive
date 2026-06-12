---
title: "Simple iptables any rule question .. hopefully"
date: 2018-02-18
forum: Networking &amp; Wireless
---

### Post by Andrew_Welham on 2018-02-18
Everything is starting to get there, just having a few issues with some any any  rules


```

$IPTABLES -N RULE_8
$IPTABLES -A INPUT -m iprange --src-range 192.168.0.1-192.168.8.253  -m state --state NEW  -j RULE_8
$IPTABLES -A OUTPUT -m iprange --src-range 192.168.0.1-192.168.8.253  -m state --state NEW  -j RULE_8
$IPTABLES -A FORWARD -m iprange --src-range 192.168.0.1-192.168.8.253  -m state --state NEW  -j RULE_8
$IPTABLES -A RULE_8  -j LOG  --log-level 6 --log-prefix "iptables: RULE 8 -- ACCEPT "
$IPTABLES -A RULE_8  -j ACCEPT

```

to allow any device in a defined range to access any ip on any service, and it generally appears to work well except for the following a few examples

```

Feb 18 13:00:23 gw1 kernel: [  874.407272] iptables: RULE 9 -- DENY IN=enp0s9 OUT=enp0s3 MAC=08:00:27:e0:0e:0e:c0:7c:d1:fd:01:82:08:00 SRC=192.168.1.4 DST=216.58.213.74 LEN=40 TOS=0x00 PREC=0x00 TTL=127 ID=7018 DF PROTO=TCP SPT=53806 DPT=443 WINDOW=0 RES=0x00 ACK RST URGP=0
Feb 18 13:00:56 gw1 kernel: [  908.179541] iptables: RULE 9 -- DENY IN=enp0s9 OUT=enp0s3 MAC=08:00:27:e0:0e:0e:c0:7c:d1:fd:01:82:08:00 SRC=192.168.1.4 DST=13.107.5.88 LEN=40 TOS=0x00 PREC=0x00 TTL=127 ID=6118 DF PROTO=TCP SPT=63899 DPT=443 WINDOW=0 RES=0x00 ACK RST URGP=0
Feb 18 13:00:56 gw1 kernel: [  908.180476] iptables: RULE 9 -- DENY IN=enp0s9 OUT=enp0s3 MAC=08:00:27:e0:0e:0e:c0:7c:d1:fd:01:82:08:00 SRC=192.168.1.4 DST=13.107.3.128 LEN=40 TOS=0x00 PREC=0x00 TTL=127 ID=24221 DF PROTO=TCP SPT=63904 DPT=443 WINDOW=0 RES=0x00 ACK RST URGP=0
Feb 18 13:00:57 gw1 kernel: [  908.544863] iptables: RULE 9 -- DENY IN=enp0s9 OUT=enp0s3 MAC=08:00:27:e0:0e:0e:c0:7c:d1:fd:01:82:08:00 SRC=192.168.1.4 DST=40.121.213.159 LEN=40 TOS=0x00 PREC=0x00 TTL=127 ID=3530 DF PROTO=TCP SPT=63905 DPT=443 WINDOW=0 RES=0x00 ACK RST URGP=0

```

it appears to be something to do with the flags, but i cant work out why an any/any rule is not working
The rules building software is fwbuilder

---

