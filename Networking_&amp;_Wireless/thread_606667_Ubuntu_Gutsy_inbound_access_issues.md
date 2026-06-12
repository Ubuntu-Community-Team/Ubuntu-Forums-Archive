---
title: "Ubuntu Gutsy inbound access issues"
date: 2007-11-08
forum: Networking &amp; Wireless
---

### Post by phazo on 2007-11-08
After searching the forums and the net for 2 days. I'm convinced I'm the only person having this issue.  Basically, no matter what I have tried, I can not access my Gutsy PC from any other PC on my network.  I'm trying to set up FTP or SAMBA for transferring files to my OSX and Windows machine and also to set up VNC, pings arent successful either.  I've got VSFTPD installed and ftp to localhost successfully so I know that the FTP server is responding, however the VSFTPD log doesn't show any attempts hitting it besides the localhost. 

I've completely opened up IP tables, and here is what my rulset for IP tables looks like
phazo@phazo-laptop:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination    

Here is the result of a tcp dump "things" is a Windows machine, and "phazo" is the Ubuntu machine:

phazo@phazo-laptop:~$ sudo tcpdump -i wlan0
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on wlan0, link-type EN10MB (Ethernet), capture size 96 bytes
07:06:31.292321 STP 802.1d, Config, Flags [none], bridge-id 8000.00:18:01:38:56:6b.8001, length 35
07:06:32.484636 IP 169.254.1.139.55408 > 169.254.1.255.5000: UDP, length 12
07:06:32.585261 IP things-4faa6f5b.home > phazo-laptop.home: ICMP echo request, id 512, seq 4608, length 40
07:06:32.587233 arp who-has things-4faa6f5b.home tell phazo-laptop.home
07:06:32.587383 IP phazo-laptop.home.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 255.1.254.169.in-addr.arpa. (44)
07:06:32.591294 arp reply things-4faa6f5b.home is-at 00:11:09:08:f5:04 (oui Unknown)
07:06:32.591309 IP phazo-laptop.home > things-4faa6f5b.home: ICMP echo reply, id 512, seq 4608, length 40
07:06:32.592577 IP things-4faa6f5b.home > phazo-laptop.home: ICMP things-4faa6f5b.home protocol 1 port 16732 unreachable, length 36
07:06:33.292373 STP 802.1d, Config, Flags [none], bridge-id 8000.00:18:01:38:56:6b.8001, length 35
07:06:33.591386 IP phazo-laptop.home.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 255.1.254.169.in-addr.arpa. (44)
07:06:35.292476 STP 802.1d, Config, Flags [none], bridge-id 8000.00:18:01:38:56:6b.8001, length 35
07:06:35.595348 IP phazo-laptop.home.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 255.1.254.169.in-addr.arpa. (44)
07:06:37.292567 STP 802.1d, Config, Flags [none], bridge-id 8000.00:18:01:38:56:6b.8001, length 35
07:06:37.377111 IP 169.254.1.125.5056 > 169.254.1.255.5000: UDP, length 12
07:06:37.387964 IP 169.254.1.46.5056 > 169.254.1.255.5000: UDP, length 12
07:06:37.591341 IP phazo-laptop.home.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 139.1.254.169.in-addr.arpa. (44)
07:06:38.060265 IP things-4faa6f5b.home > phazo-laptop.home: ICMP echo request, id 512, seq 4864, length 40
07:06:38.060345 IP phazo-laptop.home > things-4faa6f5b.home: ICMP echo reply, id 512, seq 4864, length 40
07:06:38.062163 IP things-4faa6f5b.home > phazo-laptop.home: ICMP things-4faa6f5b.home protocol 1 port 16476 unreachable, length 36
07:06:38.595371 IP phazo-laptop.home.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 139.1.254.169.in-addr.arpa. (44)
07:06:40.419347 IP 169.254.1.114.62426 > 169.254.1.255.5000: UDP, length 12
07:06:40.599410 IP phazo-laptop.home.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 139.1.254.169.in-addr.arpa. (44)
07:06:41.292777 STP 802.1d, Config, Flags [none], bridge-id 8000.00:18:01:38:56:6b.8001, length 35
07:06:42.492181 IP phazo-laptop.home.32798 > Wireless_Broadband_Router.home.domain: 56753+ PTR? 8.0.0.10.in-addr.arpa. (39)
07:06:42.500334 IP Wireless_Broadband_Router.home.domain > phazo-laptop.home.32798: 56753* 1/0/0 PTR[|domain]
07:06:42.500592 IP phazo-laptop.home.32798 > Wireless_Broadband_Router.home.domain: 43996+ PTR? 6.0.0.10.in-addr.arpa. (39)
07:06:42.508011 IP Wireless_Broadband_Router.home.domain > phazo-laptop.home.32798: 43996* 1/0/0 PTR[|domain]
07:06:42.511673 IP phazo-laptop.home.32798 > Wireless_Broadband_Router.home.domain: 62755+ PTR? 251.0.0.224.in-addr.arpa. (42)
07:06:42.536259 IP Wireless_Broadband_Router.home.domain > phazo-laptop.home.32798: 62755 NXDomain 0/1/0 (100)
07:06:42.651349 IP phazo-laptop.home.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 251.0.0.224.in-addr.arpa. (42)
07:06:43.067708 IP things-4faa6f5b.home > phazo-laptop.home: ICMP echo request, id 512, seq 5120, length 40
07:06:43.067788 IP phazo-laptop.home > things-4faa6f5b.home: ICMP echo reply, id 512, seq 5120, length 40
07:06:43.069027 IP things-4faa6f5b.home > phazo-laptop.home: ICMP things-4faa6f5b.home protocol 1 port 16220 unreachable, length 36
07:06:43.292859 STP 802.1d, Config, Flags [none], bridge-id 8000.00:18:01:38:56:6b.8001, length 35
07:06:43.655411 IP phazo-laptop.home.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 251.0.0.224.in-addr.arpa. (42)
07:06:45.292971 STP 802.1d, Config, Flags [none], bridge-id 8000.00:18:01:38:56:6b.8001, length 35
07:06:45.659351 IP phazo-laptop.home.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 251.0.0.224.in-addr.arpa. (42)
07:06:47.293076 STP 802.1d, Config, Flags [none], bridge-id 8000.00:18:01:38:56:6b.8001, length 35
07:06:47.491231 arp who-has Wireless_Broadband_Router.home tell phazo-laptop.home
07:06:47.492519 arp reply Wireless_Broadband_Router.home is-at 00:18:01:38:56:6a (oui Unknown)
07:06:47.655363 IP phazo-laptop.home.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 125.1.254.169.in-addr.arpa. (44)
07:06:48.502034 IP 169.254.1.139.55408 > 169.254.1.255.5000: UDP, length 12
07:06:48.510996 IP 169.254.1.46.5056 > 169.254.1.255.5000: UDP, length 12
07:06:48.512071 IP 169.254.1.125.5056 > 169.254.1.255.5000: UDP, length 12
07:06:48.659352 IP phazo-laptop.home.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 125.1.254.169.in-addr.arpa. (44)
07:06:49.293167 STP 802.1d, Config, Flags [none], bridge-id 8000.00:18:01:38:56:6b.8001, length 35
07:06:49.668832 IP things-4faa6f5b.home.1070 > phazo-laptop.home.ftp: S 3101907153:3101907153(0) win 65535 <mss 1460,nop,wscale 4,nop,nop,sackOK>
07:06:49.668941 IP phazo-laptop.home.ftp > things-4faa6f5b.home.1070: S 8713375:8713375(0) ack 3101907154 win 5840 <mss 1460>
07:06:49.670254 IP things-4faa6f5b.home.1070 > phazo-laptop.home.ftp: R 3101907154:3101907154(0) win 0
07:06:50.663346 IP phazo-laptop.home.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 125.1.254.169.in-addr.arpa. (44)
07:06:51.295353 STP 802.1d, Config, Flags [none], bridge-id 8000.00:18:01:38:56:6b.8001, length 35
07:06:52.620098 IP things-4faa6f5b.home.1070 > phazo-laptop.home.ftp: S 3101907153:3101907153(0) win 65535 <mss 1460,nop,wscale 4,nop,nop,sackOK>
07:06:52.620211 IP phazo-laptop.home.ftp > things-4faa6f5b.home.1070: S 2959999914:2959999914(0) ack 3101907154 win 5840 <mss 1460>
07:06:52.622207 IP things-4faa6f5b.home.1070 > phazo-laptop.home.ftp: R 3101907154:3101907154(0) win 0
07:06:52.659366 IP phazo-laptop.home.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 46.1.254.169.in-addr.arpa. (43)
07:06:53.293349 STP 802.1d, Config, Flags [none], bridge-id 8000.00:18:01:38:56:6b.8001, length 35
07:06:53.663354 IP phazo-laptop.home.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 46.1.254.169.in-addr.arpa. (43)
07:06:55.293475 STP 802.1d, Config, Flags [none], bridge-id 8000.00:18:01:38:56:6b.8001, length 35
07:06:55.442141 IP 169.254.1.114.62426 > 169.254.1.255.5000: UDP, length 12
07:06:55.663387 IP phazo-laptop.home.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 46.1.254.169.in-addr.arpa. (43)
07:06:57.294002 STP 802.1d, Config, Flags [none], bridge-id 8000.00:18:01:38:56:6b.8001, length 35
07:06:57.666585 IP phazo-laptop.home.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 114.1.254.169.in-addr.arpa. (44)
07:06:58.528292 IP 169.254.1.125.5056 > 169.254.1.255.5000: UDP, length 12
07:06:58.530504 IP 169.254.1.46.5056 > 169.254.1.255.5000: UDP, length 12
07:06:58.629340 IP things-4faa6f5b.home.1070 > phazo-laptop.home.ftp: S 3101907153:3101907153(0) win 65535 <mss 1460,nop,wscale 4,nop,nop,sackOK>
07:06:58.629419 IP phazo-laptop.home.ftp > things-4faa6f5b.home.1070: S 379278171:379278171(0) ack 3101907154 win 5840 <mss 1460>
07:06:58.630680 IP things-4faa6f5b.home.1070 > phazo-laptop.home.ftp: R 3101907154:3101907154(0) win 0
07:06:58.667328 IP phazo-laptop.home.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 114.1.254.169.in-addr.arpa. (44)
07:06:59.297794 STP 802.1d, Config, Flags [none], bridge-id 8000.00:18:01:38:56:6b.8001, length 35
07:07:00.671348 IP phazo-laptop.home.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 114.1.254.169.in-addr.arpa. (44)
07:07:01.293746 STP 802.1d, Config, Flags [none], bridge-id 8000.00:18:01:38:56:6b.8001, length 35
07:07:02.563738 IP phazo-laptop.home.32798 > Wireless_Broadband_Router.home.domain: 16173+ PTR? 1.0.0.10.in-addr.arpa. (39)
07:07:02.579832 IP Wireless_Broadband_Router.home.domain > phazo-laptop.home.32798: 16173* 1/0/0 PTR[|domain]
07:07:03.293870 STP 802.1d, Config, Flags [none], bridge-id 8000.00:18:01:38:56:6b.8001, length 35
07:07:03.527250 IP 169.254.1.139.55408 > 169.254.1.255.5000: UDP, length 12
07:07:05.293971 STP 802.1d, Config, Flags [none], bridge-id 8000.00:18:01:38:56:6b.8001, length 35

Thanks to anyone who can possibly help with this as I'm about to start ripping my hair out.

---

### Post by phazo on 2007-11-09
Well I have an update.  Its not an application issue, apparently its just my wireless adapter. 

Hard cabled in to my router, the PC will respond to everything, pings, vnc, ftp, etc. on the IP of my Ethernet connection

Must be something in the wireless driver that can't handle inbound requests...

If anyone has any thoughts, definitely let me know.

---

