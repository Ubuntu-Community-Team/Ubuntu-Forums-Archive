---
title: "X Server"
date: 2009-09-28
forum: New to Ubuntu
---

### Post by ItsAlwaysSunnyIn... on 2009-09-28
I successfully installed Ubuntu Studio 9.04 and booted with no problem. Immediately I was prompted to download and install updates so before I left for work this morning I let it go. I returned home to find the installation stalled so I had to power down and reboot. Now I'm getting a "Failed to start the X server..." message. What's up with this? I'm a newbie so please ignore my ignorance. 

Thanks.

---

### Post by grturner on 2009-09-28
Well a good place to look is in the xorg log files /var/log/Xorg.0.log

if you find any errors there you can search more in depth for them

```
less /var/log/Xorg.0.log
```

---

### Post by CRAY-4 on 2009-09-28
hmmm, try to boot into recovery mode from grub and do all the options:lolflag:

---

### Post by ItsAlwaysSunnyIn... on 2009-09-29
Thanks,

I can't even start the system to get to the terminal. How do I start in recovery mode??

---

