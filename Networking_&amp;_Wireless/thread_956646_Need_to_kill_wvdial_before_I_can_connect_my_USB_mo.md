---
title: "Need to kill wvdial before I can connect my USB modem for wireless internet"
date: 2008-10-23
forum: Networking &amp; Wireless
---

### Post by temba on 2008-10-23
Hi everyone,

been a long time since I've been here :)

I have a Huawei E169 (I'm pretty sure) modem and I'm running the latest kubuntu. Vodafones software has also been used with varying success, perhaps the same issue is happening with it. I have configured wvdial with the correct settings and have managed to wangle a connection to the internet sometimes.  

Wangle is the operative word.

I need to kill wvdial that root automatically runs when I connect the modem to the laptop. However, the PID changes each time and so I cannot include this in my script. Root's wvdial locks the ttyUSB0 so my wvdial cannot connect to the modem.

Can anyone tell me if I can kill the process through my script in another way? I don't mind having to type the root password to kill the process in order for wvdial to run immediately afterwards.

Any help is appreciated, even a wholly different solution.

cheerio
temba

---

