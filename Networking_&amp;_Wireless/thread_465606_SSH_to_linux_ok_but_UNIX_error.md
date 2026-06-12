---
title: "SSH to linux ok but UNIX error"
date: 2007-06-05
forum: Networking &amp; Wireless
---

### Post by adamscao on 2007-06-05
Hi all,

    I have feisty on DELL latitude D610, the network setup by DHCP correctly. 

```
[~]$ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:15:C5:19:42:FA  
          inet addr:133.37.55.224  Bcast:133.37.55.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:43502 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9371 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9917810 (9.4 MiB)  TX bytes:1844350 (1.7 MiB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:16:6F:93:F0:F7  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:576837 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52551 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0x8000 Memory:dfcff000-dfcfffff 

eth1:avah Link encap:Ethernet  HWaddr 00:16:6F:93:F0:F7  
          inet addr:169.254.11.65  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:18 Base address:0x8000 Memory:dfcff000-dfcfffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

```

I visit internet by gateway 133.37.55.3, and visit internal network by gateway 133.37.55.1, so I add route like this:

```
[~]$route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
133.37.55.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     0      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth0
133.0.0.0       133.37.55.1     255.0.0.0       UG    0      0        0 eth0
default         133.37.55.3     0.0.0.0         UG    0      0        0 eth0
default         *               0.0.0.0         U     1000   0        0 eth1

```

Then I can ping the internal server, which is HP server(HP-UX), But I can't ssh it. When I type the ssh command, it has nothing response. It make me puzzled if I ssh a linux server, it works perfect.

I guess, it maybe has an error firewall setup, so I clean all iptables config, but it still can't work.

```
[~]$sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy DROP)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

The HP server provide SSH, TELNET, FTP, HTTP, ORACLE services. Each service have problem when I visited, no response.

```
[~]$ftp sc131
Connected to sc131.
220 xz_bak FTP server (Version 1.1.214.4(PHNE_34544) Fri Feb 24 15:03:24 GMT 2006) ready.
Name (sc131:adams): bill
331 Password required for bill.
Password:
230 User bill logged in.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> ls
200 PORT command successful.
425 Can't build data connection: Connection timed out.
ftp> 

```

```
[~]$telnet sc131
Trying 133.37.8.131...
Connected to sc131.
Escape character is '^]'.

HP-UX xz_bak B.11.11 U 9000/800 (ta)

login: bill
Password: 
Please wait...checking for disk quotas


```

```
[~]$tnsping testbill_131

TNS Ping Utility for Linux: Version 10.2.0.1.0 - Production on 06-JUN-2007 10:04:45

Copyright (c) 1997, 2005, Oracle.  All rights reserved.

Used parameter files:


Used TNSNAMES adapter to resolve the alias
Attempting to contact (DESCRIPTION=(ADDRESS_LIST=(ADDRESS=(PROTOCOL=TCP)(HOST=133.37.8.131)(PORT=1521)))(CONNECT_DATA=(SERVER=DEDICATED)(SID=testbill)))
OK (10 msec)
[~]$sqlplus bill/lm_bill@testbill_131

SQL*Plus: Release 10.2.0.1.0 - Production on Wed Jun 6 10:04:58 2007

Copyright (c) 1982, 2005, Oracle.  All rights reserved.


```

I haven't any way to deal this, then I catch the data from tcpdump when ssh. Because I'm newbie, I don't understand information from these data.

```
[~]$sudo tcpdump host sc131
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes

0 packets captured
0 packets received by filter
0 packets dropped by kernel
[~]$sudo tcpdump -vv host sc131
tcpdump: listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes
10:15:46.717582 IP (tos 0x0, ttl  64, id 11079, offset 0, flags [DF], proto: TCP (6), length: 60) 133.37.55.224.34951 > sc131.ssh: S, cksum 0x6aea (correct), 2787586721:2787586721(0) win 5840 <mss 1460,sackOK,timestamp 5118438 0,nop,wscale 5>
10:15:49.714282 IP (tos 0x0, ttl  64, id 11080, offset 0, flags [DF], proto: TCP (6), length: 60) 133.37.55.224.34951 > sc131.ssh: S, cksum 0x67fc (correct), 2787586721:2787586721(0) win 5840 <mss 1460,sackOK,timestamp 5119188 0,nop,wscale 5>
10:15:49.716042 IP (tos 0x0, ttl  61, id 63844, offset 0, flags [DF], proto: TCP (6), length: 64) sc131.ssh > 133.37.55.224.34951: S, cksum 0x85a8 (correct), 3201509725:3201509725(0) ack 2787586722 win 32768 <mss 1460,nop,nop,sackOK,wscale 0,nop,nop,nop,timestamp 1017660215 5119188>
10:15:49.716097 IP (tos 0x0, ttl  64, id 11081, offset 0, flags [DF], proto: TCP (6), length: 52) 133.37.55.224.34951 > sc131.ssh: ., cksum 0x44be (correct), 1:1(0) ack 1 win 183 <nop,nop,timestamp 5119188 1017660215>
10:15:49.789950 IP (tos 0x0, ttl  61, id 63845, offset 0, flags [DF], proto: TCP (6), length: 72) sc131.ssh > 133.37.55.224.34951: P, cksum 0x11ac (correct), 1:21(20) ack 1 win 32768 <nop,nop,timestamp 1017660222 5119188>
10:15:49.790119 IP (tos 0x0, ttl  64, id 11082, offset 0, flags [DF], proto: TCP (6), length: 52) 133.37.55.224.34951 > sc131.ssh: ., cksum 0x4491 (correct), 1:1(0) ack 21 win 183 <nop,nop,timestamp 5119206 1017660222>
10:15:49.790280 IP (tos 0x0, ttl  64, id 11083, offset 0, flags [DF], proto: TCP (6), length: 90) 133.37.55.224.34951 > sc131.ssh: P 1:39(38) ack 21 win 183 <nop,nop,timestamp 5119207 1017660222>
10:15:49.994294 IP (tos 0x0, ttl  64, id 11084, offset 0, flags [DF], proto: TCP (6), length: 90) 133.37.55.224.34951 > sc131.ssh: P 1:39(38) ack 21 win 183 <nop,nop,timestamp 5119258 1017660222>
10:15:49.995184 IP (tos 0x0, ttl  61, id 63847, offset 0, flags [DF], proto: TCP (6), length: 52) sc131.ssh > 133.37.55.224.34951: ., cksum 0xc50b (correct), 21:21(0) ack 39 win 32768 <nop,nop,timestamp 1017660243 5119207>
10:15:49.995221 IP (tos 0x0, ttl  64, id 11085, offset 0, flags [DF], proto: TCP (6), length: 764) 133.37.55.224.34951 > sc131.ssh: P 39:751(712) ack 21 win 183 <nop,nop,timestamp 5119258 1017660243>
10:15:50.066763 IP (tos 0x0, ttl  61, id 63848, offset 0, flags [DF], proto: TCP (6), length: 52) sc131.ssh > 133.37.55.224.34951: ., cksum 0xbf89 (correct), 661:661(0) ack 751 win 32768 <nop,nop,timestamp 1017660250 5119258>

```

The host "sc131" is "133.37.8.131" which define in /etc/hosts.

I'm sorry for my bad english, “light bless you”;) can catch what I means. Thank you for concerning my trouble&#65292; and any suggestion?

---

### Post by adamscao on 2007-06-07
Could anyone help me ?

Everything(visit ssh, httpd, oracle server) is ok in windowz.

---

