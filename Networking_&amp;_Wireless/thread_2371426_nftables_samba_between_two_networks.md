---
title: "nftables samba between two networks"
date: 2017-09-14
forum: Networking &amp; Wireless
---

### Post by corsairetc on 2017-09-14
Hello I start learning with nftables. So far so good. Now I can't figureout how to allow samba betwenn two networks.
I have lan_net (172.16.1.0/24) 
I have dmz_net (10.10.10.0/24)
I allow in forward chain this:
```
ip saddr { $lan_net } udp dport {137,138} ip daddr { $dmz_net } log prefix "SmbLanToDmz:" ct state new accept
                ip saddr { $lan_net } tcp dport {139,445} ip daddr { $dmz_net } log prefix "SmbLanToDmz:" ct state new accept
                ip saddr { $dmz_net } udp dport {137,138} ip daddr { $lan_net } log prefix "SmbDmzToLan:" ct state new accept
                ip saddr { $dmz_net } tcp dport {139,445} ip daddr { $lan_net } log prefix "SmbDmzToLan:" ct state new accept
```
OUTPUT chain is accept for all. 
sysctl.conf has allow ipv4 forward to 1. 
Thank you for any help.

---

### Post by SeijiSensei on 2017-09-14
Does Samba work if you have no firewall rules in place?

---

### Post by corsairetc on 2017-09-14
I have smb share on windows 7 computer for anyone in dmz_net (10.10.10.0/24) and also smb share on second computer for anyone in lan_net (172.16.1.0/24).
 The liunx firewall act only as router for connect this two network together via forward rule, as attach rules up. Strange is the firewall log says this computers can contact and nftables let them connect see attach log:
