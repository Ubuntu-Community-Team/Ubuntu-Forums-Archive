---
title: "eth problems"
date: 2008-04-02
forum: Networking &amp; Wireless
---

### Post by EnvisiblePenguin on 2008-04-02
I have had frequent crashes on my computer and it appears to be from the eth0/eth1 interface. So here is what I've noticed. I constantly get this message in the /var/log/kern.log file when the computer freezes (including after X has completely frozen and nothing else works)

```
Apr  2 01:28:38 cerebrum kernel: [ 3837.244252] Inbound IN=eth1 OUT= MAC= SRC=192.168.1.2 DST=192.168.1.255 LEN=158 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=138 
Apr  2 01:28:51 cerebrum kernel: [ 3850.308958] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:13:72:18:62:1c:08:00 SRC=10.23.7.220 DST=10.23.7.255 LEN=96 TOS=0x00 PREC=0x00 TTL=128 ID=48988 PROTO=UDP SPT=1984 DPT=20001 LEN=76 
Apr  2 01:28:52 cerebrum kernel: [ 3851.071981] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:13:72:18:62:1c:08:00 SRC=10.23.7.220 DST=10.23.7.255 LEN=96 TOS=0x00 PREC=0x00 TTL=128 ID=49061 PROTO=UDP SPT=1984 DPT=20001 LEN=76 
Apr  2 01:28:53 cerebrum kernel: [ 3851.837126] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:13:72:18:62:1c:08:00 SRC=10.23.7.220 DST=10.23.7.255 LEN=96 TOS=0x00 PREC=0x00 TTL=128 ID=49063 PROTO=UDP SPT=1984 DPT=20001 LEN=76 
Apr  2 01:28:54 cerebrum kernel: [ 3852.602020] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:13:72:18:62:1c:08:00 SRC=10.23.7.220 DST=10.23.7.255 LEN=96 TOS=0x00 PREC=0x00 TTL=128 ID=49101 PROTO=UDP SPT=1984 DPT=20001 LEN=76 
Apr  2 01:28:55 cerebrum kernel: [ 3853.367062] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:13:72:18:62:1c:08:00 SRC=10.23.7.220 DST=10.23.7.255 LEN=96 TOS=0x00 PREC=0x00 TTL=128 ID=49164 PROTO=UDP SPT=1984 DPT=20001 LEN=76 
Apr  2 01:29:09 cerebrum kernel: [ 3868.217100] Inbound IN=eth1 OUT= MAC= SRC=192.168.1.2 DST=192.168.1.255 LEN=158 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=138 
Apr  2 01:29:25 cerebrum kernel: [ 3884.108722] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:13:72:18:62:1c:08:00 SRC=10.23.7.220 DST=10.23.7.255 LEN=96 TOS=0x00 PREC=0x00 TTL=128 ID=54253 PROTO=UDP SPT=1988 DPT=20001 LEN=76 
Apr  2 01:29:26 cerebrum kernel: [ 3884.871528] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:13:72:18:62:1c:08:00 SRC=10.23.7.220 DST=10.23.7.255 LEN=96 TOS=0x00 PREC=0x00 TTL=128 ID=54492 PROTO=UDP SPT=1988 DPT=20001 LEN=76 
Apr  2 01:29:27 cerebrum kernel: [ 3885.637248] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:13:72:18:62:1c:08:00 SRC=10.23.7.220 DST=10.23.7.255 LEN=96 TOS=0x00 PREC=0x00 TTL=128 ID=54767 PROTO=UDP SPT=1988 DPT=20001 LEN=76 
Apr  2 01:29:28 cerebrum kernel: [ 3886.401582] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:13:72:18:62:1c:08:00 SRC=10.23.7.220 DST=10.23.7.255 LEN=96 TOS=0x00 PREC=0x00 TTL=128 ID=54945 PROTO=UDP SPT=1988 DPT=20001 LEN=76 
Apr  2 01:29:28 cerebrum kernel: [ 3887.166446] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:13:72:18:62:1c:08:00 SRC=10.23.7.220 DST=10.23.7.255 LEN=96 TOS=0x00 PREC=0x00 TTL=128 ID=55216 PROTO=UDP SPT=1988 DPT=20001 LEN=76 
Apr  2 01:29:30 cerebrum kernel: [ 3889.268359] Inbound IN=eth0 OUT= MAC=00:11:d8:ab:14:0d:00:60:6e:70:3a:02:08:00 SRC=10.23.7.102 DST=10.23.7.209 LEN=60 TOS=0x00 PREC=0x00 TTL=32 ID=11659 PROTO=ICMP TYPE=8 CODE=0 ID=512 SEQ=62720 
Apr  2 01:29:33 cerebrum kernel: [ 3891.697358] Inbound IN=eth0 OUT= MAC=00:11:d8:ab:14:0d:00:60:6e:70:3a:02:08:00 SRC=10.23.7.102 DST=10.23.7.209 LEN=60 TOS=0x00 PREC=0x00 TTL=32 ID=11660 PROTO=ICMP TYPE=8 CODE=0 ID=512 SEQ=62976 
Apr  2 01:29:40 cerebrum kernel: [ 3899.189851] Inbound IN=eth1 OUT= MAC= SRC=192.168.1.2 DST=192.168.1.255 LEN=158 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=138 
``` 

On average I get about 10 of those every minute. I'm not really sure what to make of it. Any ideas would be greatly appreciated.

---

