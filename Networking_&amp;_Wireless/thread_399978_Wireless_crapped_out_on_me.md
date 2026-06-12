---
title: "Wireless crapped out on me?"
date: 2007-04-03
forum: Networking &amp; Wireless
---

### Post by badgie523 on 2007-04-03
Sooo, I came back from spring break, only to find that for some reason my desktop decided to stop detecting my wireless card (which is a d-link WDA-1320).  It worked fine out of the box until now.  I couldn't get it to work by fiddling with settings, so I took it out and put it back in, and still nothing.

Any suggestions?

I am a TOTAL Ubuntu newb, only been using it since January or so, so forgive me if I'm slow or ask dumb questions. :P

---

### Post by amohanty on 2007-04-03
In a termina, type in the following and post the output:

ifconfig -a
iwconfig 

the contents of your /etc/network/interfaces (remember to X out your wireless key and essid)

AM

---

### Post by badgie523 on 2007-04-03
Will do as soon as I get home.

---

