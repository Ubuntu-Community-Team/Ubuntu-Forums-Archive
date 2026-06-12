---
title: "Equiv For Scandsk in Linux?"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by Lifes_Reject on 2008-12-20
Hi everyone:

I was wondering if there was a program in the repos that I could dwnld that is an equivalent to Wimdoze Scan Disk? :frown:

The reason I'm asking is I took out a Flash Drive to my wife who's still using Wimdoze after I'd dwnld some pics for her.
Well once she was done she didn't unmount the Drive before pulling it out.

I put it back on my Intrepid Lappy and it said it couldn't mount because of unclean shut down.
And to use ScanDisk and Defrag to fix it....

So I had to go back out to use her Wimdoze PC to fix it so I could get it to mount on my Lappy.  :twisted:

To have to lower myself to actually have to touch a M$ based Computer!!!

OH the Humiliation...  Anyways Thanks for your Help... :KS

---

### Post by bluefrog on 2008-12-20
teach your wife to demount correctly (in windows) a removable disk.

in linux, just format the usb disk and create a new fat if you need to use that disk with windows.

---

### Post by igknighted on 2008-12-20
It's a CLI program called fsck, and I cannot guarantee that it will work with windows filesystems (although with fat32/vfat you at least have a chance)

---

### Post by Pconfig on 2008-12-20
Hm, it doesn't tell you can actually get rid of the unclean shutdown log yourself?

When typing
sudo mount -t ntfs-3g /dev/NAMEOFUSBSTICK /mnt -o force

Name of USB stick can be found in the details of the error normally :P
(Correct me if i'm wrong)

---

### Post by hivelocitydd on 2008-12-20
file system check, a built in tool, it automatically runs upon so many reboots, or you can manually run it your self, not sure about the exact syntax, so you should check the man page, but it might be "fsck /dev/hda4", the number of course, depending upon what partition you want to check. 

Check the man page first though, you may have to add an option, again not sure, such as "-t ext2".

---

### Post by Lifes_Reject on 2008-12-20
Thanks all for the input, I'm most Grateful...  :)

Teaching my wife something New is next to impossible, But then again she does use Windows! :tongue:

---

### Post by adobrakic on 2008-12-20
> **hivelocitydd said:**
> file system check, a built in tool, it automatically runs upon so many reboots, or you can manually run it your self, not sure about the exact syntax, so you should check the man page, but it might be "fsck /dev/hda4", the number of course, depending upon what partition you want to check. 

Check the man page first though, you may have to add an option, again not sure, such as "-t ext2".

+1

this is how i do it

---

