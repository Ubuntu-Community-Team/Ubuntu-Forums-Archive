---
title: "How to dual boot Windows XP with an already installed Ubuntu 10.04?"
date: 2011-01-17
forum: New to Ubuntu
---

### Post by chinggisk on 2011-01-17
Hey all,

So I've been running Ubuntu 10.04 (the 64-bit one) for a few months now, I love it, and I finally have just about everything running exactly how I want it to run.  This is except for a few games that I can't get running properly for the life of me, so I've decided I'm giving up on trying to get them working with Wine and will just dual-boot Windows XP.  However, it took me *forever* to get Ubuntu running how I like it now and I really, really don't want to have to try to figure everything out again.  Can someone be super cool and walk me through exactly how to set myself up with a Windows XP dual boot  without reinstalling Ubuntu?  I found a few guides but they all either seemed out of date or were over my head (I'm still very much a noob when it comes to Linux), and I'm extremely paranoid about screwing up.

Thanks!

---

### Post by mlentink on 2011-01-17
So did you read this: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by hansolo4949 on 2011-01-17
Okay, you should just have to reinstall GRUB when you install windows, and be careful with it's options, because it wants to use your entire HDD, not just one partition. If you get past that, you should reinstall grub, and you'll be good to go!

---

### Post by oldfred on 2011-01-17
It may be easy or difficult depending on how you have partitioned. You need to create a primary NTFS partition with the boot flag for the windows installer to see where to install.

Use gparted to create a primary partition. Primary will be sda1 thru sda4.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

Then after you install windows, you can use the guides posted above to reinstall grub2 with a liveCD.

---

### Post by DOSIX on 2011-01-17
you can also try running a virtualbox. i think it's less risky.

---

### Post by Rowanmf on 2011-01-17
I had to do this once , i found a good step by step walk through on the net , i followed it to the letter and it was brilliant and it worked very well , since then i have removed XP as i thought i no longer needed it , only to find out last year that i had to have it back , so a friend suggested virtualbox .
Well mu suggestion to you is virtualbox as well , as i have been really impressed with it , i run a few games and the one thing i need , which i am not going to mention ... ever . 

Goog luck with what ever you choose

---

