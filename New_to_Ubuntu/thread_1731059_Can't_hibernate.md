---
title: "Can't hibernate"
date: 2011-04-16
forum: New to Ubuntu
---

### Post by MarkTrent on 2011-04-16
Hello, I'm using Ubuntu 10.10 but I cannot hibernate. I have 2.5GB of RAM and 4.25GB of swap space.

In kern.log I have the entry:

```
Apr 16 22:34:24 HTPC kernel: [  179.907293] PM: Free swap pages: 63099
Apr 16 22:34:24 HTPC kernel: [  179.907295] PM: Not enough free swap
Apr 16 22:34:24 HTPC kernel: [  179.963459] Restarting tasks ... done.
```Running the command 'free' I get:

```
mark@HTPC:~$ free
             total       used       free     shared    buffers     cached
Mem:       2572540     594920    1977620          0     116660     106160
-/+ buffers/cache:     372100    2200440
Swap:      4217020       9460    4207560

```Does anyone know why this is?

Thanks,
Mark

---

### Post by r-senior on 2011-04-16
Is all that swap in a swap partition, or is all or part of it a swap file?

---

### Post by MarkTrent on 2011-04-16
It's in two swap partitions.

```
mark@HTPC:~$ cat /proc/swaps
Filename                Type        Size    Used    Priority
/dev/sdg5                               partition    265036    0    1
/dev/sda4                               partition    3951984    0    1

```

---

### Post by Bucky Ball on 2011-04-16
Hibernation = double your RAM.

2.5x2=5, not 4.25. You should have one /swap partition. ;)

---

### Post by MarkTrent on 2011-04-16
Ah ok thanks, I'll give that a try.

NB. I use two swap partitions as I never have to dip into it, so I've got a small amount of swap on a fast storage just in case, and the larger swap on slow storage for hibernation (ignore the priorities there, I changed them while playing around to test hibernation).

---

### Post by yetiman64 on 2011-04-16
> **Bucky Ball said:**
> Hibernation = double your RAM.

2.5x2=5, not 4.25. You should have one /swap partition. ;)
Actually that may be old info, to hibernate only should require same swap size as RAM size.
The bolded text below may be of interest to you in this case. From the --[Community Documentation swap FAQ--]("https://help.ubuntu.com/community/SwapFaq").


> **How much swap do I need?**

 **As a base  minimum**, it's highly recommended that the swap space should be **equal to  the amount of physical memory **(RAM). Also, it's recommended that the  swap space is **twice the amount of physical memory** (RAM) **depending upon  the amount of hard disk space available for the system (although this  "recommendation" dates back from a time when physical RAM was very  expensive and most Unix systems ran with many processes in swap space - a  situation that hardly applies in most situations these days, but  ancient Unix/Linux myths like this "recommendation" tend to survive well  past their "use by" dates)**. In reality, if you use hibernation you need  what was outlined the relevant paragraph above, otherwise you need as  much swap space as your system will use - which may be actually be very  little in a modern hardware setup. The only downside to having more swap  space than you will actually use is the disk space you will be  reserving for it. I agree though with having only one swap partition OP, the first is far too small (/dev/sdg) for swap and if the system is attempting to use it then I'd expect a failure. The second however should be large enough by itself for use as swap with 2.5 GB RAM.

I'd try removing the partition /dev/sdg5 from being used as swap in /etc/fstab (just comment it out with a # symbol at the start of the line and restart) and check the details in there for the swap on /dev/sda4 are correct.

---

### Post by Blasphemist on 2011-04-16
I agree with the yeti and can offer this link.
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

