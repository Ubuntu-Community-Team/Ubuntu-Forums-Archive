---
title: "'disk read error' after resizing windows partitions"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by bistro on 2009-05-12
Hi

I just resized my XP hard drive to dual boot with Ubuntu 9.04; Ubuntu starts just fine, but when I select XP from the grub menu I receive a message 'disk read error'

Not sure what to do - I checked menu.lst which shows:
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

and ntfs is in partition dev/sda1 so I guess there is nothing wrong there. 

Any suggestions please?

Thanks

Dave

---

### Post by Jazzy_Jeff on 2009-05-12
Did you defrag your harddrive before you messed the the partitions? That could have messed up your MS Windows if you did not.

---

### Post by bistro on 2009-05-12
Thanks for the reply

er, no I didn't defrag - by 'messed up' do you mean 'irretrievably wrecked' by any chance?

Dave

---

### Post by Jazzy_Jeff on 2009-05-12
I am not sure on that. See if you can see the windows partition with Ubuntu. Maybe someone else will have a fix for it.

---

### Post by bistro on 2009-05-13
Hello

well, I can see the complete windows directory structure using nautilus and copy files from ntfs into ubuntu, so hopefully it is potentially fixable.

Any suggestions please?

Dave

---

### Post by lavinog on 2009-05-13
I don't think defraging is really required. windows defrag doesn't always move files to the beginning of the partition.
How full is the ntfs partition...you should leave at least 10% free.
Did you move the ntfs partition at all?
You might be able to try booting into the ubuntu live cd and using gparted to do a disk check (going from memory though, I cant remember how well this works)
otherwise you might have to use the windows disk to repair the partition. This will replace grub, so to reboot into ubuntu you have to reinstall grub.

---

### Post by lavinog on 2009-05-13
Also take this moment to backup your files you don't want to use just to be safe.

---

### Post by djdarrin91 on 2009-05-13
Exact same thing happened to me.I had to reinstall everything:(

---

### Post by sir_nasty on 2009-05-13
what partition is your ubuntu on and and which one is your xp on? are you sure that (hd0,0) is the correct drive?  what is the (hdx,x) listing for your ubuntu boot?

---

### Post by bistro on 2009-05-13
Hi

many thanks for all your replies. After looking around this and other forums some more, I installed testdisk.

The log reported "Warning: incorrect number of heads/cylinder 240 (NTFS) != 255 (HD)".

This utility was then able to fix the master file table and rebuild the boot sector - and that fixed the problem.

Best wishes

Dave

---

