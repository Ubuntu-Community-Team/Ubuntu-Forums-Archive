---
title: "Delete Key Doesn't Send to Trash?"
date: 2010-07-26
forum: New to Ubuntu
---

### Post by EnigmaticCoder on 2010-07-26
When you're in nautilus file manager and you press the delete key on a file and delete it, why doesn't the file go to trash:///?

(This happens when I'm browsing my Windows partition. Not sure if this happens normally.)

---

### Post by philinux on 2010-07-26
> **EnigmaticCoder said:**
> When you're in nautilus file manager and you press the delete key on a file and delete it, why doesn't the file go to trash:///?

(This happens when I'm browsing my Windows partition. Not sure if this happens normally.)

[http://ubuntuforums.org/showpost.php?p=4022149&postcount=17](http://ubuntuforums.org/showpost.php?p=4022149&postcount=17)


See the whole thread too.

---

### Post by Krabby.Linux on 2010-07-26
Everythng is alright .... Only Files which are being deleted from the Ubuntu Partition will be send to trash

---

### Post by -kg- on 2010-07-26
> **Krabby.Linux said:**
> Everythng is alright .... Only Files which are being deleted from the Ubuntu Partition will be send to trash

...on the Ubuntu partition.  As the thread philinux pointed out said, a "trash" file is created and used on every other partition that you delete things from.

A good demonstration of this is to plug in a USB flash drive and delete some files from it.  When you unmount it, before it unmounts it will ask you if you want to empty the trash before unmounting.  That means that the files you deleted from it are stored on the flash drive itself, and if you want the trash file emptied, you have to specify that it be done.

Same with normal partitions on the hard drive.

---

