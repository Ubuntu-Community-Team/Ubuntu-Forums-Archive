---
title: "Works in XP, not with Ubuntu."
date: 2008-02-01
forum: Networking &amp; Wireless
---

### Post by giladg on 2008-02-01
Guys,

yet another wireless annoyance post.. sorry, but i don't know how to fix it:

Setup is the following: wireless netgear router (not my fault, landlord set this up..), no security features enabled. Basically using using windows and linksys wusb54g v.4 I'm able to connect fine.

Ubuntu will not 'connect'. I think the network is recognized but something after that fails.. Here are the iwconfig and ifconfig outputs..:

IWCONFIG:
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

rausb0    IEEE 802.11g  ESSID:"Jake"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


IFCONFIG:
rausb0    Link encap:Ethernet  HWaddr 00:16:B6:4E:D6:7E  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wmaster0  Link encap:UNSPEC  HWaddr 00-16-B6-4E-D6-7E-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


I know this is probably very boring to some of you, but what i find frustrating is that it's so straight-forward in windows..

Thanks,
Gilad.

---

### Post by Hightide on 2008-02-02
Hi giladg
you probably have a driver problem and I would recommend having a look at Kevdog's wireless [tutorial]("http://ubuntuforums.org/showthread.php?t=571188")

regards

:)

---

### Post by zoke on 2008-02-02
Ubuntu has some problems with this device. See [this thread]("http://ubuntuforums.org/showthread.php?t=588045") on how to make it work in Gutsy.

---

