---
title: "Permamently mounting Windows in Linux."
date: 2009-04-21
forum: New to Ubuntu
---

### Post by Zummy on 2009-04-21
Hey, I've been following this guide to be able to access windows files on the windows partition thru linux: [http://www.cyberciti.biz/faq/mounting-windows-partition-onto-ubuntu-linux/](http://www.cyberciti.biz/faq/mounting-windows-partition-onto-ubuntu-linux/)

However, each time I reboot I have to type the sudo mount -t ntfs -o nls=utf8,umask=0222 /dev/sda1 /media/c command, is there a way to do this on start up?

---

### Post by nyk on 2009-04-21
You'll want to edit your /etc/fstab, as described in the "Mounting at Boot" section here:

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

---

### Post by Zummy on 2009-04-21
Thank you! I was able to get to my fstab, and (to my knowledge) I added in the command I think will work, by the way it is, /dev/sda1 /media/windows ntfs-fuse auto,gid=1001,umask=0002 0 0

on the bottom line, but how do I save, I don't have "priveledges"  I can't find my answer in the link you provided.

---

### Post by brunogirin on 2009-04-21
You need to edit the fstab file as root using sudo:

```
sudo vi /etc/fstab
```

or

```
gksudo gedit /etc/fstab
```

---

### Post by Godly on 2009-04-21
Thank you!

---

### Post by Zummy on 2009-04-21
Thankyou! However, the guide says to mount all drives after save and exit, so I typed sudo mount -a, and it says```
[mntent]: line 8 in /etc/fstab is bad

```

so what do I need to type to get fstab to recognise sudo mount -t ntfs -o nls=utf8,umask=0222 /dev/sda1 /media/c and work on boot up?

---

### Post by The Cog on 2009-04-21
try this:
> /dev/sda1  /media/c  ntfs  nls=utf8,umask=0222  0   2

---

### Post by Zummy on 2009-04-21
Thanks, The Cog, it seemed to work.

---

### Post by raptor2552 on 2009-04-21
Try:

/dev/sda1	/media/windows	ntfs	realtime        0       0

I assume /media/windows exists and is owned/writable by you

---

### Post by Joeb454 on 2009-04-21
I think using ntfs-config makes life so much easier than editing fstab. I've never edited fstab to permanently mount a windows drive.

There's a link to a guide I wrote here on the forums below :)

[http://ubuntuforums.org/showthread.php?t=785263](http://ubuntuforums.org/showthread.php?t=785263)

---

### Post by stchman on 2009-04-21
I have a tutorial on mounting Windows NTFS and FAT32 partitions.

[http://www.stchman.com/part.html](http://www.stchman.com/part.html)

---

### Post by The Cog on 2009-04-22
As an afterthought, I would change that last 2 to a 0 instead.

---

### Post by evaninthegarage on 2009-04-22
I feel like I could get the answer I'm looking for here... I've been searching on and off all day trying to figure this out for different drives (external hd and iPod)

Recently the two haven't been automounting, like they used to. . .
I don't know much at all about fstab and can't figure out how to restore things like they were. Can someone point me in the right direction? Many Thanks!
I'm in 8.10 btw

---

