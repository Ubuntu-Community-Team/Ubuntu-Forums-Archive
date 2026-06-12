---
title: "startup diskette?"
date: 2010-06-24
forum: New to Ubuntu
---

### Post by jfbooth on 2010-06-24
Objective:  Run fsck TO hard drive installation of Xubuntu 10.04

Can't find Live CD at the moment.  Have floppy disk drive.  Thought I would learn something (win or lose).

Strategy .. create Startup DiskETTE with STARTUP DISK CREATOR, and after booting from it, run fsck from it (assuming fsck is available).

Have floppy icon on desktop. AM able to write to it (copy small file to it from desktop .  then delete the 'test file') .. so the device is working.

Problem #1.  I don't think STARTUP DISK CREATOR creates FLOPPY startup diskettes.  CDs and maybe thumb drives (USB) but not floppies.  Maybe it does, but it does not look like it once I get into it.  I backed off of it.

Problem #2.  Since #1 seems to be the case, I 'heard about' "SuperGrub" which appears to be one way of creating such a floppy.  So, I downloaded super_grub_disk_english_floppy_0.9799.img from their website.  Their instructions say do the following to create the 'startup diskette':

dd if=super_grub_disk_english_floppy_0.9799.img of=/dev/fd0
Unmount the floppy drive to be sure the data is written on the floppy disk.

So, I right click FLOPPY ICON on desktop, and UNmount it.  Then:

