---
title: "Reinstalling XP, retaining dual boot (Intrepid)"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by Darkoan on 2009-03-01
Hi, newbie here

I recently purchased a new computer, naked, and installed XP (NTFS partition)and then Ubuntu (ext3) on a single hard disk. I also left a large part of the hard disk unpartitioned.

The XP I 'acquired' was a little dodgy to say the least, and I would like to reinstall a clean version of XP (i now have a clean XP boot disc). As Ive installed quite a few things on Ubuntu I would like to keep the Ubuntu installation.


My plan is to use Gparted to 'wipe' the current Windows NTFS and then reinstall XP.

Is this the right way to go about it? When I boot the XP cd, will it find the NTFS partition and install on that? I was of the understanding that it looks only for unpartitioned space (but then I know little).

---

### Post by presence1960 on 2009-03-01
I had my dual boot set up on separate hard disks. I may be wrong, but I believe when you install windows on the same physical disk after Linux Windows will wipe GRUB. All you need to do after Windows is installed is pop in the Ubuntu Live CD, open a terminal and follow these instructions to put GRUB back :

> 1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Go SuperUser (that is, type "sudo -s"). Enter root passwords as 
necessary.
4. Type "grub"
5. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
Use whatever your computer spits out for the following lines.
6. Type "root (hd0,1)", or whatever your hard disk + boot partition 
numbers are for Ubuntu.
7. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
whatever your hard disk + partition nr is, to install GRUB to a 
partition.
8. Quit grub by typing "quit".
9. Reboot and remove the bootable CD.

---

### Post by JoshuaRL on 2009-03-01
If you change that XP install to a blank NTFS partition, it should work just fine.  But you'll have a problem with GRUB.  Windows rewrites its MBR and wipes out GRUB.  You'll need to reinstall it, but there are a lot of HOWTOs to assist you with that.  For instance:

[http://ubuntuforums.org/showthread.php?t=358183&highlight=windows](http://ubuntuforums.org/showthread.php?t=358183&highlight=windows)

---

### Post by handy on 2009-03-01
The following link may contain helpful info' also:

*_[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)_*

---

### Post by Darkoan on 2009-03-02
Thank you all for replying so promptly.
Unfortunately the problem has evolved, mutated like a bad MS virus.

The above procedure does not work because when i load the Ubunto cd and do 'grub> find  etc", it comes up with an error 15. Tried different "find"  and there is still an error. Then using Gparted discovered the partitions that are associated with my Ubuntu are not there! (As if formatted - the NTFS Windows partition is there, but it seems the setup of Windows has mucked around with Ubuntu)

So, I reinstalled Ubuntu - no dramas, Ubuntu loaded fine, as did Grub. But then when I boot Windows, it loads up until the usual 'scrolling bar loading' XP screen and then 'BLUE SCREEN OF DEATH'! Upon booting XP in safe mode, it starts loading all the drivers and stops at MUP.sys and then again a BLUE SCREEN OF DEATH.

The mup.sys problem has plagued Windows users for a long while, and I have read many blogs on them, but solutions are arduous and inconsistent. And none I found address my specific issue - dual linux/windows booting.

After this issue I told myself fine, Ill reinstall Windows - did that and Windows worked fine, but then same issue as above - couldnt find Ubuntu/ Grub. 
so then I reinstalled Ubuntu (are we getting bored yet) and again Ubuntu works fine but XP gives my BSDeath, and thats where Im at now.

In summary, it appears installing Windows XP upsets preexisting Ubuntu, and installing Ubuntu upsets my preexisting Windows. But each works fine by themselves.

Apologies for the long post and the fact thats its a Windows issue but your help is very much appreciated.


AMD 5400 
ATI 4850
4gb ram
470W

---

### Post by Darkoan on 2009-03-02
Thank you all for replying so promptly.
Unfortunately the problem has evolved, mutated like a bad MS virus.

The above procedure does not work because when i load the Ubunto cd and do 'grub> find  etc", it comes up with an error 15. Tried different "find"  and there is still an error. Then using Gparted discovered the partitions that are associated with my Ubuntu are not there! (As if formatted - the NTFS Windows partition is there, but it seems the setup of Windows has mucked around with Ubuntu)

So, I reinstalled Ubuntu - no dramas, Ubuntu loaded fine, as did Grub. But then when I boot Windows, it loads up until the usual 'scrolling bar loading' XP screen and then 'BLUE SCREEN OF DEATH'! Upon booting XP in safe mode, it starts loading all the drivers and stops at MUP.sys and then again a BLUE SCREEN OF DEATH.

The mup.sys problem has plagued Windows users for a long while, and I have read many blogs on them, but solutions are arduous and inconsistent. And none I found address my specific issue - dual linux/windows booting.

After this issue I told myself fine, Ill reinstall Windows - did that and Windows worked fine, but then same issue as above - couldnt find Ubuntu/ Grub. 
so then I reinstalled Ubuntu (are we getting bored yet) and again Ubuntu works fine but XP gives my BSDeath, and thats where Im at now.

In summary, it appears installing Windows XP upsets preexisting Ubuntu, and installing Ubuntu upsets my preexisting Windows. But each works fine by themselves.

Apologies for the long post and the fact thats its a Windows issue but your help is very much appreciated.


AMD 5400 
ATI 4850
4gb ram
470W

---

### Post by JoshuaRL on 2009-03-02
Is it still the mup.sys thing that kills XP now that you reinstalled?

---

### Post by Darkoan on 2009-03-02
Ah yes, its still the mup.sys issue

Looking up Windows blogs on how to fix mup.sys (there are plenty) I tried the following

1)using Windows boot cd to repair, at the c:\ prompt...
   a) "chkdsk /p" -- says something about there is a major error on the disk, and doesnt appear to take any time fix anything (arrgh)
   b) "disable mup.sys" -- says there is a major error with my registry system or something (arrgh again)
 c) I tried changing the update.sys file (ie cd system32\drivers, type ren update.sys update.sp2) but "cd etc" doesnt even work at the c:\! This leads me to believe I may have a bad XP boot disk (or at lerast Recovery Console part of the disc, which would explain alot)

