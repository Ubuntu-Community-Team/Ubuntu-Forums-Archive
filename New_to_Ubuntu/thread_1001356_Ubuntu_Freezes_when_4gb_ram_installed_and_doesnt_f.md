---
title: "Ubuntu Freezes when 4gb ram installed and doesnt freeze with 1gb installed"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by fattymatty on 2008-12-03
So been having some real issues with my ubuntu since switching from windows xp 64bit but have gotten closer to the cause of the problem day by day but basicly the computer is freezing periodicaly ive gone through the logs and have tried to see if its a graphics card to no avail so i tried on a jump drive to see if it was the hard drive and wasnt that because put that jump drive on wifes comp as an idea since the jump drive was freezing too but didnt freeze on hers and cpus are the same execpt for graphics card, hard drive and psu so removed graphics card and still froze so took went and removed 3gb of ram so now only have 1gb and hasnt froze yet any ideas of why would be freezing with 4gb ram on ubuntu 8.04 64bit

Matt

---

### Post by oldos2er on 2008-12-03
Try running memtest overnight to see if there's something wrong with your RAM.

---

### Post by fattymatty on 2008-12-03
how do i configure memtest to go through lots of passes and are you refering to the one on the livecd

---

### Post by Durden on 2008-12-03
> **fattymatty said:**
> So been having some real issues with my ubuntu since switching from windows xp 64bit but have gotten closer to the cause of the problem day by day but basicly the computer is freezing periodicaly ive gone through the logs and have tried to see if its a graphics card to no avail so i tried on a jump drive to see if it was the hard drive and wasnt that because put that jump drive on wifes comp as an idea since the jump drive was freezing too but didnt freeze on hers and cpus are the same execpt for graphics card, hard drive and psu so removed graphics card and still froze so took went and removed 3gb of ram so now only have 1gb and hasnt froze yet any ideas of why would be freezing with 4gb ram on ubuntu 8.04 64bit

Matt

That's one serious run-on sentence you've got there. I'm trying to read through that but it's hard.

I'll suggest this, if you have 4gb of RAM then just put 1 in, if it works then that one is good. Take that one out, put a different one in, if that one doesn't freeze, it's good. Do that with each stick till you find the bad one.

---

### Post by oldos2er on 2008-12-04
> **fattymatty said:**
> how do i configure memtest to go through lots of passes and are you refering to the one on the livecd

 You should have an option in the grub menu to run memtest. If you don't, you can run it from the LiveCD.

---

### Post by s_shuffle on 2009-01-10
Hello,
I just came across the same problem.I've upgraded an Acer 5715Z from 2 GB to 4GB . I've got ubuntu 8.10  64 bits with kernel 2.6.27-9
And I did  run a memtest to each module , and to each memory slot at the laptop 
The memtest runs without errors in each memory module /each memory slot
 For the sake of testing I 've also did the mem test with pcthe 4 GB and I've got screen garbage(and frozen ) around the first 40%of the 1st memtest
So the laptop is now working with one 2GBmodule and another of 1GB.without problems
 I'm pending more to a BIOS problem addressing the 4GB Ram space....
I'm check with ACERto see what they reply - if they reply-being ACER....
Thanks
Tchau
P.

---

