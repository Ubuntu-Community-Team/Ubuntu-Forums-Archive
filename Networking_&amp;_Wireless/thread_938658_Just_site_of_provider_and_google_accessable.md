---
title: "Just site of provider and google accessable"
date: 2008-10-05
forum: Networking &amp; Wireless
---

### Post by joe_34 on 2008-10-05
Hello,

I have an ASUS F5SL notebook with ubuntu 8.04.1 installed. This notebook has the LAN card SIS191, which seems to create some trouble under Linux.
I read in earlier posts about problems, not recognizing the card, but it should be fixed in kernel 2.6.24 accroding to launchpad.

With me, the card is detected without any problems. I then configure pppoeconf without any problems. After configuring it, I get assigned DNS servers IPs by my provider. The host command resolves correctly as well as the ping command returns proper pinging for any website. 

Now the strange thing: I just can access [www.google.com(and](www.google.com(and) do any search successfully) and my providers website ([www.alice-dsl.de](www.alice-dsl.de), some german provider). As soon as i type some other website (e.g. [www.yahoo.com](www.yahoo.com)) or a click on some search result in google, firefox will wait for connection endlessly until it times out. I neither can download anything under adding or removig ubuntu applications.

Here my output of eth0 for ifconfig 
```

eth0      Link encap:Ethernet  Hardware Adresse 00:22:15:2b:3e:b4  
          inet Adresse:192.168.1.34  Bcast:192.168.1.255    Maske:255.255.255.0
          inet6-Adresse: fe80::222:15ff:fe2b:3eb4/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:150 errors:9 dropped:0 overruns:0 frame:9
          TX packets:177 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:73084 (71.3 KB)  TX bytes:24623 (24.0 KB)
          Interrupt:20 Basisadresse:0xdead 

```
Two things: What does it mean to have some few errors/frames just for Rx, not for Tx? What does base address: 0xdead indicates?

I guess its no driver problem, since it can connect to google and to my providers site without any problems. But what is then the problem?
I can access any website under ubuntu 8.04 on some other computer as well as under windows XP on the same notebook (ASUS F5SL).

Thanks.

---

