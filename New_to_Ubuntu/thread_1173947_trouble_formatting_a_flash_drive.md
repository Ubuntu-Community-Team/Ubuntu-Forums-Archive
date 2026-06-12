---
title: "trouble formatting a flash drive"
date: 2009-05-30
forum: New to Ubuntu
---

### Post by kd0afk on 2009-05-30
I have a 2Gig PNY USB flash drive that I am trying to put SGD on. I went into untebootin and tried it, got this error:   p, li { white-space: pre-wrap; }  [COLOR=Red]No USB flash drives were found. If you have already inserted a USB drive, try reformatting it as FAT32.[/COLOR]
[COLOR=Red][COLOR=Black]So I tried to use Gnome Format to format the drive. This is the error I get when I do that.[/COLOR][/COLOR]
[COLOR=Red]Error opening /dev/sdb: Permission denied[/COLOR]

How do I run this in terminal as SU to do this?

---

### Post by Volt9000 on 2009-05-30
Type this:

```

sudo mkdosfs -F 32 /dev/sdb

```

That's assuming your USB device is indeed /dev/sdb. Make sure of this so you don't accidentally format one of your hard drives!

---

### Post by kd0afk on 2009-05-30
> **Volt9000 said:**
> Type this:

```

sudo mkdosfs -F 32 /dev/sdb

```That's assuming your USB device is indeed /dev/sdb. Make sure of this so you don't accidentally format one of your hard drives!
How do I know what it is called? I have tried sysinfo, properties, looking at the file path. It just is called "disk"

And it is mounted in path /media/disk

---

### Post by Volt9000 on 2009-05-30
First to find out what it is, type

```

df

```

This will give you a list of the filesystem in the first column and its corresponding mount point in the far right column. Look for "/media/disk" in the far right column and see which device it matches up with in the far left column.

Now that you have the device information, unmount the USB-- you can't format something which is mounted (AFAIK.)

So to unmount it:

```

sudo umount /media/disk 

```

Now just type the mkdosfs command in my last post, substituting the device path with your USB.

---

### Post by kd0afk on 2009-05-30
That worked. I now have a bootable Super Grub Disk. One thing that I noticed with GnomeFormat is that it was saying that it couldn't find /dev/sda. And when I did the df command in terminal, it was listed as dev/sda1. How can I fix it so GnomeFormat will get the name right and be able to find it?

---

### Post by Volt9000 on 2009-05-30
> **kd0afk said:**
> That worked. I now have a bootable Super Grub Disk. One thing that I noticed with GnomeFormat is that it was saying that it couldn't find /dev/sda. And when I did the df command in terminal, it was listed as dev/sda1. How can I fix it so GnomeFormat will get the name right and be able to find it?

Devices without any numerical suffixes, i.e. /dev/sda, refer to the "root device", i.e. the device itself. The numerical suffixes refer to partitions on that particular device, so /dev/sda1 is the first partition of /dev/sda, /dev/sda2 is the second, etc.

I've never used GnomeFormat so I can't say, but it looks like it's specifically made for formatting external media. That being said, /dev/sda is probably your hard drive so you can't format it with this program.

Just to be sure, could you please paste the output of the command

```

df -h

```

If you want a more general, comprehensive formatting utility, I would suggest gparted, which you can install from the repos:

```

sudo apt-get install gparted

```

---

### Post by kd0afk on 2009-05-30
I am very sorry. I meant to say that the USB drive is dev/sdb1 not sda1. here is the output from terminal:

shawn@HAL:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              36G  5.1G   29G  15% /
tmpfs                 241M     0  241M   0% /lib/init/rw
varrun                241M  112K  241M   1% /var/run
varlock               241M     0  241M   0% /var/lock
udev                  241M  156K  241M   1% /dev
tmpfs                 241M  296K  241M   1% /dev/shm
lrm                   241M  2.4M  239M   1% /lib/modules/2.6.28-12-generic/volatile
/dev/sdb1             2.0G  1.6M  2.0G   1% /media/disk

---

### Post by Volt9000 on 2009-05-30
Alright, so based on your output, /dev/sdb is definitely your USB stick-- /dev/sda is your hard drive.

Probably the reason that /dev/sdb1 is listed instead of /dev/sdb is because there's only a single partition on the USB stick and that's what the program is going to format. That's fine.

To get a list of all partitions everywhere, type

```

sudo fdisk -l

```

This will show you all devices and partitions detected by the system, mounted or not.

---

### Post by kd0afk on 2009-05-30
Thanks

---

