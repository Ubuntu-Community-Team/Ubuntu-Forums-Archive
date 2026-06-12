---
title: "How Much RAM?"
date: 2010-11-19
forum: New to Ubuntu
---

### Post by Nottawa on 2010-11-19
How much RAM can Lucid use?  Is more better?  Is there an upper limit that it can access.  Thinking of upgrading, but don't want to over do it.  I am using a Lenovo T400 running Lucid Lynx.

Thanks.

---

### Post by sandyd on 2010-11-19
> **Nottawa said:**
> How much RAM can Lucid use?  Is more better?  Is there an upper limit that it can access.  Thinking of upgrading, but don't want to over do it.  I am using a Lenovo T400 running Lucid Lynx.

Thanks.

If your using 
32bit ubuntu: 64GB
64bit ubuntu: 256 TB (current)
^^
these are hard limits imposed by the arch of your processor.

---

### Post by theozzlives on 2010-11-19
> **sandyd said:**
> If your using 
32bit ubuntu: 64GB
64bit ubuntu: 256 TB (current)
^^
these are hard limits imposed by the arch of your processor.

WHAT?! 32 bit can only handle just under 4 GB!!! I have 64 bit maverick and 4 GB and I'm fine. I NEVER access my swap and everything runs smoothly. I'd say if your running 64 bit do 4 GB.

You really have to figure out where the bottleneck is (HD, CPU, RAM) then fix it.

---

### Post by asmoore82 on 2010-11-19
> **theozzlives said:**
> WHAT?! 32 bit can only handle just under 4 GB!!!

If your motherboard supports it, you can download the -PAE(Physical address extension) kernel.
I'm currently running 8GB on 32-bit, but never use up more than 2~3 -
and I have to virtualize 2 additional OS's for that.

---

### Post by sandyd on 2010-11-19
> **asmoore82 said:**
> If you motherboard supports it, you can download the -PAE(Physical address extension) kernel.
I'm currently running 8GB on 32-bit, but never use up more than 2~3 -
and I have to virtualize 2 additional OS's for that.

correction: its automatically downloaded. Most motherboards have this support, which is why I put the maximum RAM that can be used with the PAE kernel.

---

### Post by walt.smith1960 on 2010-11-19
Ubuntu certainly doesn't seem like a memory hog.  My old desktop running 32 bit Lucid had 1 Gb. and I'm not sure if it ever used swap.  My current machine has 2 Gb. running 64 bit and it is still only using about 700 Mb. Of course I'm just web browsing, office-type stuff etc.  If I were doing more demanding tasks more RAM would likely be in order, or if I were using onboard video and had to allocate system ram for video.   Adequate processor power seems more important than ample RAM to me.

---

### Post by weasel fierce on 2010-11-19
Its rare for my system to go over a gig, and I'd have to go out of my way to use 2.
I have 4 gigs, and are quite happy with that.

If you do stuff like running virtual machines, you'll obviously need more.

---

### Post by lobralleo on 2010-11-19
I can run Lucid (or Maverick) on a virtual machine with only 512 MB RAM and it works fine. Of course it's towards the low end and I don't use the VM for really intensive stuff anyway, but it's fine for everyday activity - surf the web, play music and videos, and so on.

My workstation (again with Lucid) has 2GB RAM and can handle a lot of heavy tasks simultaneously (including the VM) with no issues. Unless you need explicitly a lot of RAM for some specific task, I would say that 1 to 2 GB are more than enough.

---

### Post by uRock on 2010-11-19
> **theozzlives said:**
> WHAT?! 32 bit can only handle just under 4 GB!!! I have 64 bit maverick and 4 GB and I'm fine. I NEVER access my swap and everything runs smoothly. I'd say if your running 64 bit do 4 GB.

You really have to figure out where the bottleneck is (HD, CPU, RAM) then fix it.
32bit can go up to 64GB of RAM, but it can only use 2GB per application, which is good for most people.

I think the OP was aiming at wanting to know what amount of RAM the system will use. On that note, I use the 32bit version of 10.04 on my machine and it idles at around 200-250MB. I only have 2GB of RAM and have no problems running a virtual machine and surfing the net at the same time.

---

### Post by e79 on 2010-11-19
> **walt.smith1960 said:**
> My current machine has 2 Gb. running 64 bit and it is still only using about 700 Kb.

Running an OS these days with less than 1 MB footprint in RAM, I knew Linux what HOT..but not that much   ;)

:lolflag:

---

### Post by walt.smith1960 on 2010-11-20
> **e79 said:**
> Running an OS these days with less than 1 MB footprint in RAM, I knew Linux what HOT..but not that much   ;)

:lolflag:

Kb, Mb whatever it takes :redface:

---

### Post by Nottawa on 2010-11-20
Thank you for your information and opinions.  I don't have a problem, just saw a great price on ram for my system.  The other os uses a lot of memory, and I was curious about Ubuntu.  Now, how do I mark this as solved?

---

### Post by Joeb454 on 2010-11-20
The thread can be mark solved from 'Thread Tools' at the top of the page :)

Side-note: I have 6GB RAM for my system, I've still only ever broken through 4GB by running a Win7 VM with 2.5GB RAM and an Ubuntu Server with 1 GB RAM for testing things :p

---

### Post by realzippy on 2010-11-20
..unless you change ubuntu's default "[swappiness]("cat /proc/sys/vm/swappiness")" (60) setting to 0,
all available RAM will not be used (afaik).
Only once had a RAM usage of 7.9 from 8 GB during a
rmastersys full-backup creation.

---

### Post by realzippy on 2010-11-20
..unless you change ubuntu's default [swappiness]("https://help.ubuntu.com/community/SwapFaq") (60) setting to 0,
all available RAM will not be used (afaik).
Only once had a RAM usage of 7.9 from 8 GB during a
rmastersys full-backup creation.

---

