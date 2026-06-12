---
title: "Connected to network, but not internet"
date: 2008-08-24
forum: Networking &amp; Wireless
---

### Post by boaty on 2008-08-24
Hey guys.

I have an interesting little problem.  Earlier today, I used network manger to connect to my home wireless network.  It seemed like it connected fine, but for some reason it didn't connect to the internet, even though it was connected to the network.  I've had similar problems in windows, but not in ubuntu.  What can I do to find out the source of the problem and fix it?

Thanks to anyone who took the time to read this and/or make a comment and/or tries to help =]]

Edit:

Now I can't even connect to the network.  I think it's denying my key.  I'm going to disable WEP and see what happens.

Edit again:

Well I'll be a s.o.b.  After taking down my WEP it suddenly works.  I think this has something to do with a WPA Supplicant.  I read about that somewhere, but it didn't help...Any hints on how to get wireless working with WEP?

---

### Post by Mariane on 2008-08-24
I had problems with the WEP, turned out it was set as ascii while being hexadecimal. Maybe you've though of that already but I can't think of anything else. 

Mariane

---

### Post by Eversmann on 2008-08-24
Yeah, NetworkManager mess up with WEP keys, not giving you an automatic recognition of the type of the key (hexadecimal, ascii...).

The common setup is hexadec, shared key. You shouldn't have any problems setting it with WPA though.

Be sure to check how are you connected after NM sets you the connection. Type "ifconfig [netword card, wlan0, ra0......]" and se if you have an ip addressed. After that, do a ping to the gateway (router ip) to see if you have that connection, and after that, make a ping to a IP on internet (to see if you don't have a dns problem).

In most cases, it works out of the box. Hope that you resolve the problem.

---

