---
title: "How do you do a clean install?"
date: 2011-03-20
forum: New to Ubuntu
---

### Post by ichigo6420 on 2011-03-20
I tried updating to ubuntu 10.04 with from 8.04. I have exactly the same problem as this person, but I don't know how to do a clean install in  this situation
[http://ubuntuforums.org/showthread.php?p=10581369#post10581369](http://ubuntuforums.org/showthread.php?p=10581369#post10581369)

---

### Post by kroq-gar78 on 2011-03-20
you delete the ubuntu partition, and run the install cd again.

Delete the partition by installing GParted (sudo apt-get install gparted), then select the partition, then delete.

Also, which person are you have the same problem as? Perhaps you dont *have *to do a clean install. There could be a workaround (though I probably don't know any. Some expert might be able to help with you.)

---

### Post by pi3.1415926535... on 2011-03-20
You can back-up your data, then burn a live-cd and boot and install from that.

---

### Post by ichigo6420 on 2011-03-20
I just added the link. thank you :)

---

### Post by ichigo6420 on 2011-03-21
> **kroq-gar78 said:**
> you delete the ubuntu partition, and run the install cd again.

Delete the partition by installing GParted (sudo apt-get install gparted), then select the partition, then delete.

Also, which person are you have the same problem as? Perhaps you dont *have *to do a clean install. There could be a workaround (though I probably don't know any. Some expert might be able to help with you.)
Is it the same if I don't have a partition?

---

### Post by Hedgehog1 on 2011-03-21
ichigo6420,

Sorry to hear your upgrade didn't go well.

Here are the steps for a clean install:

1) Boot off of the Ubuntu 10.04 'LiveCD/LiveUSB'.
2) Select TRY, and now copy any data you want to keep to a USB stick or external drive.

Data all backed up?  Then next:

3) Click the 'Install Ubuntu' icon.
4) When the install reaches the 'Allocate Drive Space' page, select: "Erase and Use the Entire Disk".

5) Finish the install.  Your computer will reboot and do updates.
6) Copy your data from the USB stick or External Drive back onto your computer
7) Load the current versions of any applications you use.

NOTE:  If you have as separate partition for '/home', you can save a step.  If you don't know that "separate partition for '/home'" means, then just ignore this paragraph.

***The Hedge***

:KS

---

