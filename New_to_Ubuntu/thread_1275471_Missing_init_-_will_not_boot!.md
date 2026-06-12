---
title: "Missing init - will not boot!"
date: 2009-09-25
forum: New to Ubuntu
---

### Post by RichardLi on 2009-09-25
Hi all, a couple months I got my first Ubuntu (9.04) Linux system running with the help of these forums, so firstly thanks again!
 
Now I have run into a problem, my laptop mysteriously crashed (I was running [http://www.metronomeonline.com/](http://www.metronomeonline.com/) with speakers plugged in). Upon trying to start it up again, it would not start. Instead it gave me some error messages at the end included:
 
target filesystem doesn't have /sbin/init
 
I looked up a lot of solutions already for previous problems, but this one I have not found a solution yet. I have seen people with this problem exactly, but they use words in their solution I don't understand.
 
Info:
Windows Vista and Ubuntu 9.04 dual booting
 
Thanks in advanced.
 
Richard

---

### Post by RichardLi on 2009-09-26
Bump... anyone?
 
Richard

---

### Post by lisati on 2009-09-26
Is reinstalling an option?

---

### Post by baskar007 on 2009-09-26
Best is Reinstalling?


and another way:
Do you can boot ur system in windows? If yes then pass to nex step.

I dont Know, Is this work or not ,But it's newbie idea


Do you have LiveUbuntu ?
or you friends have Ubuntu

try to copy files and directory's ( /sbin/init) from theirs PC to yours ! 

Copy those file to linux partitions via windows.
[http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)    use this for accessing Linux partitions from Windows.

---

### Post by kansasnoob on 2009-09-26
I wonder if this is a true dual-boot or a Wubi install? 

If you can run from Live CD, the output of this command should help us know:

```
sudo fdisk -l
```

BTW that's a lower case L.

---

### Post by RichardLi on 2009-10-02
lisati - I don't think reinstallation really is an option, I don't want to run the possibility of loss information.

baskar - I can boot into Windows, yes. That sounds like a good idea - I do have the Live CD - but I'm not sure how to copy all the files. Looking at the file system from booting Live, it appears I *do* have an init file?

kansasnoob - I'm not sure the difference, I think it is a Wubi install. I get

Disk /dev/sda: 160.0 GB
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

Device boot   start   end   blocks   Id   System
/dev/sda1      1   5  40131  de  Dell TUlitiy
/dev/sda2     6  1280  10240000  7  HPFS/NTFS
/dev/sda3  *  1280  13057  94599392+  7  HPFS/NTFS
/dev/sda4     16015  19458  27656569  f  W95 Ext'd (LBA)
/dev/sda5     19131  19458  2619392  dd  Unknown
/dev/sda6     16015  19109  24860524+  83  Linux
/dev/sda7     19110  19130  168651  82  Linux swap/Solaris

Thanks!

Richard

---

### Post by bwang on 2009-10-03
> I have seen people with this problem exactly, but they use words in their solution I don't understand.

Which people and what websites?
To check for the presence of init, you have to look at the original installation. Verify that you are not checking the CD.

---

### Post by RichardLi on 2009-10-03
Such as this person: [http://ubuntuforums.org/showthread.php?t=241101](http://ubuntuforums.org/showthread.php?t=241101)

To check the original installation, I need to mount it correct? It appears I cannot mount it -

"mount: wrong fs type, bad option, bad superblock on /dev/sda6, missing codepage or helper program, or other error In some cases useful info is found in syslog - try dmesg | tail or so"

Thanks!

---

