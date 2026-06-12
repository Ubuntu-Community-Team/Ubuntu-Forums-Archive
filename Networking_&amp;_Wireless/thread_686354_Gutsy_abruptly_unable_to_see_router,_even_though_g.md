---
title: "Gutsy abruptly unable to see router, even though getting IP address from it!"
date: 2008-02-03
forum: Networking &amp; Wireless
---

### Post by paul.sijpkes on 2008-02-03
My Ubuntu setup has being working flawlessly for about two months until yesterday when it suddenly decided to stop connecting to the internet.  

I cannot Ping the router address 192.168.1.1 but I can get a new address for my machine with dhclient, go figure!

The router is working as I can access the web and other machines via my Windows laptop.

It is not the IPv6 issue as reported in another thread as I have tried 

dig AAA [www.google.com.au](www.google.com.au)
and 
dig A [www.google.com.au](www.google.com.au)

and neither work.

my dhclient returns: (I can't email or copy or paste it so I will give the last 4lines)

Sending on Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.4 -- renewal in 38167 seconds.

I have both a wireless card and a standard ethernet card installed as you see above.

I also cannot ping from the other machines on the network to the Gutsy machine 192.168.1.4

Any help would be appreciated before I do something I might regret. I have so much work to do and I can only complete it with a working internet connection on my beloved Gutsy development machine!

---

