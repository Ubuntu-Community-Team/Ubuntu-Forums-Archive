---
title: "mounting my drive removed the directory"
date: 2010-09-19
forum: New to Ubuntu
---

### Post by DeadMoney on 2010-09-19
(This is a double post from the General Help section. It's probly more appropriate for me to post this here.)

I have a 1.5TB sata drive with about 500GB of data I had shared on my  home network. I wanted to streamline my system so that I could just turn  it on and have the drive mount automatically and it would be ready to  go. I followed the instructions on this page:

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

but now I can't see any of my files. Tho the drive does say the 500GB are still "used" for all the good that does me.

1) How do I revise these steps so that I don't lost any data in the future (if there is a next time) and
2) What's the simplest/best way to restore the directory? I've googled it and found a dozen different options.

Thanks!

(P.S. - I'm a smart guy, but very much a n00b so pls break down all advice to a 3rd grade level. :confused:)

---

### Post by sandyd on 2010-09-19
> **DeadMoney said:**
> (This is a double post from the General Help section. It's probly more appropriate for me to post this here.)

I have a 1.5TB sata drive with about 500GB of data I had shared on my  home network. I wanted to streamline my system so that I could just turn  it on and have the drive mount automatically and it would be ready to  go. I followed the instructions on this page:

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

but now I can't see any of my files. Tho the drive does say the 500GB are still "used" for all the good that does me.

1) How do I revise these steps so that I don't lost any data in the future (if there is a next time) and
2) What's the simplest/best way to restore the directory? I've googled it and found a dozen different options.

Thanks!

(P.S. - I'm a smart guy, but very much a n00b so pls break down all advice to a 3rd grade level. :confused:)
hmm...
can you post the output of
```

cat /etc/fstab
```

And no, I don't think your data is lost, its just not showing up....

and also post the output of
```

sudo fdisk -l
```

---

### Post by DeadMoney on 2010-09-19
> **sandyd said:**
> hmm...
can you post the output of
```

cat /etc/fstab
```


fstab is back to the default from initial installation. the drive doesn't show files even when i mount it myself now.

# /etc/fstab: static file system information.
[...comment junk...]
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=0d27db60-86a0-4343-a07f-c4150b0a43cf none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

> **sandyd said:**
> and also post the output of
```

sudo fdisk -l
```


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d9d17

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18706   150253568   83  Linux
/dev/sda2           18706       19458     6034433    5  Extended
/dev/sda5           18706       19458     6034432   82  Linux swap / Solaris

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x049b51ca

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      182402  1465136128    c  W95 FAT32 (LBA)

---

### Post by sandyd on 2010-09-19
> **DeadMoney said:**
> fstab is back to the default from initial installation. the drive doesn't show files even when i mount it myself now.

# /etc/fstab: static file system information.
[...comment junk...]
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=0d27db60-86a0-4343-a07f-c4150b0a43cf none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0




Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d9d17

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18706   150253568   83  Linux
/dev/sda2           18706       19458     6034433    5  Extended
/dev/sda5           18706       19458     6034432   82  Linux swap / Solaris

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x049b51ca

   Device Boot      Start         End      Blocks   Id  System
**/dev/sdb1**   *           1      182402  1465136128    c  **W95 FAT32 **(LBA)
You don't see it, because FAT32 always has wacky permissions. To my knowledge, FAT has never worked very well with Linux.

Well, first....
```

sudo mkdir /media/sdb1
sudo mount -t vfat -o umask=000 /dev/sdb1 /media/sdb1

```The Umask should make everything with 777 permissions.

The disk should now be openable at /media/sdb1

After, if you can access your files, I would advise you to copy them off the drive, and format it with NTFS instead.

---

### Post by DeadMoney on 2010-09-19
done and done but still no files. i can tell it's mounted properly tho from the free space indicated at the bottom of the browser window.

---

### Post by sandyd on 2010-09-19
> **DeadMoney said:**
> done and done but still no files. i can tell it's mounted properly tho from the free space indicated at the bottom of the browser window.
post output of
```

ls /media/sdb1/.*

```

---

### Post by DeadMoney on 2010-09-19
> **sandyd said:**
> post output of
```

ls /media/sdb1/.*

```

ls: cannot access /media/sdb1/.Trash-1000: Input/output error
/media/sdb1/.:
ubuntu server

/media/sdb1/..:
floppy  floppy0  sdb1



..."ubuntu server" is the top level folder on the drive

---

### Post by DeadMoney on 2010-09-19
whoa. something just changed. i can see all my stuff now! o_O

Thank you!!


EDIT: I think it defaulted to FAT32 when I formatted the first time, but now I know better. ;)

---

### Post by sandyd on 2010-09-19
nvm

---

### Post by sandyd on 2010-09-19
> **DeadMoney said:**
> whoa. something just changed. i can see all my stuff now! o_O

Thank you!!


EDIT: I think it defaulted to FAT32 when I formatted the first time, but now I know better. ;)
your welcome :)

---

### Post by DeadMoney on 2010-09-19
See above. Files all show now (I guess we're both confused) but I'm trying to format and NTFS isn't an option.

---

### Post by sandyd on 2010-09-19
> **DeadMoney said:**
> See above. Files all show now (I guess we're both confused) but I'm trying to format and NTFS isn't an option.
you have to install ntfsprogs before the option will show up.

---

### Post by DeadMoney on 2010-09-19
got it already. so it'd be something like:

```
sudo mkntfs -f /dev/sdb1
```

?

---

### Post by bodhi.zazen on 2010-09-19
If you are going to format the drive, why not use a Linux native partition (ext4 ? ).

If you need to share, FAT is fine in Linux, most flash drives are FAT and the advantage is almost every OS can rw FAT.

NTFS is "OK" as well,  can be used cross platform, but if yo run into problems the Linux tools may not fix them, meaning you would need to fix the file system with Windows.

See this link for how to configure fstab to set permissions :

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131") 

=)

---

