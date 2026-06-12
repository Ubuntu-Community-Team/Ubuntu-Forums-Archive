---
title: "deleted ubuntu partition, now won't boot"
date: 2011-08-04
forum: New to Ubuntu
---

### Post by nterpin on 2011-08-04
Ok, So I decided that I wasn't using Ubuntu as I used to, so I decided to just delete the partition using the partition tool on Windows XP. Once I did that, I received the error: error: partition not found  grub rescue>.
After reading many other topics, I noticed that all of the solutions that worked for other people, did not work for me at all.  It will not recognize any of the commands.  I would like to remove it, but nothing seems to be working.  Because my laptop is a netbook, the Windows XP recovery is a partition that is built into the laptop.  Because of the GRUB issue, I can no longer access any recovery or my windows XP.
Any help would be appreciated.  Thanks!

---

### Post by YesWeCan on 2011-08-04
What you need is a new MBR boot code. :)
If you had an XP installation CD you could do a repair/fixmbr. But you probably didn't get one of these with your laptop.
Instead, lilo to the rescue.
Boot live Ubuntu CD
[COLOR="Navy"]sudo apt-get install lilo[/COLOR]
[COLOR="Navy"]sudo lilo -M /dev/sda mbr[/COLOR]
(assuming your XP disk is called sda. Look it up using Disk Manager or run [COLOR="Navy"]sudo fdisk -l[/COLOR])

---

### Post by nterpin on 2011-08-04
How can I get a Live CD?  Originally I installed from a 4gb USB stick, but that has long since been deleted for my other files.

---

### Post by westie457 on 2011-08-04
Holding down the F10 key or Alt+F10 while the power on self test is running should bring up the restore to factory settings.

---

### Post by zealibib slaughter on 2011-08-04
Grab Hirens BootCD here: [http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd)
Grab unetbootin here: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
make a bootable flash drive
boot your system from the flash drive and use the bootfix utility
see this page for more info: [http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/](http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/)

---

### Post by YesWeCan on 2011-08-04
> **nterpin said:**
> How can I get a Live CD?  Originally I installed from a 4gb USB stick, but that has long since been deleted for my other files.
You can use a USB stick too. Just go to the Ubuntu main page and follow the instructions to create a live USB. Any version of Ubuntu will do.

---

### Post by nterpin on 2011-08-04
Thank you **SO** much for your assistance! My laptop is back to normal! I am forever grateful!

---

### Post by Wim Sturkenboom on 2011-08-04
Please mark your thread as solved using the thread tools just above the first post.

Your problem is the reason why I don't like grub.

---

### Post by anewguy on 2011-08-05
I hope you don't mind, but I wanted to add some info here for any beginners or other out there who are thinking of removing Ubuntu.

If you have a dual boot system, then ubuntu's grub has modified the master boot record on your disk to point to your Ubuntu installation, not to your Windows or other OS.  The result of just deleting the Ubuntu partition(s) is that leaves the master boot record on your disk still pointing to Ubuntu, which it can't find, so it won't boot.  For dual boot with Windows systems, the easiest way I have found to do this safely is as follows (and I'm sure others will add other ways here as well).[LIST]
[*]Boot up your Windows installation
[*]get online and go to [www.downloads.com](www.downloads.com)
[*]search for and download mbrfix
[*]run mbrfix
[/LIST]
This will set the master boot record to point to your Windows installation, so now it is safe to delete the Ubuntu partitions (unless you maybe want to leave them there to try Ubuntu in the future? ;) ).

Dave ;)

---

### Post by amjjawad on 2011-08-05
> **anewguy said:**
> I hope you don't mind, but I wanted to add some info here for any beginners or other out there who are thinking of removing Ubuntu.

If you have a dual boot system, then ubuntu's grub has modified the master boot record on your disk to point to your Ubuntu installation, not to your Windows or other OS.  The result of just deleting the Ubuntu partition(s) is that leaves the master boot record on your disk still pointing to Ubuntu, which it can't find, so it won't boot.  For dual boot with Windows systems, the easiest way I have found to do this safely is as follows (and I'm sure others will add other ways here as well).
[LIST]
[*]Boot up your Windows installation
[*]get online and go to [www.downloads.com]("http://www.downloads.com")
[*]search for and download mbrfix
[*]run mbrfix
[/LIST]
This will set the master boot record to point to your Windows installation, so now it is safe to delete the Ubuntu partitions (unless you maybe want to leave them there to try Ubuntu in the future? ;) ).

Dave ;)

And the above must be done "before" deleting Ubuntu Partitions NOT after because after that, both systems won't be bootable.

GRUB Files are stored in the root partition (/) and only few lines code are stored in the MBR so by removing (/) partition, GRUB Files will be removed too and what is left is the pointer in the MBR to the partitions.

Hope Dave won't mind :)

---

