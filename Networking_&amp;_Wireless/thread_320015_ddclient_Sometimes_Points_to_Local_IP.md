---
title: "ddclient Sometimes Points to Local IP"
date: 2006-12-16
forum: Networking &amp; Wireless
---

### Post by BitTorrentBuddha on 2006-12-16
I'm trying to get ddclient to play nicely with dyndns.org to access SSH (I have a dynamic IP) from my school. However, ddclient sometimes seems to report my local IP address instead of my external, which doesn't turn out so well when I try to access it from outside the network. I would like to know what causes this and how I can make ddclient always report my external address.

---

### Post by scrooge_74 on 2006-12-16
If I remember well I had the same problem when first time using it.  Try installing it again so the config options come again, at some point I gave the wrong answer and that was the reason I got stuck with the local address.  

The sad thing is I use it over 5 months ago and don't quite remember what I did

---

### Post by BitTorrentBuddha on 2006-12-16
I think I've found the problem, I changed /etc/ddclient.conf so that the seventh line reads ```
use=web
``` Instead of something it was before. It hasn't changed back to my local yet, but if it does I will definitely give that a shot and double check my option choices.

---

### Post by BoomShaka on 2007-10-12
Thanks! I had the same issue.
I changed it from use=if to use=web.
I then ran "sudo ddclient" and it gave me a successful update message.

---

### Post by marco.tonoli@libero.it on 2008-06-03
Thanks !!!

---

