---
title: "How to Disable KMS"
date: 2010-07-24
forum: New to Ubuntu
---

### Post by Vendettaseve on 2010-07-24
Hey

Im trying to disable KMS but the way suggested seems "risky"

> for GRUB 1: edit /boot/grub/menu.lst and add nomodeset to the line beginning with # kopt=, then run sudo update-grub). (533784, 541501) 

I tried editing this file and found the # kopt= line to have a pile of data on it. I am hesitant to remove said data so I tried adding the nomodeset to the end of it all but this did nothing.

What should I do?

Thanks

V

---

### Post by jtarin on 2010-07-24
Backup the original if you feel its risky. It can be edited from the Grub prompt if there is a problem.

---

### Post by Vendettaseve on 2010-07-24
I likely should mention im using 10.04

---

### Post by Vendettaseve on 2010-07-24
So I just did it and now its doing all sorts of fun things like not booting anymore -_-

How do I restore from the backup via command line.

---

### Post by DouglasAWh on 2010-12-30
> **Vendettaseve said:**
> So I just did it and now its doing all sorts of fun things like not booting anymore -_-

How do I restore from the backup via command line.

If you haven't figured this out, you can mount the drive using a live CD and edit the file.

If you're using an LVM...good luck.

---

