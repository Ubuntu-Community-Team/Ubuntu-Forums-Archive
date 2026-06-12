---
title: "Not enough space for upgrade!"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by Phospholipid on 2009-11-02
Hi there all, 
I've been using ubuntu for a while but not really been trying to keep my disk usage down so I know nothing about what I need and what I don't.

When I went to upgrade to karmic from jaunty, using the update manager, I didn't have enough room on my hard drive. 

being the concerned owner I checked using the disk usage analyser and found that I had used 5.7gb out of 6.7gb (I thought my netbook had an 8gb harddrive) I need to make more space for the install which tells me I need to find another gigabyte.  

If anyone could help me shave down my hd usage enough to install karmic I will be quite pleased. 

Cheers
Phospholipid

---

### Post by Roger Allott on 2009-11-02
How much of that 5.7Gb is your /home folder taking up?

---

### Post by jrrader on 2009-11-02
Different file systems will leave you with different amounts of usable space so even if you have an 8GB hard drive, you will never get to use all 8GB.   Microsoft's NTFS will cause less space loss than ext3, but needs more maintenance.

I wouldn't be able to work with an 8GB HD.  I just got a terabyte HDD for $80.  Maybe get yourself a little more working room and do a clean install (you wouldn't need a TB for a netbook, but some extra room would still be nice).

---

### Post by kansasnoob on 2009-11-02
Post the output from terminal of:

```
df -H
```

and:

```
sudo fdisk -l
```

BTW that's a lower case L.

---

### Post by Phospholipid on 2009-11-02
Roger Allott: It's come up with 2.5gb. 

jrrader: Thanks for the info, although I know that different filesystems take up different space physically I don't know what deficit there can be. 

All of my stuff is backed up so something. 

Cheers,
Jesus

---

### Post by Phospholipid on 2009-11-02
kansasnoob: 

jak@MrPump:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             6.7G  5.7G  671M  90% /
tmpfs                 497M     0  497M   0% /lib/init/rw
varrun                497M  120K  497M   1% /var/run
varlock               497M     0  497M   0% /var/lock
udev                  497M  144K  497M   1% /dev
tmpfs                 497M  276K  497M   1% /dev/shm
lrm                   497M  2.2M  495M   1% /lib/modules/2.6.28-16-generic/volatile
jak@MrPump:~$ sudo fdisk -l

Disk /dev/sda: 7682 MB, 7682605056 bytes
255 heads, 63 sectors/track, 934 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x010fc343

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         887     7124796   83  Linux
/dev/sda2             888         934      377527+   5  Extended
/dev/sda5             888         934      377496   82  Linux swap / Solaris
jak@MrPump:~$ 

I hope you can see what the problem is.

---

