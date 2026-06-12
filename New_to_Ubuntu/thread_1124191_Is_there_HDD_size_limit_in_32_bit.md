---
title: "Is there HDD size limit in 32 bit?"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by k3lt01 on 2009-04-13
Basically my title is my question but a little background is probably in order.

My signature shows my "old" desktop systems basic specs. A couple of months ago I purchased a 1TB SATA HDD because I am slowly running out of space. This weekend I have tried numerous times to install various versions of 32 bit (i386) Ubuntu onto the 1TB HDD. I have tried, unsuccessfully, to set it up with a 10GB /, 2 GB Swap, and the rest as /home.

My problem occurs when it goes to format the partitions in either ext4 Jaunty, or ext3 Hardy and Intrepid. Jaunty keeps returning an error message that says it failed to create an ext3 partition remember I wanted it to be ext4 not ext3. The other 2 just say it failed to format a partition in sda6 or whatever the installer named the /home partition (it is usually 6 but has been 5).

I have never tried to install Ubuntu on a SATA drive let alone any drive so big. RedHat wont even see the drive and neither will Vista so it shows how good Ubuntu is that it sees it and at leasts tries to install onto it.

My only thoughts are that 
1. the 32 bit version cant handle such a big partition, or 
2. that my motherboard is causing a problem, or (I have since tried this in 2 computers with the same outcome so I think that squashes that idea).
3. there is a problem with my new 1TB HDD.

Does anyone have any ideas?
Thanks in advance.

Michael.

---

### Post by ELD on 2009-04-13
Is your partitioning done right? I have a 500GB hard drive and it works fine. Remember there are differences between extended, logical and all that )not that i know haha!).

