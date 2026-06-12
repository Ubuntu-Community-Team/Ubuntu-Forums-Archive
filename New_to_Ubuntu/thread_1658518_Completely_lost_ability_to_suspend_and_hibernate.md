---
title: "Completely lost ability to suspend and hibernate"
date: 2011-01-02
forum: New to Ubuntu
---

### Post by ruegore on 2011-01-02
I'm really at a loss at what happened and how to get it back.
Okay so I'm running Maverick 10.10 on my netbook and up until a little while ago, I did have suspend and hibernate working flawlessly. I've been using this computer for over a year.

Today I was trying to follow some guides on various topics, and I came across PowerTop. I installed and ran the program, selecting the helpful shortcuts to increase power savings, and sometime after that I went to restart my netbook and noticed in the Indicator Applet Session menu that "Suspend" and "Hibernate" are gone. Pressing the power button to bring up the shutdown menu lists only "Shut down" and "Restart" -- Suspend and Hibernate are gone! Alas, checking my Power Management options shows that there is no Suspend or Hibernate option for my list of actions on certain events. :(

Now the worse thing of all is that I followed a certain guide a long time ago that suggested mounting (or mapping?) /tmp, /var/tmp, and /var/log to tmpfs in the fstab file (in other words, those directories exist only in RAM, and disappear after every restart). As you can imagine, not only does this slightly break a few things (no more history in Ubuntu Software Center), but it also means I don't have any meaningful logs that can tell me what happened between now and a few hours ago (between restarts).

I've since restored the mount point of /var/log to my physical disk (and I'm gonna keep it that way).

Anyway, I have no idea how to bring Suspend and Hibernate back. I wonder if messing with PowerTop caused it to disappear? For those curious, my swap partition is 2x the size of my RAM, and it is working fine.

Can anyone please help me out?

---

### Post by ruegore on 2011-01-03
Fixed.

The problem seems to have been a direct cause of this bug: [Bug# 681488 in laptop-mode-tools (Ubuntu): "laptop-mode-tools deletes Suspend/Hibernate buttons from Indicator Applet Session"]("https://bugs.launchpad.net/ubuntu/+source/laptop-mode-tools/+bug/681488")

I'm not sure if enabling the suggestions in PowerTOP caused this.

Using Synaptic Package Manager, I found out laptop-mode-tools was installed and pm-utils was not. Installing pm-utils made laptop-mode-tools uninstall and after a restart, I had Suspend and Hibernate back. Tested and all was well again.

Bahh, all I wanted to do was save some power, and look at all the trouble I got! :lolflag:



edit: I was too excited to notice that the computer isn't going into the lock screen when coming back from Suspend or Hibernate. :-/ If anyone knows the solution to that, I'd really appreciate it.

last edit: Completely fixed. Had to install package gnome-screensaver. Locking now works where expected to. (I had previously removed gnome-screensaver because of xscreensaver, but that's another story.)

---

### Post by vacco on 2011-01-18
Thank you very much for taking the time to mark the thread as solved and submit a solution. I had the same problem (except I have not moved my directories around), and you really saved my day! :D

---

### Post by StickGrinder on 2011-07-03
I had the very same problem after trying powertop (not that much of an help actually) and your solution worked for me. :-)

Many thanks for sharing your knowledge!

---