jb@jb-desktop:~/Desktop$ sudo dd if=super_grub_disk_english_floppy_0.9799.img of=/dev/fd0
[sudo] password for jb: 
dd: writing to `/dev/fd0': Input/output error
233+0 records in
232+0 records out
118784 bytes (119 kB) copied, 9.21069 s, 12.9 kB/s
jb@jb-desktop:~/Desktop$

I/O error is discerning and is probably why the diskette does not get created.  It appears to be blank though can only use THUNAR FILE MANAGER because don't know how to access floppy from terminal.  Tried ls fd0, ls floppy, ... would love to know how to do that .. access floppy from terminal.

Any help is appreciated .. I consider this a learning experience.

Maybe SUPERGRUB is not the direction to take in order to run fsck on my hard drive ... but wondering why I can't write the .img file anyway.

Maybe there is no such thing as an XUBUNTU 10.04 'startup diskette' .. as it is too big to create one(?)

Dunno .. too much of a noob.  At this point, trying to learn more than just trying to run fsck ... though would still like to do that.

Thank you in advance.

One more 'clue' .. PROPERTIES of Floppy Icon on desktop say 

Name: Floppy Drive
Kind:  Folder
Modified:  1969-12-31 18:00:00
Accessed:  1969:12:31 18:00:00
FREE SPACE: 5.4 GB

and the floppy disk drive is, of course, 1.44MB

---

### Post by anewguy on 2010-06-24
I don't know for Ubuntu, because I've never tried it.  I do know of at least 1 other distribution (Slackware) that let's you create a boot diskette, but it uses a different boot manager (lilo) than grub.

I'll do some checking.....but I'm also not sure if you'll be able to run fsk from it or not.

Dave ;)

---

### Post by jfbooth on 2010-06-24
Thank you for the suggestion.  If I understand it, I would have to INSTALL slackware in order to create a diskette from it(?).  If so, that would not be something I wish to do.  Thank you anyway.

---

### Post by anewguy on 2010-06-24
Yes, but I wasn't actually suggesting that, instead just giving an example of Linux distribution that allows creating a boot diskette.

I guess I should ask - did you install Ubuntu from a LiveCD?  If so, you should be able to boot that disk, select the try ubuntu without changing your computer option, then run fsck (you may need to mount your existing disk first.

Also, I don't know if startup disk creator actually will create a boot diskette.  I *think* it only builds either a CD/DVD or a USB flash drive.

You may want to try a net search using your favorite search engine and put ubuntu create boot diskette in the search string and see what comes up.

Dave ;)

---

### Post by jfbooth on 2010-06-24
> **anewguy said:**
> Yes, but I wasn't actually suggesting that, instead just giving an example of Linux distribution that allows creating a boot diskette. 

Right.

> I guess I should ask - did you install Ubuntu from a LiveCD?  If so, you should be able to boot that disk, select the try ubuntu without changing your computer option, then run fsck (you may need to mount your existing disk first. 

Yes, I did, but can't find it.  Can burn another .. but wanted to learn from this.

> Also, I don't know if startup disk creator actually will create a boot diskette.  I *think* it only builds either a CD/DVD or a USB flash drive. 

I THINK you are right.

> You may want to try a net search using your favorite search engine and put ubuntu create boot diskette in the search string and see what comes up.

Dave ;)

OK.

I wonder if I could use Windows XP's chkdsk if I booted from an XP OS CD or an XP rescue disk?  Anyone know???  Isn't a 'Nix drive NTFS compatible??  CHKDSK may check for some specific disk errors but NOT errors in the 'Nix filesystem on a NTSF drive.  Dunno.

I sure want to thank you for your interest and valuable time.

---

### Post by anewguy on 2010-06-25
Completely different file system structures - Windows chkdsk won't work on a Linux system - it may even make it unusable and force a reinstall.

Dave ;)

---

### Post by anewguy on 2010-06-25
I think I found what you're looking for in this howto by herman:

[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html]("http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html")

Look there for the grub-mkrescue entry and click on it.  Please post back if you have any questions or problems.  Also, I'm not sure if fschk is on that image or not.

Dave ;)

---

### Post by jfbooth on 2010-06-25
That link does look promising.  I appreciate your efforts to help, but I think I am simply too 'noob' to 'go that far'.  I may be misunderstanding, but though that link indicates creating a bootable diskette, it looks like it is for "GRUB2" and I seem to be using GRUB 1.98-1ubuntu6 and I don't think I want to get involved in updating GRUB .. for something I am not sure will accomplish the goal .. fsck my filesystem.

I guess the best thing to do is burn another live CD .. though I believe there must be some 'simple' answer to creating a bootable floppy and running fsck from it, with what I have.

If nothing else from this thread, I would like to know how to access the floppy drive from TERMINAL.  What would the command be from jb@jb-desktop:~/Desktop$   ??

I have tried fd0, floppy, even A: (god forbid).

And of course, thank you for your kind assistance.

---

### Post by anewguy on 2010-06-25
If you're just using grub EDIT: "instead of" grub2, see this link:

[https://help.ubuntu.com/community/GrubHowto/BootFloppy]("https://help.ubuntu.com/community/GrubHowto/BootFloppy")

Dave ;)

---

### Post by jfbooth on 2010-06-25
> **anewguy said:**
> If you're just using grub and grub2, see this link:

[https://help.ubuntu.com/community/GrubHowto/BootFloppy]("https://help.ubuntu.com/community/GrubHowto/BootFloppy")

Dave ;)

Saw the link. Looked promising so I followed instructions carefully.  Here are the results:

jb@jb-desktop:~/Desktop$ sudo -s
[sudo] password for jb: 
root@jb-desktop:~/Desktop# mke2fs /dev/fd0
mke2fs 1.41.11 (14-Mar-2010)
Filesystem label=
OS type: Linux
Block size=1024 (log=0)
Fragment size=1024 (log=0)
Stride=0 blocks, Stripe width=0 blocks
184 inodes, 1440 blocks
72 blocks (5.00%) reserved for the super user
First data block=1
Maximum filesystem blocks=1572864
1 block group
8192 blocks per group, 8192 fragments per group
184 inodes per group

Writing inode tables: done                            
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 31 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.
root@jb-desktop:~/Desktop# mount /dev/fd0 /media/floppy
root@jb-desktop:~/Desktop# mkdir /media/floppy/boot
root@jb-desktop:~/Desktop# mkdir /media/floppy/boot/grub
root@jb-desktop:~/Desktop# cd /boot/grub
root@jb-desktop:/boot/grub# cp stage1 stage2 /media/floppy/boot/grub
cp: cannot stat `stage1': No such file or directory
cp: cannot stat `stage2': No such file or directory
root@jb-desktop:/boot/grub#

I assume I am using GRUB OR GRUB2.  I thought I posted GRUB ver in an above reply.

---

### Post by anewguy on 2010-06-25
I just checked in Synaptic Package Manager, because I know I'm running grub2.  Mine is listed as grub-pc installed version 1.98-1ubunt6 which has a description of GRand Unified Bootloader, version 2 (PC/BIOS version).  So, if yours matches that you are running grub2 and should follow the process I posted earlier for grub2.

Dave ;)

---

### Post by jfbooth on 2010-06-25
OK, .. looked at my package manager.  First installed item:

grub-common   1.98-1ubuntu 6 (latest version) GRand Unified Bootloader, version 2 (common files)

"GRand Unified Bootloader, version 2 (common files)

This package contains common files shared by the distinct flavours of GRUB.

Canonical provides critical updates for grub-common until April 2015."

next installed item:

grub-pc   with the same credentials as above (PC/BIOS version)

"GRand Unified Bootloader, version 2 (PC/BIOS version)

GRUB is a portable, powerful bootloader.  This version of GRUB is based on a
cleaner design than its predecessors, and provides the following new features:

 - Scripting in grub.cfg using BASH-like syntax.
 - Support for modern partition maps such as GPT.
 - Modular generation of grub.cfg via update-grub.  Packages providing GRUB
   add-ons can plug in their own script rules and trigger updates by invoking
   update-grub2.
 - VESA-based graphical mode with background image support and complete 24-bit
   color set.
 - Support for extended charsets.  Users can write UTF-8 text to their menu
   entries.

This package contains a version of GRUB that has been built for use with
traditional PC/BIOS architecture.

Canonical provides critical updates for grub-pc until April 2015."

There are only those two 'grub' items shown as installed and they PRETTY MUCH match yours .. so I conclude I have Grub2 intalled.

***IMPORTANT:  There is an item NOT installed:***

grub-rescue-pc 1.98-1ubuntu6 GRub bootable rescue images, version 2 (PC/BIOS version)

"This package contains two GRUB rescue images that have been built for use with
traditional PC/BIOS architecture:

 - grub-rescue-floppy.img: floppy image.
 - grub-rescue-cdrom.iso: El Torito CDROM image.

Canonical does not provide updates for grub-rescue-pc. Some updates may be provided by the Ubuntu community."

**---------------**

So .. dunno.  Another thing .. I am not sure what is going on but the last 'stuff' I did, ... all in TERMINAL.  It appeared that the diskette got formatted, the directories got made, etc etc.  Mount appeared to work and Umount appeared to work IN TERMINAL.  It appeared the failure was in writing:

root@jb-desktop:/boot/grub# cp stage1 stage2 /media/floppy/boot/grub
cp: cannot stat `stage1': No such file or directory
cp: cannot stat `stage2': No such file or directory

OK, fine .. whatever .. but this left the diskette mounted, because the instructions told me to mount after mk2fs .. which I did.  It even created the directories. .. point I am trying to make is the diskette should be mounted at this time.

HERE IS THE NEW PROBLEM ... there is a Floppy Drive icon on my desktop.  Right click on it, and there is an option to MOUNT VOLUME.  ????  huh?  It is mounted in terminal!!  Click on the option, and I get:

Unable to mount "Floppy Drive":
mount: wrong fs tyupe, bad option, bad superblock on /dev/fd0, missing codepage or helper program, or other error.  In some cases useful info is found in syslog - try dmesg|tail or so .... with a close button on the error window.

OK, ICON MOUNT option fails because terminal has it mounted .. can't mount a mounted floppy drive .. is my conclusion.  Umount it in Terminal.  ICON mount still doesn't work.  Nothing is making sense.  Another thing, PROPERTIES on that icon show 'free space' 5.4GB ?????? .. and it gives that capacity even with a formatted 1.44 diskette mounted.

OK, so .. start over:

root@jb-desktop:~/Desktop# umount /dev/fd0 /media/floppy
umount: /dev/fd0: not mounted
umount: /media/floppy: not mounted
root@jb-desktop:~/Desktop# mke2fs /dev/fd0    <<<FORMAT IT AGAIN
(FORMAT SUCCESSFUL)
Diskette should be BLANK .... right????
root@jb-desktop:~/Desktop# ls /media/floppy
boot
root@jb-desktop:~/Desktop# 

It ain't blank.  Soooooo, I dunno what's going on, but that desktop icon don' seem to be wurkin too gud.  I am 'seeing' a successful format (I think) yet the diskette is not blank.  I don't know if I can work with all this .. but I will try suggestion for Grub 2 you mentioned .. it refers to:

The grub-mkrescue command for making a floppy disc is the same as the command for making the .iso file but you need to add the option: --image-type=floppy.
Probably it would be best to use a different filename extension too.

grub-mkrescue --overlay=/boot/grub --image-type=floppy grub_two.dsk

This should make you a new floppy disc image file.

Uh .. ok here it is:

root@jb-desktop:~/Desktop# grub-mkrescue --overlay=/boot/grub --image-type=floppy grub_two.dsk
Unrecognized option `--overlay=/boot/grub'

