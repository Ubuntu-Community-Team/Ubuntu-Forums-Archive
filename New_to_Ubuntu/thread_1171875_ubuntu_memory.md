---
title: "ubuntu memory"
date: 2009-05-27
forum: New to Ubuntu
---

### Post by tlab on 2009-05-27
So I have a 2 gig stick of memory in my box, but it only shows 884MiB, shouldn't it be 2.0GiB?

How can I fix it?

travis@travis-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           884        413        471          0          4         75
-/+ buffers/cache:        332        551
Swap:         1906          0       1906


Hardware:
Intel atom 330
rtai-smp kernel

---

### Post by NHArticleTen on 2009-05-27
generally speaking, *nix "takes" half of your physical ram for the core system, then you get "your" half for everything running on top of the core.

Your POST test, run by your BIOS, will report the correct amount. If you have doubts about the integrity of your ram then when you have time you can use the memtest function of the live CD.

---

### Post by Paqman on 2009-05-27
> **tlab said:**
> shouldn't it be 2.0GiB?


If it's a single 2GB stick, definitely.

---

### Post by BZF on 2009-05-27
[SIZE=1][COLOR=Blue]when u install it, it will take a bit of memory[/COLOR][/SIZE]

---

### Post by Didius Falco on 2009-05-27
Don't forget the bite most video cards take right off the top, too. I've got 4 gigs of Ram, but 3.2 is all that is left after my ATI card gets done chewing on it. ;)

Regards,

Didius

---

### Post by halitech on 2009-05-27
Are you sure you have a 2gig stick? here is mine and I know I have a 2gig stick in mine as I just built the system and I'm using 256 for the onboard video.

```
daryl@debian:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1760       1745         14          0         68        797
-/+ buffers/cache:        879        880
Swap:         1945          2       1943
daryl@debian:~$ 

```

NHArticleTen - it might use it but free -m should still be showing the amount of physical ram that the system has.

---

### Post by orange-wedge on 2009-05-27
> **Didius Falco said:**
> Don't forget the bite most video cards take right off the top, too. I've got 4 gigs of Ram, but 3.2 is all that is left after my ATI card gets done chewing on it. ;)

Regards,

Didius

Actually that 3.2GB is probably because you are running the 32bit version of Ubuntu which cannot allocate memory over 2^32 addresses.

---

### Post by Didius Falco on 2009-05-27
> **orange-wedge said:**
> Actually that 3.2GB is probably because you are running the 32bit version of Ubuntu which cannot allocate memory over 2^32 addresses.

+1 on that. I just rebooted into my 64 Bit install and it's showing 3.8GB

Regards,

Didius

---

### Post by 3rdalbum on 2009-05-27
> **tlab said:**
> So I have a 2 gig stick of memory in my box, but it only shows 884MiB, shouldn't it be 2.0GiB?

Check your BIOS settings; there is sometimes one that limits addressable RAM to somewhere around 800-900 megabytes.

---

