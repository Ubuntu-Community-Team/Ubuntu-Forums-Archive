---
title: "[SOLVED] modprobe ndiswrapper causes events/0 to use 100% CPU"
date: 2008-04-22
forum: Networking &amp; Wireless
---

### Post by CrucifiedEgo on 2008-04-22
I just freshly installed the hardy RC on my sony VGN-NR260E.  I installed the driver for my atheros AR5BXB63 wireless card in my laptop using ndiswrapper -i <infname> and then sudo modprobe ndiswrapper.  when I do this, the system stops reponding for the most part.  Watching top when I do this, events/0 takes up 100% of the CPU.  Nothing in the logs indicates anything going on -- has anyone experienced this before?  This driver worked fine on a fresh install of 7.10 a month or so ago.  Thanks for any ideas you've got...

-J

---

### Post by Yiftos on 2008-04-22
> **CrucifiedEgo said:**
> I just freshly installed the hardy RC on my sony VGN-NR260E.  I installed the driver for my atheros AR5BXB63 wireless card in my laptop using ndiswrapper -i <infname> and then sudo modprobe ndiswrapper.  when I do this, the system stops reponding for the most part.  Watching top when I do this, events/0 takes up 100% of the CPU.  Nothing in the logs indicates anything going on -- has anyone experienced this before?  This driver worked fine on a fresh install of 7.10 a month or so ago.  Thanks for any ideas you've got...

-J

):P try ndiswrapper -im to create the module. then run modprobe -i to install the modules. This will make sure it is located in /etc. But before all this, please make sure that a linux native driver was not installed when you first enabled the wireless device. you can use lmod to list modules and search for it. If one does already exist, you will have to remove it with a modprobe -r 

hope this helps

---

### Post by CrucifiedEgo on 2008-11-26
Better late then never...

This ended up being caused by the native driver still being active.  I added it to the blacklist, and *poof* it worked.  

Also, to those who may be reading this in the future, I still have to use ndiswrapper on intrepid as the atheros madwifi drivers still don't work right with this laptop.

---

### Post by Chris1989 on 2008-11-26
hey guys, i am what you would call a major NOOB, i have a Compaq f700 presario, i originally installed ubuntu 8.10 on it, and it work ok, but i had to hold ctrl for it to boot up and shutdown, so i re-installed it which fixed this, i did a format for a fresh install, anyway, when i first installed it, i couldnt get the wireless card working, which is a Atheros ar242x, i looked through the forums and found something which worked, it told me to type in terminal something like, sudo get-apt ath5k, and the guy who posted it said that ubuntu has the drivers or something, but doesnt have them enabled by default, so i did that and it worked PERFECT, only problem is i cannot find the thread again, and ive been looking for weeks, and im about ready to give up on ubuntu/linux all together, i really dont want to use windows, please please please some one help me, thanks for reading

---

