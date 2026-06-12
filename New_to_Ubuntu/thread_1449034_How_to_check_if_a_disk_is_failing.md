---
title: "How to check if a disk is failing?"
date: 2010-04-07
forum: New to Ubuntu
---

### Post by Call My Function on 2010-04-07
I think one of my hard drives is failing. What can I run to check its integrity?

---

### Post by undecim on 2010-04-07
If you think it's failing, you should make a backup of everything first, then run some tests. The tests might end up being the last straw that finally makes the drive fail.

Also, have a look at [http://computer-drives-storage.suite101.com/article.cfm/seven_ways_to_tell_if_your_hard_drive_is_failing](http://computer-drives-storage.suite101.com/article.cfm/seven_ways_to_tell_if_your_hard_drive_is_failing)

---

### Post by philinux on 2010-04-07
> **Call My Function said:**
> I think one of my hard drives is failing. What can I run to check its integrity?

System>admin>disk utility. Click on the More Information link.

---

### Post by quadproc on 2010-04-07
> **Call My Function said:**
> I think one of my hard drives is failing. What can I run to check its integrity?
If it is a relatively new disk then it may have S.M.A.R.T capability.  This capability can be used to query the mini database inside the disk drive and see what it thinks about itself.  For more information, see [http://sourceforge.net/apps/trac/smartmontools/wiki](http://sourceforge.net/apps/trac/smartmontools/wiki)

Note that smartctl has been effectively disabled in Ubuntu 9.10 because when it is used on some USB flash disks it causes electrical damage to them.  That utility does exist and it works for conventional disks on 9.04.  I don't know what its status is on 10.04.

If you are observing unusual noises coming from the disk drive, unusual smells (such as hot plastic), or excessive temperature of the disk drive then chances are that it is in bad shape.

A failing disk can quit functioning altogether pretty quickly.

quadproc

---

### Post by philinux on 2010-04-07
Well I just fell foul of this bug. Oh well. Smart not available.

[https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/445852](https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/445852)

Installed gsmartcontrol from the repos. It needs a mod to its command properties. Replace su-to-root -X -c with gksu

gksu gsmartcontrol

Then it works.

---

### Post by Call My Function on 2010-04-07
The only reason I think my harddrive might be failing is because of the automatic disk checks Ubuntu does at startup on occasion. I keep seeing a message about something "failed". After this message briefly appears, Ubuntu loads normally (goes to login screen).

I find it odd, because I haven't noticed *any* problems with this computer. I don't get any suspicious errors. No missing files (that I've noticed). Doesn't run any slower than normal.

> **undecim said:**
> If you think it's failing, you should make a backup of everything first, then run some tests. The tests might end up being the last straw that finally makes the drive fail.

Also, have a look at [http://computer-drives-storage.suite101.com/article.cfm/seven_ways_to_tell_if_your_hard_drive_is_failing](http://computer-drives-storage.suite101.com/article.cfm/seven_ways_to_tell_if_your_hard_drive_is_failing)

I've noticed none of those signs, except for perhaps the sound they mention. During the checks that Ubuntu does, when it reaches the point where the "error" occurs, my computer briefly emits a sound that's hard to describe. I dunno if it's coming from some internal speaker or is my hard drive. But I've NEVER noticed this sound otherwise.

> System>admin>disk utility. Click on the More Information link.

Says all of my drives are healthy. I ran an extended self test on my storage drive, and it's fine. However, on my main drive (with the operating system), it seems to "skip" the test when I try it... it is an old drive, so maybe it can't check itself? I'm not familiar with hardware, so I dunno how these things "check" themselves.

> Well I just fell foul of this bug.

I can't quite understand what that bug is -- I know some things about computers, but not enough to understand what's written there.

And I repeat, I've noticed **NO** problems with this computer. It's only that error that worries me.

---

### Post by doas777 on 2010-04-07
> **Call My Function said:**
> The only reason I think my harddrive might be failing is because of the automatic disk checks Ubuntu does at startup on occasion. I keep seeing a message about something "failed". After this message briefly appears, Ubuntu loads normally (goes to login screen).

it sounds like you just have a file system problem, rather than a failing drive. you should be able to find the full message in system->log file viewer -> dmesg
then find out what partition is failing whatever it is failing, and post the message if you are unsure of what it is saying. a simple fsck from a live cd may fix the issue.

in that case, at the worst, you may have to backup your data, delete the offending partition, and recreate it.

---

### Post by quadproc on 2010-04-07
> **Call My Function said:**
> The only reason I think my harddrive might be failing is because of the automatic disk checks Ubuntu does at startup on occasion.Are you referring to the occasional _fsck_?  I think that this check defaults to every 37 startups, or something close to that.  If this is what you mean then whatever "failed" is indicative of a problem in the file system, probably not the hardware.  Corruption in the file system would concern me, a lot.   Are you using ext4?
> 
I've noticed none of those signs, except for perhaps the sound they mention. During the checks that Ubuntu does, when it reaches the point where the "error" occurs, my computer briefly emits a sound that's hard to describe. I dunno if it's coming from some internal speaker or is my hard drive. But I've NEVER noticed this sound otherwise.Could you describe it as a tone, or a noise such as you hear between radio stations while tuning, or something else?  Knowing this might help to identify the cause.
> Says all of my drives are healthy. I ran an extended self test on my storage drive, and it's fine.I would like to offer a caution here: modern disk drives are designed for intermittent duty.  Subjecting them to intense usage can overheat them and that will shorten their life time substantially.  The kinds of disks that were used on mainframe computers were a "horse of a diffferent breed" - they were intended to be continuously in use, and they cost a LOT more than what we can buy these days.  You typically would not have to worry about overusing those disks, but the typical PC disk these days is rather light duty.

quadproc

---

### Post by tgalati4 on 2010-04-07
Open a terminal:

dmesg | more   (spacebar to page forward, q to quit)

Look for failed messages.

Or simpler:

dmesg | grep fail

and

dmesg | grep error

and

dmesg | grep Error

---

### Post by Call My Function on 2010-04-08
> **tgalati4 said:**
> Open a terminal:
...
dmesg | grep fail
Only that command displayed anything:
[PHP][    0.972087] PM: Resume from disk failed.
[    2.552681] [drm] failed to find VBIOS tables
[    4.886618] PM: Resume from disk failed.
[/PHP]What does that mean?

---

### Post by tgalati4 on 2010-04-08
PM is the power manager.  Resume from disk failed because the kernel didn't find a hibernation file.  That's normal.  If it found a hibernation file, then it would load that instead of doing a full boot.

What is the output of:

sudo fdisk -l

---

### Post by Call My Function on 2010-04-08
> **quadproc said:**
> Are you referring to the occasional _fsck_?
I suppose that's it. I have no idea.

> If this is what you mean then whatever "failed" is indicative of a problem in the file system, probably not the hardware.  Corruption in the file system would concern me, a lot.   Are you using ext4?
In the Disk Utility, it says my filesystem is Ext3, v1.0. That's how Ubuntu set it up when I installed it -- I haven't fussed with any of the partitions except for the one on my second, storage drive. But my storage drive isn't the one with the problem.

> Could you describe it as a tone, or a noise such as you hear between radio stations while tuning, or something else?
I need to listen to it again so I can describe it more precisely, but it only occurs when "fsck" runs and it hits that "error" section. So I'll have to wait until it runs again, unless there's a way I can command it to run.

> I would like to offer a caution here: modern disk drives are designed for intermittent duty.  Subjecting them to intense usage can overheat them and that will shorten their life time substantially.
How modern are we talking? I don't recall exactly, but I'm very sure I've had this computer since at *least* 2003, and the same harddrive has served me fine all this time. In fact, this computer has been very reliable in general, aside from the fact that it can't run much newer programs. (Doesn't have the "horsepower".)

And could you better define "intense usage"? I don't keep my computer on constantly (it's not a server or anything), but I do use it a lot.

---

### Post by Call My Function on 2010-04-08
> **tgalati4 said:**
> What is the output of:

sudo fdisk -l

[PHP]Disk /dev/sda: 80.1 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0ba00b9f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9457    75963321   83  Linux
/dev/sda2            9458        9733     2216970    5  Extended
/dev/sda5            9458        9733     2216938+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0bf70bf6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321    7  HPFS/NTFS

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8900690

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001    7  HPFS/NTFS
[/PHP]sda is the one in question. sdb is my second, storage drive, and sdc is my external. Those are fine.

---

### Post by tgalati4 on 2010-04-09
Backup your data on that drive.

sudo badblocks /dev/sda

---

### Post by mikewhatever on 2010-04-09
'Resume from disk failed' means there is no resume image, and has nothing to do with a physical hardware failure.
You could try looking at /var/log/fsck/checkfs, apparently mine is an empty file.
```
cat /var/log/fsck/checkfs
```

---

### Post by mvalviar on 2010-04-09
> **philinux said:**
> System>admin>disk utility. Click on the More Information link.

I like this one.

---

### Post by quadproc on 2010-04-09
> **Call My Function said:**
>  [re: my question about fsck]I suppose that's it. I have no idea.

In the Disk Utility, it says my filesystem is Ext3, v1.0. That's how Ubuntu set it up when I installed it -- I haven't fussed with any of the partitions except for the one on my second, storage drive.OK, that should be good.  The ext4 filesystem was known to occasionally corrupt a disk.>  But my storage drive isn't the one with the problem.


I need to listen to it again so I can describe it more precisely, but it only occurs when "fsck" runs and it hits that "error" section. So I'll have to wait until it runs again, unless there's a way I can command it to run.That can be done but it may require running off of a different medium for the test - I think that you indicated that your operating system is on the disk in question.  If that is the case then you can't unmount that disk to check it; instead, you could run from a Live CD to do the fsck on the drive of interest.  You probably want the -n option which should simply look for problems but does not try to fix them.> 

How modern are we talking? I don't recall exactly, but I'm very sure I've had this computer since at *least* 2003, and the same harddrive has served me fine all this time. In fact, this computer has been very reliable in general, aside from the fact that it can't run much newer programs. (Doesn't have the "horsepower".)Unfortunately there isn't a simple answer to this question.  It is a matter of degree.  As time has passed, manufacturers have found ways to make drives less expensive to produce but at the same time, the drives have shorter lifetimes.  I think that drives made in 2010 typically have a life of about 2-3 years **if** they were handled gently during shipping.  More on this below.> 

And could you better define "intense usage"? I don't keep my computer on constantly (it's not a server or anything), but I do use it a lot.Again, this is  hard thing to answer because it depends on very many factors.  A disk just sitting there without doing any seeks, reads, or writes and running in a reasonably cool environment (say 25 degrees) will experience some wear in the motor and bearings but generally will have an easy life.  On the other hand, if you executed a loop like this: WHILE TRUE DO cp * >/dev/nul then you would be using that disk full time as fast as it can read and this would put a lot of wear and tear on its mechanical parts.  (Please note that you cannot execute the statements that I wrote; I do not want anyone to damage their disk with code from me!   I am just illustrating what could be done if someone were to try.)  Also, higher temperatures dramatically shorten the life of disk drives.  I would bet that high humidity is also a factor but I do not have any data on that subject.

One tidbit that I found on the Internet is that disk drives shipped by UPS usually fail in less than a year, while those shipped by Fedex last several years.  And my personal experience is similar: UPS has been very hard on the packages that I have received from them.  I try to get my vendors to use Fedex.  They seem to be much gentler.

Sorry that I can't give you numerical answers for lifetime questions - there are just too many variables, and many of them depend on data which you cannot obtain (such as the activation energy level of the potential defects in the ICs of the disk drive).  But I can give general answers; perhaps a simple summary would be that if the price of a disk was painfully high when it was new then it will probably last a long time.

quadproc

---

### Post by norm7446 on 2010-04-10
Come on, quadproc shame on you ( 5 Cups of Ubuntu ). Did it never occur to you to run the Hard drive manufactures own test software on the drive. Now I know that a lot of the manufacture's software are windows only, but the Ultimate Boot Disc contains most if not all known Hard Drive manufactures test software you will ever need to test the drive in question properly. As this is how the manufacturer would test the drive if you sent it to them as a faulty unit.

You can download it from the below link if you do not already have it.

[http://www.ultimatebootcd.com](http://www.ultimatebootcd.com)

You could also try Hirens BootCD and run PC CHECK. This will also give your H/drive a good test to see if it is failing or not.

[http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd)

At the end of the day, always make sure you have a back-up of all your files, as Hard Drives do fail. Mostly when you do not expect them to. Who else can remember the old DeskStar aka the DeathStar disc's of old.

---

