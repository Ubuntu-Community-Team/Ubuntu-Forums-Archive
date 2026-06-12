---
title: "Grub Error 17"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by akrchstn on 2009-05-11
I just deleted my ubuntu partion and created it to ntfs because I want to wait to switch completely to ubuntu.  When I boot up it just says grub loading then grub error 17...how do I delete the grub loader?

---

### Post by Temposs on 2009-05-11
That sounds a little backwards. First, Ubuntu uses GRUB loader, so why would you want to delete it. Second, Ubuntu doesn't use ntfs, so why would you want to create an ntfs partition if you're trying to switch completely to ubuntu?

---

### Post by SuperSonic4 on 2009-05-11
I'd use ext3 or ext4 for the ubuntu partition depending on your hdd.

You can always reinstall grub via a live cd

---

### Post by Temposs on 2009-05-11
Yes. If you're looking to switch completely to Ubuntu and you'd just like to wipe everything, just use the LiveCD to install over your entire computer. It'll take care of the partition formatting and everything.

---

### Post by cjv8888 on 2009-05-11
> **akrchstn said:**
> I just deleted my ubuntu partion and created it to ntfs because I want to wait to switch completely to ubuntu.  When I boot up it just says grub loading then grub error 17...how do I delete the grub loader?

I think he wants to WAIT to switch to Ubuntu rather than to switch to ubuntu.  

In that case you will need to use the XP or Vista rescue disk and do a repair of the MBR. This will rewrite the boot record to allow you to boot Windows again.

---

### Post by raymondh on 2009-05-11
> **cjv8888 said:**
> I think he wants to WAIT to switch to Ubuntu rather than to switch to ubuntu.  

In that case you will need to use the XP or Vista rescue disk and do a repair of the MBR. This will rewrite the boot record to allow you to boot Windows again.

If this is the case:

Boot into the Vista or XP disk > repair computer > command prompt and then type and enter

bootrec.exe/FixMbr

Hope this helps

---

### Post by Temposs on 2009-05-11
> **cjv8888 said:**
> I think he wants to WAIT to switch to Ubuntu rather than to switch to ubuntu.  

In that case you will need to use the XP or Vista rescue disk and do a repair of the MBR. This will rewrite the boot record to allow you to boot Windows again.

My apologies...I've been completely no help in this thread ^_^;;

---

### Post by imwithid on 2009-05-12
This error does not come at random. I've caused this to happen several times. Usually it is caused by using the Windows>Administrative Tools>Computer Management>Disk Management and changing something there. It happened to me yesterday.

I should add that I have a dual boot system:

Windows XP x64 on the primary partition (sda1)
Ubuntu 9.04 x64 on the secondary partition (sda2)
Swap on the third partition (sda3)
Other on the fourth partition NTFS (sda4)

On an old installation of Ubuntu (8.10), I had created a logical partition rather than a primary thus not allowing me to use GParted to merge the unallocated portion with the fourth partition (sda4). 

After installing Ubuntu 9.04 a couple of days ago, I made the mistake of transferring all the files on the last partition to a spare drive and deleting the logical drive in order to merge the unallocated space with my NTFS drive though Windows.

This led to Windows changing the MBR and thus upon rebooting, the grub directory was gone which then would not boot Windows either.

In order to fix this, I did the following after trying all other suggestions in other threads (at this point, the grub directory and menu.list are gone, you must start at the last operating system that caused the problem) :

1. Fix the MBR using your Windows CD. You do not have to repair it. The funny thing about Windows is that you can "jack ***" it into working.

(a)Boot using installation CD
(b)Choose the partition which has Windows installed on it originally (most likely C:)
(c)Select "Leave the current file system intact <no changes>"
(d) After the first few files begin to copy, commit a hard reboot or hard shut down (press the reset or power button on the computer - if you don't know which one, than it really doesn't matter).

You should be able to boot into Windows without any problems (this works for XP). The MBR is fixed prior to Windows beginning to copy the files. Those files that are copied are temporary or if they have been copied to the hard drive will leave your system unmolested.

2. Fixing Ubuntu can now be done. Simply follow the steps outlined here:

(I used the first four steps)

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)


And there you have it. Your menu.lst should be restored and the grub boot loader just as it was.


I'm very much a noob but I find it strange how other noobs fail to disclose what they did last to mess up their systems (it seems quite obvious and helps others help you).

---

