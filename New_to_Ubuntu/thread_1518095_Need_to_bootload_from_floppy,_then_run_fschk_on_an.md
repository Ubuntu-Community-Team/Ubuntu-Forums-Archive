---
title: "Need to boot/load from floppy, then run fschk on an existing file system"
date: 2010-06-26
forum: New to Ubuntu
---

### Post by anewguy on 2010-06-26
I've been trying help someone with creating a boot floppy.  I did find one post that worked to some degree - it let me create a floppy but I think all it does it boot to the grub menu.

What this user needs, and what I'd be interested in as well, is a way to boot up from another media, when you think you're main file system might be failing, and run fschk on the suspected failing file system.

The floppy thing just doesn't seem to work.

Can a person:

- boot from the LiveCD or a "LiveUSB"

- run fschk on a file system on a hard drive

I assume you can, but I also assume you have to mount that other file system some how.  

I'm quite ignorant on all of this.  I've done a LOT of searching the forum and searching the net, and just not finding what is needed.

Thanks in advance for any help - it is greatly appreciated!

Dave ;)

---

### Post by k3lt01 on 2010-06-26
Isn't there a file on the LiveCD that you can create a boot floppy with to do just that? I'll have to have a look and I haven't got access to my CDs at the moment but I'm sure there is.

EDIT: sbm.bin in the install folder is the file I am thinking of.

---

### Post by anewguy on 2010-06-26
Do you know if it creates more than just a grub2 menu disk?  The processes I found on the net only created a floppy that booted to my normal grub menu.

I'll check out smb.bin in just a little while.  I'm in the process of backing up my netbook so I can't shutdown the desktop I'm on for now.

Thanks again for the help k3lt01 !!

Dave ;)

---

### Post by k3lt01 on 2010-06-26
Dave, from memory there is an instructions file in that folder as well. I have never used it but I think it is useful for setting up over a LAN if the machine doesn't have a CD drive.

---

### Post by anewguy on 2010-06-26
I created the floppy and then found that the readme was indeed labeling things correctly - it is smart boot manager.  I really need a diskette with a bootable kernel, fschk and I guess mount.

Dave ;)

---

### Post by k3lt01 on 2010-06-26
Ah, I don't have an answer for you atm then. I'll keep looking.

EDIT: Could you create a bootable floppy (so install GRUB) and have fsck listed in the GRUB selection like Memtest is normally? Of course you will need to download and install fsck to the disk but in theory that should work.

---

### Post by anewguy on 2010-06-26
I may have found something that works, but using a CD.  There is a package called something like cdboot which says it makes a bootable cd that runs ubuntu without hard drives.  I suspect this must be like running the LiveCD.

So, I guess the question should be changed to:

Using LiveCD, or CD created by cdboot package, how do you run a file system check on an existing file system on a hard disk?

Dave ;)

---

### Post by anewguy on 2010-06-26
This may be of interest to everyone, and particularly funeral blues analysis:

The package is called bootcd.  According to the description, it makes a bootable image of your running system on a CD or it can make it an ISO image on NFS.

I'm going to install the package, then do some playing later today (need some sleep).

Dave ;)

---

### Post by anewguy on 2010-06-26
Okay, it never installed bootcdwrite on my PC so I can't create the CD.  This may be due to no RW drive being recognized on my system.  I pulled my DVD/RW and put it in an external enclosure so I can share it with my netbook, and it never shows in Ubuntu since.  Nothing shows in fstab.  I did put an old CD-ROM drive in the bay on the desktop.

Running block id shows:

```
dave@dave-desktop:~$ blkid -o value -s UUID
C6BCCC37BCCC23B1
dd2b7f5d-7245-44c8-b691-97cb3b257d93
521e43f3-b789-4241-b5de-5e18b3b1c25b
13a4a3b5-fb50-4bf4-8da7-29ca43023a61
6BE67BA74FC75893 
```


While fstab shows:
```
dave@dave-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=13a4a3b5-fb50-4bf4-8da7-29ca43023a61 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=521e43f3-b789-4241-b5de-5e18b3b1c25b /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=232db074-ad8f-48c2-9fd2-e223a77fd4d0 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
dave@dave-desktop:~$ 
```

I removed the usb mount package as it didn't seem to make any difference.

If anyone can help me get my external DVD/RW recognized, perhaps the bootcd package will install the bootcdwrite script so I can test the package.

Thanks in advance!

Dave ;)

---

### Post by anewguy on 2010-06-27
Since I really don't need a boot floppy, and the user I was trying to help has found an alternate solution, I'll be marking this thread as closed.

Dave ;)

---

