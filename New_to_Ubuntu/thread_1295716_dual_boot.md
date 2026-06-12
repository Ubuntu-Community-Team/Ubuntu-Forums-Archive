---
title: "dual boot"
date: 2009-10-19
forum: New to Ubuntu
---

### Post by javadiva on 2009-10-19
I need to be able to have a dual boot on my Acer 5610.  I have been running Ubuntu 8.04 and I want to upgrade to the 9.04 plus have Windows because there are a few applications that I have to use.  I've read previous threads and tried using the instructions.  I can't install Windows from the CD.  It gets stuck and just sits there.  I have tried to wipe the hard drive using rm -rf / but have not been able to do that either.  What am I doing wrong???

---

### Post by anewguy on 2009-10-19
I'm going to assume that right now your PC is all Linux and that you have perhaps 2 or 3 partitions on your hard drive (swap, / and perhaps a /home partition).  If there is no space free for making a new partition, Windows won't install, and you will need to resize the existing partitions so there is free space for a Windows partition.  If you don't mind completely reinstalling Linux and don't mind losing what you have (unless of course you back it up to some media), you can start up on the LiveCD, run the partitioner (parted or gparted or whatever it's called) to remove ANY partitions from your hard drive. If you do this, just install Windows right afterwards THEN install Linux - dual booting is easiest to set up when Windows is installed first.

If you have any questions at all please post back!!

Dave :)

---

### Post by pgar23 on 2009-10-19
I have a great howto video in my signature that you can check out, and also...if you are trying to install an OS, then the drive must be formatted in the filesystem that you wish to install. For instance, if you want to install Windows on a drive that previously had some version of Linux, this is not achievable because the drive has been formatted in the EXT# or EXT2 filesystem. The method that I used to achieve this task ( I did it the other night on my server) : Take a Linux installation CD (I used RHEL 5) pop it in and proceed with everything as if you were actually going to re-install Linux, then after all is said and done, when it reaches the part that says something to the effect "Are you sure you would like to format, this will write the changes to the disk, permanently" Say yes and after it gets done formatting BUT BEFORE IT WRITES THE FILESYSTEM to the drive, just hold the power button and let the comp turn off. Then try installing your Windows CD. Should work for you since it worked for me.

Hope this helps bro, post back if you have any success orr if you still need help.

---

### Post by oldfred on 2009-10-19
Windows probably does not install because it does not see an empty drive or a NTFS partition. 

Decide how you want to partition the drive, How much space for windows, how much for Ubuntu, if you want a shared NTFS partition for data to share between the systems, whether you want a separate /home or not and the size. If you have a large drive, sizes do not matter if they are a little large. Wndows depending on what you want to install should be a minimum of 20-30GB, Ubuntu if just root and separate /home of 10-20GB, shared data and /home for the rest of the drive except about 1x memory for swap last, if you may want to hibernate.

Use gparted to delete (you did backup your data), all partitions and create as a primary first partition the NTFS for windows, do not do anything else yet so that is all windows sees. Install windows and boot to make sure it works. Then set up and format the remaining partitions and do a manual install so you can say which partition is root and which is /home and  swap. The install should put grub in and see your windows.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)
[http://members.iinet.net/~herman546/]("http://members.iinet.net/%7Eherman546/")

---

### Post by javadiva on 2009-10-19
I have backed up everything on disc and on my external hd.  However, none of the above suggestions works.  My synaptic pack manager won't work and hasn't for the past two weeks.  I put in my ubuntu 8.04.1 disc and all I get is a window showing the files on the disc. It won't let me install.

---

### Post by pgar23 on 2009-10-19
try my suggestion. Judging from your reply it doesnt look like you have read my suggestion.

---

### Post by river226 on 2009-10-19
i agree with pgar23 you need to ditch/ignore your current installation the synaptic package manager has nothing to do with this, and complete format the entire hard drive with a the ubuntu partitioner or if you can get it to work the windows partitioner. then claim some space for ubuntu, and leave the rest _free_ and go into the windows install

---

### Post by javadiva on 2009-10-19
When you say use a Linux installation disc are you referring to the disc I used to install my current Linux version?  That's what I used.

---

### Post by pgar23 on 2009-10-19
Yes, the easiest way is to do the above said. Run the installation "AS IF YOU WERE GOING TO INSTALL LINUX AGAIN"..but just run the CD up and until the point that it formats your hard drive, then hold the power button and try installing WINDOWS. Should be fairly simple.

---

### Post by river226 on 2009-10-19
that's what we are referring to but you can also use the new one, 9.04.
how exactly are you going about it though, like step by step to what your doing, so we can tell whats wrong, or anything, so we can help you find the problem

---

### Post by pgar23 on 2009-10-19
Oh BTW... any linux CD can do this for you.

---

### Post by javadiva on 2009-10-19
I have tried to wipe the hd clean so I can install Windows and then install Linux but have been unable to.  When I go to gparted under administator this is what I see:
/dev/sda1  ext3   /  110.38 gib  14.86 gib  95.52 gib
/dev/sda2   extended   1.41 gib
/dev/sda5  linux-swap   1.41 gib

---

### Post by Robertjm on 2009-10-19
If you want to completely start with a clean slate just run the Windows installer and format the drive in the process. 

That's one good use for Windows....deleting data off drives!

---

### Post by pgar23 on 2009-10-19
I still think that trying to format the drive with the installation CD would be the easiest method. So far you only have partitions that apply to Linux.

Explain to us what is your goal here?  We have suggested a number of possibilities and it appears that none of them seem to fit your preferences.

---

### Post by javadiva on 2009-10-19
When I put the linux cd in the drive, I get a window labeled cdrom-file browser.

---

### Post by pgar23 on 2009-10-19
> **Robertjm said:**
> If you want to completely start with a clean slate just run the Windows installer and format the drive in the process. 

That's one good use for Windows....deleting data off drives!

LMAO. This is true. And it is also useful for iTUNEs, but other than the said two. Nothing. LOL

---

### Post by river226 on 2009-10-19
you do know you need to boot from the cd, so restart your computer and it should work. Just putting in the cd does nothing

---

### Post by pgar23 on 2009-10-19
> **javadiva said:**
> When I put the linux cd in the drive, I get a window labeled cdrom-file browser.

No no no. Turn off your computer, pop in the install CD, boot from the install cd, choose to install the CD, run it up and until it formats your hard drive. then cut the power to your comp. This should not be that difficult.

---

### Post by egalvan on 2009-10-19
> **javadiva said:**
> I need to be able to have a dual boot on my Acer 5610.
1) I can't install Windows from the CD.

