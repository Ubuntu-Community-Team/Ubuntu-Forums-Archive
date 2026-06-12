---
title: "Good Easy to use Proxy"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by KuroYoma on 2008-12-04
I want to set up a good easy to use proxy on my xubuntu 8.10 that is widely compatible and good for a beginner.

Anyone know a good one?

Also how would i set up macchanger to activate and change my mac everytime i boot up?  Is that possible?


*BUMP*

---

### Post by ethoxyethaan on 2008-12-04
If you want to set up a proxy server use SQUID proxy,

if you want to use a proxy (that is easy) use TOR.

sudo apt-get install tor

you can read the manual @ [https://www.torproject.org/](https://www.torproject.org/)

to use tor as http proxy use 127.0.0.1:8118

warning: (this sometimes displays as a transparent proxy i have no idea why)

its better to use the socks proxy from tor

127.0.0.1:9050 

you will change IP every 2 minutes, enjoy!

---

