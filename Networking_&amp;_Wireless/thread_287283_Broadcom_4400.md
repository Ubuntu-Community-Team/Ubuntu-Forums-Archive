---
title: "Broadcom 4400"
date: 2006-10-28
forum: Networking &amp; Wireless
---

### Post by Circir on 2006-10-28
I have broadcom 4400 nic which has been working properly in dapper, but ever since installing edgy and kernel higher than 2.6.15 it doesn't work properly anymore. After transferring data in LAN (higher bandwith), nic gets some sort of buffer full problems. I tried installing the driver from 2.6.15 and compiled the kernel 2.6.18 again, but that didn't help.

---

### Post by trubblemaker on 2006-10-28
are you using the native driver? if you are you might need to throttle your rate back a little.  
```
 iwlist scan 
``` will tell you the rates availble  then ```
 iwconfig 
``` will tell you your rate and essid.  figure choose a lower rate than the one your on.  I for a while was on 36M but had to drop down to 11M for stability.
to change the rate to 11M:
```
 sudo iwconfig <interface> rate 11M 
```

---

### Post by Circir on 2006-10-29
Yes it's native driver (at least I haven't downloaded a driver separately), but it isn't wireless :). Ethernet

---

### Post by trubblemaker on 2006-10-29
My bad, I think I've seen another post on this driver but can't remember try searching around on it. also dmesg might give you some error messages which might help refine your posting/searching

---

### Post by Circir on 2006-10-29
[http://lists.xensource.com/archives/html/xen-devel/2004-09/msg00189.html](http://lists.xensource.com/archives/html/xen-devel/2004-09/msg00189.html) After looking at this link, I found out that the sk-thing indeed was higher after the problem occurred.

---

### Post by trubblemaker on 2006-10-29
sounds like it's time to file a bug looking at that report. still think that looking around for a fix on the forums might help

---

### Post by Circir on 2006-10-30
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/60532](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/60532) This seems to be pretty close, if not even the exactly same error

---

