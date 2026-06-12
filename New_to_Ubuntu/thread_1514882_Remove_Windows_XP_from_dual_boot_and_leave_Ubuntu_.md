---
title: "Remove Windows XP from dual boot and leave Ubuntu 10.04 alone"
date: 2010-06-21
forum: New to Ubuntu
---

### Post by brucesmith on 2010-06-21
I have UNR dual booted with Windows XP for about a year now on my Acer A150. I needed the XP for work, but now I don't and I'd like to dump it and just leave the Ubuntu. What I've been able to find is a lot of conmplicated (for me) stuff about GRUB. What would happen if I just downloaded Lucid UNR onto a flash drive, started it from the USB, and then just reinstalled Ubuntu alone like it was the first time? Would I mess anything up?

---

### Post by lkjoel on 2010-06-21
That would clear all the data.
You can upgrade via Update Manager, but that wouldn't remove winXP

---

### Post by Rubi1200 on 2010-06-21
> **brucesmith said:**
> I have UNR dual booted with Windows XP for about a year now on my Acer A150. I needed the XP for work, but now I don't and I'd like to dump it and just leave the Ubuntu. What I've been able to find is a lot of conmplicated (for me) stuff about GRUB. What would happen if I just downloaded Lucid UNR onto a flash drive, started it from the USB, and then just reinstalled Ubuntu alone like it was the first time? Would I mess anything up?

Firstly, why not leave things as they are? You never know when you might need XP again.

To answer your question:

A fresh install (choosing the use whole disk option) will reformat the drive and install Ubuntu as the primary OS. XP, as well as all other data, will be gone.

My advice?

Backup all your important files BEFORE you do anything.

---

### Post by brucesmith on 2010-06-21
When I first set up the dual boot, I divided the hard drive fairly evenly between Ubuntu and XP...it seems a waste to have half my drive devoted to an operating system I may not use much. Is there a way to turn the "slider" back on that I used in the original installation and make the XP partition shrink and the Ubuntu grow wihtout erasing stuff?

---

### Post by lkjoel on 2010-06-21
I don't think so.

---

### Post by eriktheblu on 2010-06-21
It can be done. 
1. Back up all pertinent data.

2. Use the flash drive/CD boot to remove the NTFS partition with Gparted. 

3. Add the extra space to your existing partitions, or create a new partition if you prefer.

4. Reboot to Ubuntu.

5. Edit /boot/grub/menu.lst (assuming you are using Hardy) in your favorite text editor and remove the Windows entries. Make sure to use root permissions or it will not save.

---

### Post by waynefoutz on 2010-06-21
Fortunately you can access  the XP partition from Ubuntu, so it's  not like you're losing much. You could reformat the drive with Gparted to ext3, that would wipe out windows, but you'd still be stuck with the extra partition. The only program I know of that will grow a partition is Partition Magic, which is a commercial Windows program. You'd have to mount your drive as a second drive in a Windows machine to do that. 

I would just back up my home folder, reinstall Ubuntu to take the whole drive. That would probably be the easiest way to accomplish this.

---

### Post by ajgreeny on 2010-06-21
> The only program I know of that will grow a partition is Partition  Magic, which is a commercial Windows program. You'd have to mount your  drive as a second drive in a Windows machine to do that. 
That is not true.  Gparted will do it as well, but only from a live CD/USB; you can't do this from your installed ubuntu. as the ubuntu partition will, of course, be mounted and gparted can not work on mounted partitions.

If the OP wishes to do it, it's not very hard, but I accept there is a risk; there is always a risk to any partitioning activities on a disk with an OS that you wish to keep.

However, back up all your important files if you haven't already done so, both in Ubuntu's /home and also in your XP partition.  Now boot to the live USB you used to install, and start **System -Administration -Partition Editor** (Gparted in 10,04).  Using that, delete the windows XP partition(s), and then grab the left hand end of the ubuntu partition and move it left as far as you can to fill the empty space.  Let gparted do everything, which is a long, long business to move a partition backwards, and may take well over an hour, so make sure you are on mains power, not battery.

When it finishes you should have got rid of your WinXP and just have ubuntu on the disk.  Now just edit out the Windows entry from grub's menu.lst, and that's it.

But as someone has said already, is it really worthwhile?  Doing it this way is slow, and I think you would be better served by starting again, backing up, then installing 10.04 on the whole disk.  The 10.04 UNE is brilliant!

---

### Post by C.S.Cameron on 2010-06-21
With gparted you can shrink the Windows partition or delete it completely.
If you delete it you can expand your linux partition to suit.
You can boot from the Ubuntu Live CD or from the gparted Live CD.
If you delete it there is a small chance you might have to reinstall grub.
I understand 10.04 no longer uses menu.lst The "update-grub" command should fix up your grub.cfg file automatically.
If you decide on a clean install you can always copy your home folder to the new install.

Edit:
You should first confirm that you know what you are talking about and are actually dual booting XP and Ubuntu and not really just booting wubi from the windows partition.
If you are actually just booting wubi from the Windows partition then you will have to fall back to Plan A and install Ubuntu to the entire disk. I'm not sure how you would copy your home folder though.

---

### Post by wilee-nilee on 2010-06-21
I will say here that all the advice is correct basically but even though the OP has described a dual boot and side by side, I have seen people install wubi and build a partition in the install partitioner. What should be done here is confirm the dual boot before any advice is given don't you all think.;)

If this is a miss-installed wubi then all the instructions to use gparted will wipe the whole thing away.

This site is rampant with advice before confirmation don't be a part of the problem.

---

### Post by waynefoutz on 2010-06-21
> **ajgreeny said:**
> That is not true.  Gparted will do it as well, but only from a live CD/USB; you can't do this from your installed ubuntu. as the ubuntu partition will, of course, be mounted and gparted can not work on mounted partitions.

If the OP wishes to do it, it's not very hard, but I accept there is a risk; there is always a risk to any partitioning activities on a disk with an OS that you wish to keep.

However, back up all your important files if you haven't already done so, both in Ubuntu's /home and also in your XP partition.  Now boot to the live USB you used to install, and start **System -Administration -Partition Editor** (Gparted in 10,04).  Using that, delete the windows XP partition(s), and then grab the left hand end of the ubuntu partition and move it left as far as you can to fill the empty space.  Let gparted do everything, which is a long, long business to move a partition backwards, and may take well over an hour, so make sure you are on mains power, not battery.

When it finishes you should have got rid of your WinXP and just have ubuntu on the disk.  Now just edit out the Windows entry from grub's menu.lst, and that's it.

But as someone has said already, is it really worthwhile?  Doing it this way is slow, and I think you would be better served by starting again, backing up, then installing 10.04 on the whole disk.  The 10.04 UNE is brilliant!


Well I stand corrected...thank you.

---

