---
title: "Wired connection issue"
date: 2008-09-28
forum: Networking &amp; Wireless
---

### Post by gornomatic on 2008-09-28
Greetings

I have seen problems similar to this posted before but I have tried a couple of suggestions listed on those threads. It doesn't seem to be working though. Here is my problem : 
I'm running Hardy Heron and my Internet was working fine till yesterday. Now, today, the network manager doesn't even recognize that a wired connection exists.

What I have tried:
1) sudo lshw -C network ---- No output, I guess this means my card isn't being detected?
2) ping 127.0.0.1 ---- This is working fine

I remember having this problem once a couple of weeks back. I unplugged the cable and switched off/on the modem and rebooted it worked fine. Sadly, no such luck this time :(

Any suggestions guys? Thanks in advance.

---

### Post by superprash2003 on 2008-09-28
post output of ifconfig

---

### Post by gornomatic on 2008-09-28
Hmmm .. I did the whole thing again and it is working fine now. What do you suspect it could be? Initializing the drivers at boot time?

---

### Post by superprash2003 on 2008-09-29
possible.. are you using ndiswrapper?

---