2) in BIOS disabled USB/ keyboard support and then reboot - same mup.sys issue

3) reset CMOS and took out CMOS battery for 15 minutes and reboot - still mup.sys issue (i really thought thatd work) still same mup.sys issue

Yes perhaps I just need to get a new XP boot disk, however as I said XP loads up fine after a fresh install, its only after Ubuntu is installed it mucks up.

I am thinking it is a simple issue of partitioning perhaps - if I were to reinstall Windows, I would use Gpart to _delete_ the NTFS Windows partition, and then boot the Windows CD and have it use the partition that appears which correlates to the size of the NTFS partition i just deleted in Gparted.

Thank you for replies.

---

### Post by JoshuaRL on 2009-03-03
Sounds good.  When I wipe drives I use Parted Magic.  It's a live CD that has GPartEd and other tools on it.  For a windows partition, I go back and forth a couple times between two filesystems to completely erase it.  Let's say I'll put on NTFS, then ext3, then back to NTFS.  That should make everything clean and good.  And windows should be able to read that and install there.

---

### Post by chronicsmoke2k on 2009-03-03
ah fucck. I had ubuntu... I screwed that **** up. Then I went to winblows XPerience... Now I lost ubuntu... How can I put WinBlows and Ubuntu on... I need to dual boot ubuntu with winblows... Im also very new to ubuntu...

Sorry if all that was hard to read - 


Chronicsmoke :D:popcorn:

---

### Post by JoshuaRL on 2009-03-03
> **chronicsmoke2k said:**
> ah fucck. I had ubuntu... I screwed that **** up. Then I went to winblows XPerience... Now I lost ubuntu... How can I put WinBlows and Ubuntu on... I need to dual boot ubuntu with winblows... Im also very new to ubuntu...

Sorry if all that was hard to read - 


Chronicsmoke :D:popcorn:

First, please don't use profanity.  And in this thread there are all the links you need to figure it out.  If you still have problems, please post your own thread.  Threadjacking isn't encouraged here.

---

### Post by presence1960 on 2009-03-03
> **chronicsmoke2k said:**
> ah fucck. I had ubuntu... I screwed that **** up. Then I went to winblows XPerience... Now I lost ubuntu... How can I put WinBlows and Ubuntu on... I need to dual boot ubuntu with winblows... Im also very new to ubuntu...

Sorry if all that was hard to read - 


Chronicsmoke :D:popcorn:

+1 on the profanity.

There is no need to put down Windows by calling it Winblows. Just because you may not like it does not matter. Just as you have the freedom to choose your OS so does everyone else regardless if they choose another OS. Attitudes like this will keep Windows users from asking us for help, don't think for a minute that Windows users do not read our forums. If you really want to be helpful don't criticize something someone else likes.

---

### Post by Darkoan on 2009-03-04
> **chronicsmoke2k said:**
> ah fucck. I had ubuntu... I screwed that **** up. Then I went to winblows XPerience... Now I lost ubuntu... How can I put WinBlows and Ubuntu on... I need to dual boot ubuntu with winblows... Im also very new to ubuntu...

Sorry if all that was hard to read - 


Chronicsmoke :D:popcorn:
Im a newbie too, but I have to agree - we can communicate without the profanity - leave that to the windows and piratebay blogs, Ive had enough of 21st century manners.

yes, there are plenty of threads on dual booting - but its amazing how much assumed knowledge is there, which doesnt help us newbies (no disrespect to ubuntu pros).

Id be happy to tell you everything I know, message me - only last night solved dual boot problem after 2 weeks of late nights - I simply got a new XP boot cd and everythings fine (sorry to helpful people above, but nothing worked - it was apparently a bad version of XP).

---

### Post by JoshuaRL on 2009-03-05
> **Darkoan said:**
> (sorry to helpful people above, but nothing worked - it was apparently a bad version of XP).

Actually, I was going to suggest that next Darkoan.  It seemed that for some reason or another, XP had some bad issues.  I'm glad you found a solution.

Welcome to Ubuntu!

---

### Post by presence1960 on 2009-03-05
> **Darkoan said:**
> Im a newbie too, but I have to agree - we can communicate without the profanity - leave that to the windows and piratebay blogs, Ive had enough of 21st century manners.

yes, there are plenty of threads on dual booting - but its amazing how much assumed knowledge is there, which doesnt help us newbies (no disrespect to ubuntu pros).

Id be happy to tell you everything I know, message me - only last night solved dual boot problem after 2 weeks of late nights - I simply got a new XP boot cd and everythings fine (sorry to helpful people above, but nothing worked - it was apparently a bad version of XP).

Glad to hear you got it fixed! Now you know something someone else may not. And you are on the right track - already offering to help someone else. That's why this forum is so powerful. You don't have to be a "pro" to be able to help someone. This is like "synergy" where the final outcome is greater than the sum of it's individual parts.

---

