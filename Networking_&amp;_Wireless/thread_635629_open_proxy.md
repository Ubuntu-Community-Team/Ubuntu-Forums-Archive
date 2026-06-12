---
title: "open proxy"
date: 2007-12-08
forum: Networking &amp; Wireless
---

### Post by mouseboyx on 2007-12-08
when i try to connect to any irc network including the ubuntu one it says that i have an open proxy running on my network, even though i shut it down.

---

### Post by HermanAB on 2007-12-08
Do a nmap scan to see what is going on and run Firestarter to configure netfilter properly:
$ sudo nmap -sT -P0 -v -F w.x.y.z

Cheers,

Herman

---

### Post by mouseboyx on 2007-12-09
thanks!

---

