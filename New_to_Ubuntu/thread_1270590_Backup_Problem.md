---
title: "Backup Problem"
date: 2009-09-19
forum: New to Ubuntu
---

### Post by cmcanulty on 2009-09-19
I have been trying to backup all day. I have an external hard drive and have installed the NTFS config tool and Mount Manager. Sometimes the HD shows up on my computer, usually not. I have tried about every backup pkg but none can find the drive. A few time a backup will start but never finish just errors.

---

### Post by PrivateSNAFU on 2009-09-19
can you see the drive in dmesg?
If so does it auto mount, it could be needing force umount before being repluged in.

---

### Post by RedSingularity on 2009-09-19
Have you tried the clonezilla program?

---

### Post by cmcanulty on 2009-09-21
Clonezilla is only good for restoring the whole shebang. I like to be able to access the files on my ext HD. Can you explain how to do dmesg and how to force mount or unmount, thanks.

---

### Post by LewRockwell on 2009-09-21
> **cmcanulty said:**
> Clonezilla is only good for restoring the whole shebang. I like to be able to access the files on my ext HD.

Clonezilla can clone both complete hard drives AND individual partitions

Clonezilla can/will ask you whether you want an exact clone or an image

If you desire easy access to your data then you will want an exact clone

If you don't need that then the image will probably be the way to go
(although you will then need clonezilla to restore from that image)

[http://www.clonezilla.org/](http://www.clonezilla.org/)

.

---

### Post by cmcanulty on 2009-09-21
OK I will try that if I can get Ubuntu to recognize my hard drive, I have tried everything and several utilities now it won't even see my flash drive. Between that and no wireless I am quite frustrated I hate windows but at least the wireless and ext drives worked without a constant hassle.

---

### Post by Darkwing-Duck on 2009-09-23
Here is another option for backing up your system. Take a look at it and see if it will help you.

[http://gwos.org/udsf/doku.php/software:backup:rsync](http://gwos.org/udsf/doku.php/software:backup:rsync)

---

### Post by A_Fiachra on 2009-09-23
> **cmcanulty said:**
> OK I will try that if I can get Ubuntu to recognize my hard drive, I have tried everything and several utilities now it won't even see my flash drive. Between that and no wireless I am quite frustrated I hate windows but at least the wireless and ext drives worked without a constant hassle.


Try mounting the usb device by hand:

[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

At least see what happens when you do:

```

sudo lsusb

sudo fdisk -l

mount


```


hth

---

### Post by cmcanulty on 2009-09-24
I tried rsync and it seemed to work but the backup constantly stopped as the USB ext HD light went out (works fine in windows). Or once it went all the way and the backup was 6GB short and when I tried to open the backup folders they all had file corrupted and empty error message even though properties said several GBs . It shouldn't be this hard to do a simple backup of 78GB

---

### Post by cmcanulty on 2009-09-24
Here are the command outputs. However remember it mounts usually just won't stay mounted. I see it in my computer then rsync  (actually I use grsync) stops and when I check it is gone from my computer. Also maybe I don't have the options set correctly for grsync as it has several fairly complicated  check boxes and I am not sure what to pick.Here is the output, I had to devide it into 2 attachments as it was too long for 1

---

### Post by cmcanulty on 2009-09-24
Oh boy I had a long reply and I guess it got lost. So here it is again, it intermittently loads the extHD backup starts then it unmounts and backup ends. Once I got it to go all the way but backup was 6+ GB short and when I tried to check the folders props showed several GBs but folder was 0 KB and error message corrupted. Here is the terminal output in 2 files as it was too long for 1

---

### Post by LewRockwell on 2009-09-24
> **cmcanulty said:**
> Oh boy I had a long reply and I guess it got lost.

yes, when in doubt about a time-out you can quickly highlight all and copy to preserve your work

actually, it becomes a habit and probably a good habit at that


anyways...

backups...

utilize a stand-alone product that can work with many data sets and file systems(clonezilla)

if you need continual backup protection then a raid setup might work well

.

---

