---
title: "I would like to know how to be able to Dual Ubuntu with Boot WIndows 7"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by friyia@hotmail.com on 2009-01-29
Hey Ubuntu users out there. I have Ubuntu 8.10 and I would like to know how to get windows 7 on there as well so I can use both thanks.

---

### Post by Raccoon1400 on 2009-01-29
It shouldn't be any different from any other windows/linux dual boot.

Download the beta from the microsoft site
make a new ntfs partition with gparted, which is on the ubuntu live CD
install win7 to the new partition
you will have to reinstall grub. I don't know the ubuntu method for this, but you could look up super grub disk
you will also have to create a grub boot entry for windows, at least if you use super grub disk

---

### Post by Gotaro on 2009-01-29
_[Here's a link](http://forum.kde.org/-solved-dual-boot-wont-work-t-27813.html)_ to a thread I made about the issue of getting GRUB working again after you repartion with Gparted and get Windows installed.  You'll find two very useful links in the posts.

Also, a little heads-up..  When you create your new Windows partition, you have to make sure and format it to NTFS, because the Windows installer won't do it for you, for whatever reason.

---

