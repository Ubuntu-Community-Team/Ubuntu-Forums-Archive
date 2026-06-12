---
title: "eth0 has totally dissapeared"
date: 2006-07-22
forum: Networking &amp; Wireless
---

### Post by ironfistchamp on 2006-07-22
Afternoon all. My eth0 has dissapeared. It is the only way I can access the internet. Network Manager shows on my Wireless caed (no drivers) and my modem (broadband only for m3). 


The only reason I noticed it was gone because I was trying to install my NFORCE and NVIDIA drivers but they were complaining the kernel source was missing. There is a bz2 which is in usr/src but it doesn't like that. So anyway I tried getting it from apt-get but it kept complaining that it couldn't get to the security repo (which it never can seem to do regardless of network connection).

What is extra strange is that about 15mins ago my brother was using the computer with a user I had just created for him. He was using the net fine. Then he turned it off, I turned it back on and logged in as me and hey presto nothing.

If anyone can help I would really apreciate it.

Thanks

Ironfistchamp

---

### Post by ironfistchamp on 2006-07-22
This is totally weird I shutdown and came back an hour later or so and it had reappeared. Weird.

---

### Post by Thirsteh on 2006-07-22
Try 'ifconfig eth0 up' next time this happens.

---

### Post by ironfistchamp on 2006-07-22
Hopefully it wont but thanks :P

---

