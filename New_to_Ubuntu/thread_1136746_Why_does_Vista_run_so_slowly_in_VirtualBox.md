---
title: "Why does Vista run so slowly in VirtualBox?"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by yeehi on 2009-04-25
I am running Jaunty 64 alternate and have VirtualBox.

I setup Vista 32 bit on VirtualBox. It goes OK, but very slowly. My system has 2GB of memory. I remember when I setup Vista on VB, I used the default VB memory of 512 MB. I know that Vista is slow without much memory. This is the only thing I can think of that is slowing it down.

What can I do?

---

### Post by zeex on 2009-04-25
> **yeehi said:**
> I am running Jaunty 64 alternate and have VirtualBox.

I setup Vista 32 bit on VirtualBox. It goes OK, but very slowly. My system has 2GB of memory. I remember when I setup Vista on VB, I used the default VB memory of 512 MB. I know that Vista is slow without much memory. This is the only thing I can think of that is slowing it down.

What can I do?


Well RAM is low on VB but it's still okay for Vista Home basic. The reason i could think of is the graphics card requirement. Vista needs a DirectX-9 class graphics card with 32 MB graphics memory. Guest OS in VB doesn't see the real hardware. it's not supported in VB. The virtual graphics card provides the necessary VESA and VGA features to make the guest operative systems work just OK. You also need to install guest additions to get the higher resolution and mouse support.

---

### Post by kpkeerthi on 2009-04-25
> **yeehi said:**
> I am running Jaunty 64 alternate and have VirtualBox.

I setup Vista 32 bit on VirtualBox. It goes OK, but very slowly. My system has 2GB of memory. I remember when I setup Vista on VB, I used the default VB memory of 512 MB. I know that Vista is slow without much memory. This is the only thing I can think of that is slowing it down.

What can I do?

If you bump your guest's memory, you will cause your host to swap a lot and both the guest and host would begin to crawl. 

After all, its a virtual hardware. Your guest's requests (system calls) goes to the host first and then to the real hardware. So a lot of work needs to be done. That's the price you have to pay for virtualized setup.

---

### Post by stwschool on 2009-04-25
Vista's also pretty damn inefficient. Any chance you can swap it out for XP or 7?

---

### Post by pparks1 on 2009-04-25
AS others have said, Vista is a very hardware intensive operating system that simply doesn't run great in a virtual environment unless you have an extremely powerful host computer.   I've used Vista in VM environments with dual quad core CPU's and 16GB's of RAM and it's much better there than it is on my single Core 2 Duo laptop with 4GB of RAM.

---

### Post by chender on 2009-04-25
i have tried XP and Vista in different set ups on VB.  Clear winner is XP with 1 mg RAM allocated (I have 3Mg on my thinkpad).  Its a smooth combination for running Ubuntu (9.04) and XP when I need it.  Vista is just too bloated.  It needs way to much RAM and no benefit.  Office 2007 runs awesome and super fast in my XP set up.  
Also make sure enough disk space allocated.  I have 12 Gig allocated and XP uses 75%.  Vista needs more.

---

### Post by Roadbloc on 2009-04-25
windows vista runs slow on anything. period. the end.

---

### Post by antych on 2009-12-03
I just set up 64bit Vista in 64 Ubuntu 9.10

It's a i5 quad core with 8GB of memory. I gave the guest access to 4 cores and 2GB of RAM. The performance was so bad it was unusable. Then I gave it only 1 core and it runs great. I guess the SMP support is flaky. You might give it a try.

---