SO I TRIED:

root@jb-desktop:~/Desktop# /usr/bin/grub-mkrescue overlay=/boot/grub image-type=floppy grub_two.dsk
output file must be given

so there is a syntax problem .. I am too noob to understand it, and the example of the command does not work:

grub-mkrescue --overlay=/boot/grub --image-type=floppy grub_two.dsk

I'm pretty lost .. but await your comments.  thankx.

---

### Post by jfbooth on 2010-06-25
> Diskette should be BLANK .... right????
root@jb-desktop:~/Desktop# ls /media/floppy
boot 

ok, I think I figure out THIS problem.  I just read up on sudo updatedb
so THAT problem is 'explained'.

---

### Post by anewguy on 2010-06-26
I have successfully created a boot floppy using the instructions, as I wanted to find where your problems are.

(1) Your first attempt that failed on copying  the 2 "stage" files was because that was for grub, not grub2.

(2) I'd honestly have to sit in front of your PC and try to duplicate what you did in order to converse on the mount problem you had.  I didn't have any mount problems.

(3) The line you typed in for grub-mkrescue is for 9.10 and prior, as noted on the page where it says for Karmic Koala or earlier.

(4) The correct line to use is just a little further down - for Lucid Lynx:

Lucid Lynx version of grub-mkrescue, (GNU GRUB 1.98-1ubuntu5), thanks to moon_raker  for letting me know.


