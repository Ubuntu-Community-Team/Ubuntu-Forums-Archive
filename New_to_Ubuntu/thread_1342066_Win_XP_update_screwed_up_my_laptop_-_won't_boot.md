---
title: "Win XP update screwed up my laptop - won't boot"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by Miroslav011 on 2009-11-30
Recently I had installed Ubuntu 9.10 on my Dell Vostro 1720.  Everything was going great and I was able to dual boot XP and Ubuntu.

On Saturday I saw that a couple of Win updates were available.  I installed those and restarted.  That's where the problem started.  After a restart the computer wouldn't load grub and every time it attempted to load it it would restart.  So I'm basically stuck right before I get to choose which OS to load.

This post has two parts.  First is a warning to people that the latest Microsoft Update might screw up your computer too, and the second is a question.  Because I plan on reformatting the computer (I don't have anything on there worth saving) should I install XP first with a partition set aside for linux, or should I install XP on entire drive and as I'm installing linux allocate that space by way of Ubuntu installation CD?  Or the third option, install Linux first on one partition and Win XP on another?

Thanks for reading.

---

### Post by philinux on 2009-11-30
Just reinstall grub from the livecd.

[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

---

### Post by Miroslav011 on 2009-11-30
Heh thanks for the tip.  I will try this later tonight.  It does seem easier than a reformat.

---

### Post by Miroslav011 on 2009-11-30
Ok, so I've inserted the CD that was mailed to me but alt + F2 does nothing.  Trying Ububtu before I install it and going in to the console doesn't work with the instructions you've given me.  Hitting ESC after restarting and going in to 'text mode interface' also doesn't help.  Message given is  'Could not find kernel image:$sudo'


I'm pretty sure I'm going about this the wrong way.  Any help is appreciated.

---

### Post by Geoff918 on 2009-11-30
> **Miroslav011 said:**
> Ok, so I've inserted the CD that was mailed to me but alt + F2 does nothing.  Trying Ububtu before I install it and going in to the console doesn't work with the instructions you've given me.  Hitting ESC after restarting and going in to 'text mode interface' also doesn't help.  Message given is  'Could not find kernel image:$sudo'


I'm pretty sure I'm going about this the wrong way.  Any help is appreciated.

Are you using GRUB installer? Or are you using Windows Boot Manager?

---

### Post by bumanie on 2009-11-30
As you are using 9.10, you should be using grub2 as the bootloader - here is a guide on how to [reinstall grub2]("http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD") via a live cd. Hope it helps you.

---

### Post by qjmoss on 2009-11-30
I haven't messed with Super Grub Disk in awhile.. But back in my day this used to be the best way to repair a GRUB Boot Loader error.

I'll pot you the URL, check it out, and if you have any quesitons post it back here and i'll help you out

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)


Also, I think Unetbootin also has an option to install SGD on a USB drive. (my favorite way of making boot disks)

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Let us know =)

---

### Post by Miroslav011 on 2009-11-30
> **Geoff918 said:**
> Are you using GRUB installer? Or are you using Windows Boot Manager?

GRUB is what was managing the partitions after I installed Linux.

---

### Post by Miroslav011 on 2009-11-30
> **bumanie said:**
> As you are using 9.10, you should be using grub2 as the bootloader - here is a guide on how to [reinstall grub2]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD") via a live cd. Hope it helps you.


I've mounted the drive.  When I run this
```
sudo grub-setup -d /media/disk/boot/grub /dev/sda
```

I get No device is specified.

*disk is some long number that ls /media gives me

---

### Post by nazgulord on 2009-11-30
Yeesh...can't Microsoft do updates without messing up other OSes on the system? (Sorry, I know that isn't much help)

Anyone know what exactly might be causing this to occur? Do the updates modify the MBR?

---

### Post by Miroslav011 on 2009-11-30
> **Miroslav011 said:**
> I've mounted the drive.  When I run this
```
sudo grub-setup -d /media/disk/boot/grub /dev/sda
```I get No device is specified.

*disk is some long number that ls /media gives me


Did it again.  says grub-setup: error: Cannot open 'boot/grub/device.map'

Read a bit further on, used

```
sudo grub-setup -d /media/disk/boot/grub -m /media/disk/boot/grub/device.map /dev/sda
```

when i hit enter it just went to a new command line

---

### Post by Miroslav011 on 2009-11-30
So now that I've restarted it after that it looks like it's back to normal.  Wow.  Thanks for the help everyone.

---

### Post by oldfred on 2009-11-30
There is a bug related to some windows software that writes into the MBR. Since grub2 is slightly larger there now are confiicts.

HP ProtectTools and Dell Recovery Tool write into MBR
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)

---

