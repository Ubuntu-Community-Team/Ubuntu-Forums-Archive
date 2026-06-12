---
title: "Ubuntu re install problem"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by wStarbuck on 2009-02-24
I re installed Ubuntu, or thought i did, and after the CD ejected I shut down the PC. Now when I put in the CD I get the boot menu but when I attempt to install it i get an I/O error. 
I removed XP pro with the first install. 
 I have looked at some of the documentation and tried one solution "The user will want to use the backspace key to delete quiet splash" and it did not work.
  
  Thanks for any help

---

### Post by sneeks on 2009-02-24
mnnn,funny one,have you checked the partions with the live cd?

---

### Post by ptn107 on 2009-02-24
You can try wiping the partition table on the disk.  It's helped me during server installs when I goofed up encryption/RAID/LVM partitions that made the disk stall.

Go load up the Ubuntu CD again and get to a live session desktop (use the first option 'Try Ubuntu without any change to your computer').  From there open a terminal, Applications -> Accessories -> Terminal, and type:
```
dd if=/dev/null of=/dev/sdX bs=512 count=1
```
Where 'X' in sdX depends on where the disk is.  sda is the first drive, sdb the second, sdc the third, etc... (if you only have one hard disk its sda).  That command will blank out the boot record and partition table.  You can then reboot and attempt to install Ubuntu again and see if you still get the error.

---

### Post by wStarbuck on 2009-02-25
Thanks for the reply. I am unable however to go beyond the boot menu, cant get to the live CD. I have tried every possible way within the boot menu as well.

---