grub-mkrescue --output=rescue.iso /boot/grub


This should build it for you.  I haven't tried booting it yet to see if fschk is there, but considering it isn't in my normal installations' /bin folder, it may be a built-in.

Dave ;)

---

### Post by jfbooth on 2010-06-26
>  grub-mkrescue --output=rescue.iso /boot/grub 

iso???   aren't those for CDs??  I read .img is for floppies.

************
How To Make Your Own GRUB2RESCUE [COLOR="Red"]CD-ROM[/COLOR]

1st example for grub-mkrescue,  (Karmic Koala and earlier),
grub-mkrescue --overlay=/boot/grub GRUB2RESCUE.[COLOR="Red"]iso[/COLOR]
Where: I want to include files such as my own personalised grub.cfg from /boot/grub
Where: I want the program to name the file 'GRUB2CD.[COLOR="Red"]iso[/COLOR]'

    * if you're making a CD, you don't have to specify the 'type', because CD is the default
    * --overlay=DIR would be an important option if you want a menu based GRUB2 CD. You can make an .iso file with your own familiar GRUB Menu in it. If you don't want to do that you might instead want to make up a special grub.cfg for some special purpose or experiment you want to try. If you don't use this option you'll still have a bootable GRUB2 CD, but it will only have the Command Line Interface, see GRUB2 CLI Mode Commands.

Lucid Lynx version of grub-mkrescue, (GNU GRUB 1.98-1ubuntu5), [COLOR="Red"]thanks to moon_raker[/COLOR] for letting me know.
grub-mkrescue --output=rescue.[COLOR="Red"]iso[/COLOR] /boot/grub

    * for  the --output=rescue.[COLOR="Red"]iso[/COLOR] part of the command, you can replace the word 'rescue' with any name you  like for your new .iso file.
    * in the /boot/grub part of the command, you can specify some other file path if you are creating your own GRUB2 [COLOR="Red"]CD[/COLOR] in some other directory, but for most people, /boot/grub will probably be right.


