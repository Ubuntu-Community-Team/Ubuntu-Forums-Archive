---
title: "Dual boot install failed"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by compeng on 2009-09-15
I am attempting to do a dual boot with WinXP.  I installed windows and then installed Ubuntu.  Ubuntu works great and I am very happy with it.  Unfortunately Windows will not boot now when I select it from the boot loader.  I got the splash screen for a second then the computer reboots.  Now I am trying to fix it.

I started with a 40gig drive and had windows setup partition it into 16gig for Windows.  The rest was not formatted.  Windows installed fine.  I installed the motherboard drivers and then moved on to Ubuntu.  (I did not check the disk or run the defrag)

I installed Ubuntu from the 9.04 Live CD I burned.  When it asked about partitioning the hard drive I got confused.  I was hoping to find an option to use the unformatted partition.  I believe I ended up selecting the resize the partitions option, keeping the Windows partition the same size.  Ubuntu then created 3 more partitions automatically as it needed.  As mentioned above Ubuntu works great.

When I tried Windows again it would not boot.  So I ran the Windows install disk again and tried chkdsk.  I got a quick response of the disk has a error and cannot be checked.  So I rebooted with Ubuntu and tried to look at that partition.  Ubuntu could mount it and I was able to browse the files.  Ok, so reinstall Windows.

With the computer booted off of the Windows install disk I get to the point of looking at the partitions on the drive.  I am not given any partitions to select.  Everything seems to be a "removable disk" according to Windows's Repair command prompt.  Windows is not able to list any files.

Next I booted with the Ubuntu Live CD to try to check the partition there.  I found the gnome partition editor.  I Resized the partition for windows again to a smaller drive and the put it back to it's original size.  Booting to Windows I still got the same short splash screen and reboot.  Windows install CD also still can't see the partition.

Booting with the Ubuntu Live CD again I formatted the first partition as ntfs.  I tried again the windows install disk.  Same result. :confused::confused:

I am now looking at completely starting over.  I plan on using Ubuntu Live CD to delete all partitions and create 1 large one.  I will then try Windows again using the whole partition.  Then on the Ubuntu install I will ask it to shrink the partition to 16gig.  
Q1:Is this the only way to go or is there a better option to get the first partition recognizable by Windows?

I read the booklet for beginners in the sticky after I installed Ubuntu the first time. :rolleyes:  Based on that it looks like resizing is the way to go.  Q2: Could the fact that I did not chkdsk and defrag be the reason for my problems?

Hardware:
AMD Phenom II X4 945
Asus M4A78T-E motherboard with 4gig ram
Samsung 40gig IDE hard drive
IDE DVD-Rom 
(NOTE: I have no sata drives.  
Q3:Could this be a problem that the mobo wants to use a sata hard drive as the boot disk?)

Thanks in advance.  I suppose I could try to just install Ubuntu and use the Windows emulator for the few things I need it for.  
Q4:Any good links for this for a newbie?

---

### Post by katakaio on 2009-09-15
First things first: let's take a look at your **/boot/grub/menu.lst** to see what GRUB has to say about your partitions. The next thing to note is that when you have already partitioned your drive in some way (in your case, creating a 16GB NTFS partition for XP and leaving the rest unpartitioned), you will almost always want to select *manual* when the Ubuntu installation asks about partitioning. This allows you to not only preserve your pre-existing partitions, but it lets you see exactly how the drive is partitioned graphically and install Ubuntu successfully.

---

### Post by desperado665 on 2009-09-15
I believe there is an option for choosing "largest contiguous free space" and that option should have installed Ubuntu to your unpartitoned area.

---

### Post by LewRockwell on 2009-09-15
back-up anything you need to keep, make sure your hardware is connected the way you want it, make sure your BIOS settings are exactly the way you want them, then do a fresh install of Windows

Once Windows is installed and ALL updating is successfully done then make a clone of this fully functioning fresh install

You can use Clonezilla or whatever you like

