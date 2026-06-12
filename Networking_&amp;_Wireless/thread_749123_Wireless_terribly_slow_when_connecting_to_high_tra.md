---
title: "Wireless terribly slow when connecting to high traffic access point"
date: 2008-04-08
forum: Networking &amp; Wireless
---

### Post by Kamu on 2008-04-08
A tiny bit of context:  I am visiting a research lab where wireless is present everywhere.  If I connect from any normal office area, wireless works just peachy, speed is reasonable, etc.

I also have to sit often in a large auditorium where a few hundred people sit, all using laptops.  Connection is a bit slow for everyone of course but in my case, systematically, connection slows down to a crawl, we are talking order 1kB/s file downloads, ssh sessions timing out, wireless totally useless.

I repeat:  I can connect to the access point, no problem, I can see that the connection is active because if I wait long enough, webpages will load.  But we are talking ~2mins to load gmail.

This has been observed systematically for many visits now, and people sitting around me seem unaffected.  Why would I be systematically killed in this case and no one else?  Anyone knows?  How can I make this work at least as the level of people around me?

Technical info:  I use Kubuntu Edgy with knetworkmanager as my wireless interface, on a Thinkpad X60s with Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02).

---

### Post by nixscripter on 2008-04-08
This kind of problem is always a little difficult to debug. But I would start by seeing if your traffic gets through with this command: ```
sudo tcpdump -q -i any port 80
``` and trying to load a webpage. If you can distinguish your traffic from others, it might help debug the problem.

The other thing I would wonder about is ARP routing. Try ```
sudo tcpdump -q -i any arp
``` and see if you generate a lot of requests.

---

### Post by kevdog on 2008-04-09
You could try disabling IPv6:
[http://ubuntuforums.org/showthread.php?t=282034](http://ubuntuforums.org/showthread.php?t=282034)

---

### Post by Kamu on 2008-04-09
Thanks nixscripter, I will try this and report, the problem of course is that I need to wait until I have another meeting in that room when it is full of people.

I doubt IPv6 is the culprit, kevdog, as the problem is so very localized.

---

