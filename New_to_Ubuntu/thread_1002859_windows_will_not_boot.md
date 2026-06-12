---
title: "windows will not boot"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by altvic on 2008-12-05
just set up ubuntu 8.04 on my windows pc.  It has installed great but when I restarted and tried to boot windows nothing happens.  Help is urgently needed so I can do my work but please speak to me in ordinary language as I just cope with computers.
many thanks
altvic

---

### Post by utnubuuser on 2008-12-05
Here's a similar thread  > [https://answers.launchpad.net/ubuntu/+question/25931](https://answers.launchpad.net/ubuntu/+question/25931)

But it sounds like windows is listed in your grub menu?
Is it? And when you highlight it, it just doesn't respond?

And how many partitions are there including the windows partitions?  A hard drive can only have three partitions, so if there are more, usually you'd have to have a primary partition, and then an extended partition containing the other partitions.

you might want to read this thread:
> [http://ubuntuforums.org/archive/index.php/t-243462.html](http://ubuntuforums.org/archive/index.php/t-243462.html)

---

### Post by altvic on 2008-12-05
But it sounds like windows is listed in your rub menu?
Is it? And when you highlight it, it just doesn't respond?

Thanks for quick reply utnubuuser, windows is listed but as you say, it doesn't respond.  I'll follow your link and get back

---

### Post by altvic on 2008-12-05
I can't make sense of the message on the link you suggested,  I have absolutely no idea what grubs and so on means - a real novice I am afraid.
Is it possible for you to access my computer remotely?
Ta

---

### Post by utnubuuser on 2008-12-05
Sorry,  I've got a sticky g key.  that should've said grub.

And no, I cannot access remotely.  give me a second.

ok,  mostly I'm wondering about the number of partition.  How many partitions are there?

I've seen windows installs with three partitions, so that would be maxed out, can you recall how many partitions there were when you were installing?

In terminal type (Applications>>Accessories>>Terminal)> sudo fdisk -l

---

### Post by altvic on 2008-12-05
hi
This is a new hard drive of 350gb with a fresh windows installed two weeks ago.  today I partitioned this 350gb in half and installed ubuntu 8.04 but when I rebooted it would not boot into any system (windows or Ubuntu) and neither did it give a list of options.  Due to being stuck in the trenches and unable to access internet i re-installed ubuntu, restarted computer and then updated.
When I restart I have the ubuntu option and some other lines PLUS two other systems in the second grouping,  the first line is windows xp and the second line is what i think is the failed ubuntu original.
So, it could be that i have 3 partitions (but I'm not sure about this as I don't really know what I'm looking at!).

I hope this is helpful.
thanks again

---

### Post by utnubuuser on 2008-12-05
You're able to boot Ubuntu though, right?

And if so, can you open a terminal and try that command I listed above,  the sudo fdisk -l

That should give you a listing of all the partitions on you hard drive.

The output from that command should look something like this:> brad@brad-laptop:~$ sudo fdisk -l
[sudo] password for brad: 

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b1513

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2               1        1628    13076878+   5  Extended
/dev/sda3   *        1629        4864    25993170   83  Linux
/dev/sda5            1483        1628     1172713+  82  Linux swap / Solaris
/dev/sda6               1        1482    11904070+  83  Linux

Partition table entries are not in disk order


---

### Post by altvic on 2008-12-05
Hope this it what you require.  I had to guess that the end character was a dash and a small l for linux?


altvic@altvic-desktop:~$ sudo fdisk -l
[sudo] password for altvic: 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8696    69850588+   7  HPFS/NTFS
/dev/sda2            8697       38913   242718052+   f  W95 Ext'd (LBA)
/dev/sda5           21497       30232    70167969    7  HPFS/NTFS
/dev/sda6            8697       21130    99876042   83  Linux
/dev/sda7           21131       21496     2939863+  82  Linux swap / Solaris
/dev/sda8           30233       38553    66838401   83  Linux
/dev/sda9           38554       38913     2891668+  82  Linux swap / Solaris

Partition table entries are not in disk order
altvic@altvic-desktop:~$

---

### Post by utnubuuser on 2008-12-05
Hi --- Yes

You might have to re-install Ubuntu again

I recently added Ubuntu to my sisters laptop for her, and her Windows XP partition were also split the way yours are.
In her case, I booted with gParted, re-sized the very right-hand XP partition, thereby making room.  
If your Ubuntu is useable, how about downloading the latest stable gParted iso, burning it to cd, booting it and removing all of the ubuntu partitions.
Before I get to detailed,  I'll ask if re-installing is an option for you.
I'm no expert at partitioning,  and someone else might have other options for you to try.  
But that would be my course of action.  You'd probably want to get rid of that unusable extra Ubuntu install anyway.
Sometimes it's also possible to fix the grub loader, and it might be as easy as that.
But that's beyond my ability level.
I think you can do the re-partitioning through the live cd as well, if you give me a couple minutes I'll check and get right back to you.

---

### Post by altvic on 2008-12-05
Thanks for this.  The most important issue for me is that I can access windows xp again.  I assume gParted can be googled?  I'll have a go at getting this programme but I'd rather be operating the two systems first and then cleaning up.  Will someone automatically pick up this 'help me' issue or will I have to re-request help?

---

### Post by utnubuuser on 2008-12-05
Hey - altvic
I'm running from the live cd now and it has gParted in System>>Administration>gParted/partition editor

I checked, and you should be able to remove the Ubuntu partitions, and when you re-install, try installing as an extended partition.

There are also several threads on the forum for fixing a mbr (master boot record)
I've come across several posts about XP boot problems, and it's usually a just a matter of re-installing the grub loader.

I'll have a quick look around to see what other threads I can find.

Personally though, I usually just do a fresh install so I know everything is as should be.  I've installed at times and had similar experience with Grub not installing properly when I've had more than three partitions.
Are you comfortable setting up your partitions manually?  It's reasonably easy.
There is another application called SuperGrub, it's open source, and if you get stuck trying to get into Windows, it's the one most likely to be able to start Windows for you.  Again, it's down-loadable, and burnable.  You can use it as a boot disk to select which operating system to boot.
I also just found this posting:
> [http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)

---

### Post by grupotux on 2008-12-05
In the interests of expediency, did you see a screen toward the end of your Ubuntu intallation indicating that «another operating system has been detected, etc.»? Also, did you install Linux on a second hard disk or on the same hard disk as your Windows installation? What version of Windows are you using? What version of Ubuntu did you install?

To answer the first question, open a character-based terminal 

(Applications --> Accessories --> Terminal)

on your Gnome Panel, and write the following at the resulting terminal prompt:

cat /boot/grub/menu.lst  [Press Enter]

The file «menu.lst» (full path: «/boot/grub/menu.lst») should contain the following (your display terminal will take you to the end of the file):

### END DEBIAN AUTOMAGIC KERNELS LIST

title Windows XP
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1

Otherwise, if the file shows nothing below

### END DEBIAN AUTOMAGIC KERNELS LIST

then add the six short lines (above) beginning with:

title Windows XP  # (or identify the version of Windows you're using)
. . .
. . .
. . .
. . .
. . .

Note that you must carry out these changes, if necessary, as «superuser»
by means of a _TEXT EDITOR_ such as «gedit», «nano» or «vi». 

_YOU MUST NOT USE A WORD PROCESSOR_ such as Open Office Writer or Abiword!!! If you do, your Linux installation will no longer boot.

Write out (save) the file and reboot your machine. Hit the Escape key as soon as you see the «booting» message. A screen should appear with Windows as a choice on the last line. Use your down arrow key quickly to highlight the last (Windows) line. Press the [Enter] key. Windows should then begin its boot process within two to three seconds.

-----------------------------------------------------------

If you don't know how to become «superuser», etc., let me know and I'll send you more info. Likewise, if the above should fail, write again.

P.S. I fervently hope and trust that you did not overwrite your Windows installation while installing Ubuntu. If so, well, write once more. Good luck.

---

### Post by utnubuuser on 2008-12-05
Here is another good article/post about restoring your mbr

...seems more relevant to your scenario since your grub loader probably installed to the linux partition, and not the mbr.

> [http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)
 and if your going to re-install anyway, it might be worth your while to try this avenue.  (I'm referring to the second option quoted in the thread).

---

### Post by altvic on 2008-12-05
Totally baffled, sorry.  Below is what i think you want for the first part/question (?)  I'll need further advice from here I'm afraid.

altvic@altvic-desktop:~$ cat /boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=1d2bd4fb-e22d-4b12-8968-a169b22f1f08 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,7)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=1d2bd4fb-e22d-4b12-8968-a169b22f1f08 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=1d2bd4fb-e22d-4b12-8968-a169b22f1f08 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1d2bd4fb-e22d-4b12-8968-a169b22f1f08 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1d2bd4fb-e22d-4b12-8968-a169b22f1f08 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,7)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 8.04.1 (8.04) (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=/dev/sda6 
savedefault
boot

altvic@altvic-desktop:~$

---

### Post by utnubuuser on 2008-12-05
It looks to me as though the entry in the table > 
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1

should read > 
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional
root (hd0,1)
savedefault
makeactive
chainloader +1

but grupotux will probably be able to tell with certainty.
Try downloading SuperGrub and burning it to disk,  that way you'll be able to tell if your XP install is still ok.

---

### Post by caljohnsmith on 2008-12-05
Actually, if your Windows partition is sda1 as it looks like it is, your Grub entry for Windows that uses (hd0,0) is just fine. What exactly happens when you choose that entry from Grub? Does it give any error messages at all? Please post the following so we can check on your Windows partition:
```
sudo mount /dev/sda1 /mnt
ls -l /mnt
```
Note "-l" is a lowercase L, not a one.

---

### Post by altvic on 2008-12-05
Hi
Could plaese give me more instruction how to do this?
Thanks

---

### Post by grupotux on 2008-12-05
OK, I infer from the thread that you may be closer to success than you think. Please note:

The file «menu.lst» contains configuration instructions as well as functional boot lines. All configuration instructions are preceeded by one or more hash marks ( # ). All lines devoid of hash marks on the left margin are functional instructions.

It appears that you installed Linux twice. All lines following

## ## End Default Options ##
. . .
. . .
. . .

pertain to your first Linux installation.

The lines immediately following

### END DEBIAN AUTOMAGIC KERNELS LIST

enable your Windows boot. To render this last title line comfortably visible, do the following:

1- Search backwards to find the following line:

#hiddenmenu

It is the third of three lines separated by blank lines.

Remove the hash mark so that the line reads:

hiddenmenu

2- Move immediately down to:

# Pretty colours
#color cyan/blue white/blue

Remove only the hash mark ahead of color cyan/blue white/blue, thus

# Pretty colours
color cyan/blue white/blue

3- Modify the following near the end:

root (hd0,0)
savedefault
makeactive
chainloader +1

to read:

root (hd0,0)
savedefault
rootnoverify      # add this line
makeactive
chainloader +1


Write out the file and reboot. You should have ten seconds to highlight
the Windows line and press enter before grub boots from the first kernel listed:

title Ubuntu 8.04.1, kernel 2.6.24-22-generic
root (hd0,7)
kernel /boot/vmlinuz-2.6.24-22-generic root=UUID=1d2bd4fb-e22d-4b12-8968-a169b22f1f08 ro quiet splash
initrd /boot/initrd.img-2.6.24-22-generic
quiet

(This is the first title after

## ## End Default Options ##

My first post assumed that your Linux installation had been placed on a separate hard disk, thus the «map» instructions. Sorry about that.


If your reboot (highlighting the Windows line) does not work, change:

root (hd0,0)
savedefault
rootnoverify
makeactive
chainloader +1

to:

root (hd0,1)      # change this line only
savedefault
rootnoverify
makeactive
chainloader +1

and try again.

Assuming one of these two scripts work, you can then make Windows the default boot by changing:

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default 0

to:

default 6

This makes the seventh bootable line the default. (The count begins with 0.) You can count the «title» lines immediately following

## ## End Default Options ##

to make sure you have the right default number.

The last group:

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title Ubuntu 8.04.1 (8.04) (on /dev/sda6)
root (hd0,5)
kernel /boot/vmlinuz-2.6.24-19-generic root=/dev/sda6 
savedefault
boot

pertains to your second Linux installation. If the first one is working, you may wish to remove this. It is not necessary to do so.

Best of luck.

---

### Post by altvic on 2008-12-05
sorry about this but I don't know 'how to search backwards' or write/change lines.  I can follow _what_ you tell me to do (i think) but I don't know how to do it.  I know I'm a pain but could you tell me step by step (without repeating your instructions of course) how to search and how to write.
Much appreciated.

---

### Post by caljohnsmith on 2008-12-05
How about opening a terminal (Applications > Accessories > Terminal), and please post the output of:
```
sudo mount /dev/sda1 /mnt
ls -l /mnt
```
Note "-l" is a lowercase L, not a one. Also, you haven't yet mentioned, but what exactly happens when you choose the "Microsoft Windows XP Professional" entry from the Grub menu on start up? Do you get any errors?

---

### Post by altvic on 2008-12-05
xp does not boot. no messages, nothing but a blinking black rectangle. no computer 'thinking' lights.
Are your instructions below on two lines?  If so, I can't seem to do that as it asks for password.  When I put it in on two lines by pressing carriage return it says nothing found (or words to that effect) before I have chance to put ls etc in.

sudo mount /dev/sda1 /mnt
ls -l /mnt

---

### Post by grupotux on 2008-12-05
With pleasure, however, I'll need about a half hour or so to get back to you.

---

### Post by theozzlives on 2008-12-05
if your windows is still there, boot from your Windows CD, choose recovery mode, and type:```
fdisk /mbr
``` and ```
fixboot
``` that will get you into Windows but not Ubuntu.

---

### Post by utnubuuser on 2008-12-05
wow

Glad I'm not altvic

There are by now four different sets of instruction, none of which seems to be the actual fix.

So to reiterate, - altvic installed XP two weeks ago, using half of a 320gig hdd, then yesteday tried to install Ubuntu which refused to boot.  So a second installation was done, which boots, but XP, though it shows up in the boot menu, will not boot.
There are three OSs on the hdd  the first is XP, second a failed Ubuntu install, and third a working Ubuntu install.

Is seems to me that the easiest fix is to re-install grub, but to the mbr instead of the Linux partition.  Should be no-problem, right?

altvic has already declared total noob status, so with any more advice keep that in mind.  To a noob there's no such thing as "just do this".

What would be the effect of starting gparted, deleting the failed install partition, and resizing the working partition to use up the freed space? Could it be that the failed Ubuntu install which is sitting between the XP partitions and The good Ubuntu partition is messing up grub?  That sounds to me like a fairly safe fix to try.

---

### Post by altvic on 2008-12-06
back at desk after a few hours kip.Thanks utnubuuser you have summed everything up well.  I did try that gParted fix but everything is greyed out in the options of the program.  I also downloaded gParted but that file is now unzipped and on the desktop - beyond me what to do next with that one.  I'm in a quandry.

---

### Post by altvic on 2008-12-06
hopefully I have attached a screen shot of gParted

---

### Post by RavUn on 2008-12-06
Couldn't he boot the XP cd and use it to recover XP?  If that works, I'd say delete the ubuntu partitions and reinstall (using the guided partitioning option when reinstalling).  That's just my suggestion.  The partitioning scheme looks a little crazy right now.

As for his grub menu, it appears the option for XP is correct with hd(0,0)... that's the first partition.  I know I had to use the Vista recovery option a couple of times when trying to install OS X and it worked fairly well.

---

### Post by altvic on 2008-12-06
Just attempted the fix below - no good.  Said that fdisk was not a valid instruction.  fixboot said it could not read so I typed fixmbr but this said the world would end so I did a quick exit.


i> f your windows is still there, boot from your Windows CD, choose recovery mode, and type:
Code:

fdisk /mbr

and
Code:

fixboot

that will get you into Windows but not Ubuntu.

---

### Post by utnubuuser on 2008-12-07
Hello altvic
You downloaded gparted but not as an iso?
Sorry, I meant for you to download the liveCD iso, which should not be zipped.
You then burn the iso as a disk image ( just google that or check out the ubuntu how-to-burn-an-iso wiki).  You can then use that disk to boot and change your patitions.
I notice some of those partitions are locked, and I'm not entirely sure how to address that.
I'm not sure if I've suggested downloading SuperGrub, (again, as an iso, then burn to to cd),  but be careful with that, I've used SuperGrub and ended up with unusable partitions. But it might determine if your XP is still ok.

Also, I found this thread [http://ubuntuforums.org/archive/index.php/t-182989.html]("http://ubuntuforums.org/archive/index.php/t-182989.html")

and this is an excerpt from that thread (fourth entry)
> Thanks for the really speedy reply. I'm used to waiting around 12 hours on the mepis forums because there are less users and most of them in a totally different timezone.

Re-installing osl2000 can only be done through windows - groan.

In order to install GRUB into the root partition, wouldn't you first have to remove GRUB from the MBR first? That would make sense, but I don't know how you'd do that. This is even more complicated if you have both GRUB and LILO in the MBR. Highly confusing.


HOW TO RESET YOUR MBR SAFELY AND PROPERLY

I realize that an earlier member recommended that you create a DOS bootdisk and use fdisk /mbr in order to reset the MBR.

Let me make clear that you should NOT take any recommendation from ANYONE (including those most licensed and experienced - e.g. Doctors) without first doing your own research. I am glad I was patient and actually did my homework before I did anything, by using Google.

Now, back to fdisk /mbr. Most will recommend against using this, and remember that fdisk /mbr only applies to DOS operating systems (Windows 95, 98, etc.).

If you're using Windows 2000 or XP, you have to reset the MBR in another way. This method, from my homework, I learned is far more safe. This works by inserting a Windows XP CD, and when you get to the blue screen asking what you want to do, select the second option that will allow you to enter the Recovery Console (by pressing "R" on the keyboard). This will take you to the Recovery Console, where you will need to type in, SOME recommend, fixboot and fixmbr. I've read a lot of horror stories about using this combination. There is a specific instance when you need to use them in combination. Microsoft says:

If the primary boot partition is a FAT partition, use the FIXBOOT command from the Windows XP Recovery Console to write a new boot sector on the system partition, and then use the FIXMBR command to repair the master boot record.

Quote from: [http://support.microsoft.com/?scid=kb;en-us;314503](http://support.microsoft.com/?scid=kb;en-us;314503)

Read about fixboot and fixmbr combination nightmares here:

[http://www.anetforums.com/posts.aspx?ThreadIndex=30064](http://www.anetforums.com/posts.aspx?ThreadIndex=30064)

Using fixmbr by itself will likely not cause issues. FixMBR proved to be useful and safe for most people, but in one instance, it ruined a person's HD, but I believe that only happened, because that person did not clearly read instructions.

Read about another person's (can't find the orginal guy's story) similar experience here:

[http://www.experts-exchange.com/Storage/Q_20776578.html](http://www.experts-exchange.com/Storage/Q_20776578.html)

There is more reading you should do on using FIXMBR, such as, you shouldn't use because you have a virus. Microsoft recommends an anti-virus scan before you use FIXMBR, but let's assume you don't have any viruses.

Now, let's get to the actual steps.

1. Insert the Windows XP Installation CD (the original one you received with your computer - a Re-Installation CD will be fine too. If you can't find a single Windows XP CD, borrow one from a friend/neighbor).

2. Let everything load till you get to the blue screen with three options. The second option will allow you enter the Recovery Console by pressing "R." Don't be afraid of entering the Recovery Console, because it won't do anything automatically. It will require your input before doing anything.

3. Recovery Console ("RR") will ask you which operating system you want to log into. Select the first one...it should be Windows.

4. It will ask you for the Administrator's password. You should be able to leave this blank, and simply press ENTER. A blank password may not work, and if that happens, try your real Administrator's password. If that does not work either, there is a problem with the installation CD. Try finding another one, or you will have to go through a long and tedious process. That is because Microsoft realizes there is a problem with the CD. In that case, if you can't find another CD, you will have to follow these instructions:

[http://support.microsoft.com/?kbid=308402](http://support.microsoft.com/?kbid=308402)

5. Assuming the password was accepted, you will now see something like this:

C:/Windows/

That is where it will allow you to type in FIXMBR. Go ahead and type it in.

It will now display a serious warning:

This computer appears to have a non-standard or invalid master boot record. FIXMBR may damage your partition tables if you proceed. This could cause all the partitions on the current hard disk to become inaccessible. If you are not having problems accessing your drive, do not continue. Are you sure you want to write a new MBR?

Microsoft assures you that you can ignore this error without any problems. Type in "Y" for "Yes," and let it be. It should not take longer than a few seconds. For me, it seemed like an instant when it was done. You should not see something like "It was done succesfully."

6. Now type "Exit." This will restart your computer. While it is restarting, and the BIOS is doing its thing, quickly take out the CD by pressing the eject button. If you don't do this quickly enough, and your boot-order begins with the CD-ROM, it will go back to the Windows Installation CD. But even then, the installation CD requires you to press a button to enter it, and if you don't press a button, it will load the operating system.

All should be well now. The MBR has been reset, and you should be able to load Windows. Just a few words of advice:

You should understand you are dealing with computers, and backups are always stressed by the most experienced of people. There is, unfortunately, no way around this. Maybe in a 100 years, computers will be so reliable, we would never have to backup things up again. There is software that will allow you to backup your MBR. Do that while everything is alright. Also, buy something external that will allow you to backup files and other stuff.

One more thing: I tried to condense everything I've learned. There must be something I missed (including warnings), so remember to not give up on Google. I may create a complete How-To on this, but in the mean time, don't forget to rely on Google.

Anyone can re-use my instructions here. Feel free to do so

If you're still trying get the original xp install to load, it might be worth reading.

I had meant to ask if you can access your Windows' folders through Ubuntu.  Have you tried to access your Windows folders while in Ubuntu?

---