Expected Results -

   1. The grub-mkrescue program should make an .[COLOR="Red"]iso[/COLOR] file in your /home/username directory with your own operating system's GRUB files inside it.
   2. You need to burn the .iso file to a blank CD as an .[COLOR="Red"]iso[/COLOR] file, not as data, so it will be bootable.
   3. Your GRUB2RESCUE [COLOR="Red"]CD[/COLOR] should boot to a GNU GRUB Command Line, see GRUB2 How To Boot From CLI Mode -  NEW!  Rescue your System  
   4. To see your own personalised GRUB Menu, just run the command: configfile /grub.cfg

Also see How To Boot From CLI Mode - Rescue your Operating System.



How To Make Your Own GRUB2 [COLOR="Red"]Floppy Disc[/COLOR]
The grub-mkrescue command for making a floppy disc is the same as the command for making the .iso file but you need to add the option: --image-type=floppy.
Probably it would be best to use a different filename extension too.
[COLOR="Red"]grub-mkrescue --overlay=/boot/grub --image-type=floppy grub_two.dsk
This should make you a new floppy disc image file.[/COLOR]

[COLOR="Red"]dd if=grub_two.dsk of=/dev/fd0 bs=512 count=2880
This is how to copy your floppy disk file to your floppy disk[/COLOR].

MOONRAKER reference is in the CD creation section.  I dunno .. WAY too confused .. grub ver 1.98 is GRUB2, ISO/IMG, .. guess I am too dense.  I don't think I want to run fsck on my hard drive anymore.  One utility says diskette is mounted another says it isn't.  I don't even know where to start .. I copy commands right from instructions into terminal and get what appears to be syntax error.  

I been googling FORMAT DISKETTE XUBUNTU all night, and don't find a thing on it .. STARTUP DISK CREATOR doesn't.  Unbelievable .. just to be sure the filesystem on the hard drive is OK.  Burn a CD to do that??  Unbelievable.

Hey, .. thank you for your time.  I am sorry I could not accomplish this.  I really do appreciate your help.

---

### Post by anewguy on 2010-06-26
Well, I found a link which let me create a "boot" floppy, but I must admit it's not what I expected (and not the same as the boot floppy created, as an example, with Slackware).  When I booted using the floppy, it just came up with my regular boot menu, which isn't what I'm looking for (nor what I think you are looking for).

So, I'm going to open a thread looking for help on this idea.  I'll post back if I get some good replies.

Dave ;)

---

### Post by jfbooth on 2010-06-26
Not sure where I should go from here.  I guess we an leave this thread open .. for anything you find or other comments.  All I know is, I am so lost, I can't do anything from where we are at this time.  It's amazing how little there is with search engines on Linux and Floppy drives .. I guess they are too near obsolesence.  Thank you for all your support and patience.  I will watch for anything else you put up in this thread.

---

### Post by anewguy on 2010-06-26
You might try burning a LiveCD, booting from it, selecting the "Try Ubuntu without changing your computer" option.  Then go to a terminal and mount your file system that you suspect has problems, then run fschk.

I have never tried that, and I would now but I'm in the middle of something else so I can't reboot, so i can't tell you if that works or not.

Dave ;)

---

### Post by jfbooth on 2010-06-26
This old machine has a CD read only drive.  Can't burn with it.  Otherwise, I do believe that is the defacto way to run fschk .. from "your live CD" .. which I cannot locate.  It will also not boot from a USB stick.

I was not lamenting 'where to go from here' in the light of getting the task done .. I meant 'where to go from here' in creating an 'emergency diskette' ... for lack of a better term.

---

### Post by jfbooth on 2010-06-26
I have a feeling what I dreamed of doing cannot be done.  I don't think one can boot Ubuntu, Kubuntu, Xubuntu, from a diskette.  I could be wrong, but am beginning to think one can't.  The essentials to do so just won't fit on a floppy .. period.
There are utilities where one can 'boot' a UTILITY from a floppy and then pseudo 'boot' Linux from a CD where the bios will not allow booting directly from CD .. but one still needs the 'product' on a CD.

I just don't think one can create a floppy disk, boot from it, and directly arrive at a Ubuntu distro of Linux (or maybe any other Linux distro).

I could be wrong about this .. but that is how it is looking to me.

Even Damn Small Linux distros in a 50MB package.  Even they don't claim to be able to 'start' from a floppy.

But I could be wrong.

---

