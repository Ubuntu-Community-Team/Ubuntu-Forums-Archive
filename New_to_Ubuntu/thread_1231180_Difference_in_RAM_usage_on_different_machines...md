---
title: "Difference in RAM usage on different machines.."
date: 2009-08-04
forum: New to Ubuntu
---

### Post by user 123 on 2009-08-04
Why is it that when I do a minimal install of ubuntu with an xfce desktop on my 256MB RAM machine it only uses about 55MB of RAM at the desktop whereas on my 3GB RAM laptop it uses 120MB? I found this out using conky which im pretty sure does not count memory used for the cache. Is there any way I can reduce the RAM usage on the laptop/.

---

### Post by damis648 on 2009-08-04
Are both computers using XFCE? Is one 32-bit and the other 64-bit? Any difference at all makes a difference.

---

### Post by user 123 on 2009-08-04
No they were both installed using the minimal install disc with 32-bit os's. All i have installed on each of them are xorg, gdm and xfce4.

---

### Post by damis648 on 2009-08-04
Could you post the output of
```
free -m
```
on both computers?

---

### Post by user 123 on 2009-08-04
> **damis648 said:**
> Could you post the output of
```
free -m
```
on both computers?

I'm not sure of an easy way to do this but the figures im giving you exclude any cached memory and are from the value on the -/+ buffers/cache line.
On both systems as well this is when swap usage is 0.

---

### Post by kpkeerthi on 2009-08-04
.. And also the output of this command:
```
uptime
```

The memory usage must be recorded at almost the same instance after boot on both the PCs, as it tends to grow over time.

---

### Post by user 123 on 2009-08-04
> **kpkeerthi said:**
> .. And also the output of this command:
```
uptime
```

The memory usage must be recorded at almost the same instance after boot on both the PCs, as it tends to grow over time.

the values I've given you are taken as soon as the desktop loads and remain pretty much constant (unless of course i open another program)

---

### Post by Mighty_Joe on 2009-08-04
I'd expect that if one has more available RAM, the system would use more for caching.  
[Linux Ate My RAM!]("http://www.linuxatemyram.com/")

---

### Post by wizard10000 on 2009-08-04
> **user 123 said:**
> Why is it that when I do a minimal install of ubuntu with an xfce desktop on my 256MB RAM machine it only uses about 55MB of RAM at the desktop whereas on my 3GB RAM laptop it uses 120MB? I found this out using conky which im pretty sure does not count memory used for the cache. Is there any way I can reduce the RAM usage on the laptop/.

I know I'm not answering your question here but why mess with it?  Linux is pretty efficient when it comes to memory usage and as long as the machine isn't hitting the swap partition it's all good.

RAM should be used.  Memory that's not doing anything shouldn't be in your computer  ;)

---

### Post by kpkeerthi on 2009-08-04
I would just compare the output of **top** command (sorted by mem usage) taken from both the PCs. But frankly, considering the available RAM is 3GB, I wouldn't be bothered as long as my CPU usage doesn't spike unusually impacting the overall performance.

---

### Post by user 123 on 2009-08-04
Yeah I'm not overly concerned, I was more asking out of interest than anything. Do some processes use more RAM if there is more available or something similar?

---

### Post by wizard10000 on 2009-08-04
> **user 123 said:**
> Yeah I'm not overly concerned, I was more asking out of interest than anything. Do some processes use more RAM if there is more available or something similar?

I'm guessing here but that makes sense to me.  Maybe someone who's smarter than both of us will chime in  ;)

---

### Post by mikechant on 2009-08-04
I'm pretty sure I've read that Linux allocates more I/O buffers if you have more RAM.

---

### Post by HotShotDJ on 2009-08-04
> **wizard10000 said:**
> RAM should be used.  Memory that's not doing anything shouldn't be in your computer  ;)+1  -- if your OS isn't efficiently making use of all that RAM, why bother putting it in your system?
> **user 123 said:**
> Do some processes use more RAM if there is more available or something similar?Yes.  The more RAM you have, the more RAM the Linux kernel will use for disk caching. See the link that Mighty_Joe provided for "Linux Ate My RAM!" My favorite line from that page is this:> Disk caching makes the system much faster! There are no downsides, except for confusing newbies. 

---

### Post by kpkeerthi on 2009-08-04
Actually, the OP is observing higher RAM usage **excluding disk caches and buffers** on one of his two PCs running identical Ubuntu setup. The PC using more memory (again, excluding caches & buffers) has 3GB of RAM than the other (256 MB).

---

### Post by user 123 on 2009-08-04
> **kpkeerthi said:**
> Actually, the OP is observing higher RAM usage **excluding disk caches and buffers** on one of his two PCs running identical Ubuntu setup. The PC using more memory (again, excluding caches & buffers) has 3GB of RAM than the other (256 MB).

Thanks you, I really can't stress enough that the values I have given are EXCLUDING disk caches and buffers. Both machines have the same packages and features installed but the system with more RAM is using more memory at the desktop.

---

### Post by harry2006 on 2009-08-04
linux kernel is smart enough to make the BEST use of available RAM...you'll never see anyother kernel running on a digital watch or any other such devices having ~2mb memory...and working smoothly...linux always rocks!

---

