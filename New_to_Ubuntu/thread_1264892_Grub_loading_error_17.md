---
title: "Grub loading error 17"
date: 2009-09-12
forum: New to Ubuntu
---

### Post by dgub on 2009-09-12
There are a lot of posts about this error but none of the ones I have read address my error.

I have had several attempts at installing 8.04 which resulted in the wrong drives being used due to the fact that Ubuntu does not see the diskmap the same way as the BIOS.

I have 1 PATA and 3 SATA drives on this machine. One of the SATA drives is the boot drive. Because Ubuntu assumes that the PATA must be the boot drive I unplugged it and to be safe the second SATA that I did not want to be overwritten.

That worked ok and was able to boot Ubuntu and XP, but when I plugged back in the drives I could not boot to either and get 
"Grub loading error 17"

The advice seems to be to edit menu.lst but that command does not get a response in Terminal whatever I prefix it with (/boot/grub/menu.lst). I used the live disk (CD) to do this

If I use edit in the command I then get a blank page in the editor (GEdit - I think). I did manage to get a list of the drives up but the copy I tried to save on Win disk but it did not. I have now forgotten the command I used.

Obviously I need to edit something but don't know what or what to change. I would appreciate some help please.

Thank you.

---

### Post by talsemgeest on 2009-09-12
> **dgub said:**
> There are a lot of posts about this error but none of the ones I have read address my error.

I have had several attempts at installing 8.04 which resulted in the wrong drives being used due to the fact that Ubuntu does not see the diskmap the same way as the BIOS.

I have 1 PATA and 3 SATA drives on this machine. One of the SATA drives is the boot drive. Because Ubuntu assumes that the PATA must be the boot drive I unplugged it and to be safe the second SATA that I did not want to be overwritten.

That worked ok and was able to boot Ubuntu and XP, but when I plugged back in the drives I could not boot to either and get 
"Grub loading error 17"

The advice seems to be to edit menu.lst but that command does not get a response in Terminal whatever I prefix it with (/boot/grub/menu.lst). I used the live disk (CD) to do this

If I use edit in the command I then get a blank page in the editor (GEdit - I think). I did manage to get a list of the drives up but the copy I tried to save on Win disk but it did not. I have now forgotten the command I used.

Obviously I need to edit something but don't know what or what to change. I would appreciate some help please.

Thank you.
Well I am not too sure about the problem, but in opening the menu.lst from the live cd you have to prefix it with where the HDD is mounted.

So, first, go to the places menu and click on your hard drive (the one where Ubuntu is installed). Take a look at the location, it will probably be something like /media/disk. Now that you know the location of the hard drive, you can open the menu.lst with a command *like* this one: ```
gksudo gedit /media/disk/boot/grub/menu.lst
``` replacing /media/disk with the loaction of the hard drive.

---

