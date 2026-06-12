---
title: "Seagate 1.5 TB FreeAgent Desk Not Mounting in 8.04"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by mwimmersc on 2009-04-15
I' trying to mount a 1.5 TB Seagate external hard drive onto 8.04. Unfortunately it's not showing up on my desktop or under Nautilus. I am aware of an old problem with Seagate's power saving mode on linux, but I don't think this is related. Also, I am an absolute beginner. Any ideas?

---

### Post by Titan8990 on 2009-04-15
Manual mounting for when automount fails:

1) First you must determine the device name of the hard drive. To do this we type: 

```
sudo fdisk -l
```

This will show a formatted list of hard drives and partitions in which you should be able to determine the 1.5TB drive and its partitions. 

Device name of the drive will be like so:

/dev/sdx

Where x is a letter eg - /dev/sda will be your first drive.

Device name of the partition will be like so:

/dev/sdx#

Where # is the number of the partition on the drive eg - /dev/sda1 is the first partition on your first drive.


2) Making a directory to mount the drive. 

In UNIX, drives are simply mounted to locations in the filesystem. The only requirement is that the point you are trying to mount to exists. 

So we create a directory in which to mount the drive:

```
sudo mkdir /media/disk
```


3) Mount the disk. 

Now we can issue the mount command to mount the drive at the location we just created. For this example, I will assume the drive you are trying to mount is /dev/sda1:

```
sudo mount /dev/sda1 /media/disk
```


/dev/sda1 should now be accessible at /media/disk. If you have any problems, post your errors here.

---

### Post by mwimmersc on 2009-04-15
Thanks for your quick reply, Titan!

When I enter "fdisk -l", I see the drive under /dev/sdb1

But when I enter "sudo mount /dev/sdb1 /media/disk", "command not found" comes up.

---

### Post by halitech on 2009-04-15
can we see the entire output of the fdisk command?

---

### Post by mwimmersc on 2009-04-15
How do I post the terminal output? ctrl c didn't work.

---

### Post by lamalex on 2009-04-15
> **mwimmersc said:**
> Thanks for your quick reply, Titan!

When I enter "fdisk -l", I see the drive under /dev/sdb1

But when I enter "sudo mount /dev/sdb1 /media/disk", "command not found" comes up.

unless your system is totally broken, you have mount. Check your spacing. Do you have a space between sudo and mount?

Make sure you're not actually typing the quotes, or dollar signs or anything.

I also prefer to use gnome-mount, it does some of the work for you.
```
gnome-mount -vb --device /dev/sdb1 
```
the -v will give some extra output, which may be useful to diagnose why it's not automounting, and b will prevent it from forking, so you will actually see that extra output.

---

### Post by halitech on 2009-04-15
> **mwimmersc said:**
> How do I post the terminal output? ctrl c didn't work.

CTRL+SHIFT+C or right click copy to get the info from the terminal

---

### Post by mwimmersc on 2009-04-15
```


jimbo@jimbo-laptop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb9602301

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19104   153452848+  83  Linux
/dev/sda2           19105       19457     2835472+   5  Extended
/dev/sda5           19105       19457     2835441   82  Linux swap / Solaris

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x07044cc0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      182401  1465136001    7  HPFS/NTFS
jimbo@jimbo-laptop:~$ 

```

and

```


jimbo@jimbo-laptop:~$ gnome-mount -vb --device /dev/sdb1
gnome-mount 0.8
** Message: Given device '/dev/sdb1' is not a volume or a drive.
jimbo@jimbo-laptop:~$ 

```

---

### Post by halitech on 2009-04-15
surround it with code  /code in [  ]

---

### Post by mwimmersc on 2009-04-15
Also:

```

jimbo@jimbo-laptop:~$ sudo mount/dev/sdb1/media/disk
sudo: mount/dev/sdb1/media/disk: command not found

```

---

### Post by lamalex on 2009-04-15
Ya, your spacing is all messed up. Did you try my gnome-mount command?
If you want to use mount, you need to fix your spacing like such-
```
sudo mount /dev/sdb1 /media/disk
```
/dev/sdb1 is the path to your disk /media/disk is where you want to mount it. Get it?

---

### Post by mwimmersc on 2009-04-15
Sorry about the spacing. Here is the reply to the proper spacing

```

jimbo@jimbo-laptop:~$ sudo mount /dev/sdb1 /media/disk
fuse: failed to access mountpoint /media/disk: No such file or directory

```

Do I need to create /media/disk first? If so, how do I do that?

---

### Post by lamalex on 2009-04-15
Really, just use the gnome-mount command. It will save you a lot of trouble. Look at page 1, i told you the syntax.

---

### Post by halitech on 2009-04-15
```
sudo mkdir /media/disk
```

---

### Post by Titan8990 on 2009-04-15
> **mwimmersc said:**
> Sorry about the spacing. Here is the reply to the proper spacing

```

jimbo@jimbo-laptop:~$ sudo mount /dev/sdb1 /media/disk
fuse: failed to access mountpoint /media/disk: No such file or directory

```

Do I need to create /media/disk first? If so, how do I do that?


It was part 2 of my 3 part reply....

I added code tags for clarity

---

### Post by mwimmersc on 2009-04-15
It worked, just like suggested in the initial reply with mkdir! I can see my Seagate drive now! Thanks everybody! I'll mark it as solved.

---

### Post by halitech on 2009-04-15
Great! now for the big question, can you create folders or copy folders over to it?

---

### Post by mwimmersc on 2009-04-15
Yes, I can! I just did...

BTW: They sell the drive for $100 at Costco at the moment (actually $130, but they have a $30 coupon).

---

### Post by halitech on 2009-04-15
good to hear :)

---

