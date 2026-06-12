---
title: "ext4 partition not showing in Computer file browser"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by nishanvincent on 2009-11-01
Hi guys, just a small query. I just installed Ubuntu 9.10 and used to live cd and created partion using gparted available in the live cd. Now the issue is if I see the partion system in gparted its showing me correctly; but if I look at my computer file browser it is not showing one of my ext4 partition.
I have attached the screenshot of the gparted and the computer file browser, please let me know how can I fix this issue.

sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x54065e39

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1019     8185086    5  Extended
/dev/sda2            1020        5394    35142187+   6  FAT16
/dev/sda3            5395        5488      755055   82  Linux swap / Solaris
/dev/sda4            5489        9729    34065832+  83  Linux
/dev/sda5               1        1019     8185054+  83  Linux
--------------------------------------------------------------------------------------

thankx in advance.

---

### Post by mikewhatever on 2009-11-01
Is that a functional boot partition? If so, you can simply add a bookmark to Nautilus, pointing to /boot. By the way, 32GB is way to large for a boot partition. Depending on the number of kernel stored there, you'd probably never need more then 2-3GB.

---

### Post by ranch hand on 2009-11-01
You could also check to see if it is in your /etc/fstab.  It will mount then.

---

### Post by nishanvincent on 2009-11-01
hi, Did not not understand much on what you guys suggested. Please tell me in simple language what can I do to view and use this partition.

---

### Post by Locke_99GS on 2009-11-01
Both of your ext4 filesystems are already mounted. Once will be mounted at /boot, the other will be mounted at / (everything else)

Click on "filesystem" from within "Computer", and you'll see that /boot and everything else is there.

---

### Post by nishanvincent on 2009-11-01
Thankx got in boot folder under file system. So is there any pssiblity to bring this partition in the main computer file browser screen.

---

### Post by ranch hand on 2009-11-02
Make sure it is in your /ect/fstab.

---

### Post by nishanvincent on 2009-11-02
Can you please tell me how do I do that.

> Make sure it is in your /ect/fstab. 

All I need is that this ext4 partition should be shown in the computer file browser. Currently this partition is showing me inside the file system under boot folder.

---

### Post by ranch hand on 2009-11-02
Have you looked for it in your /etc/fstab file?  If it is there it should show in the the left column of our home menu.

If it is not there then it should be added.

If you have not looked why don't you;
```

cat /etc/fstab

```
and post the results here.

---

### Post by nishanvincent on 2009-11-02
> Have you looked for it in your /etc/fstab file? If it is there it should show in the the left column of our home menu.

If it is not there then it should be added.

If you have not looked why don't you;
Code:

cat /etc/fstab

and post the results here.

Here is the output of cat /etc/fstab

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=937f7390-1566-4d50-b986-268078dda9c1 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda4 during installation
UUID=2317a7ac-9cab-4338-aaa1-93cb71895e4d /boot           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=8b3a60fe-3161-469f-8e09-cc84d65fd07e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

-----------------------------------------------------------------

I think its there in /etc/fstab, so can we make to show in the computer file browser?

---

### Post by ranch hand on 2009-11-02
Well, that looks good.

Frankly, I do not understand why it is not showing up on the left column in your home file.

Just out of curiousity, why in flinderation do you have that huge a /boot partition?.  That is big enough for a whole OS.

I will have to look into this a bit more, right now I am trying to get set up for 10.04 testing and on a different drive from where I normally work.

If I were you I would run a search for "auto mount".  I will later.  There is something that needs added to that sda4 stanza in your fstab but I can't think what it is right off.

---

### Post by nishanvincent on 2009-11-02
to be honest, i dont have much idea of this installation. I just made to partition and installed ubuntu 9.10. So not much of an idea what is a ideal setup and how to do it. So just used the live cd and installed ubuntu. However thankx for the advice. Let me try to delete the partion and recheck.

---

### Post by nishanvincent on 2009-11-02
Yes, it worked successfully after deleting the partition and recreating the partition as etx4. Now its showing in the main computer file browser.
Thankx anyways for all ur help.

---

### Post by ranch hand on 2009-11-02
Good job.

---

### Post by QLee on 2009-11-02
HUH?

Am I reading this correctly? Did you guys just help someone to delete their boot partition and recreate it blank for holding data? What is going to happen next time the system tries to boot?

---

### Post by ranch hand on 2009-11-02
Well, I am hoping that he reinstalled grub2 in that partition.

---

### Post by Locke_99GS on 2009-11-02
I thought his problem was that he just didn't understand how mounting a partition in linux worked, and was expecting it to show as a seperate drive listed under "Computer" in Nautilus, a'la MS Windows. Aside from his thick /boot mount, I saw nothing wrong with his original setup.

---

### Post by ranch hand on 2009-11-02
I didn't either and there is some thing you add to the stanza for the partition in fstab to have it auto mount, which would make it show in where he wants it to show.

Beats me what he did or exactly why, but he seemed happy with it.  It is his box.

---

### Post by nishanvincent on 2009-11-05
Hey Guys sorry, but really I had no idea what I had done. So i just deleted the partition and when i tried to boot, It gave me the grub error. So ultimately i just reinstalled everything from the scratch. And now everythng is fine. However thanks for all your support. I just love ubuntu just becz there are so many wonderful people who are really ready to help.
Thankx

---

