---
title: "dual boot windows7"
date: 2010-01-20
forum: New to Ubuntu
---

### Post by bobheaps on 2010-01-20
i am trying to add ubuntu 9,04 to my notebook which is running windows7 i want it to be a dual boot system.
gparted showed the following
/dev/sda1 199MB
/dev/sda2 284 GB
/dev/sda3 13.5 GB
/dev/sda4 103.3 MB
I reduced the size of sda2 thinking I was creating space for Ubuntu.
sda2 was reduced in size but the saved space was marked as unusable.
Reading the forums i found that you can only have 4 primary partitions and any extra space is marked as unusable,
so the question is how can I install a second system alongside windows7?

---

### Post by steve-shinn on 2010-01-20
The simplest way is to install a second hard drive, and use that hard drive solely for your Ubuntu install

---

### Post by NCLI on 2010-01-20
Hey Bob.

No need for an extra HDD. Usually, Windows only occupies one partition. I'd suggest deleting the smaller partitions, which are most likely just there to let you easily restore Windows. As long as they're only a few gigabyte in size and you know how to install Windows from a DVD, you should be able to delete them safely. 

I would like a screenshot of the partitioning screen though, just in case. To take one, press the Print Screen(Often abbreviated to Prt Scr) button on your keyboard.

---

### Post by chuina on 2010-01-20
Are all of your 4 drives primary ?
Ubuntu require only 1 primary drive.The /boot partition.
Others Ubuntu can be installed into extended>logical partition.

If your are not sure about primary or logical.
Open a terminal from: Applications>Accessories>Terminal
And give the command and paste it's result in this forum.

```
sudo fdisk -l
```

---

### Post by NCLI on 2010-01-20
> **chuina said:**
> Are all of your 4 drives primary ?
Ubuntu require only 1 primary drive.The /boot partition.
Others Ubuntu can be installed into extended>logical partition.

If your are not sure about primary or logical.
Open a terminal from: Applications>Accessories>Terminal
And give the command and paste it's result in this forum.

```
sudo fdisk -l
```

Apparently they are, since he's unable to use the partition he's created ;)

---

### Post by bobheaps on 2010-01-20
I removed the smallest windows partition which allowed me to add Ubuntu. Everything is now up and running. now I have to figure out how to get on line with it
THANKS FOR YOUR HELP
BOB

---

### Post by corncob on 2010-01-20
I was going to say that on my Gateway NV54 sda1 boots to 'Windows reinstall', sda2 boots to 'Windows Restore', sda3 boots to Windows 7, and sda4 is the extended partition where I have Ubuntu.  This explains why my installation of Ubuntu Ultimate disappeared into 'unallocated space'

---

