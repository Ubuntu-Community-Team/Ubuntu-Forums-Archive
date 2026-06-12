---
title: "Swap continuously increasing..."
date: 2010-12-20
forum: New to Ubuntu
---

### Post by tonycm1 on 2010-12-20
My work laptop has a 120GB HD and 1GB RAM. I've installed Ubuntu 10.04 using WUBI and allocated 15GB on the HD. Originally, the setup only had 256MB of SWAP space but I increased it to 1GB.

Now... what's happening is that when I boot up in Ubuntu, everything is great (swap is at approx 0). Over time, swap continuously keeps increasing and by the next day, the OS is crawling in speed.

Last night, I had left a few downloads going... expecting them to be done by morning. When I got up in the morning to check the status, the OS was sooooooooo slow that I couldn't even get it out of sleep mode.

Any thoughts on this? Should I remove swap entirely (swapoff -a) or bring the swap size back down to 256MB? Also, do you guys know why the swap would just keep continuously increasing like that... and barely decrease when I close my apps?

---

### Post by cariboo on 2010-12-21
It sounds like something you are running has a memory leak, you can monitor ram usage either using System->Administration->System Monitor, or top, in a terminal. Look for an application whose ram usage keeps going up.

---

