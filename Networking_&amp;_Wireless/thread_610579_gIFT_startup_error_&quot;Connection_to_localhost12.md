---
title: "gIFT startup error &quot;Connection to localhost:1213&quot; failed"
date: 2007-11-12
forum: Networking &amp; Wireless
---

### Post by bvm177 on 2007-11-12
I've been trying to get gIFT up and running all night. I'm using Ubuntu 7.10. I've installed all the required packages through Synamptic as well as the giftui frontend. When I open giftui I get this error

[IMG]http://img337.imageshack.us/img337/5397/gifthosterroroe6.png[/IMG]

I've got a router connected to my pc via Ethernet. I ran **ipconfig** and got the following:

[I]eth0      Link encap:Ethernet  HWaddr 00:0D:61:0E:C5:E0  
          inet addr:192.168.1.33  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:61ff:fe0e:c5e0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26253 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24331 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23389933 (22.3 MB)  TX bytes:4026717 (3.8 MB)
          Interrupt:18 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1400 (1.3 KB)  TX bytes:1400 (1.3 KB)[/I]


Tried putting in my local 192. IP address, my Broadcast address, 127.0.0.1 and my 124. IP address to the internet. Tried changing the port, nothing.

One thing I haven't done is port forwarding, mainly because it doesn't like to work on my Zyxel Prestige 600 router. However Limewire and uTorrent run fine on their own, The internet also works fine. I haven't done any sort of network set-up for the past 8 days since I've had Ubuntu installed. I also never had a problem with any p2p network when WinXP was installed on this computer.

Can anyone please help?

---

