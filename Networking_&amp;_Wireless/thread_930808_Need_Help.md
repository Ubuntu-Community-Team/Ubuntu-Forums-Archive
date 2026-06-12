---
title: "Need Help"
date: 2008-09-26
forum: Networking &amp; Wireless
---

### Post by StRoNiX on 2008-09-26
I have a problem with internet
It is kinda working with pauses...
Any1 knows how to solve this please ?
Thanks in advance

---

### Post by a.kurtz on 2008-09-26
Pauses?

Pauses as in, you go to a new website and it's slow to start but loads quickly, or pauses as in, you're downloading something and it starts hanging then continues with speed.

First could be a DNS issue - when resolving a new host, your DNS is really slow and so it takes a long time to find.

What's /etc/resolv.conf show and what happens when you do "nslookup cheese.com" or some other site you've never been to?

If the second, you could be experiencing packet loss. If you do something like ping google.com, do you start seeing really high lag or see packets failing to reply?

---

### Post by StRoNiX on 2008-09-27
when i`m updating download rate is normally at 250kbps then it stops and download rate is unknown and after a minute or two download rate is 1500kbps...
and i have to reload every page, not only where i am for the first time, because it won`t load them...

---

### Post by StRoNiX on 2008-09-27
when i type nslookup on site ive never been it shows:
 nslookup [www.domaci.de](www.domaci.de)
Server:		195.66.160.1
Address:	195.66.160.1#53

Non-authoritative answer:
Name:	[www.domaci.de](www.domaci.de)
Address: 85.214.98.2

and /etc/resolv.conf
nameserver 195.66.160.1
nameserver 195.66.160.2

---

### Post by j.bunce on 2008-09-27
Check your xDSL connection. Sessions can become "stale" sometimes. Turn it off for 20 mins then wack it back on again. See what happens.

---

### Post by StRoNiX on 2008-09-28
same thing again...

---

