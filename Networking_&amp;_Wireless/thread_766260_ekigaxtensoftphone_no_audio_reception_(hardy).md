---
title: "ekiga/xtensoftphone no audio reception (hardy)"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by redlever on 2008-04-25
I have set up Ekiga.  In the "Configuration Druid", the audio test works fine (my recorded voice is played back OK).  Skype works fine.

I am able to register my SIP accounts fine, but calls to the 500@ echo test and other numbers reveal that I'm not getting any incoming audio at all.  It *appears* that outgoing audio is OK, but I don't have a way to really test that yet.

I tried using xtensoftphone, which worked recently (I wiped a Gentoo install, where xtensoftphone worked, and installed Hardy Heron), but it too doesn't have any audio.

More info:  Configuration Druid detects Port Restricted NAT, and suggests using stun.ekiga.net, which I did.  I also tried it with the two other options (None/IP Translation).

$ netstat -nr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.111.0   0.0.0.0         255.255.255.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         192.168.111.1   0.0.0.0         UG        0 0          0 eth0

My computer is connected via a Netgear WGT624 v3 router, then on to my ISP.  I tried setting my computer as the DMZ in the router; I also tried forwarding port 5060.  No change in behavior (always Port Restricted NAT).
UPnP is on, and things like Transmission work OK.

Does anyone know what steps I might take to track down the source of this problem?

Thanks!

---

### Post by arashiko28 on 2010-04-23
I have the exact same problem... what hopes do I have if this has 2 years with no answers? I'm using 9.10.

---

