---
title: "Getting rid of Windows"
date: 2009-09-29
forum: New to Ubuntu
---

### Post by Ben_T_B on 2009-09-29
Hi there, I recently made my 5th foray into the world of Linux and have found in 9.04, a possible Windows killer OS. On my laptop, everything just works after having installed Ubuntu and I'm loving the new environment and having to learn my way around all over again.

I would like to remove Windows, free up the 80GB NTFS partition and add it to my Linux filesystem without having to reinstall Ubuntu. Is this possible?

I had the idea of booting from the XP disk and deleting the partition to free up some space and then using some Linux wizardry to add the space to my Linux filesystem.

Remembering that the only thing I know about Linux is how to shutdown the OS and display the contents of the current directory, is this something I will be able to do?

Any advice is greatly appreciated.

---

### Post by wildman4god on 2009-09-29
Unfortunatly the way partitions work it isn't as easy as one would think. the easiest and quickest way would be to back up your data and wipe your whole hard drive and then do a freash install of ubuntu. There may be ways to do it with out having to reinstall ubuntu but moving partitions take forever, you could reinstall ubuntu 5 or 6 times before you could move your ubuntu partition to where it needs to be. So in the end just backup, wipe and reinstall.

---

### Post by yknivag on 2009-09-29
You can remove the NTFS partition to make "free space" on the disk and then grow your Linux partition using gparted.  Once that's done you can grow the filesystem to fit.

Alternatively, after you've removed the NTFS partition to "free space" you can use it to create a second Linux partition which you can mount to /home to allow you to preseve your documents through future re-installs etc.

What ever you decide to do though, please backup your data first! :)

---

