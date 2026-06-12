---
title: "Somethings happening with my PC-FSCK,No Gome desktop, Routine check of drives. HELP!!"
date: 2010-01-12
forum: New to Ubuntu
---

### Post by suomalainen on 2010-01-12
Ubunteros,

I've been running Linux-Ubuntu since November of 2007. I use 8.04LTS. Until today, I have never experienced any sort of MAJOR problem with Ubuntu. Now I may have an issue. You will soon tell me.

Here is what's going on:

1. Booted up computer normally. Everything appeared normal. Entered password & user name and waited for desktop to appear.

2. Desktop did not appear. An error message popped up stating that gnome desktop could not load.

3. With this info I decided to re-boot my PC.

4. When I rebooted my PC I got an error message that GRUB was loading and then it was followed by Error 18

5. I had to re-boot my machine about 5 times until this error 18 message finally went away. However, things got a little wierd?? Although, I finally did not reveive the error 18 msg on the 6th go around the PC went into some sort of self diagonisc mode. Just a black backgound with scrolling white text appeared before me.

6. When this "self-diagonstic" test finished it stated something to the effect that I could run a fsck but when I tried that didn't do anything.

7. So I rebooted my PC and then Ubuntu went into a "Routine Check of drives: /dev/sda1..." mode. This seems to run REAL slow as I'm on 10% for last five minutes.

8. I tried to by pass the Routine Check by hitting ESC but after I enter my password and user name the system seems to just hang.

I'm not too sure what to think or what is going on. Maybe after this ROUTINE CHECK OF DRIVES finished I'll be back up and running???

In any case, I looked up some info and I'm hoping I don't have a harddrive propblem. I have a 500GB Seagate that is only 2 years onld.

Any ideas as to what I may be experiencing most appreciated.

Thank You!!!!

---

### Post by adam814 on 2010-01-12
The routine check of drives is an fsck.  It might take a while with a 500GB drive, especially if you're using ext3.

That's my first guess, if you're getting far enough that ubuntu is doing that there's not an issue with GRUB or your kernel per se.  It should be able to fix any simple filesystem issues.

---

### Post by suomalainen on 2010-01-12
Golly, I hope Your right! I'm at 19% complete so you can see how long this is taking.

---

### Post by adam814 on 2010-01-12
Yeah, that's one of the reasons I never liked ext3 (even though it's more stable than what I end up using otherwise).  For the longest time I used reiserfs, but after experiencing a lot of fragmentation and a filesystem corruption issue I switched to ext4 which (fingers crossed) hasn't caused me the problems it has for some.

---

### Post by suomalainen on 2010-01-12
"Routine Check of drives: /dev/sda1..." mode was at 19% and then the following error below appeared. This is the very same message I noted in item # 5 above.

DO I HAVE A SERIOUS PROBLEM??????

Checking drive /dev/sda1: 19% (stage 1/5, 1024/3638)
Error reading block 33554683 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.

/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
(i.e., without -a or -p options)
fsck died with exit status 4

[fail]

* An automatic file system check (FSCK) of the root filesystem failed. A manual fsck must be performed, then the system restarted. The fsck should be performed in maintenance mode with the root filesystem mounted in read-only mode.

* The root filesystem is currently mounted in read-only mode.
A maintenance shell will now be started.
After performing  system maintenance, press CONTROL-D to terminate the maintenance shell and restart the system.
bash: nojob control in this shell
bash: groups: command not found
bash: lesspipe: command not found
bash: Command: command not found
bash: The: command not found
bash: dircolors: command not found
bash: Command: command not found
bash: The: command not found
root@jukka-desktop:~#

---

### Post by ajgreeny on 2010-01-12
Boot to the ubuntu live CD, make sure no hard disks are mounted and run ```
sudo fsck /dev/sda1
```in terminal.  That may do the job, but it may still be quite slow, so don't worry about that at the moment.

I hope this does the job for you!  Good luck.

---

### Post by suomalainen on 2010-01-12
ajgreeny or anyone else,

I typed "fsck" after "root@jukka-desktop:~# " as described in post #5. It appears that some sort of "Check" is being performed as we speak. Would this be the same as Booting from the ubuntu live CD????

It sure looks like this check is gonna take some time.

I'd also like to point out that another error message came up:

