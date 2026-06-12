---
title: "ubuntu black screen !!!!!!"
date: 2010-04-23
forum: New to Ubuntu
---

### Post by computerguts on 2010-04-23
I recently installed ubuntu 9.10 for about the tenth time, 
I have been having trouble booting ubuntu. Whenever I boot ubuntu it comes to the white ubuntu icon and then the screen hangs. What I used to do is change the boot on the grub menu but that option is no longer avliable since I reinstalled ubuntu. This is very frustrating what I have to do is do a hard shut down and reboot the system about three times for the system to boot and the user log in to appear. How can I fix this, this is a very annoying prolbem and it would be nice if I could fix it and just be able to turn on my computer and the user login to appear. 

Thanks

I meant to add that I am running ubuntu 9.10 on a dimension 2400 PC with and pentium 4 processor and 1.2 GB of ram

---

### Post by QIII on 2010-04-23
Did you do an md5sum check on the iso image?  Did you use the option to  "Check disk for errors" before you installed?  Have you run memtest?

Does a Live session work?
 
 Eliminate hardware as the source of the problem.
 
 Check/clean/reseat:
 
 Memory, peripheral cards, cabling.  

Your video is integrated Intel, so  you won't be able to do anything about that.  The problems with Intel video in Jaunty were pretty much solved in Karmic.
 
 Inspect thermal compound under CPU.

---

### Post by computerguts on 2010-04-23
I have done all of those things, I think it may be a software incompatibility error because my PC worked just fine with Jaunty. 

Maybe ubuntu 10.04 will solve this problem

the live session works great and I have already tried to eliminate any other problems that may be causing it listed above also I had ubuntu 9.10 installed eralier and it worked fine when I changed the boot option on the grub boot menu by pressing "e" to edit and then selecting intgid, (I don't think thats the correct spelling but it's close.) But now when I installed ubuntu I does not give me the option on the grub boot menu to change the boot selection. If I could fix this that could be a temporary fix to my problem, at least until the new version of ubuntu comes out.

---

### Post by QIII on 2010-04-23
If you can't get a good install of Karmic, remember that the RC for Lucid was released a couple of days ago.

If the LiveCD for Lucid works, it might save some frustration just to install the Lucid RC.  It'd sure be a pain to try over and over to install Karmic for 5 days until the final release of Lucid comes out -- and you'd probably want to install that anyway.

I've been using Lucid as my primary since the first Beta without any problems.

---

