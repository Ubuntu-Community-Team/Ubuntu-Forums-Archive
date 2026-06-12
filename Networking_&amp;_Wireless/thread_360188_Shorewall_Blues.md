---
title: "Shorewall Blues"
date: 2007-02-12
forum: Networking &amp; Wireless
---

### Post by andytof47 on 2007-02-12
Hi I am having major headaches getting a 2 NIC system up and running using Shorewall

I am using shorewall because I want to use a 3 NIC setup once My 2 NIC is up and running

I am Using webmin, so you wouldn't think that I could get it wrong but I have

I am connected to a router on eth1 192.168.1.2 this is my net interface

then i have another interface called loc 192.168.2.5

I can access the internet from the machine running shorewall but not from 192.168.2.9 - a Linsys voip box

here is my config

hereis my rules
```
ACCEPT	loc	net	tcp	5060	5060
ACCEPT:info	net	loc	tcp	5060	5060
ACCEPT	$FW	loc	tcp	29000	29000
ACCEPT	loc	$FW	tcp	29000	29000
 #ACTION SOURCE DEST PROTO DEST SOURCE ORIGINAL RATE USER/
# PORT PORT(S) DEST LIMIT GROUP
ACCEPT net fw icmp 8
ACCEPT fw net icmp
ACCEPT net fw tcp ssh,www,https,smtp,pop3,pop3s,imap2,imaps,submission
ACCEPT net fw udp https
#ACCEPT net:216.162.217.194 fw tcp munin 

```


Here is my policies
```
#SOURCE    DEST        POLICY      LOG LEVEL    LIMIT:BURST
fw	net	ACCEPT	info
fw	loc	ACCEPT	info
net	all	DROP	ULOG
all        all         REJECT      info

```

Here is my zones
```
#ZONE   TYPE   OPTIONS                 IN                      OUT
#                                      OPTIONS                 OPTIONS
fw      firewall
net     ipv4
loc     ipv4
wifi     ipv4
```

Here is my syslog

```
Feb 13 12:58:02 cc-desktop kernel: [17194398.536000] BANDWIDTH_OUT:IN=eth0 OUT=eth1 SRC=192.168.2.9 DST=203.2.124.165 LEN=66 TOS=0x00 PREC=0x00 TTL=249 ID=8166 PROTO=UDP SPT=15775 DPT=53 LEN=46 
Feb 13 12:58:02 cc-desktop kernel: [17194398.536000] Shorewall:all2all:REJECT:IN=eth0 OUT=eth1 SRC=192.168.2.9 DST=203.2.124.165 LEN=66 TOS=0x00 PREC=0x00 TTL=249 ID=8166 PROTO=UDP SPT=15775 DPT=53 LEN=46 
Feb 13 12:58:03 cc-desktop kernel: [17194399.536000] BANDWIDTH_OUT:IN=eth0 OUT=eth1 
```

So i'm not sure exactly why REJECT is Coming up if anyone can help it would be greatly appreciated

I really need my VOIP up and running through this little setup

---

