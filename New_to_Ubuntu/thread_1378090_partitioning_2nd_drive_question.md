---
title: "partitioning 2nd drive question"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by clay woodruff on 2010-01-11
i have a second hard drive i want to add. my main drive has 9.10 installed. can i use the 9.10 disc to dump whatever is on the XP drive leaving me only a drive with windows xp on it. so i can boot to it if i want to use windows xp and if so will it delete any password/usernames associated with XP

---

### Post by talsemgeest on 2010-01-11
> **clay woodruff said:**
> i have a second hard drive i want to add. my main drive has 9.10 installed. can i use the 9.10 disc to dump whatever is on the XP drive leaving me only a drive with windows xp on it. so i can boot to it if i want to use windows xp and if so will it delete any password/usernames associated with XP
You can indeed. First, run ```
sudo fdisk -l
``` to see what the device numbers are, then use dd to move the partition across. So, if the XP partition is /dev/sda2, and the new hard drive is /dev/sdb, you would run ```
sudo dd if=/dev/sda2 of=/dev/sdb
``` Then you need to reinstall the XP bootloader to the second hard drive, so follow the XP instructions here: [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Also, it will not delete any usernames/passwords in windows xp.

---

### Post by clay woodruff on 2010-01-11
i apologize the 2nd drive already has XP on it. i got the hard drive from a computer someone had thrown out. only when i boot to that drive i get the username password screen and i dont have that info. and i was hoping i could use the 9.10 disc to dump any of that info and whatever files might be there and leave me with a clean XP hard drive

---

### Post by talsemgeest on 2010-01-11
You can access any of the files on the new hard drive, either from your existing ubuntu installation or from a live cd. If you need the password for the other drive, you could use ophcrack, there is a how-to [here](http://lifehacker.com/232963/screenshot-tour-how-to-crack-a-windows-password-with-ophcrack-live-cd).

---

### Post by clay woodruff on 2010-01-11
yeah i downloaded that and burned it to a disc but didnt do anything maybe it was a bad burn, try your link and i will see what happens

---

### Post by talsemgeest on 2010-01-11
> **clay woodruff said:**
> yeah i downloaded that and burned it to a disc but didnt do anything maybe it was a bad burn, try your link and i will see what happens
It is a bootable cd, you would need to boot it in the same way as the Ubuntu Live CD.

---

