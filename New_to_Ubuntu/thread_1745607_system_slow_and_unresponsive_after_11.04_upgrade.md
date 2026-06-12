---
title: "system slow and unresponsive after 11.04 upgrade"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by rocka on 2011-05-01
Hi all,
since I've upgraded to 11.04, I've noticed my system seems to be really slow and unresponsive and "sticky". Switching between windows or even between firefox tabs is not smooth any more, and sometimes there's quite a delay. Youtube videos are quite jerky, movies on my hard drive played by Movie Player are a bit jerky but not as much. But still certainly not smooth like they used to be.

Clearly something is wrong.

I started up system monitor, and I see that all the CPUs are running really high, where as before the would typically sit between 20 - 40% now they're up around 80%. When I took this screencap I only had a couple of firefox tabs open, and movie player playing some streaming radio in the background. Quite a typical scenario for me, and there never used to be any trouble at all before.

Interestingly, I note that there is something being uploaded at close on 120KiB/s - I don't know what tat would be. Again, it never used to do that before the upgrade to 11.04...

---

### Post by d0.higgs on 2011-09-24
Any hint?

---

### Post by aura7 on 2011-09-24
Load the results of top or system-monitor process view... sorted by CPU usage.

---

### Post by wildmanne39 on 2011-09-24
Hi, also please post the results of:
```

sudo lshw

```
Thank you

---

