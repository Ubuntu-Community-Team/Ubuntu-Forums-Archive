---
title: "usb lash as boot key"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by gaziks on 2009-01-18
hello all. i wish to ask is it possible to boot ubuntu only if usb flash or SD card is inserted in my laptop otherwise it boots Win xp without that screen where it asks either boot xp or ubuntu. cause i need to keep in secret... :) 
Thank you!!

---

### Post by rkh on 2009-01-18
If I understand you correctly, then yes. When you are booted to ubuntu go to System>Administration>Create a USB startup disc. I couldn't get this to work until I formatted the flash drive first (one big ext2 partition via System>Administration>Partition Editor (be careful that you select the correct drive!). Once I did this it worked like a charm. Once you have done all of this, just make sure that you set the bios to boot from usb and you should be good to go.

---

### Post by niteshifter on 2009-01-18
Hi,

Keep the existence of Ubuntu on a machine's HD secret? The answer is no. All anyone would have to do is boot from a Live CD (or USB drive) and look at the  HD partitioning, mount the partitions and browse through them. Even if one opts to encrypt the Ubuntu install - the existence of a second OS can not be hidden, /boot has to be unencrypted.

Boot a machine  with Ubuntu on a USB device and leave no trace? The answer is yes. I boot 8.04.1 from a USB key drive on my work-supplied laptop (XP installed on it) frequently.

---