### Post by sturdy on 2009-09-12
FWIW, I had similar error messages for several weeks. I was able to wait until something apparently timed out then the system would boot as expected. I have 1 SATA HD, 2PATA HD, and 2 PATA opticals. I found the problem a couple of days ago. Both opticals were on the same controller but one was jumpered for cable select and the other was jumpered for master. Changed both to CS and now all is good. All that time I blamed the HD for the problem but could not find it :(

---

### Post by dgub on 2009-09-13
> **talsemgeest said:**
> Well I am not too sure about the problem, but in opening the menu.lst from the live cd you have to prefix it with where the HDD is mounted.

So, first, go to the places menu and click on your hard drive (the one where Ubuntu is installed). Take a look at the location, it will probably be something like /media/disk. Now that you know the location of the hard drive, you can open the menu.lst with a command *like* this one: ```
gksudo gedit /media/disk/boot/grub/menu.lst
``` replacing /media/disk with the loaction of the hard drive.

Thank you for your help. I managed to work my way through that but am still having the original problem.

Looking at the device.map

> 
(hd0)	/dev/sda

(hd1)	/dev/sdb


I thought that changing the hd0 & hd1 mapping would solve it, but makes no difference.

My boot partition is /dev/sdb1
and Ubuntu is on /dev/sdd1

I was only able to get this information by running Gparted.

Below is an extract from menu.lst

> 
title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=73fcf5ff-e5b0-4084-8b01-f53bafb407cb ro quiet splash
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=73fcf5ff-e5b0-4084-8b01-f53bafb407cb ro single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 8.04.3 LTS, memtest86+
root		(hd1,0)
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



I would appreciate it if someone could let me know what should be changed please.

---

### Post by LewRockwell on 2009-09-13
make sure everything is physically connected and jumpered properly and the way you want it

then try out Super Grub Disk

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

.

---

### Post by dgub on 2009-09-13
> **LewRockwell said:**
> make sure everything is physically connected and jumpered properly and the way you want it

then try out Super Grub Disk

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

.

Thanks

I have tried Supergrub but it fails the same way. It again assumes that the PATA disk is the boot disk which it is not.

---

### Post by SuaSwe on 2009-09-13
What sort of partitioning are you using? According to [[color="blue"]this post[/color]]("http://ubuntuforums.org/showthread.php?t=1203368"), Grub Error 17 means that ...

> 
... the specified root drive (hd1,0 in the example) does exists, but you have specified the wrong partition. So try another partition (e.g. hd1,1). Remember that these numbers are base 0 (1st partition is 0 not 1).


What do you get from 'sudo fdisk -l' (no quotes) in Terminal run from your LiveCD?

---

### Post by oldfred on 2009-09-13
Try changing your root entry to a UUID entry. My old motherboard sometimes had this problem depending on which drive came up first, so I changed to UUIDs and never had a problem. My new system is all sata and the motherboard lets me set everything so there is no problem with (hdx,y) entries.

Make a backup first just in case this is not correct:

Change
root		(hd1,0)

to:
uuid        73fcf5ff-e5b0-4084-8b01-f53bafb407cb

If your grub is on the same partition(standard install) as your kernel this should work. If you had a separate boot partition  or separate grub partition the UUIDs could be different.

---

### Post by talsemgeest on 2009-09-13
> **SuaSwe said:**
> What sort of partitioning are you using? According to [[color="blue"]this post[/color]]("http://ubuntuforums.org/showthread.php?t=1203368"), Grub Error 17 means that ...



What do you get from 'sudo fdisk -l' (no quotes) in Terminal run from your LiveCD?
Try running ```
sudo grub
find /boot/grub/stage1
```
 from the live cd, that should tell you which drive you should be using.

---

### Post by K7522 on 2009-09-13
I found my issue with getting a Grub error 17 was actually that the /boot folder was too far back on the hard drive to be properly read. This can happen with older MoBo's and newer hard drives.

The way I fixed this was to create a partition mounted to /boot at the beginning of the drive, then create your swap and / mounted partition.

Good luck!

---

### Post by dgub on 2009-09-13
Thanks to all of you - I will go off and try those ideas.

---

### Post by dgub on 2009-09-14
I am not getting anywhere with this.

By removing drives and was able to load up 8.04 and then following your instructions was able to edit menu.lst. I did make a backup of it first, but the alterations I made to the file locked me out of my computer. I tried the Live CD to work from there but cannot work out the simplest of command. In MSDOS if want to change to another disk/partition it is M:\. I have been searching all afternoon but cannot find how to do in Linux. This is the most frustrating of O/S's - it feels that I am working in the last century with this command line stuff. I can point and click at the file I want but it does not allow me to enter a password so that I can change it.

Fortunately I have a Win image in which I was able to restore the MBR and that gets XP working again.

Tried supergrub again but that just corrupts boot.ini and fails to load Ubuntu. I then restored a copy of that.

So now I am not sure how to proceed - giving up is high on the agenda.

Any ideas welcome.

---

