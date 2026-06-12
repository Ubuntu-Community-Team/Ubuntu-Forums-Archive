---
title: "multi-threading"
date: 2009-09-29
forum: New to Ubuntu
---

### Post by fwin on 2009-09-29
Hi,
 I am new to the linux world and I have been using UBUNTU for about 2 months on a very old laptop. I really liked the OS and I plan to buy a new dual core DELL laptop with UBUNTU 9.04 already installed on it. The reason why i need a more powerful laptop is because i need to run multiple programs at the same time lilke a VIRTUAL MACHINE, a few 3D cad programs, LATEX and MOZILLA FIREFOX. My question is:

1. Is ubuntu 9.04 a multi-threading OS, (will it use the two cores automatically)?

I don't want to buy a dual core laptop and have no use for the extra processor.

Thanks

---

### Post by undecim on 2009-09-29
Yes, Ubuntu (just as all other Linux distros) is very much a multi-threading OS. It will make the most out of any number of cores. (In fact, this is why most supercomputers, which have thousands of CPUs and CPU cores run Linux)

---

### Post by fwin on 2009-09-30
that is what i needed to know, thank you very much.

---

### Post by 3rdalbum on 2009-09-30
It will assign different programs and threads to different cores depending on how much work they are doing.

Single-threaded programs will still only push one core, but you can run two at a time.

If you want to do video encoding to the h.264 format using FFMPEG, then you can use the "-threads 2" switch to enable multi-threaded encoding.

Dual-core works very well with virtual machines, too, because each VM is another process/program.

---

### Post by fwin on 2009-10-01
Thanks [3rdalbum]("http://ubuntuforums.org/member.php?u=61044") , that was helpful too.:)

---

