---
title: "Attansic L1 1Gbit NIC performing badly, Ubuntu 8.04.1"
date: 2008-10-04
forum: Networking &amp; Wireless
---

### Post by atroxes on 2008-10-04
Hey Ubuntu forum! :)

I have a problem with my server that's been driving me absolutely crazy since Day 1.

My network performance is at about 4MB/s. I tried troubleshooting Samba, but found out the problem was also present when using FTP or HTTP for transfers. My guess in on the NIC driver. I update it from [http://atl1.sourceforge.net](http://atl1.sourceforge.net), installs perfectly, still have the same problem.

And here's the part that makes me want to pull out my hair:

At random times, maybe right after a boot, maybe after 100 hours of being turned on, the Gbit NIC performs flawlessly! 60-70MB/s to my Vista desktop, both on Samba and FTP/HTTP. As I said, this is a server, so I don't touch it, it just sit on my floor and hums. After a random amount of time, anything from 15 minutes to 10 days, it suddenly decides to go back to 4MB/s!

I know this sounds like my dog might be chewing on my CAT6 but that's not the issue :)

I would REALLY like to get this issue resolved.




Here's some output from different sources:

Ethtool
> 
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 1000Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: umbg
	Wake-on: d
	Current message level: 0x0000003f (63)
	Link detected: yes



Samba socket options (tried changing them, makes no difference at all):
> 
socket options = TCP_NODELAY SO_RCVBUF=16384 SO_SNDBUF=16384


ifconfig:
> 
eth0      Link encap:Ethernet  HWaddr 00:1e:8c:93:bd:1e  
          inet addr:192.168.1.41  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:8cff:fe93:bd1e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2275066 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1250422 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:527074208 (502.6 MB)  TX bytes:697005671 (664.7 MB)


Thank you in advance fellow Ubuntu people!

---

### Post by atroxes on 2008-10-09
Found out what it was.

Vista has a nice feature called Multimedia Class Scheduler Service (MMCSS). When playing audio, or just having a program open that could potentially use your soundcard, Vista decides to slow down your NIC as to not make the sound jitter.

Go figure... I use 0-1% CPU when playing music with winamp and Vista decides 4MB/s instead of 30-40MB/s is appropriate.

MMCSS can be turned off by going into the registry, find the Windows Audio service, removing the MMCSS dependency, deactivating MMCSS (not stopping, just deactivating) and then rebooting.

Have fun with Vista, I did.

---

