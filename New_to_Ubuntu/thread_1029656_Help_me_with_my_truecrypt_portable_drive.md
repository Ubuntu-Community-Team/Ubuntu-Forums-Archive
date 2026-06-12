---
title: "Help me with my truecrypt portable drive"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by lipidicman on 2009-01-03
Hello, looking for any help you guys can offer to a relative newcomer.

As a Windows user til now, I've been carrying a portable drive around with a Truecrypt NTFS partition on it.  (I sync it at a couple of sites using a windows RSync)

I want to move to Ubuntu, but keep my Windows options open.  i.e. at some sites I will be forced to use windows (although I can install software).

I'm not keen on FAT32 for big drives (My portable is 250Gb).  In the old days I found FAT drives a bit flaky

Should I stick with NTFS & Truecrypt?  Any issues with NTFS-3g and Truecrypt?

Or would converting to ext3 and adding a driver to windows be more reliable?  Would this work with the windows version of Truecrypt?

Thanks in advance

---

### Post by valuntahr on 2009-01-04
I've had no problems with accessing my NTFS external drives under Ubuntu. NTFS Truecrypt volumes also mount with no issues.

---

### Post by semi_fiction on 2009-01-04
I have used NTFS Truecrypt external drives with my Ubuntu laptop before with no problems, you should be fine.

---

### Post by nhasian on 2009-01-04
i have two 1TB external usb drives with NTFS with truecrypt.  it works fine between my window XP, Vista, and Ubuntu.  only issue i bumped into was that somewhere along the line i got foldernames with : colons in them and windows doesnt like to read those folders.

---

### Post by lipidicman on 2009-01-04
Thanks for the replies so far.  Sounds promising.  I was sure someone was going to warn me off.

Now I need to go learn Truecrypt under linux.  As I remember from a little research I did it was a tad tricker than windows.

---

### Post by lipidicman on 2009-01-06
Can anyone offer advice on going with ext3 then using the windows ext2 driver to access this when needed.  Will this work with the windows truecrypt?  I was hoping linux would become my main environment.

Or, is there really no advantage to the above.  Obviously sticking with NTFS is really the easiest option, but is it the best?

---

### Post by nhasian on 2009-01-06
you can partition the external drive with EXT3 instead of NTFS.  yes it will work with truecrypt and yes you can access it from windows.  You'll want to install EXT2IFS from here:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

the only problem with NTFS is that if you unplug it in linux and forget to unmount it you will need to plug it back into a windows machine so it can have a clean unmount.  you can avoid this issue by using EXT3.  plus you dont need to defragment EXT3 volumes as you do with NTFS ones.

---

### Post by lipidicman on 2009-01-08
Thanks.

Clarify one point for me.  Ext3 will work in windows with the add-on, but have you tried it as a truecrypt encrypted partition?.

I might have to do a trial attempt for myself

Thanks again all

---

### Post by lipidicman on 2009-01-10
> **nhasian said:**
> the only problem with NTFS is that if you unplug it in linux and forget to unmount it you will need to plug it back into a windows machine so it can have a clean unmount.

How would I go about this?  Do you have to run a checkdisk or the like?

---

### Post by lipidicman on 2009-01-21
Hmm, i'm having problems with this.

I have Truecrypt 6.1a installed in Ubuntu and Windows

I have installed ext2IFS in windows.

When I mount the TC partition (which was created as ext3 in Ubuntu).  Windows reports it as unformatted as I might expect,however I cannot use ext2IFS to mount it.

Do these two not work together?

---

### Post by bthodla on 2009-02-11
I have an external USB drive setup as an NTFS TrueCrypt volume (the whole device). I recently moved over from WinXP to Ubuntu 8.10. I installed True Crypt on Ubuntu and was able to mount the NTFS volume and read/write data from/to it. However, a couple of days ago, I installed KDE (I don't know if it has anything to do with KDE) and found that it was no longer recognizing the USB device. Nor did True Crypt. I switched back to Gnome Desktop with the same result.

I tried mounting the device as a TrueCrypt volume from another laptop running WinXP (I share this volume across the two laptops) but kept getting the message "Not a True Crypt volume" which is the same message I get on Ubuntu.

Can anyone please help and let me know how I can re-mount this volume and access the data either in WinXP or Ubuntu?

Thanks.

---

