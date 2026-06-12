---
title: "UFW allow port anywhere but drops some packets anyway"
date: 2014-08-20
forum: Networking &amp; Wireless
---

### Post by andrew102 on 2014-08-20
I'm noticing UFW is dropping some legitimate traffic that we allow to port 443. (Note the first source aa.bb.cc.dd was a genuine block on port 22)

```
Aug 20 15:54:55 localhost kernel: [1373415.450195] [UFW BLOCK] IN=eth0 OUT= MAC=00 SRC=aa.bb.cc.dd DST=yy.yy.yy.yy LEN=40 TOS=0x00 PREC=0x00 TTL=114 ID=256 PROTO=TCP SPT=42855 DPT=22 WINDOW=16384 RES=0x00 SYN URGP=0 
Aug 20 15:55:06 localhost kernel: [1373426.062421] [UFW BLOCK] IN=eth0 OUT= MAC=00 SRC=xx.xx.xx.xx DST=yy.yy.yy.yy LEN=40 TOS=0x00 PREC=0x20 TTL=60 ID=0 DF PROTO=TCP SPT=56739 DPT=443 WINDOW=0 RES=0x00 RST URGP=0 
Aug 20 15:55:26 localhost kernel: [1373446.790480] [UFW BLOCK] IN=eth0 OUT= MAC=00 SRC=xx.xx.xx.xx DST=yy.yy.yy.yy LEN=40 TOS=0x00 PREC=0x20 TTL=60 ID=0 DF PROTO=TCP SPT=56883 DPT=443 WINDOW=0 RES=0x00 RST URGP=0 
Aug 20 15:56:12 localhost kernel: [1373492.265662] [UFW BLOCK] IN=eth0 OUT= MAC=00 SRC=xx.xx.xx.xx DST=yy.yy.yy.yy LEN=40 TOS=0x00 PREC=0x20 TTL=60 ID=0 DF PROTO=TCP SPT=57283 DPT=443 WINDOW=0 RES=0x00 RST URGP=0 
Aug 20 15:56:12 localhost kernel: [1373492.273190] [UFW BLOCK] IN=eth0 OUT= MAC=00 SRC=xx.xx.xx.xx DST=yy.yy.yy.yy LEN=40 TOS=0x00 PREC=0x20 TTL=60 ID=0 DF PROTO=TCP SPT=57284 DPT=443 WINDOW=0 RES=0x00 RST URGP=0 
Aug 20 15:56:12 localhost kernel: [1373492.275641] [UFW BLOCK] IN=eth0 OUT= MAC=00 SRC=xx.xx.xx.xx DST=yy.yy.yy.yy LEN=40 TOS=0x00 PREC=0x20 TTL=60 ID=0 DF PROTO=TCP SPT=57285 DPT=443 WINDOW=0 RES=0x00 RST URGP=0
```


Current UFW status is something like

```
80                         ALLOW       Anywhere
443                        ALLOW       Anywhere
```


I only realised this when checking out the logs before I went to change UFW to allow only specific address.

Worried that if I ONLY allow this address may become restricted.

Why would it be dropping some of the packets from one of main IP (lots of traffic) to this one port 443? You can see it's dropping several per minute, is it a "burst" limit ?

```
80                         ALLOW       xx.xxx.xxx.xxx
443                        ALLOW       xx.xxx.xxx.xxx
```

---

