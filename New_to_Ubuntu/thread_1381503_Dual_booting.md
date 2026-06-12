---
title: "Dual booting"
date: 2010-01-14
forum: New to Ubuntu
---

### Post by pyrofreak99 on 2010-01-14
today i tried to dual boot windows7 and ubuntu but the problem im having is it needs to be in a ntfs format but linux is in a ext4 format therefor wont convert  is there anyway to put one of those partions in a ntfs format?

---

### Post by dmillerct on 2010-01-14
> **pyrofreak99 said:**
> today i tried to dual boot windows7 and ubuntu but the problem im having is it needs to be in a ntfs format but linux is in a ext4 format therefor wont convert  is there anyway to put one of those partions in a ntfs format?

While there are many guides to walk you through how to accomplish this, I found this one pretty straight forward and uncomplicated.

[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony]("http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony")

Check it out and let me know if you have any additional questions.

---

### Post by pyrofreak99 on 2010-01-14
ok i want to make sure the computer is formated to ntfs before i go and wipe the whole thing i tried that once and it was still in linux format

---

### Post by pizza-is-good on 2010-01-14
If I understand right, you want to make your whole HDD as single partition?

If so, just boot into a live CD of Ubuntu, go to GParted, and format your disk. Note: this will erase all your data.

If you need help with the process, just let me know.

---

### Post by Sef on 2010-01-15
If you want to dual boot, do this:

Windows - NTFS - on first primary partition.

Ubuntu - ext4 - on primary or logical partition

home partition - NTFS - any other partition

swap - swap partition

---

### Post by kansasnoob on 2010-01-15
Well I don't know where you're at with this right now. You first said:

> today i tried to dual boot windows7 and ubuntu but the problem im having is it needs to be in a ntfs format but linux is in a ext4 format therefor wont convert is there anyway to put one of those partions in a ntfs format?

Then you said;

> ok i want to make sure the computer is formated to ntfs before i go and wipe the whole thing i tried that once and it was still in linux format

Now if you still have Ubuntu installed look at pages 3 and 4 here:

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

Note: since you're using Ubuntu 9.10 those grub instructions are no longer valid!!!!!!!!!

Anyway you'll see they didn't format anything to ntfs. Just leave the space you want to use unpartitioned and unformatted.
 
To restore grub in Karmic afterwards look here:

[http://www.openpeta.com/index.php/how-to-recover-ubuntu-grub-after-windows-installation/](http://www.openpeta.com/index.php/how-to-recover-ubuntu-grub-after-windows-installation/)

---