[http://clonezilla.org/](http://clonezilla.org/)

Now that you have a clone you can revert to that instead of doing a ground zero install ever again(hopefully that is common sense)

Then you can do all the multiple defrags, partition reductions, and checkdisk operations that are covered repeatedly in other threads, guides, and tutorials

some links for your enjoyment:

[http://ubuntuforums.org/showthread.php?t=1222961](http://ubuntuforums.org/showthread.php?t=1222961)

[http://ubuntuforums.org/showthread.php?t=1252042](http://ubuntuforums.org/showthread.php?t=1252042)

.

---

### Post by compeng on 2009-09-15
Thanks all for the replies.

I am now looking at the Clone software.  Thanks LewRockwell. I hope it works with Ubuntu, assuming it does.  Then I don't need to do that part again since it is still running.  Otherwise, is there a backup utility that is recommended?  Off to search.

katakaio:  I thought I did select manual and I then selected an option after that.  Ahh . . . who knows.  I was tired from getting all the hardware setup.  It is fun to learn about all the new connections you have to deal with every 5-7 years. :)

BTW: my old system is still running so data is not a problem.  I plan on moving that hard drive to the new system once everything is running and tested.

Thanks again all.

---

### Post by compeng on 2009-09-15
So I found this link and it shows Windows Vista doing exactly what my XP system did.  How do you get to the repair on an XP disk?
 [http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)

---

### Post by compeng on 2009-09-16
I downloaded the Vista Repair disk and tried to get it to "repair" the Windows partition.  No luck there.  It said it was not repairable.

I then deleted the partition in Gnome Partition Editor.  I tried the Win XP install CD again.  Still said disk is unrecognizable.

I guess I am stuck.  I did not have a chance to get the GRUB output last night.  I need to find the command to run too.

---

### Post by HarrisonNapper on 2009-09-16
> **compeng said:**
> I downloaded the Vista Repair disk and tried to get it to "repair" the Windows partition. No luck there. It said it was not repairable.

I then deleted the partition in Gnome Partition Editor. I tried the Win XP install CD again. Still said disk is unrecognizable.

I guess I am stuck.  I did not have a chance to get the GRUB output last night.  I need to find the command to run too.

When you deleted the Windows partition with GParted, did you reformat the empty partition as "ntfs" before trying to reinstall Windows?

---

### Post by katakaio on 2009-09-16
Just to clarify: are you currently able to boot into Windows? I'm a little confused as to what the disk currently looks like. Can you use GParted to show us a partition table?

---

### Post by LewRockwell on 2009-09-16
> **compeng said:**
> I downloaded the Vista Repair disk and tried to get it to "repair" the Windows partition.  No luck there.  It said it was not repairable.

Vista will not repair XP(they create the boot sectors differently)

> **compeng said:**
> I then deleted the partition in Gnome Partition Editor.  I tried the Win XP install CD again.  Still said disk is unrecognizable.

Are you saying the XP installation disk is unrecognizable...or are you saying that the XP Installer is telling you that your hard drive is bad?

Otherwise, the XP Installer should just tell you that it is going to format the entire hard drive and install XP

> **compeng said:**
> I guess I am stuck.

See my previous post above

.

---

### Post by compeng on 2009-09-16
Windows is now gone because I reformatted the partition in an attempt to reinstall Win XP.  I tried to install Windows with the partition formatted as ntfs and as unformatted disk space.  The Windows XP install CD gives me the following errors:
Setup cannot access this disk.  Also gives me Unknown Disk several times.  I believe the unknown disk is the Ubuntu partitions.

The GParted screen capture is linked below:
[IMG]http://picasaweb.google.com/lh/photo/lCjW0lEkLtFuU_SyhwiHeQ?feat=directlink[/IMG][http://picasaweb.google.com/lh/photo/lCjW0lEkLtFuU_SyhwiHeQ?feat=directlink](http://picasaweb.google.com/lh/photo/lCjW0lEkLtFuU_SyhwiHeQ?feat=directlink)

my menu.lst file is as follows if it helps.  I can choose which system to boot fine though.  Of course with XP gone I have not tried selecting to boot with it.
```
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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=f03234b2-2dcd-4993-bafa-6f50ad257142 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f03234b2-2dcd-4993-bafa-6f50ad257142

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        f03234b2-2dcd-4993-bafa-6f50ad257142
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=f03234b2-2dcd-4993-bafa-6f50ad257142 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        f03234b2-2dcd-4993-bafa-6f50ad257142
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=f03234b2-2dcd-4993-bafa-6f50ad257142 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        f03234b2-2dcd-4993-bafa-6f50ad257142
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=f03234b2-2dcd-4993-bafa-6f50ad257142 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        f03234b2-2dcd-4993-bafa-6f50ad257142
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=f03234b2-2dcd-4993-bafa-6f50ad257142 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        f03234b2-2dcd-4993-bafa-6f50ad257142
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1

```

---

### Post by compeng on 2009-09-18
After talking to a long time linux user about my plans, I have decided to hold off the Windows install until I can get a larger hard drive.  40 gig will be tough.  Can't wait for Thanksgiving!   Thanks for all the help so far.  I have learned a lot.  I have reinstalled Ubuntu using the whole drive.

Now to get the software configured and find out what is going on with my graphics driver.

---

### Post by bigboy7foru on 2009-09-18
> **compeng said:**
> After talking to a long time linux user about my plans, I have decided to hold off the Windows install until I can get a larger hard drive. 40 gig will be tough. Can't wait for Thanksgiving! Thanks for all the help so far. I have learned a lot. I have reinstalled Ubuntu using the whole drive.
 
Now to get the software configured and find out what is going on with my graphics driver.
 
 
 
a bigger drive would be better... i dont know alot about linux but  my friend is helping me set up my dual boot and he has windows installed and then installs ubuntu and selects a certian amount of space that he wants to use
 
so yeah once i get mine set up wich will probally be sunday night or monday ill message you if i can remember lol

---

### Post by katakaio on 2009-09-19
Thanks for the info and the screencap, compeng. I think you're doing it right with only one OS on a 40GB drive (and of course, Ubuntu is the one to use :P). One thing to note is that, with Windows gone, you can remove your extended partition and have simply root and swap partitions. My personal favorite is to have partitions made for root, swap and home, but feel free to experiment and make it your own.

---

### Post by compeng on 2009-09-19
Yep. I did blow away the original partitions.  I now have 2.  I was hoping the hibernation would work but my test today failed.  So there goes over 4 gig:lolflag:.  No worries.

Thanks Bigboy7foru.  I look forward to the message.  Good luck.  I am learning how to fix hardware issues like seeing the temp sensor on my CPU.  Much to learn have I.

---

### Post by bigboy7foru on 2009-09-21
> **compeng said:**
> Yep. I did blow away the original partitions. I now have 2. I was hoping the hibernation would work but my test today failed. So there goes over 4 gig:lolflag:. No worries.
 
Thanks Bigboy7foru. I look forward to the message. Good luck. I am learning how to fix hardware issues like seeing the temp sensor on my CPU. Much to learn have I.
 
 
 
so im doing it in a few hours so i hope i dont blow my home computer away haha
 
im going to install ubuntu inside of windows... they say that works great

---

