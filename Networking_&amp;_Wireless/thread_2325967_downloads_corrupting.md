---
title: "downloads corrupting"
date: 2016-05-27
forum: Networking &amp; Wireless
---

### Post by Bob_Findlay on 2016-05-27
hi all

I'm having real problems with downloads corrupting on ubuntu 14.04 LTS.  It's affecting package updates, browser downloads wget etc.  there are no errors in syslog. 

For example, trying to download the latest plex via firefox fails.  Using wget I get

```
paul@paul-PC:~/Downloads$ wget https://downloads.plex.tv/plex-media-server/0.9.16.6.1993-5089475/plexmediaserver_0.9.16.6.1993-5089475_amd64.deb--2016-05-27 06:45:25--  https://downloads.plex.tv/plex-media-server/0.9.16.6.1993-5089475/plexmediaserver_0.9.16.6.1993-5089475_amd64.deb
Resolving downloads.plex.tv (downloads.plex.tv)... 104.20.6.9, 104.20.7.9, 2400:cb00:2048:1::6814:609, ...
Connecting to downloads.plex.tv (downloads.plex.tv)|104.20.6.9|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 128328832 (122M) [application/x-debian-package]
Saving to: &#8216;plexmediaserver_0.9.16.6.1993-5089475_amd64.deb.4&#8217;


 0% [                                                                                             ] 293,909     1.21MB/s   in 0.2s   


2016-05-27 06:45:26 (1.21 MB/s) - Read error at byte 293909/128328832 (error:1408F119:SSL routines:SSL3_GET_RECORD:decryption failed or bad record mac). Retrying.
```

if I download with http instead of https it seems to work fine but then the archive is corrupt.  Here's 4 different attempts to download the same file.  as you can see they're all different

```
paul@paul-PC:~/Downloads$ crc32 plex*1993*
ac4ae8a1    plexmediaserver_0.9.16.6.1993-5089475_amd64.deb
e04b13d0    plexmediaserver_0.9.16.6.1993-5089475_amd64.deb.1
8cb5dd73    plexmediaserver_0.9.16.6.1993-5089475_amd64.deb.2
c80d8cdb    plexmediaserver_0.9.16.6.1993-5089475_amd64.deb.3
```


I have the following network card

```
00:19.0 Ethernet controller: Intel Corporation 82567LM-3 Gigabit Network Connection (rev 02)
```

I don't seem to have any errors on the network card 
```
eth0      Link encap:Ethernet  HWaddr 00:1c:c0:fa:1e:8f            inet addr:192.168.1.153  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:c0ff:fefa:1e8f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:934182 errors:0 dropped:0 overruns:0 frame:0
          TX packets:681599 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1145579254 (1.1 GB)  TX bytes:234954196 (234.9 MB)
          Interrupt:20 Memory:e0600000-e0620000 
```
I have tried disabling iptables to no effect

I'm pretty sure my disk is OK as any non download operations I perform have no issues.  Including storing/playing big media files.

Any suggestions gratefully received!

thanks

---

### Post by TheFu on 2016-05-27
The only time I've seen something like this is when a cracked motherboard was causing it.  Can't see anything other than a HW issue being the cause - somewhere in the chain, but probably not between the router/switch and the NIC. Don't remember if that NIC was onboard or a separate NIC. Try reseating it.  Simplify and test over and over until you have isolated the issue. Next i'd swap the NIC out.

Also, try downloading a file from a different server. Might just be the plex guys issue, right?

---

### Post by Bob_Findlay on 2016-05-28
thanks for the suggestion.  the NIC is onboard, so I can't reseat, but I will be getting a USB wireless NIC to take the NIC out of the equation.

It's not just plex.  I can't even do ubuntu updates as the downloads corrupt

---

### Post by TheFu on 2016-05-28
If it still happens after the wifi is tested, then you've got issues from the router upstream and will need to get the ISP involved.  Check the modem for S/N issues.

Wifi is seldom the solution to networking issues.  It is usually the problem, sad to say.  I'd much rather see you spend $25 for an Intel PRO/1000 NIC, which would be useful in other machines too rather than go wifi.  I use wifi only when required, otherwise, it is hard to compare the throughput with GigE (920+ Mbps) to any real-world wifi.

---

