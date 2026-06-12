---
title: "Ahhh! Corrupt hard disk!"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by Neon_Knight on 2009-06-05
I'm on my live CD at the moment.

Basically, I tried to change my graphics card to a newer one, and found that the new one was faulty, so I switched it back again.  During this process, the hard disks were unplugged and replugged again. (I have 4 hard disks by the way)

Well now the grub can't load, it comes up with an error 21 (sometimes 22 depending on what the arrangement of SATA cables is).  Well after booting into the liveCD, and running Gparted I can see that my 250GB hard drive which used to be split up into more or less 200GB for Ubuntu boot partition and 40GB for Windows (10GB swap) is now as one 232GB "unknown" filesystem with a little warning triangle next to it.  And 7.84MB of unpartitioned space.

Is there any possible way to fix this?  I don't know how it got corrupt - perhaps it got knocked inside the PC?  I don't know but I want to know if Ubuntu LiveCD offers any way to fix this. 

Surely all of my data is still there? I mean it can't just have gone.  That's 250GB, some of it quite important, I'm not too keen to just start formatting...  

I'll do that if the worst comes to the worst, but I'd rather not have to.  

Thanks for any help you can give.

---

### Post by LewRockwell on 2009-06-05
you'll need to do this

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by marshall.robert on 2009-06-05
I would also recommend making sure they are plugged in in the same order as they were before you replaced the GPU. Just to be safe.

---

### Post by ajgreeny on 2009-06-05
Backups?  If you have some, what's the problem with reformatting?

---

### Post by Neon_Knight on 2009-06-05
> **marshall.robert said:**
> I would also recommend making sure they are plugged in in the same order as they were before you replaced the GPU. Just to be safe.

Ah that's just the thing, I have no idea what order they were in before I replaced the GPU.  


And the problem with formatting is losing my data.  I can't make any backups because I can't access the partitions because the partition type is "unknown" and it isn't auto-mounted at start (when all other partitions on other disk have mounted) which leads me to assume that there's a reason why it can't be mounted.  (Especially considering, to Ubuntu's eyes, the two partitions have merged into one. I wouldn't like to see the results of *that* mount)

---

### Post by Neon_Knight on 2009-06-05
Also, I'm currently running
> 
sudo gpart /dev/sda -W /dev/sda

(which I found from google) 

in the terminal and it's output 

> 
Begin scan...
Possible extended partition at offset(7mb)
   Possible partition(Windows NT/W2K FS), size(45786mb), offset(7mb)


Which means it's seen my 40GB NTFS drive.   I'm not sure exactly what it's done - Gparted looks the same.. somebody inform me if I've wrecked my chances of recovering my data, please. :D


And - TestDisk seems geared towards recovering NTFS - I have one NTFS and one Ext2/3 (can't remember exactly..), so is that going to be a problem?

---

### Post by LewRockwell on 2009-06-05
> **Neon_Knight said:**
> Ah that's just the thing, I have no idea what order they were in before I replaced the GPU.

this information should have been disclosed in the original post, btw...

---

### Post by Neon_Knight on 2009-06-05
> **LewRockwell said:**
> this information should have been disclosed in the original post, btw...

I'm sorry, I didn't think of that.

Anyway it's only the one hard disk that's corrupt, the others have mounted just fine, so it's just a case of finding out which hard disk it is that's corrupted and repairing it.. right?

---

### Post by marshall.robert on 2009-06-05
Well it could be a case of simply rewriting the partition table to the correct one, leaving your data intact (hopefully). I couldn't tell you what the commands or anything are, but I came across a situation where I had to do a similar thing.

---

### Post by Neon_Knight on 2009-06-05
Well I've used TestDisk and it successfully found my partitions and I could browse my files in that, and so I restored the partition table.  

I rebooted, and now I have the linux swap partition restored to normal, but the NTFS and the Ext3 partitions are both merged back into "unknown".  Anything I can do about that?

---

### Post by LewRockwell on 2009-06-05
I believe you'll need to run testdisk again to continue your corrections

---

### Post by marshall.robert on 2009-06-05
This is out of my league now, sorry. But good luck!

---

### Post by Neon_Knight on 2009-06-05
Well I'm trying to change the characteristics of the partitions, but when I set to make my linux one "primary bootable" by putting a little star by it, it goes STRUCTURE: BAD!  I feel a bit nervous about doing that, but it is supposed to be the main booted partition.

---

### Post by Neon_Knight on 2009-06-05
Well I don't really know what to do now.  I don't want to do things with testdisk that I'm not really confident with, I don't want to mess things up.


Edit:

I just noticed - after a reboot, my lost partitions have successfully mounted and they show up just fine with no warnings in Gparted!

The GRUB didn't load at start though, I'm still on this liveCD so now my problem has shifted.

---

### Post by LewRockwell on 2009-06-05
Along with reading the complete webpage that I linked to originally:

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)


You might gain further knowledge by checking these out as well:
(these links are also found on the original link)

[http://www.cgsecurity.org/wiki/Running_TestDisk](http://www.cgsecurity.org/wiki/Running_TestDisk)

[http://www.cgsecurity.org/wiki/Data_Recovery_Examples](http://www.cgsecurity.org/wiki/Data_Recovery_Examples)

---

### Post by Neon_Knight on 2009-06-05
Right I've managed to reinstall the GRUB, and the partitions are fixed and they mount just find on the liveCD but now the GRUB can't load the partitions - because according to the GRUB, error 22 partition doesn't exist.  

I think this is because the hard disks are in a different order.  Any way to get the GRUB to search for the right partitions or manually select which partitions the GRUB refers to?

---

### Post by 73ckn797 on 2009-06-05
Download SGB (Super Grub Boot disk) and burn it to a CD. Boot computer from it and see if it can correct the grub. It usually works great when I have switched things around.

[www.**supergrub](www.**supergrub)**disk.org/

---

