---
title: "Removing ubuntu 11.4"
date: 2011-05-08
forum: New to Ubuntu
---

### Post by jotnarta on 2011-05-08
Hi All
How can I remove the ubuntu 11.4 upgrade and back to previous 10.10??

---

### Post by Elfy on 2011-05-08
Reinstall with the 10.10 install medium you have.

Back up data you wish to keep.

You can install over the 11.04 install by picking the manual/advanced/not sure what it's called this time around partition options.

---

### Post by jotnarta on 2011-05-08
Thank you..

My problem is that I installed GNOME on my ubuntu 11.4, and it was working fine. After isntallation, the splash screen disappeared, the title bar disappeared, desktop effects disappeared, Simply, everything was screwed up.. restore my ubuntu 11.4??? please help

---

### Post by Hedgehog1 on 2011-05-08
If you wish to put the 'factory default' Natty 11.04 back over the modified 11.04, or 'downgrade; to 10.10, the steps are the same.

1) Backup your data in Ubuntu you wish to keep.

2) If you don't already have your '/home' in a separate partition, it is something you might want to consider: **_[SeparateHomePartition]("http://www.psychocats.net/ubuntu/separatehome")_**

3) The pictures below show an upgrade/refresh/downgrade with a separate '/home' partition.

[SIZE="3"]**Your actual partition numbers may be very different, so please determine which partitions on your PC hold the '/' (root) & '/home' and substitute these for the /dev/sda5 & /dev/sda7 shown in the pictures.**[/SIZE]

Here is what the allocation screen looks like:

[IMG]http://img27.imageshack.us/img27/6770/03allocdrivespace1.png[/IMG]

First, make /dev/sda5 your '/' (root) partition:

[IMG]http://img31.imageshack.us/img31/7520/04allocdrivespace2.png[/IMG]

[IMG]http://img130.imageshack.us/img130/9673/05allocdrivespace3.png[/IMG]

Next, set up the swap partition.  This usually sets itself up just fine, but double check it.

[IMG]http://img263.imageshack.us/img263/7656/06allocdrivespace4.png[/IMG]

The last partition to setup is the '/home' one:

**[SIZE="4"]IF YOU ARE DOING AN UPGRADE/DOWNGRADE/OS REFRESH, DO NOT FORMAT THIS PARTITION![/SIZE]**

[IMG]http://img202.imageshack.us/img202/6828/07allocdrivespace5.png[/IMG]

This separates your documents and 'stuff' from the system files and 'stuff' in the '/' partition.

This brings you to here:

[IMG]http://img34.imageshack.us/img34/6017/08allocdrivespace6.png[/IMG]

[SIZE="4"]**Please install the Boot Loader on /dev/sda !**[/SIZE]

Press "Install Now" and you are on your way:

[IMG]http://img855.imageshack.us/img855/7153/09installbegin.png[/IMG]



***The Hedge***

:KS

---

