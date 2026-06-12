---
title: "I just instaled Unbnutu, my computeur is so slow! I can't use it..it is normal?"
date: 2009-12-07
forum: New to Ubuntu
---

### Post by Rambobino on 2009-12-07
Hi,
I'm really new on unbuntu. I've decided to try it because I was tired of windows. My computer was slow and I was hoping to improove a little bit with Unbuntu.
So I've instaled Unbuntu 9.10. Now it takes about 7 min to start, and it is so slow I can't open a new application or anything. I'm sure there is something wrong I've done.
My computer is an AMD Athlon XP1700+, 1.47GHz, 256MoRam
My computer is running ok with window XP SP3, but a bit slow.
What I have done, download the CD iso image of the last version of Ubuntu --> 9,10
Instal the programm so at startup I can choose Window or Unbuntu
Then now when I choose Ubuntu it is so slow I can take a nap between every mouse clic.
If I run window, everything is normal... a bit slow.
What I have done wrong?

Thank you for your support. 

Rambobino

---

### Post by The_Pirate_King on 2009-12-07
Do you know if you are installing WUBI or using a separate partition for Ubuntu? 

If you selected "Install Ubuntu as a program inside windows" when you were installing, you are using WUBI.
If you selected "Install Ubuntu permenantly alongside Windows", you have made a partition. 

WUBI is generally a lot slower, and since your system specs are very low [the processor looks fine but that is a very small amount of RAM] your Ubuntu system may run very slowly.  I would recommend creating a dedicated partition for Ubuntu if you want it to run faster.

---

### Post by Rambobino on 2009-12-07
Thank you for the answer,
I have installed Wubi. It is the reason why it is so slow. (and the amount of RAM)
I'will try to do the partition.

---

### Post by perlluver on 2009-12-07
You might want to try Xubuntu, or another lightweight Distro, like DSL, or Puppy.  Or try the LXDE Desktop.  With that amount of RAM, Ubuntu could be a problem, since the minimum recommended is 256MB.

---

### Post by diablo75 on 2009-12-07
Since you are running with 256MB of RAM you'll not get a very good experience.  Xubuntu uses the more lightweight desktop environment XFCE which doesn't require as much RAM, so you should try that instead of Ubuntu if upgrading your RAM is out of the question.

---

### Post by mikewhatever on 2009-12-07
Some good suggestions have been made to use a more light weight version, but the cause of the slowness is probably fragmentation of the Windows partition. Since you've used wubi to install Ubuntu inside Windows, high fragmentation if the Windows file system can severely cripple Ubuntu's performance. If you want to try wubi again, free up as much space as possible in Windows and defragment several time, before installing Ubuntu.

---

