---
title: "Pick between Hard Drives to boot up on?"
date: 2010-09-24
forum: New to Ubuntu
---

### Post by held7over on 2010-09-24
Ubuntu 10.04  I have two 250 gig Hard Drives on an older system. Currently, one is slaved to the other. 

I have a Ubuntu 10.04 operating system installed on each of them, but no personal data stored on either yet.

I want to be able to pick which one I boot up on. What do I need to do to accomplish this?

Thanks! :)

---

### Post by andrewthomas on 2010-09-24
```
sudo update-grub
```

---

### Post by held7over on 2010-09-24
Thanks andrewthomas,

I ran the command. It listed the kernels on sda1 and then listed the sda1 drive, but did not list the sdb1 drive. 

I have tried booting twice, and it does not appear to give me an option to boot off the second drive.

---

### Post by andrewthomas on 2010-09-24
go to system > administration > disk utility

When you open that up, does it recognize both drives?

---

### Post by held7over on 2010-09-25
Yes! Disk Utility sees both drives. Nautilus also lists the second drive.

---

