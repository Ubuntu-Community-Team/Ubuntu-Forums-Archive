---
title: "Problem with wired connection"
date: 2013-11-02
forum: Networking &amp; Wireless
---

### Post by l.k.1234 on 2013-11-02
I am using ubunt 13.04 for quite a while now and I never had any issues with my internet connection. But last week while surfing the pages suddently stopped loading. So I turned the connection off and on again. The status changed to connecting and after about 2 minutes it went off again. I tried fixing this by restarting the computer, I chose another kernel the problem stayed (I tried 3.10, 3.9 self compiled, 3.8). But the problem stayed. An hour later I decided to give up. When I turned the computer on again, the connection worked fine again.
But today the problem reappeared. I tried:
 ```
ifdown eth0
ifup eth0
``` and it said:
```
Ingnoring unknown interface eth0=eth0
```
But according to ifconfig eth0 is set up the right way (as far I can tell).
Also there are some strange lines in dmesg:
```
eth0 link down
```

I'd like to add some more information but I don't want to tip that much by using my mobile

EDIT: I was even unable to reach 127.0.0.1

thanks in advance for any help

---

