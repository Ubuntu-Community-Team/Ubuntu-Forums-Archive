---
title: "Help!!!"
date: 2010-11-27
forum: New to Ubuntu
---

### Post by rvgsd on 2010-11-27
Hi! I had 2 Ubuntu 10.04, 10.10 installations and windows 7 on my hard disk. (Ubuntu's are on extended partition.)
I deleted the 10.04 partition from windows partition manager. Now I cannot boot, it says, 
"Grub error: No such partition". I believe I damaged the grub2.. How can I recover/reinstall grub?? 

This is kind of urgent! any help would be gladly appreciated!

---

### Post by rmockler on 2010-11-27
Reboot from your Ubuntu CD. go to the command line, and key in:
  sudo update-grub
Then do a restart, remove the CD and reboot

---

### Post by Ocxic on 2010-11-27
extended partitions are connected, so if you created 2 extended partitons say partition #1, and partition #2. And deleted partition #1, your would also loose partition #2, because they are linked in series. that is most likely what happend.

try using "testdisk" from a live CD to recover your partitions.(IF you have not made changes to your other partitons.)

---

### Post by rmockler on 2010-11-27
From the OP's description of the problem, I don't believe the Windows partition was part of the extended partition.

---

### Post by rvgsd on 2010-11-27
Thanks for help!!
windows is on the primary partition, and the Ubuntu's are(were) on the logical.
I am trying it now..i'll update in a few minutes!

---

### Post by rvgsd on 2010-11-27
when i do a 'sudo update-grub' from the live cd, i get
```
/usr/bin/grub-probe: error: cannot find a device for / (is /dev mounted?)
```

From 'sudo fdisk -l' I can see all my partitions are good.

Any suggestions?

---

### Post by rvgsd on 2010-11-27
Thanks for the help guys!! I was able to fix this from:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
:p

---

