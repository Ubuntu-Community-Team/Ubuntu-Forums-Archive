---
title: "Black screen on switching on power !!"
date: 2011-03-08
forum: New to Ubuntu
---

### Post by neewbi on 2011-03-08
I have ubuntu 10.04 and windows 7 dual boot with separate partition for ubuntu..my windows 7 was preinstalled in my samsung laptop..A few weeks ago i installed ubuntu on a separate partition disk..Yesterday, i checked the samsung recovery drive and made no changes to it..Then i restarted my system and all of a sudden, none of the operating system is booting!!! All i see is a blank black screen with the cursor at the top most corner...And after a few seconds commas and weird symbols come up!! PLS HELP!!!

---

### Post by Daveth on 2011-03-08
explain a little more around the "checked the samsung recovery drive" comment- did you "launch" it? I'm wondering whether windows has thrown a dizzy fit and messed up grub, leaving the poor pc floundering around looking for a boot regime.

---

### Post by neewbi on 2011-03-09
Hey daveth, Thanks for ur reply :)..i did launch that recovery drive which was coming up in the grub as a windows vista drive..It took me to the samsung recovery drive mode were in i was provided with 3 options to back up my files, and 2 more options which i dont remember!! As i wasnt interested in any of the options,i just restarted my computer and from den on the same problem is persisting!!! Pls help!!

---

### Post by neewbi on 2011-03-09
Guys i want to get this thing sorted as fast as possible...can any1 help me out with this!!

---

### Post by fabricator4 on 2011-03-09
> **neewbi said:**
> Guys i want to get this thing sorted as fast as possible...can any1 help me out with this!!

It seems that when you booted the Windows recovery it re-wrote your MBR (where grub lives) without asking, or even telling you what it was doing.

Try the instructions in [the grub2 guide]("http://ubuntuforums.org/showthread.php?t=1195275") to get your grub back. See section 13

Chris

---

### Post by wep940 on 2011-03-09
I'm not sure what happened - I would have thought that if it had overwritten the mbr that you would at least be able to boot Windows.   Perhaps the timing in the recovery mode is to first write out a "nonsense" mbr thinking that there will be nothing bootable until the recovery is complete.  Therefore, I agree with fabricator4 - you need to recover grub2.
 
Please also remember the forum rules/suggestions - don't bump your post up before 24 hours after your last attempt.  Since this is all voluntary, sometimes you just have to wait for help.  While I feel your pain for your particular problem - not being able to boot to anything on your PC - understand that others also feel their problems are extremely important as well.  Things get handled here as best as can be, so I wish you only the best!

---

### Post by neewbi on 2011-03-10
Thanks for your replay

As i Restarted the Grub using the Ubuntu Live CD and i have applied sudo  fdisk -l and some other commands , then i got my problem solved.

-----Thank You-------

---

### Post by wep940 on 2011-03-10
Glad you got it working!  Good job!

---

