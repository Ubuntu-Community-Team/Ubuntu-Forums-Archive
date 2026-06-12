---
title: "New error appearing when drives are opened"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by Krishnan.V on 2009-02-06
[IMG]http://img19.imageshack.us/img19/9413/screenshot2qf6.png[/IMG]

Don't know why this problem is occuring? Kindly provide a suggestion

---

### Post by rgb96 on 2009-02-06
We need more info than that. What error is it?

---

### Post by perlluver on 2009-02-06
Is that a Hard Drive with Windows installed on it?  If so, is it a dual boot?  If both of them apply, then did you shut down the computer by pressing the power button or do a hard reboot?  If all of them apply then, you will need to boot into Windows, let it run Checkdisk, and hopefully it will fix any problems that may have happened.

---

### Post by Pollox on 2009-02-06
Are you trying to mount your Windows partition?  If so, is that partition hibernated, or did it not shut down properly?  You might try booting into Windows and shutting it down again.

---

### Post by Krishnan.V on 2009-02-06
Hi,I am using a Mult-os i.e. Windows xp and Ubuntu simultaneously and the above error is coming when i open my windows drives. Kindly assist

---

### Post by Krishnan.V on 2009-02-06
Yes, these are my hard drives installed with my computer

---

### Post by ajgreeny on 2009-02-06
You need to boot into windows making sure all the drives are readable in that,  and then shutdown windows properly.  Wait until it has completely shutdown, then boot into ubuntu, and you should be able to mount the drives without problem.

It is strange that you have seen this on an internal drive, as it is usually only seen on USB drives which have been accessed in windows and then pulled out without removing safely from the system first, though it can be seen if a windows drive is only in hibernation, or if windows crashed and a forced poweroff took place.  Which ever your situation, boot to windows, and then ubuntu again, and all should be well.

---

### Post by Krishnan.V on 2009-02-07
Now i am able to open the drives, but the second time. First time i get this below error. Kindly have a look and please provide a solution.
[IMG]http://img22.imageshack.us/img22/672/screenshotsx7.png[/IMG]

---

### Post by ajgreeny on 2009-02-07
In ubuntu please show the output in terminal from ```
sudo fdisk -l
``` and then ```
cat /etc/fstab
```This will show all your partitions on the machine and their file systems and then fstab shows what you have asked to be automounted at boot.  It may also be useful to see the output of ```
ls -l /media
```to see if you have mount points for those partitions you want to mount manually.

---

