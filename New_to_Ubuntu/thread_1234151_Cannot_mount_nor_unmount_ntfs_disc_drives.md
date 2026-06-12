---
title: "Cannot mount nor unmount ntfs disc drives"
date: 2009-08-07
forum: New to Ubuntu
---

### Post by Norman Thom on 2009-08-07
I have ubuntu 9.06 duel booted with windows XP
2 hard drives on computer, both formated NTFS
have mounted one drive using NTFS configuration tool
Added 2nd drive but get error when I try to mount (open) that drive saying I am not privileged to mount this drive.
Now I am not permitted to unmount original NTFS drive

In desperation I have tried changing my authority to no avail

Is there a Terminal command to mount hard drives and can any one help me with my problem

Thanking you in advance

---

### Post by Zeroangel on 2009-08-07
NTFS drives have problems mounting if they are flagged as 'dirty' (ie: due to an improper shutdown). In most cases booting into windows and letting it run its disk check will fix the problem -- but a quicker solution is to run this command
```
sudo ntfsfix /dev/sda1
```This is assuming that sda1 is the hardware address of your NTFS partition. The only caveat is that it clears the dirty status, as well as the journal (which logs the errors on the disk and instructions on how to fix them) -- which means that if there really is an error on the disk it might not get fixed as well as if it was recovered from the journal.

---

### Post by kansasnoob on 2009-08-07
With the addition of two packages from synaptic I'm able to mount any and all ntfs drives (internal or external). Those packages are 'ntfsprogs' and 'pmount' and you can install either using Synaptic or from terminal as such:

```
sudo apt-get install pmount ntfsprogs
```

Lots of useful, but powerful, tools in ntfsprogs so be careful!

[http://man.linux-ntfs.org/](http://man.linux-ntfs.org/)

---

### Post by Paddy Landau on 2009-08-07
> **Norman Thom said:**
> I am not privileged to mount this drive.
Now I am not permitted to unmount original NTFS drive
Sounds like you need sudo.

A normal user isn't allowed to use mount or umount, although usually you can unmount automatically mounted drives from the nautilus.
```
sudo mount ...
sudo umount ...
```

---

### Post by Diabolis on 2009-08-07
> **Paddy Landau said:**
> Sounds like you need sudo.

A normal user isn't allowed to use mount or umount, although usually you can unmount automatically mounted drives from the nautilus.
```
sudo mount ...
sudo umount ...
```

It all depends on how your /etc/fstab file is edited.
> The user option allows normal users to mount the device, whereas nouser lets only the root to mount the device. nouser is the default, which is a major cause of headache for new Linux users. If you're not able to mount your cdrom, floppy, Windows partition, or something else as a normal user, add the user option into /etc/fstab.
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

You can mount drives directly without using the sudo command by doing something like this:
```
mount -U 12345678 /media/storage
```
Probably nautilus does something like that.

Find out the UUID of the drive:
```
sudo ls -l /dev/disk/by-uuid/
```

---

### Post by bodhi.zazen on 2009-08-07
If you want to mount a partition as a user, without sudo, you either need to use pmount (there is a small edit required to allow pmount to mount internal partitions) or add an entry to fstab.

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by cusinmex on 2009-08-26
> With the addition of two packages from synaptic I'm able to mount any and all ntfs drives (internal or external). Those packages are 'ntfsprogs' and 'pmount' and you can install either using Synaptic or from terminal as such:

Code:

sudo apt-get install pmount ntfsprogs

Lots of useful, but powerful, tools in ntfsprogs so be careful!





used the [COLOR="Red"]ntfsfix[/COLOR] command
and it worked !!

thx in advance

---

### Post by Diabolis on 2009-08-26
Of course they won't show up in any menu, those are command line tools.
```
man ntfsprogs
man pmount
```

---

### Post by cusinmex on 2009-08-26
> **Diabolis said:**
> Of course they won't show up in any menu, those are command line tools.
```
man ntfsprogs
man pmount
```

yeahh i found that out
right after i posted the reply
and i edited

thx
i appreciate it \\:D/

---

