---
title: "Busybox after encrypted installation"
date: 2011-06-22
forum: New to Ubuntu
---

### Post by roodypoo on 2011-06-22
I installed Ubuntu using the alternate CD for encryption. I have a 200MB /boot partition that is unencrypted and the rest of the disk is encrypted. When I boot the system I get the page to select the kernel, then it goes to a busybox prompt.

How do I get by that? I can access the encrypted part of the drive with the LiveCD.

---

### Post by roodypoo on 2011-06-22
I forgot to mention that I get to enter the passphrase for the encrypted drive, then it goes to busybox.

---

### Post by disabled20191128 on 2011-06-22
And where exactly did you install the system in the 200mb /boot partition?

---

### Post by roodypoo on 2011-06-22
I have 2 partitions, one for /boot at 200MB and one for / that is the rest of the disk.

---

### Post by disabled20191128 on 2011-07-17
Try making a partition mount point / containing the system and an other encrypted one containing your files mount point /home + the swap partition.

---

### Post by bodhi.zazen on 2011-07-17
Sounds as if encryption is not properly configured.

You can either re-install, or boot a live CD and try to fix the problem.

See : [https://help.ubuntu.com/community/EncryptedFilesystemsViaUbiquity](https://help.ubuntu.com/community/EncryptedFilesystemsViaUbiquity)

If you need assistance we need a lot more information. Are you using LVM ? How did you set up encryption ?

---

