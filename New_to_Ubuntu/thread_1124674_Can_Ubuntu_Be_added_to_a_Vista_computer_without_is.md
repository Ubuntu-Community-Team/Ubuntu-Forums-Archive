---
title: "Can Ubuntu Be added to a Vista computer without issue?"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by Noise... on 2009-04-13
The other night I was all ready to install Ubuntu, but then saw the thread about severe GRUB issues cause by Vista and SP1.

Is this the case with every install of Ubuntu on a Vista SP1 computer? I want to dual boot, but if I'm going to have to repair the MBR every time I boot into Vista, that will be a pain.

I have Vista SP1 now, and want to install Ubuntu Studio and dual-boot.

Will I likely get this issue with my install? Is there a way around it so that I can just get a nice, clean dual boot install?

---

### Post by RedSingularity on 2009-04-13
You only have to worry about repairing grub if you reinstall vista when Ubuntu is already on the computer.

---

### Post by Jakey_TheSnake on 2009-04-13
Dual-boot only really screws up the MBR when installing Ubuntu, and THEN adding XP/Vista afterwards. 

If you add Ubuntu to a computer with Vista on it already, your MBR should be fine.

---

### Post by lisati on 2009-04-13
The laptop I'm using right now is a dual-boot setup with Vista and Ubuntu 8.10 - it can be done, and so far I haven't had any issue with Grub

As usual with any major changes to a system, I'd suggest doing the following things, "just in case":
[LIST]
[*]Make a backup of your important data
[*]Make sure you have a set of recovery disks. (My Toshiba laptop came with a program preinstalled that could do this)
[*]For Ubuntu, have a "Live CD" available if you can.
[/LIST]

---

### Post by Noise... on 2009-04-13
Oh, ok. Sweet. I'm going to go make a copy of Super Grub Disk regardless, but then I'll install.

With the Ubuntu Studio disk I can set up the partition and dual boot, right? I just do the normal install, then manually partition?

Will that partition be able to be resized later (if I opt to install all of my media into Ubuntu instead of Windows?)

---

### Post by benerivo on 2009-04-13
> **Noise... said:**
> ...I just do the normal install, then manually partition?...Will that partition be able to be resized later (if I opt to install all of my media into Ubuntu instead of Windows?)

I would partition as you want from the live cd, then install. You can also resize partitions later (best done from within a live cd session). I have a partition that is just personal files, rather than storing my stuff inside 'My Documents' in Windows, or my 'Home' folder in Linux. I would also download a copy of [this .iso]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") which allows you to easily restore the vista mbr if you ever want to.

---

### Post by jhenager on 2009-04-13
I never heard of Studio until now, but if it was me, I'd just install the latest version of Ubuntu from the Live CD. All the applications available through Studio can easily be added, and I know you'd have no problem resizing the free space on your hard drive and dual booting with Ubuntu.
As always, though, if you are dealing with critical, irreplaceable data, you must do a backup first. You never know what might happen when you make major changes to a computer.
The only other possible problem might be you would find using Windows is not as fun or visually pleasing as Ubuntu, and you'll have money to spend on other stuff because all your software is now free. :)

---

### Post by Noise... on 2009-04-13
Edit; Rather than getting further off-topic in this thread, I'm just marking it Solved, as the initial question was answered!

---