### Post by Bucky Ball on 2009-09-29
And what ever you decide to do use the Live CD to manipulate partitions with Gparted as the partition MUST be unmounted. You can not resize the Linux OS partition from a hard drive boot (as you can't unmount the partition the OS is running on).

---

### Post by pmlxuser on 2009-09-29
using g parted in ubuntu you can
1. delete the windows partition
2. add partition to the ubuntu partition (might also require moving the partitions abit)

However as advised above it really nice to backup data before startin to mess up with parttion.

it yourboot record is also in the windows parttion you might find that you might need to do a grub reinstall after the partion dleting and moving...

but if you clealy follow the instruction provide on gparted you are likely to succed -- if you did not install ubntu inside windows using wubi....

---

### Post by hockeytux on 2009-09-29
Whatever you do, you are probably going to back up your data on Windows anyway so +1 for full backup, wiping and installing Ubuntu on the entire HDD. Power and simplicity.

---

### Post by Ben_T_B on 2009-09-29
Actually, the Laptop has only just been reinstalled with Windows/Linux and there's a separate data partition (NTFS I believe) that Linux seems to be able to access fine.

Reason I'm saying all this is that all I've got in Linux is WINE and VLC installed, plus some rubbishy games. All my data is already backed up so maybe I should just reinstall and use the whole disk for Ubuntu this time?

---

### Post by philinux on 2009-09-29
And if you reinstall put /home on it's own partition.

---

### Post by atomizer on 2009-09-29
+1 for gparted for being the right way (Use livecd so the partitions are not mounted)

+1 for reinstall for being the easy way (don't forget to backup everything in windows AND linux /home directory and don't forget to reinstall all your software + codec + everything I forgot)

---

### Post by Ben_T_B on 2009-09-29
> **philinux said:**
> And if you reinstall put /home on it's own partition.

Would you mind elaborating on this please?

---

### Post by philinux on 2009-09-29
> **Ben_T_B said:**
> Would you mind elaborating on this please?

Ok, so you decide to install to the full HD from the livecd. Choose manual partitioning. At this point you would delete all partitions, so hope your backup plan has worked. Create 3 partitions root, swap and home. I give root 12 gig, swap 2gig as I have 2 gig ram and I want to hibernate, the rest for home.

---

### Post by mikewhatever on 2009-09-29
I'd recommend deleting the Windows partition with GParted, but instead of adding the unallocated space to the Ubuntu partition, create a separate one for storage and backup. Anyhow, it should work and reinstalling in not necessary.

---

### Post by philinux on 2009-09-29
> **mikewhatever said:**
> I'd recommend deleting the Windows partition with GParted, but instead of adding the unallocated space to the Ubuntu partition, create a separate one for storage and backup. Anyhow, it should work and reinstalling in not necessary.

+1 for that mike too. He can always edit fstab for say a data partition.

---

### Post by admiralspark on 2009-09-29
Putting /home on it's own partition allows you to update the Ubuntu OS (say, from 9.04 to 9.10) without erasing all of your personal data. Basically, it will only adjust the OS partition in a reinstall/upgrade, and leave the personal data alone. VERY useful and trust me, you'll kick yourself later if you don't set it up now.

Out of curiosity, what do you use for a computer? I'm assuming it has an nVidia graphics card? How big is the HDD? I'm trying to plan out my next purchase so that I get something 100% compatible with Ubuntu, since I want to break away from windows completely in the future. 

Let us know how it works!

EDIT: I just reinstalled Windows/Ubuntu on an older computer, and deleted the windows install by reformatting the NTFS partition (still NTFS). After that, it was a simple matter of adjusting the partition with GParted. I know it doesn't completely erase all data but it worked for me?

---

### Post by blackened on 2009-09-29
> **mikewhatever said:**
> I'd recommend deleting the Windows partition with GParted, but instead of adding the unallocated space to the Ubuntu partition, create a separate one for storage and backup. Anyhow, it should work and reinstalling in not necessary.

I agree Mike. The benefit of doing it this way is that your partition layout won't get borked and you won't have to futz with fixing GRUB.

You could also mount portions of the root filesystem (I'm thinking /usr) to this partition in fstab.

If you choose the originally suggested way it will go like this:

1. Boot to Live CD and start gparted.
2. Unallocate the Windows partition (likely the first on the drive).
3. Grow the Ubuntu partition into the unallocated space.
4. Reinstall GRUB so that it will recognize the new partition scheme.

Because the original layout was with Windows at hd0,0 and Ubuntu likely at hd0,1 the new layout will have Ubuntu at hd0,0 and you'll have to account for that. The whole layout will be shifted one (logical) partition to the left.

---

### Post by philinux on 2009-09-29
Hey guys, see what the OP wrote.

> Remembering that the only thing I know about Linux is how to shutdown the OS and display the contents of the current directory, is this something I will be able to do?

I think a reinstall is a good idea.

---

### Post by Ben_T_B on 2009-09-29
Thanks for the help guys.

Seeing as it's a brand new install of Ubuntu, I think i'll just reinstall.

I have a 200GB HD that already has a 100GB split for data. When I reinstall, I should setup 3 partitions for Root, Swap and Home giving 12gb, xgb (where x is RAM size) and the rest for Home?

That sounds easy enough. Do I need to format them using specific types? Ext2 Ext3 that kind of thing?

Sorry for all the stupid questions, I feel like a fish out of water at the moment.

---

### Post by Ben_T_B on 2009-09-29
> **admiralspark said:**
> Putting /home on it's own partition allows you to update the Ubuntu OS (say, from 9.04 to 9.10) without erasing all of your personal data. Basically, it will only adjust the OS partition in a reinstall/upgrade, and leave the personal data alone. VERY useful and trust me, you'll kick yourself later if you don't set it up now.

Out of curiosity, what do you use for a computer? I'm assuming it has an nVidia graphics card? How big is the HDD? I'm trying to plan out my next purchase so that I get something 100% compatible with Ubuntu, since I want to break away from windows completely in the future. 

Let us know how it works!

EDIT: I just reinstalled Windows/Ubuntu on an older computer, and deleted the windows install by reformatting the NTFS partition (still NTFS). After that, it was a simple matter of adjusting the partition with GParted. I know it doesn't completely erase all data but it worked for me?

This is my laptop that I'm playing with. It's an Acer Aspire 5735z

---

### Post by philinux on 2009-09-29
> **Ben_T_B said:**
> Thanks for the help guys.

Seeing as it's a brand new install of Ubuntu, I think i'll just reinstall.

I have a 200GB HD that already has a 100GB split for data. When I reinstall, I should setup 3 partitions for Root, Swap and Home giving 12gb, xgb (where x is RAM size) and the rest for Home?

That sounds easy enough. Do I need to format them using specific types? Ext2 Ext3 that kind of thing?

Sorry for all the stupid questions, I feel like a fish out of water at the moment.

Yep select ext3 for root and home and swap file type for guess what swap!

Just make sure you really got a backup of anything important.

---

### Post by blackened on 2009-09-29
> **Ben_T_B said:**
> ...I should setup 3 partitions for Root, Swap and Home giving 12gb, xgb (where x is RAM size) and the rest for Home?...

I prefer 15-20Gb for root. Especially on a drive that big. Better to have too much than too little. Format this as ext4 if you're on Jaunty, ext3 if other.

Swap the same as your RAM if you intend to use hibernate. This will be of the type linuxswap (not ext2/3/4)

/home should also be ext4 and use the rest of the drive if you intend for Ubuntu to be your only OS. Otherwise use ext3 for compatibility.

---

### Post by philinux on 2009-09-29
> **blackened said:**
> I prefer 15-20Gb for root. Especially on a drive that big. Better to have too much than too little. Format this as ext4 if you're on Jaunty, ext3 if other.

Swap the same as your RAM if you intend to use hibernate. This will be of the type linuxswap (not ext2/3/4)

/home should also be ext4 and use the rest of the drive if you intend for Ubuntu to be your only OS. Otherwise use ext3 for compatibility.

Good catch, my jaunty install was yonks back when ext4 was a bit iffy. Now I would use ext4 unreservedly.

---

### Post by Ben_T_B on 2009-09-29
Great, thanks for that guys. I'll do this tonight when I get home. 

Also, I don't have anything important to back up other than stuff on my data partition. Now, while I'm a Linux n00b, I like to think I have enough intelligence not to delete the data partition (we'll see!).

---

### Post by Bucky Ball on 2009-09-29
> **Ben_T_B said:**
>  Now, while I'm a Linux n00b, I like to think I have enough intelligence not to delete the data partition (we'll see!).

You will see it quite clearly when you get to the Manual Partition part of the install. Just don't go there.

---

### Post by Ben_T_B on 2009-09-29
Haha 'don't go there'. Why do so many people say that to me? :P

---

### Post by chrisjsmith on 2009-09-29
TBH, I'd keep the 80Gb partition and mount it elsewhere such as /vol/backup and use it as a backup partition.

---

### Post by Ben_T_B on 2009-09-29
I wasn't planning on doing anything to it. It seems to work as it is right now. 

Which reminds of another question I wanted to ask. When I access something on that Partition, it shows on my desktop as being mounted. Do I NEED to unmount it after? Are there any consequences of not un-mounting it?

---

### Post by philinux on 2009-09-29
> **Ben_T_B said:**
> I wasn't planning on doing anything to it. It seems to work as it is right now. 

Which reminds of another question I wanted to ask. When I access something on that Partition, it shows on my desktop as being mounted. Do I NEED to unmount it after? Are there any consequences of not un-mounting it?

You need to be careful with removable drives. At shutdown all drives get unmounted cleanly.

---

### Post by Ben_T_B on 2009-09-29
Thanks for that tip but i was referring to the data partition rather than a removable drive.

---

### Post by chrisjsmith on 2009-09-29
Same with data partition.  It gets unmounted.

Mounting/unmounting is only an issue with non-fixed disks.

---

### Post by steveneddy on 2009-09-29
> **Ben_T_B said:**
> Actually, the Laptop has only just been reinstalled with Windows/Linux and there's a separate data partition (NTFS I believe) that Linux seems to be able to access fine.

Reason I'm saying all this is that all I've got in Linux is WINE and VLC installed, plus some rubbishy games. All my data is already backed up so maybe I should just reinstall and use the whole disk for Ubuntu this time?

My recommendation exactly.

Just wipe the drive and totally reinstall.

You and Ubuntu will be much happier.

As for putting /home on it's own partition, this is something that you can do after the installation when you feel your "skills" are a little more developed.

---

### Post by Ben_T_B on 2009-09-29
Thanks for the help guys, I'm quite looking forward to getting stuck in.

Referring to putting the Root, swapfile and /Home on their own partitions, I take it I can do all this before install in some kind of partition manager? I seem to recall seeing one when I installed Ubuntu before but I steered well clear of it for fear of wading in with my size 12's and causing my laptop to commit seppuku.

---

### Post by pricetech on 2009-09-29
Assuming you have your data backed up to some external media, which I take it you have, it shouldn't matter how you partition.  If you prefer to proceed with caution and learn as you go, then just let the installer do the partitioning for you.

Not trying to start a flame war over partitions, just trying to make things easier for someone just starting out.

If you do manually partition, I'd use a swap larger than the amount of physical memory.  (mem x 1.5 or mem x 2)  At least that was conventional wisdom back when I tinkered with such things manually.

Welcome to the community either way and best of luck whatever you decide to do.

---

### Post by Ben_T_B on 2009-09-29
Ok, using the partition manager I think I've succeeded. The output of df -h shows the following:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              20G  2.1G   17G  12% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  108K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  152K  1.5G   1% /dev
tmpfs                 1.5G   76K  1.5G   1% /dev/shm
lrm                   1.5G  2.4M  1.5G   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sda7              74G  186M   70G   1% /home
/dev/sda5             133G  9.3G  124G   8% /media/Data

sda5 is the data partition and is actually a lot larger than I remembered but it looks like I've got things where I want them now.

I want to thank everyone on this thread, you were all very patient and helpful.

---

