---
title: "ufw ignoring rules"
date: 2018-07-13
forum: Networking &amp; Wireless
---

### Post by joe52 on 2018-07-13
Hello, I need some help, I am stumped.  Freshly installed 18.04 on a VM and trying to use OpenConnect VPN (ocserv) on it, so i can connect remotely and access my home network.  I am able to login via AnyConnect on my iPhone, and can access all my resources, except for my Camera system.  It is on IP 192.168.1.13 TCP port 9000.

First, created this rule in ufw, "ufw allow 9000".  But I can not access the camera system.  I turned on ufw logging and got this:

Jul 13 10:00:46 w******u kernel: [ 5260.300697] [UFW BLOCK] IN=vpns0 OUT=enp0s3 MAC= SRC=192.168.1.14 DST=**192.168.1.13** LEN=64 TOS=0x00 PREC=0x00 TTL=63 ID=0 DF PROTO=TCP SPT=54811 **DPT=9000** WINDOW=65535 RES=0x00 SYN URGP=0

When i disable ufw, it works, so it has something to do with either ufw or iptables.  Below is my ufw & iptables output:

root@w******u:/etc/ocserv# ufw status
Status: active


To                         Action      From
--                         ------      ----
22                         ALLOW       Anywhere
80                         ALLOW       Anywhere
443                        ALLOW       Anywhere
9000                       ALLOW       Anywhere
53                         ALLOW       Anywhere
139                        ALLOW       Anywhere
445                        ALLOW       Anywhere
137                        ALLOW       Anywhere
138                        ALLOW       Anywhere
22 (v6)                    ALLOW       Anywhere (v6)
80 (v6)                    ALLOW       Anywhere (v6)
443 (v6)                   ALLOW       Anywhere (v6)
9000 (v6)                  ALLOW       Anywhere (v6)
53 (v6)                    ALLOW       Anywhere (v6)
139 (v6)                   ALLOW       Anywhere (v6)
445 (v6)                   ALLOW       Anywhere (v6)
137 (v6)                   ALLOW       Anywhere (v6)
138 (v6)                   ALLOW       Anywhere (v6)


root@w******u:/etc/ocserv# iptables -L -v -n |grep 9000
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:9000
    1    40 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:9000
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:9000
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:9000
	

I have tried resetting the ufw from scratch, and re-building, and still nothing.  

The whole point of this, is i have a server running Debian 8 and have the same issue, so i tried to replicate it on a fresh install of Ubuntu and it does the same thing.

I was wondering if i need to try some other ufw commands or iptables commands.

Basically i want all traffic on interface vpns0 able to access everything on interface enp0s3 (VM interface).

---

