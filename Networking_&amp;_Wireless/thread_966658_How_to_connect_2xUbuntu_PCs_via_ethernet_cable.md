---
title: "How to connect 2xUbuntu PCs via ethernet cable?"
date: 2008-11-01
forum: Networking &amp; Wireless
---

### Post by paziek on 2008-11-01
Hello,

I've got 2 PCs using Ubuntu 8.04 and 7.10
I have been trying to connect them with cross ethernet cable, but for some reason they can't connect.
No response via HTTP, SSH, FTP, Samba

**It worked** before, but with Ubuntu 8.04 and Win XP.
Is there any howto on doing that kind of LAN? I don't have any routers or whatever, its a direct connection from eth0 to eth0.


Here is output of some tools, might be useful in finding whats the problem:



**tcpdump -vv**
```
sudo: unable to resolve host Lolita
tcpdump: listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes
16:48:49.844750 IP (tos 0x0, ttl 64, id 7514, offset 0, flags [DF], proto TCP (6), length 60) 10.1.1.2.34018 > 10.1.1.1.www: S, cksum 0x0dcf (correct), 2844323318:2844323318(0) win 5840 <mss 1460,sackOK,timestamp 61612 0,nop,wscale 5>
16:48:52.842973 IP (tos 0x0, ttl 64, id 7515, offset 0, flags [DF], proto TCP (6), length 60) 10.1.1.2.34018 > 10.1.1.1.www: S, cksum 0x0ae1 (correct), 2844323318:2844323318(0) win 5840 <mss 1460,sackOK,timestamp 62362 0,nop,wscale 5>
16:48:58.843019 IP (tos 0x0, ttl 64, id 7516, offset 0, flags [DF], proto TCP (6), length 60) 10.1.1.2.34018 > 10.1.1.1.www: S, cksum 0x0505 (correct), 2844323318:2844323318(0) win 5840 <mss 1460,sackOK,timestamp 63862 0,nop,wscale 5>
16:49:10.843112 IP (tos 0x0, ttl 64, id 7517, offset 0, flags [DF], proto TCP (6), length 60) 10.1.1.2.34018 > 10.1.1.1.www: S, cksum 0xf94c (correct), 2844323318:2844323318(0) win 5840 <mss 1460,sackOK,timestamp 66862 0,nop,wscale 5>
16:49:14.771132 IP (tos 0x0, ttl 64, id 33293, offset 0, flags [DF], proto TCP (6), length 60) 10.1.1.1.41126 > 10.1.1.2.www: S, cksum 0x24fe (correct), 773039403:773039403(0) win 5840 <mss 1460,sackOK,timestamp 360949 0,nop,wscale 5>
16:49:14.771263 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto TCP (6), length 60) 10.1.1.2.www > 10.1.1.1.41126: S, cksum 0xddf2 (correct), 3499870299:3499870299(0) ack 773039404 win 5792 <mss 1460,sackOK,timestamp 67844 337699,nop,wscale 5>
16:49:15.843134 arp who-has 10.1.1.1 tell 10.1.1.2
16:49:15.843164 arp reply 10.1.1.1 is-at 00:30:4f:2d:b0:77 (oui Unknown)
16:49:15.975137 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto TCP (6), length 60) 10.1.1.2.www > 10.1.1.1.41126: S, cksum 0xdcc5 (correct), 3499870299:3499870299(0) ack 773039404 win 5792 <mss 1460,sackOK,timestamp 68145 337699,nop,wscale 5>
16:49:34.843291 IP (tos 0x0, ttl 64, id 7518, offset 0, flags [DF], proto TCP (6), length 60) 10.1.1.2.34018 > 10.1.1.1.www: S, cksum 0xe1dc (correct), 2844323318:2844323318(0) win 5840 <mss 1460,sackOK,timestamp 72862 0,nop,wscale 5>
16:50:03.211215 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 258) 10.1.1.1.netbios-dgm > 10.255.255.255.netbios-dgm: 
>>> NBT UDP PACKET(138) Res=0x110A ID=0xA3E IP=10 (0xa).1 (0x1).1 (0x1).1 (0x1) Port=138 (0x8a) Length=216 (0xd8) Res2=0x0
SourceName=LOLITA          NameType=0x00 (Workstation)
DestName=
WARNING: Short packet. Try increasing the snap length


16:50:03.211249 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 235) 10.1.1.1.netbios-dgm > 10.255.255.255.netbios-dgm: 
>>> NBT UDP PACKET(138) Res=0x110A ID=0xA3F IP=10 (0xa).1 (0x1).1 (0x1).1 (0x1) Port=138 (0x8a) Length=193 (0xc1) Res2=0x0
SourceName=LOLITA          NameType=0x00 (Workstation)
DestName=
WARNING: Short packet. Try increasing the snap length


16:50:22.843662 IP (tos 0x0, ttl 64, id 7519, offset 0, flags [DF], proto TCP (6), length 60) 10.1.1.2.34018 > 10.1.1.1.www: S, cksum 0xb2fc (correct), 2844323318:2844323318(0) win 5840 <mss 1460,sackOK,timestamp 84862 0,nop,wscale 5>
16:50:27.843680 arp who-has 10.1.1.1 tell 10.1.1.2
16:50:27.843706 arp reply 10.1.1.1 is-at 00:30:4f:2d:b0:77 (oui Unknown)

15 packets captured
15 packets received by filter
0 packets dropped by kernel
```

