---
title: "Trying to understand memory, need explanation"
date: 2011-07-08
forum: New to Ubuntu
---

### Post by s1baker on 2011-07-08
Hi,
I am trying to understand the memory in Ubuntu.
when I type free -m in the terminal I get this:


```
             total       used       free     shared    buffers     cached
Mem:          2011       1870        140          0         91        826
-/+ buffers/cache:        952       1059
Swap:         4025          0       4025

```

As you can see, it says that I have only 140M of memory free
but I have only a few things running. Sometimes it will fill up to where there is on 50 or 60 megs free and stay around there as more and more programs are run. The -/+ buffers/cache though, shows 1059 free. I have yet to see any swap used ( have had my 2 Gig memory upgrade for about 3 weeks now).
So what is the buffers, and is it really the true free memory that I have?

thanks

---

### Post by foxmulder881 on 2011-07-08
Install htop and see what it gives.

---

### Post by diesch on 2011-07-08
The "used" field in the "-/+ buffers/cache" line shows you how much of the "used" memory is used for disk buffers.

Linux tries to use as much of your memory as possible (unused memory is wasted memory) so memory not used by apps is used to buffer your disks to speed up file access.

This memory is freed if needed by apps, so the "free" field of the "-/+ buffers/cache" line shows you the amount of memory (without swap space) that is available for your apps. For you that's 1059 MByte.

---

### Post by s1baker on 2011-07-08
so my programs that were running in this instance had grabbed 952 megs of my memory, leaving 1059 that can be used, and the 952 that the programs have grabbed, can be released if needed by other programs. That makes sense, but I am still confused what the 140 megs free means in the "Mem:" row.

---

### Post by bodhi.zazen on 2011-07-08
A google search will yield some interesting pages on linux and ram (memory) use.

See:

[http://chrisjohnston.org/2009/why-on-linux-am-i-seeing-so-much-ram-usage](http://chrisjohnston.org/2009/why-on-linux-am-i-seeing-so-much-ram-usage)

[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

### Post by psusi on 2011-07-08
> **s1baker said:**
> so my programs that were running in this instance had grabbed 952 megs of my memory, leaving 1059 that can be used, and the 952 that the programs have grabbed, can be released if needed by other programs. That makes sense, but I am still confused what the 140 megs free means in the "Mem:" row.

No, 952 is used by applications, 140 is free, and the rest is being used to cache the disk, which will be given up if needed.

---

### Post by wojox on 2011-07-08
> **bodhi.zazen said:**
> 
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

:lolflag:

Try :

```
man free
```

It will give you some good info such as display the amount of memory in megabytes:

```
free -m
```

---

### Post by s1baker on 2011-07-08
just read the excellent article about memory:


[http://chrisjohnston.org/2009/why-on-linux-am-i-seeing-so-much-ram-usage](http://chrisjohnston.org/2009/why-on-linux-am-i-seeing-so-much-ram-usage")

this explains it all clearly, this should be required reading for anyone wanting to understand memory.

---