Checking drive /dev/sda1: 89% (stage 1/5, 1024/363
Error reading block 654094 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.

/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
(i.e., without -a or -p options)
fsck died with exit status 4

[fail]

* An automatic file system check (FSCK) of the root filesystem failed. A manual fsck must be performed, then the system restarted. The fsck should be performed in maintenance mode with the root filesystem mounted in read-only mode.

* The root filesystem is currently mounted in read-only mode.
A maintenance shell will now be started.
After performing system maintenance, press CONTROL-D to terminate the maintenance shell and restart the system.
bash: nojob control in this shell
bash: groups: command not found
bash: lesspipe: command not found
bash: Command: command not found
bash: The: command not found
bash: dircolors: command not found
bash: Command: command not found
bash: The: command not found
root@jukka-desktop:~# 

AND perhaps because i got to 89% this allowed me to run the fsck command????

Anyway, if anyone has any ideas what's going on I'd sure like to know....

Thank you

---

### Post by adam814 on 2010-01-12
Did you have a power outage or hard-reset the machine before it happened?  It's kind of a cryptic message, but I've gotten similar ones when things like that have happened before.  Hopefully a manual fsck fixes it.

---

### Post by suomalainen on 2010-01-13
After alot of rebooting and going as far as Routine disk check would go, everything seemed to get to a point that FSCK could be run.

After that Ubuntu 8.04 booted up normally and everything appears ok now....

But talk about a hipcup!!! Wow..  This was an eye opener... But is Ubuntu really this good? I mean can it really take care of itself and turn a bad situation into good? That's what it feels like to me.....

But on the other hand I'm wondering what really was going on? I guess we can rule out a hard drive failure but is there anything else????

---

### Post by adam814 on 2010-01-13
It will almost always return the filesystem to a consistent state.  It may not always get your data back, so you might want to check that anything important is still there.

The usual cause for that is failure to sync the disks before powering off.  Or it could be caused by a single bad sector in the wrong place.  It would just be reassigned on a write, but if it was the ext3 superblock for example it wouldn't be mountable until an fsck re-wrote it.

---

### Post by suomalainen on 2010-01-13
Adam814,

Can you clarify your definition of

> you might want to check that anything important is still there.


Thanks!

---

### Post by adam814 on 2010-01-13
I simply mean if there's anything you consider important you might want to make sure it's still there rather than look for it later and not find it. Any time you have that much of a filesystem issue there is the potential for data loss.

---

### Post by suomalainen on 2010-01-13
Adam814,

My Ubuntu o/s is on a 500GB hard drive. Any files I work with, create, maintain or want are stored on another 500GB hard drive.

I guess I might be safe since my important files are on a separate drive.

Or what do you think? Could this issue have effected both drives?

---

### Post by oldos2er on 2010-01-13
Sooner or later, all PC or laptop hardware will fail; it's just a fact of life. It's always best to be prepared (backup, backup, backup!)

---

### Post by suomalainen on 2010-01-13
Not sure how that answers my question??????????????????

---

### Post by Sef on 2010-01-13
[From the GRUB Manual - GRUB error 18]("http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2-errors"):

>  Selected cylinder exceeds maximum supported by BIOSThis error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general).       

---

### Post by suomalainen on 2010-01-13
ok. And what is this suppose to mean to me??? In my case it only appeared once and then disappeared after fsck was manually run.

Now I'm back up and running and everything appears ok.

Do you mean something is lurking in the background?

I need more information as to what you mean exactly pertains to the issue I was in?

Also my HDD is way over 8GB. See attachment. If something was gonna happen it should have happened 2 years ago when I build the machine. Besides, who builds a system on 8 GB these days anyway????

Thanks alot

---

### Post by oldos2er on 2010-01-13
> **suomalainen said:**
> Not sure how that answers my question??????????????????

No, it was just an observation. If you expect things to fail and act accordingly, you won't be surprised or caught off guard when they do.

---

### Post by lavinog on 2010-01-13
1: Always have a backup solution, because harddrives don't live forever, and are likely to fail without warning.

2: Inconsistancies can happen if the computer is turned off, or locks up before files can be syncronized.  If you saved a file within 5 mins of the system locking up, you should see if that file is still available.

3:  Sometimes it is better to split up your drive into partitions.  Keep your home folder seperate from your system files...generally ubuntu won't need more than 20g of space for the system files.  This way when fsck needs to check the system partition, it only needs to check a 20g partition instead of a 500g partition.  I take this one step further and make another partition for storing files like pictures videos, and music.  They are files that don't change often, and have a different fsck schedule than everything else.

4: see #1 again.

---

### Post by adam814 on 2010-01-13
Yeah, you should be fine.  If the other drive was affected you'd have had to manually fsck it too.

---

