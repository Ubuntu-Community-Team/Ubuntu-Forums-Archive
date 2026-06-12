---
title: "xp/ubuntu dual boot without corrupting xp"
date: 2010-12-02
forum: New to Ubuntu
---

### Post by david78 on 2010-12-02
Hi

I tried a dual boot install ubuntu / xp with xp (sp3) installed first. I used a 15GB partition at the end of my disk.

Ubuntu worked ok, but there was no boot loader on startup and I couldn't see a way to get back into xp. In the end I had to use MBRwiz to fix the MBR and allow XP to boot. XP works (kind of) ok now but 1000s of files are corrupted. I had my data backed up, but a lot of programs won't work, + i think i'll have to reinstall XP.

I'd like to try install ubuntu again. I've since used testdisk to remove the linux partitions. Now a testdisk analyze looks like this:

```

Disk /dev/sda - 320 GB / 298 GiB - CHS 38913 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0   1  1  3186 254 63   51199092
 2 E extended LBA          3187   0  1 37022 254 63  543575340
 5 L HPFS - NTFS           3187   1  1 37022 254 63  543575277
```After selecting quicksearch in testdisk, it gives this output:

```

Disk /dev/sda - 320 GB / 298 GiB - CHS 38914 255 63
     Partition               Start        End    Size in sectors
* HPFS - NTFS              0   1  1  3186 254 63   51199092
L HPFS - NTFS           3187   1  1 37022 254 63  543575277
L Linux                37023   1  1 38827 254 63   28997262
L Linux Swap           38882 108 11 38913 254 63     507266
```

So my question is, if I install ubuntu again, how do I ensure I can boot back into XP ok, and without corrupting files?

thanks.

---

### Post by oldfred on 2010-12-02
Welcome to the forums

Have you run chkdsk on the NTFS partitions? Is sda1 your windows or sda5? Some say you do not have to defrag before shrinking the windows partition but I find the shrink is quicker if you do. Did you leave 20-30% free space inside the NTFS partition as that is the minimum windows NTFS partitions need.

Not sure why you had issues, the install normally installs grub2 to the MBR and lets you boot either windows or Ubuntu. 

See first link on some issues:
Some examples of installs and issues:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)

---

### Post by nm_geo on 2010-12-02
David I would recommend you get a live USB working with Ubuntu 10.04 or 10.10.  The main Ubuntu webpage explains it really well. Then you can test drive for awhile then decide to install the distro to your HD.  Gparted will works well at shrinking your XP partition and you can actually see graphically what you are doing.  Gparted will be on the live USB just for the use of shrinking and  buidling your new Ubuntu partitions.  Read all the stuff you can and your install will be a snap.  I did exactly what you are wanting to do, and now I am adding more distros to my unallocated space.  By the way our drives are about the same size and I left my XP3 at about 100 GB more than enough for me.

By the way I would heed oldfred's advise about the defraging your HD before you attemp the install and as soon as you shrink your windows stop and reboot into windows and chkdisk will run right away.

---

### Post by david78 on 2010-12-02
After getting back into XP i ran chkdsk. It ran for hours and the recovery filecount was 200,000+ on the D drive.

sda1 is C:, 25GB, where xp is installed
sda5 is D:, 260GB

I had already partitioned the last 15GB using partition magic, so didn't need the ubuntu installer to do the partitioning.

The thing I can't understand is on this screen, it doesn't give you an option for which partition to install to:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=177223&stc=1&d=1291330452[/IMG]


It just says "use entire partition" but which partition? How can you change which partition it's installing to?

many thanks for your help.

---

### Post by oldfred on 2010-12-02
A lot of people click on that and total erase hard drive.

See first link on issues I posted before.

This is why I prefer to use manual partitioning as then you know exactly what partition sizes are and where they are. Then with manual install you choose which partitions to use. (of course if you have a lot of partitions like I do, do not choose wrong one like I once did:))

---

### Post by nm_geo on 2010-12-02
I believe that advanced partition tool would be Gparted. It will let you look closely at your drives.

By the way, I followed oldfred's links when i did my install.

---

### Post by david78 on 2010-12-07
I ran through the exact same ubuntu install process, this time the boot loader showed up + i'm able to get in and out of XP and ubuntu no problem. No idea what I did different but thanks for the help anyway.

---