```
Sep 14 14:14:31 gateway kernel: [ 8346.286377] SmbLanToDmz:IN=enp4s0 OUT=enp1s0 MAC=00:30:4f:1c:40:1d:f8:ca:b8:45:74:56:08:00 SRC=172.16.1.10 DST=10.10.10.177 LEN=52 TOS=0x00 PREC=0x00 TTL=127 ID=6387 DF PROTO=TCP SPT=49609 DPT=445 WINDOW=8192 RES=0x00 SYN URGP=0
Sep 14 14:14:34 gateway kernel: [ 8349.302839] SmbLanToDmz:IN=enp4s0 OUT=enp1s0 MAC=00:30:4f:1c:40:1d:f8:ca:b8:45:74:56:08:00 SRC=172.16.1.10 DST=10.10.10.177 LEN=52 TOS=0x00 PREC=0x00 TTL=127 ID=6392 DF PROTO=TCP SPT=49609 DPT=445 WINDOW=8192 RES=0x00 SYN URGP=0
Sep 14 14:14:34 gateway kernel: [ 8349.666003] SmbLanToDmz:IN=enp4s0 OUT=enp1s0 MAC=00:30:4f:1c:40:1d:f8:ca:b8:45:74:56:08:00 SRC=172.16.1.10 DST=10.10.10.177 LEN=78 TOS=0x00 PREC=0x00 TTL=127 ID=6396 PROTO=UDP SPT=137 DPT=137 LEN=58
Sep 14 14:14:36 gateway kernel: [ 8351.174839] SmbLanToDmz:IN=enp4s0 OUT=enp1s0 MAC=00:30:4f:1c:40:1d:f8:ca:b8:45:74:56:08:00 SRC=172.16.1.10 DST=10.10.10.177 LEN=78 TOS=0x00 PREC=0x00 TTL=127 ID=6401 PROTO=UDP SPT=137 DPT=137 LEN=58
Sep 14 14:14:38 gateway kernel: [ 8352.688015] SmbLanToDmz:IN=enp4s0 OUT=enp1s0 MAC=00:30:4f:1c:40:1d:f8:ca:b8:45:74:56:08:00 SRC=172.16.1.10 DST=10.10.10.177 LEN=78 TOS=0x00 PREC=0x00 TTL=127 ID=6402 PROTO=UDP SPT=137 DPT=137 LEN=58
Sep 14 14:14:40 gateway kernel: [ 8355.308873] SmbLanToDmz:IN=enp4s0 OUT=enp1s0 MAC=00:30:4f:1c:40:1d:f8:ca:b8:45:74:56:08:00 SRC=172.16.1.10 DST=10.10.10.177 LEN=48 TOS=0x00 PREC=0x00 TTL=127 ID=6405 DF PROTO=TCP SPT=49609 DPT=445 WINDOW=8192 RES=0x00 SYN URGP=0
Sep 14 14:21:39 gateway kernel: [ 8773.990563] SmbLanToDmz:IN=enp4s0 OUT=enp1s0 MAC=00:30:4f:1c:40:1d:f8:ca:b8:45:74:56:08:00 SRC=172.16.1.10 DST=10.10.10.177 LEN=52 TOS=0x00 PREC=0x00 TTL=127 ID=6558 DF PROTO=TCP SPT=49624 DPT=445 WINDOW=8192 RES=0x00 SYN URGP=0
Sep 14 14:21:42 gateway kernel: [ 8777.009809] SmbLanToDmz:IN=enp4s0 OUT=enp1s0 MAC=00:30:4f:1c:40:1d:f8:ca:b8:45:74:56:08:00 SRC=172.16.1.10 DST=10.10.10.177 LEN=52 TOS=0x00 PREC=0x00 TTL=127 ID=6565 DF PROTO=TCP SPT=49624 DPT=445 WINDOW=8192 RES=0x00 SYN URGP=0
Sep 14 14:21:42 gateway kernel: [ 8777.373156] SmbLanToDmz:IN=enp4s0 OUT=enp1s0 MAC=00:30:4f:1c:40:1d:f8:ca:b8:45:74:56:08:00 SRC=172.16.1.10 DST=10.10.10.177 LEN=78 TOS=0x00 PREC=0x00 TTL=127 ID=6569 PROTO=UDP SPT=137 DPT=137 LEN=58
Sep 14 14:21:44 gateway kernel: [ 8778.881811] SmbLanToDmz:IN=enp4s0 OUT=enp1s0 MAC=00:30:4f:1c:40:1d:f8:ca:b8:45:74:56:08:00 SRC=172.16.1.10 DST=10.10.10.177 LEN=78 TOS=0x00 PREC=0x00 TTL=127 ID=6575 PROTO=UDP SPT=137 DPT=137 LEN=58
Sep 14 14:21:45 gateway kernel: [ 8780.395116] SmbLanToDmz:IN=enp4s0 OUT=enp1s0 MAC=00:30:4f:1c:40:1d:f8:ca:b8:45:74:56:08:00 SRC=172.16.1.10 DST=10.10.10.177 LEN=78 TOS=0x00 PREC=0x00 TTL=127 ID=6577 PROTO=UDP SPT=137 DPT=137 LEN=58
Sep 14 14:21:48 gateway kernel: [ 8783.015836] SmbLanToDmz:IN=enp4s0 OUT=enp1s0 MAC=00:30:4f:1c:40:1d:f8:ca:b8:45:74:56:08:00 SRC=172.16.1.10 DST=10.10.10.177 LEN=48 TOS=0x00 PREC=0x00 TTL=127 ID=6578 DF PROTO=TCP SPT=49624 DPT=445 WINDOW=8192 RES=0x00 SYN URGP=0
```
It take some time and then windows 7 says cannot find network path.

---

### Post by SeijiSensei on 2017-09-14
Are you using references like \\server-name\share on Windows or //server-name/share on Linux?  If so, try replacing the server names with their IP addresses like \\10.10.10.10\share.  That way we'll know if it's a problem with name resolution.

---

### Post by corsairetc on 2017-09-15
Hello,
Yes I am using ms way \\server\share or ip both not work. Strange is one thing it takes very long time until windows say can't connect. Maybe I missing some port to allow.

---

### Post by corsairetc on 2017-09-15
Hello, I solved the problem. I have to manually add to windows firewall rule for TCP and UDP ports (135,136,137,138,139,445) the it start working.

---

