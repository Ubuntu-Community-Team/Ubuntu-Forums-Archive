---
title: "DNS not resolving LAN hostnames"
date: 2018-05-30
forum: Networking &amp; Wireless
---

### Post by alanwalterthomas on 2018-05-30
I'm having a similar problem.
My machine won't resolve local LAN hostnames, but works otherwise.
The hostname in question is U35WF. It's at 192.168.1.101
My home router is at 192.168.1.2. It's name is E3000 and I can't access it via hostname either. If I ssh into it via its ip address it correctly resolves U35WF to 192.168.1.101.

Here are my results for the commands you asked to run, plus a couple others.
```
alan at P100 in ~ 
$ apt policy netplan
netplan:
  Installed: (none)
  Candidate: 1.10.1-5build1
  Version table:
     1.10.1-5build1 500
        500 http://archive.ubuntu.com/ubuntu bionic/universe i386 Packages

alan at P100 in ~ 
$ apt policy netplan.io
netplan.io:
  Installed: 0.36.1
  Candidate: 0.36.1
  Version table:
 *** 0.36.1 500
        500 http://archive.ubuntu.com/ubuntu bionic/main i386 Packages
        100 /var/lib/dpkg/status

alan at P100 in ~ 
$ ip address
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether 00:16:36:de:17:0e brd ff:ff:ff:ff:ff:ff
3: wlan0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 00:19:d2:3a:65:06 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.99/24 brd 192.168.1.255 scope global dynamic noprefixroute wlan0
       valid_lft 82163sec preferred_lft 82163sec
    inet6 fe80::abce:be2d:e90:60c6/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
4: virbr0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether 52:54:00:67:01:5e brd ff:ff:ff:ff:ff:ff
    inet 192.168.122.1/24 brd 192.168.122.255 scope global virbr0
       valid_lft forever preferred_lft forever
5: virbr0-nic: <BROADCAST,MULTICAST> mtu 1500 qdisc fq_codel master virbr0 state DOWN group default qlen 1000
    link/ether 52:54:00:67:01:5e brd ff:ff:ff:ff:ff:ff

alan at P100 in ~ 
$ ip route
default via 192.168.1.2 dev wlan0 proto dhcp metric 600 
169.254.0.0/16 dev virbr0 scope link metric 1000 linkdown 
192.168.1.0/24 dev wlan0 proto kernel scope link src 192.168.1.99 metric 600 
192.168.122.0/24 dev virbr0 proto kernel scope link src 192.168.122.1 linkdown 

alan at P100 in ~ 
$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

alan at P100 in ~ 
$ cat /etc/resolv.conf
# This file is managed by man:systemd-resolved(8). Do not edit.
#
# This is a dynamic resolv.conf file for connecting local clients to the
# internal DNS stub resolver of systemd-resolved. This file lists all
# configured search domains.
#
# Run "systemd-resolve --status" to see details about the uplink DNS servers
# currently in use.
#
# Third party programs must not access this file directly, but only through the
# symlink at /etc/resolv.conf. To manage man:resolv.conf(5) in a different way,
# replace this symlink by a static file or a different symlink.
#
# See man:systemd-resolved.service(8) for details about the supported modes of
# operation for /etc/resolv.conf.

nameserver 127.0.0.53

alan at P100 in ~ 
$ cat /etc/nsswitch.conf
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat systemd
group:          compat systemd
shadow:         compat
gshadow:        files

hosts:          files mdns4_minimal [NOTFOUND=return] wins dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

alan at P100 in ~ 
$ nslookup ubuntu.com
Server:		127.0.0.53
Address:	127.0.0.53#53

Non-authoritative answer:
Name:	ubuntu.com
Address: 91.189.94.40


alan at P100 in ~ 
$ nslookup U35WF
Server:		127.0.0.53
Address:	127.0.0.53#53

** server can't find U35WF: SERVFAIL


alan at P100 in ~ 
$ dig ubuntuforums.com

; <<>> DiG 9.11.3-1ubuntu1-Ubuntu <<>> ubuntuforums.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 6265
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;ubuntuforums.com.		IN	A

;; ANSWER SECTION:
ubuntuforums.com.	600	IN	A	91.189.94.12
ubuntuforums.com.	600	IN	A	91.189.94.16

;; Query time: 138 msec
;; SERVER: 127.0.0.53#53(127.0.0.53)
;; WHEN: Wed May 30 00:05:26 EDT 2018
;; MSG SIZE  rcvd: 77


alan at P100 in ~ 
$ dig U35WF

; <<>> DiG 9.11.3-1ubuntu1-Ubuntu <<>> U35WF
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 10085
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;U35WF.				IN	A

;; Query time: 0 msec
;; SERVER: 127.0.0.53#53(127.0.0.53)
;; WHEN: Wed May 30 00:05:32 EDT 2018
;; MSG SIZE  rcvd: 34


alan at P100 in ~ 
$ dig U35WF @192.168.1.2

; <<>> DiG 9.11.3-1ubuntu1-Ubuntu <<>> U35WF @192.168.1.2
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 21027
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;U35WF.				IN	A

;; ANSWER SECTION:
U35WF.			0	IN	A	192.168.1.101

;; Query time: 2 msec
;; SERVER: 192.168.1.2#53(192.168.1.2)
;; WHEN: Wed May 30 00:05:41 EDT 2018
;; MSG SIZE  rcvd: 50


alan at P100 in ~ 
$ ping 192.168.1.101
PING 192.168.1.101 (192.168.1.101) 56(84) bytes of data.
64 bytes from 192.168.1.101: icmp_seq=1 ttl=64 time=2.51 ms
64 bytes from 192.168.1.101: icmp_seq=2 ttl=64 time=2.38 ms
64 bytes from 192.168.1.101: icmp_seq=3 ttl=64 time=2.52 ms
^C
--- 192.168.1.101 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 2.387/2.474/2.526/0.074 ms

```

If you can tell me how to fix this, great. If you can explain how you knew what to fix, better yet.

Thanks.

---

### Post by papibe on 2018-05-30
**Moved to its own thread to help with visibility.**

(from here: [https://ubuntuforums.org/showthread.php?t=2391351](https://ubuntuforums.org/showthread.php?t=2391351))

---

### Post by HNmYk3h on 2018-05-30
See the last reply here:

[https://ubuntuforums.org/showthread.php?t=2392800](https://ubuntuforums.org/showthread.php?t=2392800)

---

### Post by alanwalterthomas on 2018-05-31
These answers
[https://ubuntuforums.org/showthread.php?t=2391351](https://ubuntuforums.org/showthread.php?t=2391351)
[https://ubuntuforums.org/showthread.php?t=2392800](https://ubuntuforums.org/showthread.php?t=2392800)
don't accomplish what I want.
I don't want to disable or replace systemd. I'd prefer to keep my system close to vanilla ubuntu.
I also don't want to specify a nameserver with my router's IP. It may change, and I don't want to be bothered to reconfigure it.
Things should automagically work, even with systemd. They don't, but I'd like to focus on figuring out what's wrong with it.

So, how to fix this without replacing systemd and without needing to specify a static IP address as my nameserver? I'm using ubuntu desktop version.

---

### Post by HNmYk3h on 2018-05-31
On my system /run/systemd/resolve/resolv.conf has nameserver set correctly (my router at 192.168.1.1) by default. The problem is that /etc/resolv.conf is linked to /run/systemd/resolve/stub-resolv.conf instead of /run/systemd/resolve/resolv.conf. I haven't figured out why this is happening, but for now I'm content to change the link and hope for a fix down the road.

---

