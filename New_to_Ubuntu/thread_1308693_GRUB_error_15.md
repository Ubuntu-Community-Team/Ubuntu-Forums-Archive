---
title: "GRUB error 15"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by Java Geek on 2009-10-31
Hello, 
When I boot up normally, I receive a simple GRUB error 15. However, when I pop in the live cd, and select boot from first hard disk, I can boot up into my linux machine only (I had dual boot :( ).

However, upon booting up, I type sudo grub
and find this:

```

stephen@Stephen-Desktop:~$ grub
The program 'grub' is currently not installed.  You can install it by typing:
sudo apt-get install grub
grub: command not found

```

So, should I install it, or would that cause me more problems.
I just installed Kubuntu 9.10 onto my machine, so I'm rather curious as to why it is not working...

Thanks!

---

### Post by kansasnoob on 2009-10-31
> **Java Geek said:**
> Hello, 
When I boot up normally, I receive a simple GRUB error 15. However, when I pop in the live cd, and select boot from first hard disk, I can boot up into my linux machine only (I had dual boot :( ).

However, upon booting up, I type sudo grub
and find this:

```

stephen@Stephen-Desktop:~$ grub
The program 'grub' is currently not installed.  You can install it by typing:
sudo apt-get install grub
grub: command not found

```

So, should I install it, or would that cause me more problems.
I just installed Kubuntu 9.10 onto my machine, so I'm rather curious as to why it is not working...

Thanks!

If you install the package "grub" you'll end up with legacy grub. To install grub 2 you need to install the package "grub-pc". Either would work and can be changed later if you change your mind.

Look at the following link keeping in mind that the main instructions are for installing and setting up legacy grub, and the instructions in Appendix 2 are for installing and setting up grub 2:

[http://ubuntuforums.org/showpost.php?p=8071880&postcount=18](http://ubuntuforums.org/showpost.php?p=8071880&postcount=18)

---

### Post by Java Geek on 2009-10-31
I currently have an ext-4 linux file system (as opposed to ext-3) and windows 7 that I need to load. Which one would wourk better?

---

### Post by Java Geek on 2009-10-31
So, I went to install grub-pc and found it was already installed. Should I install grub or grub2 now?

---

### Post by kansasnoob on 2009-10-31
For a simple dual boot I'd go with grub 2.

It should automatically find the Win installation so you'll have no menu.lst editing to do or anything. (it no longer even has that file)

As I said you can easily change from one to the other.

If you went with legacy grub you'd have to manually add Windows to the menu.lst.

In fact you should be able to just:

sudo apt-get install grub-pc
sudo update-grub
sudo grub-install /dev/sda **(replace /dev/sda with your proper destination)**

If you have only one hard drive sda is normally where it would be installed by default, but if you're unsure post the output of:

```
sudo fdisk -l
```

---

### Post by kansasnoob on 2009-10-31
> **Java Geek said:**
> So, I went to install grub-pc and found it was already installed. Should I install grub or grub2 now?

The package grub-pc is grub 2. What happens now when you run:

```
sudo update-grub
```

---

### Post by Java Geek on 2009-10-31
```


Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcec3c9c2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15196   122061838+   7  HPFS/NTFS
/dev/sda2           33419       38913    44138587+   f  W95 Ext'd (LBA)
/dev/sda3           15197       33418   146368215    7  HPFS/NTFS
/dev/sda5           33419       38913    44138556    7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9bd38ccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19083   153284166   83  Linux
/dev/sdb2           19084       19457     3004155    5  Extended
/dev/sdb5           19084       19457     3004123+  82  Linux swap / Solaris

Disk /dev/sdc: 8178 MB, 8178891776 bytes
33 heads, 63 sectors/track, 7683 cylinders
Units = cylinders of 2079 * 512 = 1064448 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        7684     7987183    b  W95 FAT32

```

and
```

stephen@Stephen-Desktop:/boot$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done

```

And really, after following the entire tutorial, there is still no menu.lst...which I KNOW should be there, but it's not!

---

### Post by kansasnoob on 2009-10-31
> **Java Geek said:**
> ```


Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcec3c9c2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15196   122061838+   7  HPFS/NTFS
/dev/sda2           33419       38913    44138587+   f  W95 Ext'd (LBA)
/dev/sda3           15197       33418   146368215    7  HPFS/NTFS
/dev/sda5           33419       38913    44138556    7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9bd38ccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19083   153284166   83  Linux
/dev/sdb2           19084       19457     3004155    5  Extended
/dev/sdb5           19084       19457     3004123+  82  Linux swap / Solaris

Disk /dev/sdc: 8178 MB, 8178891776 bytes
33 heads, 63 sectors/track, 7683 cylinders
Units = cylinders of 2079 * 512 = 1064448 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        7684     7987183    b  W95 FAT32

```

and
```

stephen@Stephen-Desktop:/boot$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done

```

And really, after following the entire tutorial, there is still no menu.lst...which I KNOW should be there, but it's not!

Grub 2 has no menu.lst.

I see you have 3 hard drives. Are any of them external?

---

### Post by Java Geek on 2009-10-31
Oh no... It's seeing my flash disk..

updated:
```

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcec3c9c2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15196   122061838+   7  HPFS/NTFS
/dev/sda2           33419       38913    44138587+   f  W95 Ext'd (LBA)
/dev/sda3           15197       33418   146368215    7  HPFS/NTFS
/dev/sda5           33419       38913    44138556    7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9bd38ccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19083   153284166   83  Linux
/dev/sdb2           19084       19457     3004155    5  Extended
/dev/sdb5           19084       19457     3004123+  82  Linux swap / Solaris
stephen@Stephen-Desktop:~$

```

---

### Post by kansasnoob on 2009-10-31
> **Java Geek said:**
> Oh no... It's seeing my flash disk..

You need to remove that. If that was there during the installation that may be what went wrong, I  hope it didn't hose any data on that disk.

I need a few minutes to try and figure out whether to put grub2 on the mbr of sda or sdb. Expect more questions:)

---

### Post by kansasnoob on 2009-10-31
Had you ever run any Ubuntu or Linux on drive #2 (sdb) previously, or is this a totally new thing?

Also what version of Windows is this? (Sorry if you already said)

---

### Post by Java Geek on 2009-10-31
Yah this was an upgrade gone wrong, so I downloaded 9.10 off the website and wiped my version. I've been using Kubuntu for 2 years! Its not showing... I have Windows 7 and thanks for the help so far.

---

### Post by KinKiac on 2009-10-31
Is your windows on a separate HD than your ubuntu?  I had a problem before where it was giving me a similar error and it turned out that it wasnt reading my HDD properly due to a PSU issue.  I had too many things on one rail and had to reconfigure how I had it set up.  After that it just worked.  However in my case I couldnt boot to anything at all when I got the error.  Loose cable maybe?

---

### Post by Java Geek on 2009-10-31
> **KinKiac said:**
> Is your windows on a separate HD than your ubuntu?  I had a problem before where it was giving me a similar error and it turned out that it wasnt reading my HDD properly due to a PSU issue.  I had too many things on one rail and had to reconfigure how I had it set up.  After that it just worked.  However in my case I couldnt boot to anything at all when I got the error.  Loose cable maybe?

Yes, different drive. No......no loose cable, I can *see* it!:-(

---

### Post by Java Geek on 2009-10-31
Well, all that that did was to add Windows 7 to the GRUB list. The Live CD bootloader found it, but I still get Error 15 if I do not use the Kubuntu CD. Thanks!

---

### Post by kansasnoob on 2009-11-01
Sorry to get side-tracked. My son called and needed to talk. Family first:)

Let me review things.

---

### Post by kansasnoob on 2009-11-01
OK, so we know sda is Windows and sdb is Ubuntu. We can tell that because sda is all NTFS and sdb is all Linux:

> Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcec3c9c2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15196   122061838+   7  HPFS/NTFS
/dev/sda2           33419       38913    44138587+   f  W95 Ext'd (LBA)
/dev/sda3           15197       33418   146368215    7  HPFS/NTFS
/dev/sda5           33419       38913    44138556    7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9bd38ccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19083   153284166   83  Linux
/dev/sdb2           19084       19457     3004155    5  Extended
/dev/sdb5           19084       19457     3004123+  82  Linux swap / Solaris
stephen@Stephen-Desktop:~$

Now keep in mind that grub 2 is new to all of us, but since you had this set up as a dual boot before and you're not getting a Windows error when you try to boot, and you said:

> However, when I pop in the live cd, and select boot from first hard disk, I can boot up into my linux machine only

I'm **thinking** it would do no harm to try:

```
sudo grub-install /dev/sdb
```

Be sure to follow that with:

```
sudo update-grub
```

I'm going to have to set up a two drive system to do some experimenting on I guess, but since that's the Linux drive we can't totally blow things up!

And since choosing "boot from first hard drive" worked we can be fairly certain that the BIOS is already set to boot from sdb first!

---

### Post by Java Geek on 2009-11-01
Thanks! But after last night's experiments, when I use the boot from first drive feature I am able to access Kubuntu and recovery, two memtests and now win 7. It seems as though something is just MISSING from my installed grub that allows it to get started. 

Is grub-pc still in beta?! It says GNU GRUB v. 1.97 Beta 4. (I think). I think I might try legacy just to see what happens. Thanks!

---

### Post by kansasnoob on 2009-11-01
Yes, grub-pc (aka: grub 2) is still in beta.

Nothing wrong with reverting to legacy grub. You will have to manually edit the menu.lst to add Windows but otherwise it should work fine.

---

### Post by Java Geek on 2009-11-01
Done. Thanks!

---

