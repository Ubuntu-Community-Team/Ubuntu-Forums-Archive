---
title: "Problems with dhclient"
date: 2006-08-17
forum: Networking &amp; Wireless
---

### Post by mostrovoi on 2006-08-17
Hi there,
I have an AMD PCNet 79C978 HomePna card. At the beginning I was not even able to get an IP address. I finally succeeded thanks to this thread: 

[http://www.ubuntuforums.org/showthread.php?t=193167](http://www.ubuntuforums.org/showthread.php?t=193167)

The problem now is that the routing table (route command) does not show the default gw. After I executed the command:
dhclient eth0

My HomePNA does the handshaking with the gw and I finally get Internet connection but only for around half a minute or sometimes even less!! :sad: Afterwards, I have to run dhclient again and over and over again. I dont know why this routing information changes or does not work even though the gw grants me the IP for around 8000 seconds.
Thank you in advance :D

---

