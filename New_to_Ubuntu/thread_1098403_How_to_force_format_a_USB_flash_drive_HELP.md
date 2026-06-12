---
title: "How to force format a USB flash drive HELP?"
date: 2009-03-17
forum: New to Ubuntu
---

### Post by 11010110 on 2009-03-17
Hi everyone, 

I recently tried to turn a 4Gb flash drive into a portable version ubuntu with persistance. I tried the default options for the program that i decided to use (Portable Linux) and when i used the drive i noticed that I only had 250Mb of space to save changes to the OS. I tried re-running the portable linux program to give me more space and it would not go because it said that the drive contained a mounted filesystem. I have tried unmounting it and re-running it and I have had no luck. Also I have tried to use Gparted to reformat it and It shows that there is a 705Mb space with an unknown filesystem (where the ISO for Ubuntu is stored I presume). This 705Mb partition will not under any circumstances format. It just keeps giving me an error. I was wondering if there was a way that I could force a format onto it and just skip past any errors and fully format the drive. 

Thank you very much in advance for any replies. Any help is appriciated. 

Thanks

---

### Post by Rolcol on 2009-03-17
If it's unmounted, you can try to zero the entire drive so no traces of information exists.  It may take a while and you can cancel if all you want to do is erase the partition table.  Replace /dev/sdb with the device name.

```
sudo dd if=/dev/zero of=/dev/sdb
```
The Partition Table (Master Boot Record) resides in the first 512 bytes of the drive.  If you only want to clear the partition table without having to cancel, you can slightly modify the command.
```
sudo dd if=/dev/zero of=/dev/sdb bs=512 count=1
```

This should be enough to allow GParted to format and partition.

[COLOR="Red"]**Caution:  Replacing the output file (of=/dev/sdb) with the wrong device can cause data loss**[/COLOR]

---

### Post by jimmy the saint on 2009-03-17
couple things to double check:

you aren't booting from the drive and attempting to reformat it at the same time?  If so, it may work better to boot into a live cd and just wipe the drive that way.

Also, double check that the partition is unmounted.

---

### Post by lindsay7 on 2009-03-17
If you get to a windows machine, this tool will clean and format the usb back to factory settings, HP USB Disk Storage Format Tool v2.1.8. Search for it on the internert.

---

### Post by 11010110 on 2009-03-17
Hi again everyone,

Thank you to everyone who replied. I used a mixture of gparted, fdisk, windows formater and the HP tool. I FINALLY through a combination of those tools was able to get past the error. I have never seen anything like that lol. All is well now and I finally have my portable ubuntu!

Thanks again everyone!

---

