---
title: "overloaded hard disk - upgrade/recovery options"
date: 2010-12-31
forum: New to Ubuntu
---

### Post by Toafan on 2010-12-31
I think I managed to max out my boot disk.
Ubuntu runs (ran - it won't boot anymore, explained later) just fine on my computer normally, but I installed some more software and I think I overloaded my disk. Admittedly, it's only a 3-gig disk, but I screwed up ignoring the errors as I was installing junk. (yes, 3-gig HDD. This ancient computer is why I love Ubuntu, because even though it's close to 15 years old Ubuntu runs fine on it.)
I can boot from my live CD (Ubuntu 10.04, same as I have installed) and mount the drive, but when I try to boot from the hard disk Ubuntu tries to check the drive and hangs up. I seem to have introduced irrecoverable errors to my drive. Since I just lately got [s]Ubuntu[/s] my desktop set up the way I want it and can get by without the games I installed, I would like to recover my previous set-up.

Now, I potentially have access to a 'new' hard drive that's way bigger than my current one (by like 10-20x), and I might switch that out on this laptop. But I also will want to migrate later if/when I get around to upgrading to another computer altogether. So, I would like to know [LIST=1]
[*]What my recovery options are if I stay on this hard drive (if any), and
[*]The best way to migrate Ubuntu setup/preferences/installed software from one computer/hard disk  to another
[/LIST]
Help would be greatly appreciated - I was thinking of installing on the new-er, larger drive and then just copying my entire existing filesystem from the old (3-gig) drive to the new one.
Oh - I also have the ability to back up the most important files to a flash drive (also bigger than the boot disk - but partially spoken for), but as the flash drive is in FAT32 files is all I'll be able to back up (no links).
Thank you all very much in advance-
Toafan

---

### Post by cariboo on 2011-01-01
I would suggest you make some empty space on the hard drive, and then try to run fsck on it again. What a lot of people forget is that all the packages you install are archived in /var/cache/apt/archives. The quick way to remove them is to open a terminal and type:

```
sudo apt-get clean
```

Even though you can't boot from your hard drive, you should still be able to mount it and and chroot it. Follow these instructions:

Boot from the Live CD, and once at the desktop, open a terminal, at the prompt type the following commands, pressing Enter after each one:

[LIST=1]
[*]sudo mount /dev/sda1 /mnt
[*]sudo mount -o bind /dev /mnt/dev
[*]sudo mount -o bind /sys /mnt/sys
[*]sudo mount -o bind /proc /mnt/proc
[*]sudo chroot /mnt
[/LIST]

now at the prompt you should be able to run the first command I gave you, without the sudo.

Once you are finished with the above, you can umount your hard drive by pressing Ctrl-D and then at the prompt type:

[LIST=1]
[*]sudo umount /mnt/porc
[*]sudo umount /mnt/sys
[*]sudo umount /mnt/dev
[*]sudo umount /mnt
[/LIST]

Once everything is unmounted, you should be able to run fsck on it.

If you have a large enough usb drive, and the total used space of the hard drive is less than 4Gb, you should be able to use [clonezilla]("http://clonezilla.org/") to create an image of your hard drive.

---

### Post by Paqman on 2011-01-01
Chroot might be getting a little bit techy. From the LiveCD you should just be able to mount the drive then delete all the files in /var/cache/apt/archives. If however you were going to chroot in, then you've got [a few more options]("http://ubuntuforums.org/showthread.php?t=140920") than just cleaning out the APT cache. Emptying the trash would be a good idea too.

+1 for Clonezilla btw. Just plug in the second disk, boot up into a Clonezilla LiveCD and do a disk-to-disk copy. Clonezilla is a bit crusty and ancient looking, but does the job very well once you get the hang of it.

If you're going to stay on this 3GB disk, it'll be a good idea to keep an eye on how full it is. Even Linux file systems start to suffer from fragmentation if they're continually run very full. Try to keep the disk no more than about 80% full as much as possible. You can see how full the disk is in System Monitor.

---

### Post by Toafan on 2011-01-04
(first, apologies for the late reply)
Thank you both for the help. My machine is now working again.
It turns out I did have to use chroot to do work on the hard disk - it wouldn't let me delete stuff normally, but that doesn't seem to matter anymore since it's working :)

I'm curious about using clonezilla, though. If I use it later to migrate to the larger hard disk, will I need to make the partition larger manually or can it take care of that automatically? Based on some poking around I'm guessing that it can.
(or, I could just try it and do some more looking afterwards if I have problems...)
Thanks again

---

