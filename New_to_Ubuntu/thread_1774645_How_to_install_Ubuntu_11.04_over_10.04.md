---
title: "How to install Ubuntu 11.04 over 10.04?"
date: 2011-06-03
forum: New to Ubuntu
---

### Post by jrozo17 on 2011-06-03
I'm getting kind of 'bored' you could say of 10.04, and I want to have 11.04 installed. I really don't want to upgrade because I've had numerous problems doing that. So pretty much I want to do a fresh install and get rid of 10.04... but the thing is I have Windows XP on my other partition.

So I guess this is a yes or no question... Is it possible overwriting 10.04 with 11.04 while still maintaining XP untouched? Or would I just have to look for alternatives such as Wubi? Thanks.

---

### Post by wolfen69 on 2011-06-03
Just choose your previous ubuntu installation and overwrite it.

---

### Post by jrozo17 on 2011-06-03
> **wolfen69 said:**
> Just choose your previous ubuntu installation and overwrite it.

Its as easy as that? I didnt know there was that option, I thought I would either have to make a 3rd partition or overwrite everything.

---

### Post by wolfen69 on 2011-06-03
> **jrozo17 said:**
> Its as easy as that? I didnt know there was that option, I thought I would either have to make a 3rd partition or overwrite everything.

Yes, it's that easy. If you are still unsure when you get to that part, post back.

---

### Post by jrozo17 on 2011-06-03
> **wolfen69 said:**
> Yes, it's that easy. If you are still unsure when you get to that part, post back.

Will do. Thanks :popcorn:

---

### Post by vivek.pandey on 2011-06-04
> **jrozo17 said:**
> I'm getting kind of 'bored' you could So pretty much I want to do a fresh install and get rid of 10.04... but the thing is I have Windows XP on my other partition.



surprised that you are not BORED of windows xp even though it was released much before 10,04 :-)

---

### Post by aravindsuhruth on 2011-06-04
i can't see the reason for not upgrading from 10.04...

For a fresh install, You can easily overwrite the existing ubuntu partition during the installation of 11.04... without touching XP.

---

### Post by fanosth on 2011-07-05
i've tested the 11.04 through the installation cd and i was thrilled by the graphics, so i want to over-write my ubuntu 10.04 partition(the other partition has windows XP, but as you have mentioned above, this is irrelevant).

my question is: if i simply upgrade my partition from 10.04 to 11.04(and how can i do this??), then all my files, cookies, bookmarks, updates etc, will be saved but if i over-write the partition then i will lose them?? (for example, i've managed to install microsoft office on my ubuntu after a long effort, what will happen to it in either case??)

and what would be better, to upgrade or to over-write??

thnx in advance!

---

### Post by dFlyer on 2011-07-05
I would recommend you back up your /home folder and go with a fresh install from the live cd over your old install.

---

### Post by oldfred on 2011-07-05
If you have a standard install, then everything is overwritten and you have a total clean install. Two choices, dual upgrade once to 10.10, then to 11.04. Some find upgrades work ok, others have issues with each upgrade. The other is to backup everything including all user settings & data in /home and make notes or backup any system settings you made in /etc (you do not restore the full file as new version may be different). You would also want to extract a list of installed apps to make it easy to reinstall all programs.

If you have a separate /home then you only need your system settings from /etc and the list of programs. I normally only do clean installs, do not need a image backup and my recovery plan is just another clean install. So my backup is intended to let me totally restore from a new install and backups.

Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
Oldfred's list of stuff to backup May 2011 - based on above script:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

If you have a separate /home and 20GB of space you can create another / (root) partition and install to that. Then you can still boot the old install until you get new install configured the way you want. I am now up to 5-20GB /. I am on 10.10, but have two old installs and Natty & Oneiric installed also.

---

### Post by fanosth on 2011-07-06
thanks a lot guys!!

---

