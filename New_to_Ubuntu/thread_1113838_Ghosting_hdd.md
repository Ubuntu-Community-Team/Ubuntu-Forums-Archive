---
title: "Ghosting hdd"
date: 2009-04-02
forum: New to Ubuntu
---

### Post by Drenriza on 2009-04-02
How can i take an exact copy of a hdd with the ubuntu command-list?

The hdd has made a head-crash and i wanna try to safe the data. I know that in ubuntu their is a program auto-installed that can copy the files 1bit at a time. But i don't know the codes. Hope some1 can help me

Thanks

---

### Post by scorp123 on 2009-04-02
```
sudo dd if=/dev/sdXX of=/path/to/output.file
```

Replace "sdXX" with the correct device name and number for your harddrive, e.g. /dev/sda1 or whatever is correct for your system. WARNING: see what hyper_ch wrote: ONLY do this when the file system is NOT in use, e.g. using a Live CD!! You can't boot into your OS and then do this while the harddrive is active!

Once you have that image file you can "loop-mount" it and take a look at what's inside, e.g. ```
sudo mount -o loop /path/to/file/you/took/with/dd /mnt/olddisk
```

The mointpoint "/mnt/olddisk" very likely doesn't exist on your system. Either use a mountpoint that is valid or simply create that mountpoint directory and then try again: ```
sudo mkdir /mnt/olddisk
```

---

### Post by hyper_ch on 2009-04-02
but use this only while /dev/sdXX is not mounted.

---

### Post by lkraemer on 2009-04-03
You could always download the ISO of Clonezilla, burn the ISO as
Disk at Once (DAO) and at 4x or 8x.  Power off, install a bare drive
to receive the data, boot Clonezilla, and copy Drive to Drive, or
Partition to Partition.

Clonezilla is very easy to use and works wonderful.

Windows software similar to Clonezilla is xxclone

If the drive is FAT32 SpinRite ver 5 will try, and repair the data.
Newer versions of Spinrite (Windows Software) will work on NTFS.
Is your DATA's value worth $80.00?

lkraemer

---

### Post by asmoore82 on 2009-04-03
> **lkraemer said:**
> Clonezilla is very easy to use and works wonderful

I highly recommend Clonezilla as well - [http://clonezilla.org/](http://clonezilla.org/)

it is a sparse cloning tool so there is a small chance that you could
pull a complete image of a near-dead drive with no data loss.

---