**ping 10.1.1.2**
```
PING 10.1.1.2 (10.1.1.2) 56(84) bytes of data.

--- 10.1.1.2 ping statistics ---
44 packets transmitted, 0 received, 100% packet loss, time 42999ms
```

**arping 10.1.1.2**
```
WARNING: interface is ignored: Operation not permitted
ARPING 10.1.1.2 from 10.1.1.1 eth0
Unicast reply from 10.1.1.2 [00:11:85:86:E7:BC]  1.232ms
Unicast reply from 10.1.1.2 [00:11:85:86:E7:BC]  0.625ms
Unicast reply from 10.1.1.2 [00:11:85:86:E7:BC]  0.628ms
Unicast reply from 10.1.1.2 [00:11:85:86:E7:BC]  0.627ms
Unicast reply from 10.1.1.2 [00:11:85:86:E7:BC]  0.630ms
Unicast reply from 10.1.1.2 [00:11:85:86:E7:BC]  0.629ms
Unicast reply from 10.1.1.2 [00:11:85:86:E7:BC]  0.627ms
Unicast reply from 10.1.1.2 [00:11:85:86:E7:BC]  0.625ms
Unicast reply from 10.1.1.2 [00:11:85:86:E7:BC]  0.629ms
Unicast reply from 10.1.1.2 [00:11:85:86:E7:BC]  0.631ms
Unicast reply from 10.1.1.2 [00:11:85:86:E7:BC]  0.626ms
Unicast reply from 10.1.1.2 [00:11:85:86:E7:BC]  0.628ms
Unicast reply from 10.1.1.2 [00:11:85:86:E7:BC]  0.633ms
Unicast reply from 10.1.1.2 [00:11:85:86:E7:BC]  0.636ms
Unicast reply from 10.1.1.2 [00:11:85:86:E7:BC]  0.638ms
Unicast reply from 10.1.1.2 [00:11:85:86:E7:BC]  0.630ms
Unicast reply from 10.1.1.2 [00:11:85:86:E7:BC]  0.627ms
Unicast reply from 10.1.1.2 [00:11:85:86:E7:BC]  0.719ms
Unicast reply from 10.1.1.2 [00:11:85:86:E7:BC]  0.627ms
Unicast reply from 10.1.1.2 [00:11:85:86:E7:BC]  0.627ms
Sent 20 probes (1 broadcast(s))
Received 20 response(s)
```

**ifconfig**
```
eth0      Link encap:Ethernet  HWaddr 00:30:4f:2d:b0:77  
          inet addr:10.1.1.1  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::230:4fff:fe2d:b077/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11235 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2135 errors:0 dropped:0 overruns:0 carrier:0
          collisions:1089 txqueuelen:1000 
          RX bytes:3937217 (3.7 MB)  TX bytes:216287 (211.2 KB)
          Interrupt:16 Base address:0xec00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:888 errors:0 dropped:0 overruns:0 frame:0
          TX packets:888 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:285079 (278.3 KB)  TX bytes:285079 (278.3 KB)

```
Second PC has more or less the same ifconfig output, just the last char on MAC is different, and IP is 10.1.1.2

iptables are empty on both PCs (via **sudo iptables -F**)



Thanks in advance for any help,
Paziek.

---

### Post by alpage2 on 2008-11-01
Work through the NFS HOWTO, and post again if you get stuck:

[http://tldp.org/HOWTO/NFS-HOWTO/index.html](http://tldp.org/HOWTO/NFS-HOWTO/index.html)

Alan

---

