---
title: "Unbuntu10.10- Very Slow boot"
date: 2010-10-26
forum: New to Ubuntu
---

### Post by anshulfy on 2010-10-26
Hi Frnds,

I am new to ubuntu. I just had a fresh install of ubuntu10.10. I heard that booting is very fast for it. But I do not find so :( . For me booting take almost 50 sec. 
I have HP laptop, with 1GB ram. Dual operating system with windows XP. I found something about bootchart and installed it, but i dont understand anything from it. I have attached the bootchart. Plz help me. 

Thnaks in advance,
Anshul

---

### Post by lavinog on 2010-10-26
It looks like on that particular boot, there was a file system check that can cause a delay in the boot.

Can you try booting again and send that bootchart so we can see if the fsck occurs again.

Also it looks like ureadahead is not providing any boot caching.
You might need to remove the pack files.

```

sudo rm -v /var/lib/ureadahead/*pack*

```

After removing the pack file(s), the next reboot will take longer, but subsequent reboots should be faster.

---

### Post by lavinog on 2010-10-26
Also can you provide the output of
```

df -h

```
This will show the partition size and the free space available.

---

### Post by anshulfy on 2010-10-26
Hi lavinog,

Thanks for your reply. I am attaching another bootchart after removing the pack files, as suggested by you.

Also the details of partitions size are as follows,

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6               7.4G    4.9G    2.2G    70%   /
none                           491M   308K    491M     1%    /dev
none                            497M    100K    497M     1%    /dev/shm
none                            497M    208K   496M     1%    /var/run
none                           497M       0        497M     0%   /var/lock
/dev/sda9               894M     19M      827M     3%   /boot
/dev/sda7                15G     4.9G     9.1G    35%  /home
/dev/sdb3               245G    126G     119G   52%  /media/DSK3
/dev/sdb1                245G    113G     132G   47%  /media/DSK1
/dev/sdb2                245G   195G     50G    80%  /media/DSK2
/dev/sdb4               200G    167G      33G    84%  /media/DSK4

Thanks for your help.

---

### Post by lavinog on 2010-10-26
The second bootchart shows a 10s improvement.
It still shows fsck, but it looks like it is a ext2 fsck and not a ext4.

Can you do a df -T and see if you are showing ext2 or ext4 for sda6 9 & 7.

If it is ext2, this could be a big part of your speed issue.

---

### Post by anshulfy on 2010-10-27
Hi lavinog,

After doing df -T if find that i have ext 2 for sda6,9 and 7. Can you please explain me, What is the issue and what should I do to have some improvement ? Thanks for your help.

Filesystem    Type   1K-blocks      Used Available Use% Mounted on
/dev/sda6     ext2     7689384   5062960   2235820  70% /
none      devtmpfs      502464       308    502156   1% /dev
none         tmpfs      508036       100    507936   1% /dev/shm
none         tmpfs      508036       208    507828   1% /var/run
none         tmpfs      508036         0    508036   0% /var/lock
/dev/sda7     ext2    15378832   5069380   9528244  35% /home
/dev/sda9     ext2      914501     18988    846720   3% /boot
/dev/sdb2  fuseblk   256003804 204017572  51986232  80% /media/DSK2
/dev/sdb3  fuseblk   256003804 131255384 124748420  52% /media/DSK3
/dev/sdb1  fuseblk   256003772 118128692 137875080  47% /media/DSK1
/dev/sdb4  fuseblk   208748608 174782408  33966200  84% /media/DSK4

---

### Post by lavinog on 2010-10-27
Ext2 does not have journaling and therefore can be extremely slow to fsck.
The versions of Ubuntu prior to 9.04 have used ext3 by default.
Afterwards ext4 was the default filesystem type.

[http://en.wikipedia.org/wiki/Ext2](http://en.wikipedia.org/wiki/Ext2)
[http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)
[http://en.wikipedia.org/wiki/Ext4](http://en.wikipedia.org/wiki/Ext4)

Until recently windows could not read ext4, but apparently recent drivers have been created to change this.
[http://sourceforge.net/projects/ext2read/](http://sourceforge.net/projects/ext2read/)


A ext2 filesystem can be converted to ext4, but without some of the features like extents (which offers some speed improvements)
The following has some information about converting:
[https://ext4.wiki.kernel.org/index.php/Ext4_Howto#Converting_an_ext3_filesystem_to_ext4](https://ext4.wiki.kernel.org/index.php/Ext4_Howto#Converting_an_ext3_filesystem_to_ext4)

To get the full benefit of ext4 you will need to format the filesystems and reinstall.

---

### Post by anshulfy on 2010-10-27
Ok, thank you lavinog. Should I convert all ext2 filesystems to ext4 during reinstallation? Also I would like to ask that my Harddisk shows some bad sectors. I have attached a screen shot showing the badsector information. Can this also affect the speed performance? Are there too many bad sectors in my harddisk? Also please tell me if I can do something about these badsectors?

---

### Post by lavinog on 2010-10-27
The relocated sector count has been under debate whether it is an issue or not.
My stance is that it is not a major issue because the manufacturer specifies a threshold value of 24 and SMART doesn't consider it an issue until the normalized value falls below that value.

Usually laptop users tend to see the relocated sector count increase more than desktop users.  This is usually because the drive gets moved around more.  The harddrive manufactures take this into consideration and reserve dedicated sectors to be used as backup sectors if a sector cannot be written to properly.  It is kind of how lcd manufacturers treat dead pixels.  One dead pixel is not considered an issue because the average consumer will not likely notice it.

Most likely your drive is getting close to its end of life, and drives do tend to be slower over time (ECC errors can slow things down)
Hard drives don't always store your data bit for bit...many times the drive uses statistics and error correction techniques to get the correct data from the drive.  The reported uncorrectable sectors can be a good indication of how reliable the drive is...ideally this should have zero unrecoverable sectors.

Considering that you have an 80g drive, it is likely to be about 4 years old.
Laptop hardrives usually only have a 3 year warranty, and I have replaced a number of drives that were only 3-5 years old.
What is odd thought is that the screenshot provided only shows 2.1 hours of run time.  That doesn't seem right even for a new drive if you just installed ubuntu and you have 5900 powercycles.

My recommendation would be to just keep a good backup plan.

---

### Post by anshulfy on 2010-10-27
ok, thanks. Please answer me, before i go for reinstallation of ubuntu. Should i convert all ext2 to ext4 file system?

---

### Post by lavinog on 2010-10-27
> **anshulfy said:**
> ok, thanks. Please answer me, before i go for reinstallation of ubuntu. Should i convert all ext2 to ext4 file system?

To be honest, I have never really done the conversion before, so I do not know of what type of issues that can occur.

I usually shrink the existing data partitions (like home) then do a fresh install using new partitions.  Once complete I moved the old data to the new home partition, delete the old partition, then either expand the new to take up the remaining space, or just create another partition to be used for specific uses like photos and videos.

rsync is a very handy utility for moving data:
```

rsync -av --progress sourcefolder destinationfolder

```

---

### Post by anshulfy on 2010-10-27
No, I will not do the conversion. I will do a complete fresh installation and format all partition including (/home). Then is there any problem?

---

### Post by lavinog on 2010-10-27
> **anshulfy said:**
> No, I will not do the conversion. I will do a complete fresh installation and format all partition including (/home). Then is there any problem?

I don't think so.
When you do the install, did you manually do the partitioning?  If so there should be a drop down menu when you select the filesystem type to set it to ext4.  Just make sure you do that.

If you do the let installer partition the drive for you, it should be ext4 by default, but I don't think it gives you the ability to have a separate home (unless they just added that feature)

---

### Post by anshulfy on 2010-10-27
Last time when I did the installation, I did the manual partitioning. I made separate partition for /home, / , and /boot). For all the partition I selected the ext2 file system (except swap). In the same way can't I select ext4 again at the time of reinstalling?

---

### Post by lavinog on 2010-10-27
> **anshulfy said:**
>  In the same way can't I select ext4 again at the time of reinstalling?

Are you saying it won't let you select ext4?

---

### Post by anshulfy on 2010-10-27
Hi,

I did a fresh installation with all partition converted to ext4 file system. 

Filesystem    Type   1K-blocks      Used Available Use% Mounted on
/dev/sda6     ext4     7689384   2298892   4999888  32% /
none      devtmpfs      502440       308    502132   1% /dev
none         tmpfs      508036       168    507868   1% /dev/shm
none         tmpfs      508036        84    507952   1% /var/run
none         tmpfs      508036         0    508036   0% /var/lock
/dev/sda8     ext4      472036     29436    418229   7% /boot
/dev/sda7     ext4    15859672    212588  14841452   2% /home
/dev/sdb3  fuseblk   256003804 131255384 124748420  52% /media/DSK3
/dev/sdb1  fuseblk   256003772 122923792 133079980  49% /media/DSK1
/dev/sdb2  fuseblk   256003804 204017572  51986232  80% /media/DSK2
/dev/sdb4  fuseblk   208748608 174782408  33966200  84% /media/DSK4

Even after this I dont see much improvement in boottime :( . Bootchart is also attached. Please look at the issue.

---

### Post by lavinog on 2010-10-27
That last bootchart shows the boot time at 32.32s while the original bootchart showed 49.2s.

I suspect that the ureadahead data is old since the disk utilizition appears to be spread out some.

Make sure all of the updates have been applied, then purge the old pack files:
```

sudo rm -v /var/lib/ureadahead/*pack*

```
You might get an error that no files exist (normally, applying updates to system packages are supposed to remove these files.)

The next boot will create new pack files, then the following boot should be faster.


After that, I don't think it is going to get much faster than that.

The 10s boot time is based on SSD drives, and the time is based on the time from the grub loader to the user desktop.

Also, you should uninstall bootchart when you are not needing it, as it contributes to some delay in booting.


Does your laptop have an nvidia card?

---

### Post by anshulfy on 2010-10-28
Hi,

Thanks for your help. There seems to be very little improvement (2sec.) after creating new page file. Bootchart I also attached.

Also to answer you, I don't have any nvidia card. While booting I see black screen for sometime. I saw many threads about  it. Mentioning some problem with nvidia card and plymouthd. But i could  not understood it.

---