Is there a way to run the installer in terminal and give us the output? You could even try gparted to make the partitions -> [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

It is a live cd partitioner, very useful, i am going to use it today or tomorrow to sort out my partitions (i have free space of like 340GB which i can't use as my partitions are messed up and all over the place woops!).

---

### Post by deanjm1963 on 2009-04-13
I've had similar problems with very large ext3 partitions.

Now I make a fairly small home partition e.g. 20gb, and make other partitions to fill my disk, e.g. 200gb (/stuff) 300gb (/video) etc.

Personally I wouldn't trust ANY file system with such a large partition to hold all my data. If root and home go you at least have all your data on other partitions.

---

### Post by hyper_ch on 2009-04-13
paste the output of

```

sudo fdisk -l

```
and
```

df -h

```

---

### Post by k3lt01 on 2009-04-13
ELD: I have use 2 different versions of Gparted trying to format to ext3 and ext4. It simply fails to do the job.

deanjm1963: Somehow I think your solution will be the eventual outcome. The problem with that will be the tidying up afterwards (i.e. the linking back to the real /home folder).

I don't even know enough about the other file system formats to even consider them.

---

### Post by k3lt01 on 2009-04-13
> **hyper_ch said:**
> paste the output of

```

sudo fdisk -l

```
and
```

df -h

```Hyper: I shall do that as soon as I have time, thanks for your input.

---

### Post by deanjm1963 on 2009-04-13
> **k3lt01 said:**
> deanjm1963: Somehow I think your solution will be the eventual outcome. The problem with that will be the tidying up afterwards (i.e. the linking back to the real /home folder).

What do you mean by linking back to the home folder? I just make sure those extra partitions have write permissions, create a bookmark/shortcut in nautilus and "bobs ya uncle"

to give yourself ownership of a partition open a terminal and type

```
sudo chown -R yourname:yourname /nameofpartition
sudo chmod -R 755 /nameofpartition

```

---

### Post by k3lt01 on 2009-04-13
> **deanjm1963 said:**
> What do you mean by linking back to the home folder?Exactly what you went on to type. I have been through that before. I had to create a symlink in my old setup for my 200gb disk.

---

### Post by k3lt01 on 2009-04-13
Because the relevant machine doesn't have net access this is a total retype not a cut and paste

> **hyper_ch said:**
> paste the output of

```

sudo fdisk -l

```
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 headss, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 =8225280 bytes
Disk identifier: 0x00072d35

Device Boot     Start     End     Blocks    ID     System
/dev/sda1           1    1216    9767488+   83     Linux
/dev/sda2        1217    1459    1951897+   82     Linux Swap / Solaris
/dev/sda3        1460  121601  965040615    83     Linux
ubuntu@ubuntu:~$
```

> **hyper_ch said:**
> ```

df -h

```

```
ubuntu@ubuntu:~$ df -h
Filesystem       Size  Used  Avail  Use%  Mounted on
tmpfs            252M   17M   236M    7%  /lib/modules/2.6.24-19-generic/volatile
tmpfs            252M   17M   236M    7%  /lib/modules/2.6.24-19-generic/volatile
varrun           252M   92K   252M    1%  /var/run
varlock          252M     0   252M    0%  /var/lock
udev             252M   44K   252M    1%  /dev
devshm           252M   12K   252M    1%  /dev/shm
tmpfs            252M   16K   252M    1%  /tmp
gvfs-fuse-daemon 252M   14M   239M    6%  /home/ubuntu/.gvfs
ubuntu@ubuntu:~$
```I am surprised by the df -h output. Does this mean the format actually worked and the real failure was writing the system files?

---

### Post by CatKiller on 2009-04-13
It's not a 32-bit limit, but there is a capacity limit. If your BIOS isn't using 48-bit LBA then you cannot address a partition that is larger than 137 GB (128GiB). You may need to either upgrade your BIOS or set an option in the BIOS to enable 48-bit addressing.

---

### Post by k3lt01 on 2009-04-13
> **CatKiller said:**
> It's not a 32-bit limit, but there is a capacity limit. If your BIOS isn't using 48-bit LBA then you cannot address a partition that is larger than 137 GB (128GiB). You may need to either upgrade your BIOS or set an option in the BIOS to enable 48-bit addressing.
That is exactly why I mentioned my signature, I have a 200GB partition so the 137GB 48 bit LBA BIOS limit does not apply to this situation.

---

### Post by LowSky on 2009-04-13
Do you have the same issue if you try to create the partition using FAT32 or NTFS?

I just formated a 750GB drive. the size should not be an issue. Large Hard drives have there place like in media centers or data servers.

It could be a bad hard drive, it does happen. Also Windows might not see it because it does not have drivers for the newer drive, a friend of mine ran into that issue.

---

### Post by askreet on 2009-04-13
Hrm, scratch that.

---

### Post by k3lt01 on 2009-04-13
LowSky: I'll try NTFS and maybe another file format type tonight. I am worried it is a bad HDD, I have never had difficulty with Western Digital drives but I know drives can be bad out of the box. Unfortunately its a pretty expensive issue if thats the case.

---

### Post by askreet on 2009-04-14
> **k3lt01 said:**
> LowSky: I'll try NTFS and maybe another file format type tonight. I am worried it is a bad HDD, I have never had difficulty with Western Digital drives but I know drives can be bad out of the box. Unfortunately its a pretty expensive issue if thats the case.

All components have a failure rate.  I find it funny that some people say "I have never had a problem with western digital," yet **I** have lost at least 7 WD drives and won't buy one :)  I once built a raid-5 with 4 disks and 3 of them died in the same week!

It's just bad timing, all manufacturers have bad runs.

I like Seagate ;)

- Kyle

---

### Post by LowSky on 2009-04-14
> **askreet said:**
> 
It's just bad timing, all manufacturers have bad runs.

I like Seagate ;)


Many are disappointed with the newer  1TB Seagate drives... 

[http://www.newegg.com/Product/ProductReview.aspx?Item=N82E16822148299](http://www.newegg.com/Product/ProductReview.aspx?Item=N82E16822148299)

[http://www.newegg.com/Product/ProductReview.aspx?Item=N82E16822148373](http://www.newegg.com/Product/ProductReview.aspx?Item=N82E16822148373)

It is because of they new way they have to manufacture the drives. Using lead free solder has horrible effects on very tiny electronics. this doesn't just effect Seagate or hard drvie manufacturer, but many other tech companies 
[http://en.wikipedia.org/wiki/Whisker_(metallurgy](http://en.wikipedia.org/wiki/Whisker_(metallurgy))

---

### Post by lavinog on 2009-04-15
> **LowSky said:**
> Many are disappointed with the newer  1TB Seagate drives... 

[http://www.newegg.com/Product/ProductReview.aspx?Item=N82E16822148299](http://www.newegg.com/Product/ProductReview.aspx?Item=N82E16822148299)

[http://www.newegg.com/Product/ProductReview.aspx?Item=N82E16822148373](http://www.newegg.com/Product/ProductReview.aspx?Item=N82E16822148373)

It is because of they new way they have to manufacture the drives. Using lead free solder has horrible effects on very tiny electronics. this doesn't just effect Seagate or hard drvie manufacturer, but many other tech companies 
[http://en.wikipedia.org/wiki/Whisker_(metallurgy](http://en.wikipedia.org/wiki/Whisker_(metallurgy))

Seagates issue seems to be a serious bug in the firmware. I know this because my 500g drive died recently. The bug causes the drive to panic when the onboard event log fills (can range from 1 Month to a year depending on use). Luckly the drive can be repaired and the data should still be intact. Googling '0 LBA' shows how to fix the issue.
If you have a seagate drive with firmware SD15 you should go to seagate's site and get the update. (note there is another firmware version that is affected also...so go to seagate's site if you have a seagate drive 500Gb or 1Tb)

---

### Post by k3lt01 on 2009-05-09
Just thought I'd fill you all in on what has happened since my last post in this thread. I tried multiple file formats and nothing worked. I took the drive back to where I purchased it (6 months to the day after purchasing it to). They quickly checked it out and pronounced it dead on arrival 8 days later I got my replacement free of charge and this morning I am transferring approximately 440GB worth of files of my 500GB external drive so I can clean it up.

---

### Post by rhcm123 on 2009-05-09
> **LowSky said:**
> Do you have the same issue if you try to create the partition using FAT32 or NTFS?

Go with NTFS, fat32 only supports 4 GiB drives

EDIT: Just read your post above mine - that's great. (heck, i try and help and it's already been fixed :D)

---

