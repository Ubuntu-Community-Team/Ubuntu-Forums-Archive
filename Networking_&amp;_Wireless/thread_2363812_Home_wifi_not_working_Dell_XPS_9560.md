---
title: "Home wifi not working Dell XPS 9560"
date: 2017-06-14
forum: Networking &amp; Wireless
---

### Post by Trixiante on 2017-06-14
Hi,

I am experiencing an issue with my Ubuntu 16.04 installed on a Dell XPS 9560: massive packet loss when connecting to the home network while normal operation when connecting to my phone's hot spot or the WiFi at work.
I ran the wifi script, results attached.

I tried to update the firmware: [http://launchpadlibrarian.net/311659084/linux-firmware_1.164_all.deb](http://launchpadlibrarian.net/311659084/linux-firmware_1.164_all.deb) as suggested by a askubuntu post but nothing changed

Do you guys have any suggestions?

Thanks!

---

### Post by Trixiante on 2017-06-14
Apparently I was on a wild goose chase ... 
I am running Docker on my machine and it created a bridge interface bound to 192.168.0.1:

br-167d2bda48db Link encap:Ethernet  HWaddr 02:42:a5:14:eb:4d  
          inet addr:192.168.0.1  Bcast:0.0.0.0  Mask:255.255.240.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

My home Wi-Fi network was also setup such that the gateway (router) was 192.168.0.1.
Don't know exactly what was happening there but I can only guess that after a while all the packets got routed to this interface and got lost.

**THE SOLUTION:** change the Wi-Fi network subnet to 192.168.1.X (or anything other than the already in use 192.168.0.1)

---

