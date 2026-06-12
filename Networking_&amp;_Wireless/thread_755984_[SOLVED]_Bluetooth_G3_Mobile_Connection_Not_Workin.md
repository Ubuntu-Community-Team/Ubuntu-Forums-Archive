---
title: "[SOLVED] Bluetooth G3 Mobile Connection Not Working"
date: 2008-04-15
forum: Networking &amp; Wireless
---

### Post by Desmo UK on 2008-04-15
Hi all, my first question here so go easy :p

I'm trying to get my laptop connected via 3G from my mobile. I've installed Blueman 1.9 (had to use an older version as the newer one wouldn't install) and also installed kppp.

Now, I can get my mobile to connect to the laptop, "dial up" and it completes the connection. The mobile shows the 3G symbol and I seem to get an IP address. But that's it, no data flows in either direction apart from the first few packets of data which I'm assuming is just the connection data.

So, I'm at a loss as to what to check next. It seems it should be working but just doesn't. I'm using a Nokia N73 and my provider is O2 in the UK. OS is Gutsy.

---

### Post by Desmo UK on 2008-04-16
Sorted now :)

Seems it just couldn't find it's way out to the net. Adding in ip route add default via <ip> dev ppp0 (ip being 10.6.6.6 for O2 in the UK) seemed to do the trick..

---

