---
title: "Internet suddenly stopped working on my thinkpad, please help"
date: 2017-12-07
forum: Networking &amp; Wireless
---

### Post by armstrong3066 on 2017-12-07
[FONT=verdana]Hey guys, I am at the end of my road here.... I've tried everything I could find regarding this issue on google. I just got a lenovo thinkpad laptop and set up ubuntu on it. It has been working fine until just now! my laptop froze so I had to do a hard restart and then once it came back up, I cannot for the life of me connect to the internet. I have tried multiple networks and even using an ethernet cord and still nothing.... it says that I'm "connected" but I cannot access any website and it just shows a question mark where the wifi symbol is up in the right corner. One weird thing is that I AM able to access my router gateway by entering my ip, but that's all I can access. I am truly hoping somebody here can help me solve this issue. Thanks[/FONT]

---

### Post by ub-newbie on 2017-12-07
please post the output from ```
ip route
``` specifically, the "default via" IP value

---

### Post by armstrong3066 on 2017-12-07
> **ub-newbie said:**
> please post the output from ```
ip route
``` specifically, the "default via" IP value

thanks for the response. the output for default via is below

```
default via 192.168.1.1 dev wlp3s0 proto static metric 20600
```

---

### Post by Autodave on 2017-12-08
Does that laptop have an easily removable battery? If so, give this a try: it won't cost a thing but 10 minutes of your time and it is the very first thing I try when a laptop starts doing something unusual:

  	 	 	 	   1. Power down and disconnect power cord.
2. Unplug all peripherals.
3. Remove battery.
4. Wait 10 minutes.
5. Reinstall battery.
6. Connect power cord.
7. Boot computer and test to see if condition is gone.
8. If good so far, now you can reconnect peripherals.

---

### Post by ub-newbie on 2017-12-09
that seems to show that your "Gateway" is set up.   How about a DNS issue?   Can you:
```
Ping 8.8.8.8
```
if so, then
```
nslookup 8.8.8.8
```

---

