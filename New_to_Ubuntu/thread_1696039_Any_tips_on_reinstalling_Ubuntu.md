---
title: "Any tips on reinstalling Ubuntu"
date: 2011-02-26
forum: New to Ubuntu
---

### Post by NotSoheavyD on 2011-02-26
So besides missing drive space now my install of Ubuntu 10.04 is completely hosed. (Basically upgraded from 9.10 and the upgrade messed it up. Can't say I'm surprised, I had heard how brittle linux is.) Anyway is there any guide out there that can give me some tips about doing a reinstall. (I'll probably go for 10.10 at this point.) Basically I figure I'll just blow away the previous install and start from scratch.

---

### Post by Hedgehog1 on 2011-02-26
> **NotSoheavyD said:**
> ... Can't say I'm surprised, I had heard how brittle linux is...

*When asking for help/guidance, these are not the best choice of words.*

For reinstalling, will Ubuntu be the only OS, or do you have in mind a dual-boot situation with Windows?

If Ubuntu will be the only OS the drive can be wiped clean and 3 partitions can be made for a nice install('/', 'Swap' & '/home').

If you want to dual boot, you will need t clean up your hard drive first to get rid of the mish-mash of partitions you have (as I recall from on your earlier thread).

Which way do you want to install?

---

### Post by seawolf167 on 2011-02-26
[Here]("https://help.ubuntu.com/community/WindowsDualBoot") is a dual boot guide

[Here]("https://help.ubuntu.com/10.04/installation-guide/i386/index.html") is a Ubuntu installation guide

Let us know if you have any specific questions or concerns when reinstalling

---

### Post by josephmills on 2011-02-26
go take a look at this [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)  hope it helps:)

---

### Post by NotSoheavyD on 2011-02-27
> **Hedgehog1 said:**
> *When asking for help/guidance, these are not the best choice of words.*
 
For reinstalling, will Ubuntu be the only OS, or do you have in mind a dual-boot situation with Windows?
 
If Ubuntu will be the only OS the drive can be wiped clean and 3 partitions can be made for a nice install('/', 'Swap' & '/home').
 
If you want to dual boot, you will need t clean up your hard drive first to get rid of the mish-mash of partitions you have (as I recall from on your earlier thread).
 
Which way do you want to install?
 
That's true. Just a little annoyed that I managed to hose my install because I did an upgrade.(Very strange, somehow I got to the point I can log in but now it won't recognize a mouse.) 
 
Anyway it was and will be a dual boot computer. (With Windows.) I'll have to look over the guides mentioned in other posts in this topic.

---

### Post by Hedgehog1 on 2011-02-27
The key to a good reinstall of Ubuntu in a dual boot situation is to (in this order):

1) Get windows to boot without Grub (**FIXMBR** in XP, **bootrec /FixMbr** in Vista and Windows 7)

2) THEN delete all the Ubuntu paritions

3) Finally, reinstall Ubuntu manually and control the creation of partitions ('/', 'Swap','/home').

After that, I think most of your issues will stop.

:KS

---

### Post by NotSoheavyD on 2011-02-27
> **Hedgehog1 said:**
> The key to a good reinstall of Ubuntu in a dual boot situation is to (in this order):
 
1) Get windows to boot without Grub (**FIXMBR** in XP, **bootrec /FixMbr** in Vista and Windows 7)
 
2) THEN delete all the Ubuntu paritions
 
3) Finally, reinstall Ubuntu manually and control the creation of partitions ('/', 'Swap','/home').
 
After that, I think most of your issues will stop.
 
:KS
 
Thanks for the info. I'll give that a try. Well actually I think I'll do a test run install in a virtual environment so I can practice this first.

---

### Post by Hedgehog1 on 2011-02-27
> **NotSoheavyD said:**
> Thanks for the info. I'll give that a try. Well actually I think I'll do a test run install in a virtual environment so I can practice this first.

+1

I have found testing in a VMware or Vbox virutal machine to be a great tool for learning without hammering the main system.

I have 12 Vbox images (Ubuntu 32 and 64 bit, Dual boot Ubuntu with XP and Win 7, XP and Win7 straight, other Linux dustros).

I use Virtual Box, and have a 'before' save by exporting the machine as a virtual appliance.  That way I can put it back after I change it/screw it up.

:KS

---

