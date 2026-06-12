---
title: "removing Windows XP in dual boot"
date: 2010-09-30
forum: New to Ubuntu
---

### Post by beew on 2010-09-30
Hello,

When I started trying Linux I installed Ubuntu to dual boot with WindowsXP. I
was afraid that I might not like Ubuntu, or something might have gone wrong so I wanted to have the option of falling back on XP if needed. That was a few months ago and for all that time I haven't logged into XP once. I think it is time to give the whole hard drive to Ubuntu.

However, it may be a bit tricky to get rid of XP because it was installed first. I am wondering if it is possible to use gparted to delete the XP partition and then extend my Ubuntu / partition to the left and then shrink it on the right to make room for my /home partition.

I attach a screenshot of my hard drives' configuration for reference.

Thanks.

---

### Post by skumnull on 2010-09-30
Just Delete the windows partition and resize the ubuntu partition to use the entire HDD. Thats what i did. But then i decided to put Windows back on... Not as easy as taking it off.

---

### Post by emoguitarist06 on 2010-09-30
> **skumnull said:**
> Just Delete the windows partition and resize the ubuntu partition to use the entire HDD. Thats what i did. But then i decided to put Windows back on... Not as easy as taking it off.

You have **CAN **delete the windows partition with gparted while logged into Ubuntu but you **CANNOT** resize ubuntu. You'll have to run gparted while running a **[COLOR="Red"]LIVE CD/USB of Ubuntu [/COLOR]**and you MAY HAVE TO reinstall **[COLOR="Blue"]GRUB/GRUB2[/COLOR]**

---

### Post by adwhitenc on 2010-09-30
If you ever need to use XP again, you can use virtualbox ([www.virtualbox.org](www.virtualbox.org))
It installs the system in your ubuntu partition in the hidden virtualbox file so you dont need to worry about ever needing the space back.

P.S. Install the proprietary version as well as guest additions, they really help.

Thank you for using ubuntu. :)

---

### Post by sikander3786 on 2010-09-30
Delete the Windows partition and resize your Ubuntu partition from a live CD session as suggested above. I don't think there would be any need to re-install Grub.

```
sudo update-grub
```

should remove the Windows entry from the Grub menu.

See here.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by Mark Phelps on 2010-09-30
If the Windows XP partition is "to the left" of the Ubuntu partition when viewed in Partition Editor, when you remove it, your GRUB menu will be wrong because the index into your Ubuntu partition will have changed.

What might work is the following:
1) While in Ubuntu, open the Partition Editor and remove the XP partition
2) Close the partition editor
3) Open a terminal and enter "sudo update-grub". This will generate a new GRUB menu that will get the correct new index of your Ubuntu partition.
4) Reboot

Once that works, you will have to boot from a LiveCD (Ubuntu or GParted) if you want to move and/or resize the Ubuntu partition.

---

### Post by mikechant on 2010-10-01
Mark, you said
> If the Windows XP partition is "to the left" of the Ubuntu partition when viewed in Partition Editor, when you remove it, your GRUB menu will be wrong because the index into your Ubuntu partition will have changed.

But I don't think that's right in this case.
If you delete a logical partition in the extended partition, higher numbered partitions *are* renumbered as you said(reduced by 1).

However, if (as in this case) you are deleting a primary partition, the numbers of the other partitions do not change (e.g. I had four primary partitions sdb1,2,3,4, deleted partitions 2 and 3 and I now have sdb1 and sdb4 - sdb4 was not renumbered to sdb2). This is because the primary partitions are defined by four fixed table entries in the MBR, whereas the logical partitions within the extended partition are defined as a linked list so deleting an item in the middle of the list renumbers the later items.

The problem in this case is that the free space is not where we want it. If sda2 was expanded backwards into the free space created by deleting sda1, this would give loads of extra space for the / filesystem, but the extra space is probably more likely to be wanted in /home. In that case what needs doing is:
1/ Delete sda1
2/ Move (without resizing) sda2 to the start of the disk.
3/ Resize sda3 by moving its start point to the end of sda2
4/ Resize sda5 by moving its start point to the start of sda3

---

