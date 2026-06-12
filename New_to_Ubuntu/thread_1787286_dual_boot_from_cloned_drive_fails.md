---
title: "dual boot from cloned drive fails"
date: 2011-06-20
forum: New to Ubuntu
---

### Post by lister171254 on 2011-06-20
I'm running 10.10 and dual boot to Windows 7.

I have a separate /boot partition on a single disk which also contains Windows7 and a RAID 1 for the rest of Linux

As my single drive started to develop errors on some sectors I decide to clone (Clonezilla) the drive.

When rebooting from the new drive, I get the grub menu and can boot into Windows7, but when trying to boot into Linux I get:

error: file not found
error: you need to load the kernel first

So I guess there is something wrong with Grub. While there are many posts on how to reinstall, update, etc. Grub2, I have a specific question.

What files other than in /boot are modified during an update/reinstall? The reason I'm asking is that I have a working system right now (although with some dud sectors) and I just want to make sure I don't loose that.

Thanks

---

### Post by dFlyer on 2011-06-20
Windows is more tolerable to bad sectors then linux. My advice is to backup what you want to keep and replace the drive ASAP. To answer your question if your home directory is not separate from root a reinstall will overwrite you home folder. So any data in the home folder will be lost.

---

### Post by lister171254 on 2011-06-20
Sorry about the confusion, but I only want to reinstall Grub.

---

### Post by amjjawad on 2011-06-21
> **lister171254 said:**
> Sorry about the confusion, **but I only want to reinstall Grub**.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

If that is what you really need/want :)

---

### Post by lister171254 on 2011-06-21
Thanks for the link, but as mentioned in my original post, there is no lack of resources on how to do this.

My problem is that I have a working boot disk, although with some dodgy sectors and a cloned dual boot disk that should be working but isn't.

My concern/question is around what happens to the rest of the file system when I reinstall Grub (ie. what files other than files on /boot are changed) and what's the likelihood of my current system not booting when the reinstall/config off Grub fails on the cloned disk

Cheers

---

### Post by amjjawad on 2011-06-21
> **lister171254 said:**
> Thanks for the link, but as mentioned in my original post, there is no lack of resources on how to do this.

My problem is that I have a working boot disk, although with some dodgy sectors and a cloned dual boot disk that should be working but isn't.

My concern/question is around what happens to the rest of the file system when I reinstall Grub (ie. what files other than files on /boot are changed) and what's the likelihood of my current system not booting when the reinstall/config off Grub fails on the cloned disk

Cheers

Re-installing GRUB2 will do nothing to your files. You're re-installing a Boot-Loader not a complete OS.

Edit: However, in any case, you should have a backup to your files. better safe than sorry ;)

---

### Post by mfstutz on 2011-06-21
I've been in the situation a number of times.  My problem has almost always been that the clone wasn't a complete clone . . . as in . . . the boot information (Windows, Unix, etc.) wasn't copied correctly.

I bought Acronis Disk Director ($50 program) a few years ago, and it faithfully clones a disk.  If you have an extra $50, buy it & get a proper clone.  If you DON'T have an extra $50, there's probably some guru's around here that can point you to a proper open source disk cloning utility that will handle the boot information properly.

---

### Post by lister171254 on 2011-06-21
Thanks for you prompt reply

Yes, I do have backups. I guess the other thing to do is to mount "/" ro, given that I have a separate /boot partition.

I've also played around with the Grub CLI as per this link [http://members.iinet.net/~herman546/p20/GRUB2%20How%20To%20Boot%20From%20CLI%20Mode.html](http://members.iinet.net/~herman546/p20/GRUB2%20How%20To%20Boot%20From%20CLI%20Mode.html)

Have executed (a variation) of these 

grub> linux   (hd0,1)/vmlinuz-2.6.27-9-generic root=/dev/sda1
grub> initrd  (hd0,1)/initrd.img-2.6.27-9-generic
grub> boot

but when it starts to boot it fails after mounting my array. it reports an error about an unknown partition table on the array and drops me to initramfs

Weird

---

### Post by lister171254 on 2011-06-21
I've attached part of RESULTS.txt file from the Boot Info script output nd while both results (the original and the clone) are identical, I noticed the they both report that the core.img cannot be found.

Not sure of the significance.

---

### Post by lister171254 on 2011-06-22
I think I figured out why the clone does not boot; it seem to use an old kernel.

I have no idea how this can happen, but I noticed that I have on my original disk the following under the /boot partition

/boot/grub/
/boot/boot/grub

When booting from the original disk it uses the grub.cfg file from /boot/grub/

When booting the cloned disk it uses the grub,cfg file from /boot/boot/grub

I have no idea how the /boot/boot/grub directory was created; I'm sure it's incorrect

I'd appreciate any suggestions what to do next.

---

### Post by lister171254 on 2011-07-06
Please see [http://ubuntuforums.org/showthread.php?t=1787931](http://ubuntuforums.org/showthread.php?t=1787931) for a full explanation

---

### Post by amjjawad on 2011-07-06
> **lister171254 said:**
> Please see [http://ubuntuforums.org/showthread.php?t=1787931](http://ubuntuforums.org/showthread.php?t=1787931) for a full explanation

Multiple threads again? sorry, can't follow up with two at the same time.

---

### Post by jtarin on 2011-07-06
Boot from the Live CD....CHROOT into your installed environment and reinstall and update GRUB. (and I'm not following two threads either)

---

