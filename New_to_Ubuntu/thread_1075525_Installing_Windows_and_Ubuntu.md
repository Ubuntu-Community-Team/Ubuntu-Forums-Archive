---
title: "Installing Windows and Ubuntu"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by gzav on 2009-02-20
Hi all,

I've formatted my computer to start from scratch and want to do a dual boot machine with winXP and Ubuntu. I've got 2 hard drives, and i want to make a 12 gig partition on the first one for windows and a 8 gig partition, still on the first, for Ubuntu.

But which one should i install first? When i installed windows, i got the option to create partitions, but then when i try to install Ubuntu, i can't choose the partition i created for it, and only managed to squash my windows install... 

So, how should I do it?

---

### Post by sailthesea on 2009-02-20
which version of Ubuntu are you trying?

---

### Post by gzav on 2009-02-20
8.10

---

### Post by sailthesea on 2009-02-20
You could install within windows using Wubi as I did, its a lot easier and doesn't really affect performance You'll probably have to re-enlarge the partition though

---

### Post by stim on 2009-02-20
Install Windows first. After Windows is installed, install Ubuntu.  Boot from the live cd and follow the instructions. When presented with the disk partition screen, [see link] choose 'manual'. You will then be able to install to the partition you created.  

[http://www.techotopia.com/images/5/52/Ubuntu_disk_partitioning_screen.jpg]("http://www.techotopia.com/images/5/52/Ubuntu_disk_partitioning_screen.jpg")

When Ubuntu is finished installing, it will create the correct GRUB entries for you and you will be able to select windows or Ubuntu upon the next reboot.

---

