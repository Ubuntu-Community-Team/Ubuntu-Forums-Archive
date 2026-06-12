---
title: "Dell Wireless 5720 Sprint / Ubuntu 8.10 64 / XPS M1530"
date: 2008-11-21
forum: Networking &amp; Wireless
---

### Post by davidflaiz on 2008-11-21
I have a Dell XPS M1530 with an internal** Dell Wireless 5720 Sprint Mobile Broadband (EVDO Rev-A) MiniCard**. I'm dual boot between Windows Vista and Ubuntu 8.10 64bit. The card works under Windows, but in spite of a lot of googling and looking for help on IRC at #Ubuntu I can't get it to work in Ubuntu. If I go to Network Connections and try to set up a new Mobile Broadband connection, the wizard only offers connections for AT&T and T-Mobile.

The bug report [here]("https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/288888") gave me the impression that the card should work. I've looked at my 10-modem.fdi file and verified that it has the mentioned changes.

Any help on this would be greatly appreciated even if it's just letting me know that this won't work.

System details below.

Bus 006 Device 002: ID 413c:8134 Dell Computer Corp. Wireless 5720 Sprint Mobile Broadband (EVDO Rev-A) Minicard Status Port


wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3B-9B-0B-C1-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  no wireless extensions.

david@david-laptop:~$ lsb_release -d
Description:	Ubuntu 8.10
david@david-laptop:~$ uname -mr
2.6.27-7-generic x86_64

david@david-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface wlan0=wlan0.

---

### Post by CalaverX11 on 2009-02-06
Bump for relevance. Anybody?

---

### Post by Mach1US on 2009-02-09
If you can not get it connected via network manager look here:

[http://ubuntuforums.org/showthread.php?t=343989&highlight=evdo](http://ubuntuforums.org/showthread.php?t=343989&highlight=evdo)

---

