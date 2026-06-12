---
title: "beginner help please."
date: 2009-01-20
forum: New to Ubuntu
---

### Post by zmufasa on 2009-01-20
Hello,I just got Ubuntu a few days ago,and i has been great to me.But a recent problem has occured.If I start my computer up normally the system goes to the boot screen,but begins scanning at the welcome screen saying that it is due to an improper shut down.It runs and when it is at stage 1/4 42.0% it launches to the maintenance shell and requires that I run fsck with the hdd mounted in read only mode.After doing that it runs scans but never finishes.Point being I just press Ctrl-D and system reboots and then I press Esc and go to the second option and it works about 50% of the time.The other fifty it says that I need to do the fsck again.so all in all it just takes 10-20 minutes to boot which is not terrible but seems excessive.If anyone has a sollution please help me if you can.And Thank you in advance.

---

### Post by oldos2er on 2009-01-20
If you have a LiveCD, boot from it and fsck from there.

---

### Post by ajgreeny on 2009-01-20
To add to oldos2er's comments, boot the live CD and use the terminal to make sure you get the right partition for your ubuntu install with the command ```
sudo fdisk -l
```Now using the partition info you have run ```
sudo fsck /dev/sda2
```but of course change the sda2 to whatever your ubuntu has been shown to be.

---

