---
title: "One Screen blinks out"
date: 2011-07-14
forum: New to Ubuntu
---

### Post by lile001 on 2011-07-14
Just upgraded to Ubuntu 11.04.  This problem never occurred before that:

Occasionally, the right screen on my dual screen monitor blinks off.  Doesn't happen very often, nor for more than a second or so, then proceeds to work normally.  I don't really have any idea where to start asking about troubleshooting this except to ask here.  I'll be watching it to try to get a sense of timing, and so forth.  I haven't noticed any particular thing I am doing that is associated with it, except using a browser.  

Any hints as to how to start troubleshooting this?

---

### Post by lile001 on 2011-07-14
> **lile001 said:**
> Just upgraded to Ubuntu 11.04.  This problem never occurred before that:

Occasionally, the right screen on my dual screen monitor blinks off.  Doesn't happen very often, nor for more than a second or so, then proceeds to work normally.  I don't really have any idea where to start asking about troubleshooting this except to ask here.  I'll be watching it to try to get a sense of timing, and so forth.  I haven't noticed any particular thing I am doing that is associated with it, except using a browser.  

Any hints as to how to start troubleshooting this?


looks like it might be happening every 6 minutes or so.  Just enough to be annoying.

---

### Post by Snowboi on 2011-07-15
> **lile001 said:**
> looks like it might be happening every 6 minutes or so.  Just enough to be annoying.

Can i see the output of 

```
lspci | grep VGA
```

---

### Post by lile001 on 2011-07-18
> **Snowboi said:**
> Can i see the output of 

```
lspci | grep VGA
```

Thanks for replying! 

lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation G86 [Quadro NVS 290] (rev a1)

I am noticing that the right-hand screen blinks offmore often when the left hand screen changes dramatically, like bringing up a new window or closing one.  Not every time, not consistently, but I have observed it happen more than once a minute when switching around between windows (or whatever you call them in Ubuntu)

---

### Post by lile001 on 2011-11-01
> **lile001 said:**
> Thanks for replying! 

lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation G86 [Quadro NVS 290] (rev a1)

I am noticing that the right-hand screen blinks offmore often when the left hand screen changes dramatically, like bringing up a new window or closing one.  Not every time, not consistently, but I have observed it happen more than once a minute when switching around between windows (or whatever you call them in Ubuntu)

Does anyone have any further idea how to troubleshoot this problem?

---

