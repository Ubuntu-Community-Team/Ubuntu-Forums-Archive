---
title: "Slow internet driving me insane!"
date: 2007-06-30
forum: Networking &amp; Wireless
---

### Post by AriciU on 2007-06-30
I don't know what else to do about this. I've completly disabled IPV6 support so it's OFF for good. I use firefox with fasterfox extension with all the "tweak" settings. I've used swiftfox and opera.

The problem is that loading pages is much slower then on Windows. About 10-15 seconds slower to be exact witch is totally unnacceptable for 100Mbit and instant loading on windows.

The pattern is always the same -> [www.website.com](www.website.com) -> resolving host name -> 5-10seconds pass -> ip of the hostname is resolved and page starts loading -> 5-10 seconds pass -> page fully loads.

It's driving me insane and making me switch back to windows in frustration so if there **is** something that you can do about it to make it all work **like it should** then please let me know.

---

### Post by jasmuz on 2007-06-30
Are your DNS servers configured correctly.. those little issues can lead to slow response time.

---

### Post by AriciU on 2007-07-01
I'm using the same DNS addresses as i use in Windows if that's what you are asking me about.

---

### Post by AriciU on 2007-07-01
LMAO :D

I've deleted the DNS ip's that my ISP gave me from my Network configuration and page loading is BLAZING fast now. I have those dns ip's entered in Windows and it's fine so can't really figure out what the problem was or why an ISP would even give you DNS ip's if everything works better without them entered.

EDIT: now pages don't load at all. WTF?!

EDIT2: Ok. This was the problem. I have 2 DNS ip's from my ISP to use. The first one didn't work and the second one does. Loading time was slow because the system tried to use the 1st DNS IP, witch didn't work, and only after a timeout (5-10secs) it would skip to the other DNS IP witch worked. Now everything is fine again and load times are OK.

---

### Post by jasmuz on 2007-07-01
Im glad to read that it was just a DNS configuration error.

---

### Post by AriciU on 2007-07-01
Thanks for pointing me in the right directon :KS

---

