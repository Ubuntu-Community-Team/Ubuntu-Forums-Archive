---
title: "Leave Windows disk alone, put Ubuntu on USB disk?"
date: 2011-09-04
forum: New to Ubuntu
---

### Post by anewguy on 2011-09-04
I think I've got this pretty much figured out, but I would like it if someone could verify for me as right now I can't be touching the structure of the hard disk on my new laptop.

Scenario:  I bought a new laptop - Acer, 17.3", quad-core, etc., etc..  I also bought a 2nd external USB hard drive - this one 500gb so I can do some backups to it with Macrium Reflect.  However, I would also like to run Ubuntu on the laptop with the caveat that until the warranty expires (I've got an extra couple of years) I don't want to mess with the structure of the hard disk so I won't have any problems with them if something happens to the laptop.

My understanding:  The way I look at it, using a LiveCD for installation, I can select installation to the external drive (and appropriate repartitioning as needed) and when the review of options comes up I can direct grub to the external drive.  This would allow me to boot Ubuntu with the external drive plugged in, or boot Windows without (or for that matter, with) the external drive - e.g., the MBR on the internal disk wouldn't be touched.

I believe all of this to be correct, however I really don't want to accidentally change the MBR of the internal disk.  So......for those who do know, am I correct on this?

If I can do this, perhaps I can write a how-to for installing to an external drive without affecting your current installation (if it hasn't already been done).

Thanks in advance!

Dave ;)

---

### Post by afz12 on 2011-09-05
Hi Dave

I tried this when the hard drive failed on my Acer 5920 notebook. I used an external 500 GB USB drive and installed Ubuntu 10.10 on it as if it were a standard hard drive. This worked well but was a bit slower booting than using an internal drive.

The only think I needed to change was the bios boot sequence (F2 at turn on). You need to place the USB drive at the start of the boot list in bios. The the notebook booted from this USB drive as if it were an internal drive.

However, since I replaced the failed hard drive I haven't tried running both together - there may be some boot conflict.

Good luck

---

### Post by anewguy on 2011-09-05
I was pretty sure that was what I needed to do.  Thanks for the info!

I think I will document it as I go so I can create a how-to for it.

Thanks again!
Dave ;)

---

### Post by oscarivera9 on 2011-09-05
> Hi Dave

I tried this when the hard drive failed on my Acer 5920 notebook. I used  an external 500 GB USB drive and installed Ubuntu 10.10 on it as if it  were a standard hard drive. This worked well but was a bit slower  booting than using an internal drive.

The only think I needed to change was the bios boot sequence (F2 at turn  on). You need to place the USB drive at the start of the boot list in  bios. The the notebook booted from this USB drive as if it were an  internal drive.

However, since I replaced the failed hard drive I haven't tried running both together - there may be some boot conflict.

Good luck

There will definitely be some boot conflict if you try to run both together.  If you bought the external HDD with the intention of making a copy of the internal one, then having both run together will cause the computer to make one of the Windows installations the  main one and the other unable to boot by itself.  This would basically go against what you were originally trying to do.  Especially if the internal HDD becomes the one that can't boot.

---

### Post by oscarivera9 on 2011-09-05
If you want to install Ubuntu on your laptop, the best choice would be to make an exact replica of your hard drive on another one of the same capacity that you can then install inside. There is a cable that you can use to power and connect the new hard drive via USB to the laptop so that you can make the copy.  If you already have Macrium Reflect you can go ahead and use that if you'd like.  If you buy an internal Western Digital hard drive, those come with a True Image Home WD Edition that you can download from their website for this type of scenario.  I've actually done the same thing with my last two desktops.  It is important that you first make a disc either with Macrium Reflect or with True Image so that the whole process takes place with Windows being shut down, in other words you would be booting into this Live CD that will help you make the copy.  After you make the clone, and I mean right after, shut the computer down (this prevents it from starting up with two hard drives and the MBR changing so that one hard drive is rendered useless as I stated in my previous post).  Then, take out the original hard drive and leave that one in the packaging the new one came in.  From this point on, the original hard drive will remain untouched and you can make as many changes to your computer as you want because the hard drive inside the laptop will be the new one that has the copy of Windows as well as Ubuntu and whatever else you decide to throw in there.  This way you are definitely leaving Windows alone, but at the same time you have a fast Ubuntu as well.
The other scenario, if you don't want to go through all of that, is to have two external hard drives.  One with Ubuntu, and the other one with the copy of Windows.
Either way, you'll have to buy another hard drive, unless of course, you decide that you will give up on Ubuntu and stick to Windows;  but we wouldn't really want that now, would we?  I hope not.

---

### Post by anewguy on 2011-09-05
Actually not what I'm after at all.

I have the external disk.  I've just completed what I needed to do.  I shrank the NTFS partition, installed Ubuntu to the new space, pointed grub to the new partition.  Works fine.  I did this on my desktop.  I then took it to my laptop and it again works fine - you get a quick warning about not being able to find one of the disks (the internal disk on the desktop, as I haven't updated grub yet) but it boots fine.  Of course being different hardware platforms things like the wireless and video are different, but it does give me a way to run Ubuntu on my laptop for now without touching the internal drive.

I always use Macrium Reflect in Windows and make an image of my entire drive as backup for the Windows things.  This file, and many, many more, will still fit in the shrunk NTFS partition.  Since I don't have Linux on the laptop there is no need to image it.  I have Linux on my desktop and have a completely different pair of external disks I rotate backups to.

Dave ;)

---

### Post by oldfred on 2011-09-05
The important thing with any install is to use manual install as that is the only way you get the combo box on which drive;s MBR to install grub2's boot loader to. I always partition in advance so I never have had an issue, but any of the auto install options default to grub in sda.

Herman has lots of detail:
Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

If you do get grub in the wrong drive:

Boot Problems:Computer does not boot without external drive
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

---

### Post by anewguy on 2011-09-05
Yeah, already had that figured out - go advanced on the review screen, be sure grub is being installed where you want.

Since I do have this all working, I'll mark the thread as solved.

Thanks oldfred - I always learn from your posts!

Dave ;)

---

