---
title: "Yet another &quot;Checking battery state&quot; error"
date: 2010-05-19
forum: New to Ubuntu
---

### Post by Squatting Monk on 2010-05-19
Hey there, folks. I'm quite new to Ubuntu and to Linux in general, so this problem has me totally stumped. I've used Google and the forum search in an attempt to solve this myself, but have not had any luck with the solutions given.

I installed Ubuntu 10.04 LTS on an old Dell Dimension 2400 desktop (ancient, I know, but I can't afford anything better right now). I can boot up and log in just fine, but when I go to do just about anything, it crashes to a black screen that reads "Checking battery state". It sits there for a second or two, then starts flashing multicolored bars. At that point, all I can do is punch the power button and boot back up again.

I've read that this is a problem with X crashing, and that it supposedly has something to do with video drivers. This box has an old integrated Intel chip, so none of the Nvidia fixes I've found apply. I found one thread that talked about going to the software center and downloading the Intel i915 drivers. Unfortunately, every time I try to open the software center, the crash gets triggered.

Any ideas?

---

### Post by -humanaut- on 2010-05-20
Alright, when you get too the login in screen hit ctrl+alt+f1 and login via TTY1 and type sudo init3 

This will kill X then type sudo apt-get update && sudo apt-get upgrade 

Upgrade the system then type: sudo apt-get install xserver-xorg-video-intel

then sudo init5 && exit

Login and see if that helps.

---

### Post by Squatting Monk on 2010-05-21
Hmm... it didn't seem to have any effect. I did notice that it told me it did not update, add, or remove any packages. However, it did tell me that there were some unneeded headers that could be removed using sudo autoremove. When I tried doing that it told me I couldn't because I wasn't root. :confused:

---

### Post by -humanaut- on 2010-05-21
When you tried to install the video driver it didn't tell you it was up to date? or already installed or anything? I'm not really sure where the underlying problem is can you install or boot to any other version of Ubuntu? Also have you added any new hardware such as RAM recently I had a stick of ram that refused to work with my Motherboard and would not boot Ubuntu what so ever.

---

### Post by Squatting Monk on 2010-05-21
It said it was already the latest version. I retried the steps and got the same thing, but this time I got a lot of "too much work for irq17" errors interspersed with everything. Could that have anything to do with the problem, or would that be a separate issue. (Total n00b at this sort of thing.)

I haven't updated any hardware on the computer. I was just looking for a cheap Windows box I could test things out on. I had previously installed gNewSense (on accident; I thought I was installing Debian) and problems with xorg wouldn't let me boot up at all. I can try using a different version of Ubuntu, but I wanted to see if maybe it was a configuration or driver problem before I went back to square one again.

---

### Post by subramanyamn on 2010-06-08
Same thing happens on my Compaq Presario V2000. Intel Centrino M 1.6, 1.2GB DDR. The screen goes blank, says 'Checking battery state [OK]' and keeps flashing till I hold down the power button. No matter what application I use, it just crashes and I've more than once ended losing unsaved data. 
Any help would be greatly appreciated! Thanks.

---

### Post by e.m.fields on 2010-09-06
Same bug here. Maverick 10.10 Alpha 3. Please post if you get a solution.

---

### Post by devanalias on 2010-11-20
check that xinit works

---

