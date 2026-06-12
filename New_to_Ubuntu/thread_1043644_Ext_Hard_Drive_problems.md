---
title: "Ext Hard Drive problems"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by fknyeah on 2009-01-18
I don't have a windows machine to be able to remove my external hard drive safely from, and right now the HDD will not mount.  Please help, I have no idea what to do and this is my only way of backing up.

It is formatted to ntfs.

---

### Post by chriscross93 on 2009-01-18
> **fknyeah said:**
> I don't have a windows machine to be able to remove my external hard drive safely from, and right now the HDD will not mount.  Please help, I have no idea what to do and this is my only way of backing up.

It is formatted to ntfs.

Its probably being considered "dirty" by ubuntu (because of not being safely removed).  Does it have any data on it, or is okay if you format it?

---

### Post by baruch60610 on 2009-01-18
How does this drive connect?  Via USB?  

I find that when I reboot, I have to reconnect the external (USB) drive so that my system can "discover" the new device and deal with it.  I don't know of a way to automate this, though I'm sure some Linux guru could do it.

---

### Post by adam_kimber on 2009-01-18
IF you plug in the drive and an icon for it appears in the Computer, and then if you double click that icon it pops up a box stating "unable to mount due to x" then the drive is probably unclean as chriscross stated. Unclean means the filesystem has not been unmounted properly and contains some information not stored properly. 

Now you can force a mount to "clean" the drive but it can lead to data loss.

---

### Post by fknyeah on 2009-01-18
There is nothing on the drive so I don't care about formatting it, I just want to be able to use it. It connects through USB 2.0

---

### Post by MenZa on 2009-01-18
> **fknyeah said:**
> There is nothing on the drive so I don't care about formatting it, I just want to be able to use it. It connects through USB 2.0

Do so then - open gparted from System &#8594; Administration &#8594; Partition Editor and slam an ext3 partition on that baby. :)

---

### Post by fknyeah on 2009-01-18
> **MenZa said:**
> Do so then - open gparted from System &#8594; Administration &#8594; Partition Editor and slam an ext3 partition on that baby. :)

Thank you, I didn't realize it was that easy.

---

### Post by bigav on 2009-02-01
what if you want to keep the inforamtion on the ext hdd?

---

