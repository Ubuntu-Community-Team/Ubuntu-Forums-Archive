---
title: "Gparted can't see partitions!"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by Johnny-A on 2009-05-12
Sorry to disturb you,

I have installed Mandriva as a third OS after Windows-xp and Ubuntu. Now I want to repartition Mandriva and install again the Ubuntu.

Ubuntu CD Gparted can't see the partitions in one of steps of installing procedure, it sees the whole hard drive as one, and I can't risk going on to not lose the windows partition.

If any answer appreciated.

---

### Post by Didius Falco on 2009-05-12
Hi,

First, let's get a look at what the situation is. Download the BootInfoScript linked in my signature. You can download it to the desktop from Your Live CD. After you have it on the desktop, open a terminal and type ```
sudo bash ~/Desktop/boot_info_script*.sh
```

The script will gather a lot of information that will help figure out the problem into a file named RESULTS.txt

Open that file, select all and paste it in this thread, then put code tags (the # on the toolbar) around it.

It'll help to figure out the answer faster...

Regards,

Didius

---

### Post by swoody on 2009-05-12
Hi Johnny-A, and Welcome to Ubuntu, and the Forums ):P

Try Didius Falco's suggestion first^^

It sounds like your issue may be caused by a faulty partition. This is most often caused by Windows, so try Dowloading [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk_Download") and running it in **Windows** following [this first]("http://www.cgsecurity.org/wiki/Running_TestDisk") and then [this.]("http://www.cgsecurity.org/wiki/Menu_Analyse") See if that comes up with any errors on your system, and if it fixes any of them. Afterwards, try to go through the setup process again with your LiveCD, and see if it recognizes your partitions. Post back here, and let us know if it works out, or if you encounter any new issues :D

---

### Post by waspbr on 2009-05-12
doesn't mandriva use LVMs?

---

