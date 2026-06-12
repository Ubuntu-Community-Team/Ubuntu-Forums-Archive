---
title: "Messed something up during re-boot"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by radioactiveman69 on 2009-01-12
Hey guys and Gals,

I messed up for some reason and i rebooted.. now when I reboot, it goes to " grub> " and it wont boot up the GUI.

Any ideas?

Cheers

Ryan

---

### Post by Bölvaður on 2009-01-12
1. after changing config files, restarting will make your computer worse. You see... turning things on and off or closing and opening your eyes will not make anything better.

> 
I messed up for some reason and i rebooted..
Can you please state what you actually was doing?


Can you boot up from grub on a different kernel? (there are different kernel versions to pick from in GRUB (boot loader) where you can run ubuntu on older versions (that might work)).
IF you did nothing to mess up the system, then this could be because you need to install the video driver again (what video card do you have?) and you are able to boot up with the previous kernel with no problems.

---

### Post by radioactiveman69 on 2009-01-12
i removed open office and then my computer froze and then I restarted.

---

### Post by Bölvaður on 2009-01-12
Ok that sounds very abnormal, perhaps ctrl+alt+backspace would have been better than doing a hard restart.

Lets get more info on your system.

1.
[http://img150.imageshack.us/img150/1682/grub4kt.jpg]("http://img150.imageshack.us/img150/1682/grub4kt.jpg")
In this (GRUB) menu do you have more than 1 ubuntu? (note that recovery mode and memory test are not counted so this picture has only 1 kernel to boot ubuntu with)

2.
What graphical card do you have?

3.
Are you on a laptop or a board computer?

4.
Do you have any personal data or heavily modified system so you would not consider doing a reinstall?

---

### Post by radioactiveman69 on 2009-01-12
1.
[http://img150.imageshack.us/img150/1682/grub4kt.jpg](http://img150.imageshack.us/img150/1682/grub4kt.jpg)
In this (GRUB) menu do you have more than 1 ubuntu? (note that recovery mode and memory test are not counted so this picture has only 1 kernel to boot ubuntu with)

** I have only 1 verson of ubuntu installed with a dualboot with windows xp.. its grub4dos 0.4.4


2.
What graphical card do you have?

I have a laptop and i dont remember what the card is

3.
Are you on a laptop or a board computer?
I am on a laptop

4.
Do you have any personal data or heavily modified system so you would not consider doing a reinstall?

I dont have anything that isnt backed up.. im just curious why it would do this after I restarted.

---

### Post by radioactiveman69 on 2009-01-12
Is the only way to recover it formatting?

---

### Post by zzHanks on 2009-01-12
> **radioactiveman69 said:**
> I dont have anything that isnt backed up.. im just curious why it would do this after I restarted.
Sounds like a re-install to me.

It will probably save you some trouble.

---

### Post by Bölvaður on 2009-01-12
The fact is that you aren't really giving any information on anything at all. That in turn will make it impossible to know what the problem is and find out how to tackle it.

In my opinion it should be the next step for anyone that does not know how to solve the problem, to begin from the beginning (that is installing over the current installation).

It is extremely easy to overwrite the current installation. Just put the cd back in and follow the install wizard. When you come to partitions, do not auto partition the hard disk drive, but rather do it manually.
When you do the partitions you have to select the partitions used by the current installation by clicking them and "mount" as / (file system).
[http://news.softpedia.com/news/Installing-Ubuntu-8-04-LTS-84314.shtml]("http://news.softpedia.com/news/Installing-Ubuntu-8-04-LTS-84314.shtml") This webpage gives you an idea on what to do.


I urge you to read every post I have done in this thread and answer the questions to solve the problem. OR do a complete reinstall.

---

