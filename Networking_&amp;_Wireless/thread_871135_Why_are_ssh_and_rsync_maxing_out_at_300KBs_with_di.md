---
title: "Why are ssh and rsync maxing out at 300KB/s with direct ethernet connection?"
date: 2008-07-26
forum: Networking &amp; Wireless
---

### Post by Frem on 2008-07-26
I'm moving about 60gigs of data from one laptop (Arch Linux) to another (Ubuntu). First, I tried connecting both machines to an 8 year old router by ethernet and running scp overnight. That was moving at about 2Mb/s last night, but when I work up this morning, it had dropped down to about 200Kb/s. I tried using rsync instead, but it's only moving at between 200Kb/s and 300KB/s. 

Finally, I tried connecting the two laptops with an ethernet cord, using Wicd to set the ip addresses manually with one as the gateway, and using rsync. That's averaging about 300Kb/s. I *know* I saw a 2Mb/s transfer rate going on last night, but I have no idea why the speed dropped down so low or why I can't reproduce it. Normally I wouldn't care, but speeding up the transfer will cut *days* off it.

The rsync command I'm using is
```
rsync -r -t -v --progress --ignore-existing -i -l james@192.168.1.10:* /home/james/incoming
```

Any assistance is appreciated.

---

### Post by kevdog on 2008-07-26
How are you measuring bandwidth?

---

### Post by Frem on 2008-07-28
Rsync tells you what your transfer speed is.

---

