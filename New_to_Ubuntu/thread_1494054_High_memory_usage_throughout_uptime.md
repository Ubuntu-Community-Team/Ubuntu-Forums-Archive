---
title: "High memory usage throughout uptime"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by rampageoberon on 2010-05-26
Hi,

I've noticed a problem very recently in my Lucid installation. On boot the memory usage is very high (700mb+) and with the X server not running its still 600mb.

When I first installed Lucid, I didn't face this problem, with the system hardly going over 300mb memory usage on boot.

Please help identify what the problem might be? If anyone else is seeing this as it can be quite a bugger with lower end machines. How can I fix this?

PS: the memory usage doesn't increase (so not sure its GEM leak) but is abnormally high from the word go.

Thanks,

---

### Post by -humanaut- on 2010-05-26
Does the memory increase at all while just sitting idle? Have you added any additional software that may be loading when you boot?

---

### Post by rampageoberon on 2010-05-26
No memory doesn't increase when idle. Its just a lot higher than I expect it to be. Up until last week it would once desktop is loaded it would still be using less than 300mb ram.

On boot just have lighttpd, samba, and ssh server that start up.

---

### Post by stoogiebuncho on 2010-05-26
I have lucid installed on two machines.  On my desktop, it generally takes around 500-600mb of memory just to sit there.  On my laptop, it takes less than 200mb of memory.  

I have a lot more memory on my desktop, so I had just assumed that if there was extra available memory, Ubuntu would use it for something, and if not, it wouldn't.  But I don't really know.

---

### Post by rampageoberon on 2010-05-26
When i first installed Lucid on my desktop it would take at most 300mb to just sit.

I'm not sure if its one of the updates that I applied, or what could be doing that - but just noticed today that its consuming 600mb to just sit after boot.

Don't think thats normal for it. And this is memory excluding cache.

---

### Post by SabreWolfy on 2010-06-07
My Karmic server used about 8% of it's 2GB RAM. After upgrading to Lucid, about 31% is being used! I restarted the server a few times for various other reasons, and RAM usage dropped to 4-8%. After another restart for something else, it was back to 31%. I can't tell from 'top' what is taking up almost 620MB of RAM on a non-X server! :(

---

### Post by rampageoberon on 2010-06-07
> **SabreWolfy said:**
> My Karmic server used about 8% of it's 2GB RAM. After upgrading to Lucid, about 31% is being used! I restarted the server a few times for various other reasons, and RAM usage dropped to 4-8%. After another restart for something else, it was back to 31%. I can't tell from 'top' what is taking up almost 620MB of RAM on a non-X server! :(

Hi SabreWolfy, my problems stayed for a while and went away with some updates. Still haven't figured out what non X server application was eating close to 600mb ram. Its back to 200mbish usage on boot now, and hope it stays that way on future updates. Hopefully your issue is fixed in the same way.

---

### Post by SabreWolfy on 2010-06-07
Reboot again and now it's only using 5% of the RAM. I wonder what's going on here.

---

### Post by stoogiebuncho on 2010-06-07
Yeah, when I add up all the processes in my System monitor, it comes to around 450mb (I have several large programs open right now).  But when I look at the RAM usage, it says that I'm using 665MiB.  I don't get it.

---

### Post by SabreWolfy on 2010-06-07
@rampageoberon: My server is fully updated though, so I'm not sure what update fixed your system. There was a memory leak in Lucid, but it was in the RC and was X-related IIRC. I'm very surprised that my server uses 5% or 31% between one reboot and the next...

---

### Post by SabreWolfy on 2010-06-07
> **stoogiebuncho said:**
> Yeah, when I add up all the processes in my System monitor, it comes to around 450mb (I have several large programs open right now).  But when I look at the RAM usage, it says that I'm using 665MiB.  I don't get it.

Yeah. On my server I have a few apache and mysqld processes running. The normal 5-8% usage (of 2GB) seems about right (the server is not under any load). So 31% means over 600MB of RAM on an idling server with no X/GUI. Something's wrong somewhere...

It seems to fluctuate between one reboot and the next though ... 5% ... 31% ... 5% ...

---

### Post by SabreWolfy on 2010-06-07
Similar discussions, but related to desktops not servers:

[http://ubuntuforums.org/showthread.php?t=1478329](http://ubuntuforums.org/showthread.php?t=1478329)

[http://ubuntuforums.org/showthread.php?t=1474932](http://ubuntuforums.org/showthread.php?t=1474932)

---

### Post by rampageoberon on 2010-06-07
Definitely something wrong with headless server using 31% of 2GB ram. Don't like the reboot fixed issue so much - better to know the problem and plug it I feel. Will keep digging and hope it doesn't occur again.

---

### Post by SabreWolfy on 2010-06-08
A [thread]("http://ubuntuforums.org/showthread.php?t=1504110") I started previously on this issue, for reference. Nothing new there at the moment though.

---

### Post by SabreWolfy on 2010-06-21
Related thread [here]("http://ubuntuforums.org/showthread.php?t=1490677") and site [here]("http://www.linuxatemyram.com/").

So "disk caching" takes up almost 650MB of RAM on my Lucid Ubuntu server, but not when it was running Karmic? I'm running dovecot, apache, mysql and postgresql under virtually no load. Under Karmic 8% of 2GB RAM was used. Under Lucid it's 32%. Adding up memory footprints from 'top' comes nowhere near to 650MB. How else can I see what's using RAM?

---

### Post by SabreWolfy on 2010-06-21
I've used [htop]("http://htop.sourceforge.net/index.php?page=main") before, but have not paid much attention to the memory graph it displays. The green in the memory bar shows "used" memory, the blue shows buffers and the brown shows cache. Output from htop in attachment. Total used is 650MB, with more than half buffer/cache. However:

```

$ free -m
             total       used       free     shared    buffers     cached
Mem:          2003       1829        174          0         90       1093
-/+ buffers/cache:        644       1358
Swap:         9609          0       9609

```

Shows that total used us 1829MB (!), but of that 644MB is buffer/cache. :confused:

---

### Post by rampageoberon on 2010-06-22
After the system updates my issues have disappeared. Still not figured out what took up all that memory. Use 200mb on boot at present.

---

