---
title: "Dell D420 ; WiFi won't associate with access point"
date: 2006-08-10
forum: Networking &amp; Wireless
---

### Post by pruyss on 2006-08-10
Hello,

Seems like I'm one of the first to try and install Dapper Drake on the new Dell Latitude D420.  There's no help yet for this machine on [http://www.linux-on-laptops.com/](http://www.linux-on-laptops.com/)
So I'm writing down my findings as I proceed.  The resulting web page will be submitted to [http://www.linux-on-laptops.com/](http://www.linux-on-laptops.com/)
But I have a major problem getting my wireless network connection to work.
Rather than repeating everything here, I refer to my webpage describing the problem : [http://users.ugent.be/~pruyss/D420/](http://users.ugent.be/~pruyss/D420/)
Anyone smarter than me who's got some suggestions ?

Thanks.
Piet.

---

### Post by meng on 2006-08-10
After all the iwconfig (etc), does anything happen if you use
ifconfig wlan0 up

possibly followed by
dhcpcd wlan0

(I'm not certain if this would work, but I'm pretty sure it can't hurt. I have recently been playing around with several distros on my Dell Inspiron 8200, getting the wireless card to work with them.)

---

### Post by pruyss on 2006-08-10
> **meng said:**
> After all the iwconfig (etc), does anything happen if you use
ifconfig wlan0 up

possibly followed by
dhcpcd wlan0

(I'm not certain if this would work, but I'm pretty sure it can't hurt. I have recently been playing around with several distros on my Dell Inspiron 8200, getting the wireless card to work with them.)


ifconfig wlan0 up
doesn't help

and it's too early to send out a dhcp request before the interface is up, I'm afraid.

Piet.

---

