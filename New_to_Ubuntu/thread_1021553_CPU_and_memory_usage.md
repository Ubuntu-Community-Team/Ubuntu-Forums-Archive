---
title: "CPU and memory usage"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by mdewet on 2008-12-25
I saw in the system monitor that both my processors are constantly running at +- 40%, even when the system is idle.  Also the 1 GB RAM is 70% full while the 2 GB swap uses only about 5%.  

I am using advanced desktop effects with the onboard video card (intel 128MB) which mayby can explain this, but I don't really know.  My system still works fine, but I wasn't used to this when using XP, and I want to learn more about the memory usage and swap area for linux. Is this normal for linux systems? 

Hardware:

Intel Core 2 Duo 1.8 GHz
1 GB RAM
Hardy 8.04 x64

---

### Post by zzHanks on 2008-12-25
System monitor it self takes a lot of process.

I added it to the panel, more accurate.

---

### Post by nhasian on 2008-12-25
instead of using the system monitor which itself uses a lot of resources, in a terminal type

```
top
```

to quit top press q, to kill a process press k

---

### Post by adobrakic on 2008-12-25
Does it use a lot of resources if it's the one in the panel?

---

### Post by wolfen69 on 2008-12-25
> **adobrakic said:**
> Does it use a lot of resources if it's the one in the panel?

my system monitor on the panel only uses 5mb. hardly a resource hog. if 5mb is a big deal to you, get more memory or switch to a lighter distro.

---

### Post by mdewet on 2008-12-26
> **nhasian said:**
> instead of using the system monitor which itself uses a lot of resources, in a terminal type

```
top
```

to quit top press q, to kill a process press k

this answered my cpu question thanks.  The system monitor itself takes up the cpu performance of 40%, but when using top it's down to +- 0.1%.

---

### Post by mcduck on 2008-12-26
What comes to the memory usage, that's also normal. After running a while your system will be using almost all of the RAM. But that doesn't mean the memory is hogged by applications, it's used as cache to speed up the system.

Reading from RAM is roughly 1000 times quicker than reading from hard disk (which is also where the swap would be), so Linux uses your free RAM as a temporary storage for all the data you use. If a program then needs more memory the system simply drops some of this cached data to free more memory. So, the RAM used for cache still counts as "free" for programs to use.

To check the "real" memory usage you can run "free -m" in a terminal, and then read from the "+/- buffers/cache"-line.

Of course it can just be that you are using some memory-intensive application, for example Firefox with lots of extensions or lots of pages open can easily eat loads of RAM. So if the memory usage seems high even without including the cache you should check what application is using that much RAM.

---

### Post by hovzio on 2008-12-26
Hi, htop is also an awsome program to view processes, you can view all processes, search, kill, sort by cpu, ram, user, usage and so forth. You can view the processes in a tree structure, its really neat. Above all its a little more accurate than gnome-sys-monitor since it doesnt use up nearly as many resources.

---