2) It gets stuck and just sits there.

3) I have tried to wipe the hard drive using rm -rf / but have not been able to do that either.

  What am I doing wrong???

---
#1. What type of "WIndows CD" are you using?
 is it a Retail Install?
 is it a Restore CD?

A Retail Install has an option to delete any and all partitions on the drive,
and then to create one or more partitions.

A Restore CD almost always has a "restore to factory/original",
which will erase the drive and restore the machine to "as shipped" condition.
I have never encountered a Restore CD that did NOT have this option.

---
#2 What ***exactly*** do you mean by "It gets stuck and just sits there" ?
how far in the boot process does it get to?
Are any error messages shown?

---
#3 the command **rm -rf** is usually enough to hose a partition, but it will only hose partitions that are in the path.
BUT it does NOT erase partitions, it is only removing files.


To truly "nuke" a drive, I have used Darik's Boot and Nuke

dban.org

it has never failed.
but it does "nuke from orbit" as Ripley said....
I've never recovered anything from a nuked drive.



PartedMagic LiveCD is an excellent "mini-distro" with great gparted  and TestDisk support... it's worth the download time.

partedmagic.com

---

### Post by javadiva on 2009-10-19
I get an error message when I try to run the Windows installer.  It says I don't have enough room for the temporary files.

---

### Post by egalvan on 2009-10-19
> **Robertjm said:**
> If you want to completely start with a clean slate just run the Windows installer and format the drive in the process. 

That's one good use for Windows....deleting data off drives!


A "clean slate" ?

"deleting files" ?

LMAO :P

I beg to differ...

Windows neither "cleans slates" nor does it "erase files" worth a durn.
I've made a tidy fortune recovering files from "Windows Format" and "Windows Delete".
Not to mention Criminal Forensic File Recovery.

:guitar:

---

### Post by river226 on 2009-10-19
your gonna have to give us more then that. can you please take the time to write out a full report on what exactly you have gone through, the steps, what you were doing when such-and-such happens and what not? it would make this a lot easier if you gave us full details

---

### Post by egalvan on 2009-10-19
> **javadiva said:**
> I get an error message when I try to run the Windows installer.  **It says I don't have enough room for the temporary files.**

At this point  you have gone past the "partition process".

But we need more info...

So Please, see #1 in my first post.

---

### Post by javadiva on 2009-10-19
I've tried booting from the CD before I got on Forum.  It just goes to my ubunto log in screen.

---

### Post by river226 on 2009-10-19
> **javadiva said:**
> I've tried booting from the CD before I got on Forum.  It just goes to my ubunto log in screen.

and it doesn't do that for windows? well thats odd, have you tried other ubuntu disks?

---

### Post by anewguy on 2009-10-20
If you are having trouble booting from a LiveCD, be sure it is the one you used for installation (e.g., it needs to have been burned as an image, not just as a data disk) and be sure your BIOS is set to try booting from the CD before the hard disk.  Boot using the LiveCd (the one you install with).  When asked, just choose the option to try Ubuntu without installing it.  When that comes up, click applications/accessories/terminal.  Once that terminal window comes up, type gparted and press enter (I think the graphical version on the LiveCd is gparted but I haven't checked in a long time).  The partition manager should now come up.

this stuff of pressing power off (no offense, but it's not a good choice) should be avoided.  Instead, use gparted to remove your existing partitions so the entire disk is free.  Then shutdown from the LiveCD, put in your Windows CD and boot from it, just use the entire disk and run defrag a couple of times afterwards.  Once Windows is installed, shutdown and put in your Ubuntu LiveCD and boot from it.  Go through the installation procedure, choosing guided for the disk partitioning, and shrink the size of your Windows partition to allow space for the Linux partitions you want and then continue on with the installation.

Dave :)

---

