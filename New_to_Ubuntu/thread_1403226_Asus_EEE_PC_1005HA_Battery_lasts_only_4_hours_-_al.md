---
title: "Asus EEE PC 1005HA Battery lasts only 4 hours - also, hard drive partition issue"
date: 2010-02-10
forum: New to Ubuntu
---

### Post by candlepop on 2010-02-10
I am very new to Ubuntu/Linux.  I've been living in Uganda the last few months and my windows-running Asus EEE PC 1005HA got hit be a virus on two separate occasions, completely wiping it out.  So, I got fed up and switched to Ubuntu Netbook Remix 9.10.  But, while running windows (through Asus's super hybrd engine), I really was able to reach about 8-8.5 hours of battery life.  On Ubuntu, I can't come close to that.  I am averaging 4 hours of battery life.  

I tried searching the forums but couldn't find any good ideas on how to solve this problem.

On a separate note, the guy who installed my ubuntu set it up as a dual boot so that it still has windows on it if I ever need to access windows.  I am ok with that except that my 160gb hard drive is split 50-50 between windows and ubuntu and now my ubuntu hard drive is almost fully while the 79gb file system (that is what it is called in my files) is for windows (I think) and it has 60 available gb on it, but I can't access them.  I tried pasting some pics into that 79gb file to open up some space for other stuff on my ubuntu hard drive, but after doing that I couldn't access them from ubuntu (if I tried to open the pics in ubuntu, i got an error).  Does anyone have a suggestion on how I can either use that 79gb drive in ubuntu or partition the hard drive differently so that I get 130 or 140gb for ubuntu and the rest for windows? 

Thanks so much.  (Hope this all makes sense and that I didn't write too much - new to all this stuff!)

---

### Post by goseph on 2010-05-27
BUMP on the battery life stuff.

also try booting from a live CD and running a program called gparted to resize your partitions.

---

### Post by lidex on 2010-05-27
See this thread:
[http://ubuntuforums.org/showthread.php?p=9371680#post9371680]("http://ubuntuforums.org/showthread.php?p=9371680#post9371680")

---

### Post by the-edmeister on 2010-05-28
candlepop, 

Ubuntu shouldn't have filled a 79GB partition.

Open the Terminal and run this command to see your actual disk usage.
> df -h

I have an older eeePC 900 with  4GB and 20GB SSD's (solid state drives), and I have just filled the 4GB drive after installing Ubuntu 10.04 (the EasyPeasy netbook version) and doing 3 weekly updates of 10.04. I now have to figure out why the Ubuntu installation didn't use the entire 20GB, as the original Xandros installation did.
As far as the size or the Windows parttion, IMO 30MB is the minimum size to shoot for.

---

