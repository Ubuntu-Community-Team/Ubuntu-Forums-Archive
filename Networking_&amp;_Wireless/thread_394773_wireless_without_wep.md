---
title: "wireless without wep"
date: 2007-03-27
forum: Networking &amp; Wireless
---

### Post by chimanrao on 2007-03-27
I have installed Kubuntu 6.10.

I disabled wep on my wireless, because it was causing a lot of grief.

I am ablt connect to the wireless network, but If I restart my machine, I have to start all over again. This what I mean.

after restarting If I run

iwconfig

under eth0 I can see my wireless essid and mac address of the access point. But If I try to connect using wireless assistant, it does not connect.

I noticed that the mode was set to master so I set it auto using iwconfig.
I followed it up by the followign commands

sudo ifdown eth0
sudo ifup eth0

I have to repeat these commands 2-3 times and voila... it suddenly gets connected.

Is there any way to do avoid doing all this circus?
I tried putting the information in /etc/network/interfaces file but that did not seem to work.

The router and the wireless dongle are both Airlink 101.

Regards
Chimanrao

---

