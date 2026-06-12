---
title: "what should you do if computer freezes?"
date: 2009-09-29
forum: New to Ubuntu
---

### Post by zhanglini on 2009-09-29
I normally would just turn off the computer with "Power" button.  But some people here say that it would screw up the harddrive.
So is there a better way?

---

### Post by doas777 on 2009-09-29
check this out:
[http://kember.net/articles/231/reisub-the-gentle-linux-restart](http://kember.net/articles/231/reisub-the-gentle-linux-restart)

hold Alt + PrntScrn, and enter these letters while holding:
reisub

---

### Post by Aquilastudio.com on 2009-09-29
It is always better to turn off your comp using the menu. Shutting of your computer like that could cause the hard drive reader( which levitates above the disk) to crash on to the hard drive and create scratches. The other hardware could get messed up too.

Sorry misread the question. You should use System rescue keys. Look them up on google.

---

### Post by grturner on 2009-09-29
while there is a chance that it could screw up your hard drive, with modern journaling hard drives. the chance is minute. when linux used the ext2fs, the chance was much higher that you would have data loss. in fact if the filesystem wasnt unmounted properly, upon mounting it again it would force a filesystem check.

---

### Post by doas777 on 2009-09-29
> **grturner said:**
> while there is a chance that it could screw up your hard drive, with modern journaling hard drives. the chance is minute. when linux used the ext2fs, the chance was much higher that you would have data loss. in fact if the filesystem wasnt unmounted properly, upon mounting it again it would force a filesystem check.


it is my understanding that ubuntu disables journaling on ext3/4 by default.

---

### Post by admelfo on 2009-09-29
Good time to take a walk.  ;)

---

### Post by flux_user on 2009-09-29
doas777 is correct; you use the magic print screen.

[http://en.wikipedia.org/wiki/Reisub](http://en.wikipedia.org/wiki/Reisub)

Wikipedia has a nice write up about it.  It will safely take your system down.

---

### Post by ankspo71 on 2009-09-29
This is why I like having a reset button on my pc. It quickly reboots the pc without cutting power to the hard drive (as far as I can tell) so I think it's safe. My method will cause any OS to not save session changes though, which could mean I loose changes to a document or whatever I was working on. After it reboots, I can then shut down normally. A few months ago I turned off my pc and went to bed. The next morning I woke up to a pc that was stuck still trying to shutdown lol. I'm glad it didn't hurt my pc. From now on I'm waiting until it's completely shut down.

---

### Post by bigboy_pdb on 2009-09-29
If my desktop freezes, I usually switch to another terminal (by holding CTRL+ALT then pressing F1, F2, ..., or F6) and then kill the process that's causing the problem from the command line (and then use CTRL+ALT F7 to get back).

Also, holding CTRL+ALT and then pressing Backspace restarts the X-server (although that may be disabled in current versions of Ubuntu, but I'm not going to check right now since doing this closes all of your windows and logs you out).

If the system is frozen so that I cannot do either of these and waiting doesn't seem to help then I usually press the reset button.

---

### Post by inobe on 2009-09-29
i make sure their is sufficient memory and each memory module is working...

if something is freezing you have severe hardware issues anything from power supply to heat related.

as a computer user you must assume responsibility for any maintenance needed.


memory is a most common issue that can be easily remedied by testing one ram module at a time to find which of them are bad.

another common problem is lack of memory resources especially if the system has 256mb of ram.

heat can contribute to this behaviour as well, it doesn't take long for a cpu heatsink getting packed with debris in which cpu temps can exceed threshold temperatures, these high temps can permanently damage the cpu.

the power supply itself can be full of debris causing heat and failing to a point where the system board isn't getting enough power' or it's simply on it's way out.....

these issues are rarely software related, in fact' the most common software issue's are drivers, poorly coded proprietary drivers like ati's or nvidia's were known "in the past" to do this on other platforms, these drivers cause gpu temps to climb then causing lock ups and freezes.


note: backing up your important information is probably the most important part of computer maintenance.

---

### Post by zhanglini on 2009-09-29
Thank you guys for the answers --- you learn something everyday!
I never noticed that "Sys Rq" key until today, lol.

---

### Post by skillllllz on 2009-09-29
> **doas777 said:**
> it is my understanding that ubuntu disables journaling on ext3/4 by default.


This is not true. In fact with ext4, it now checksum's the journal, which helps prevent a bad situation from becoming worse if the journal were to become corrupted too.

---

### Post by Garyhans on 2009-09-29
I'm a big fan of Alt Sys Request REISUB type slowly.. works for me.. although I have a rare freeze.

---

### Post by cmcanulty on 2009-09-29
If you go to System-Prefs-Power Management-general you can set shutdown by pushing power button. Makes it easier to turn off, and if it freezes the power button is a safe way to shut down if you set it up that way

---

