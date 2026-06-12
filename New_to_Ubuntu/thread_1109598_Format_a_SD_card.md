---
title: "Format a SD card???"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by sillyboy on 2009-03-28
I have a 8 in 1 USB thumb drive with a 4 GB SD card in.  The SD card became "full" all of a sudden.  I believe I forgot to unmount it, before I removed it. Is there a way to format the SD card in Ubuntu?  I need to be able to transfer files using the SD card to my Windows box.

Thanks

---

### Post by SuperSonic4 on 2009-03-28
You can use gparted on the live cd or qparted which I believe is the kde frontend.

Formatting the card will cause the loss of all the data though

---

### Post by sillyboy on 2009-03-28
Thanks.  How is this accomplished?

---

### Post by SuperSonic4 on 2009-03-28
You can use adept to search for qparted and then mark it for install and adept will do the rest. You'll need to be root so launch it with ```
kdesu qparted
```

I also may have got the package name wrong slightly so look around if qparted is not it

[KDE Partition Editor]("http://www.kde-apps.org/content/show.php/KDE+Partition+Manager?content=89595") is a good frontend but installation is a bit advanced as it involves adding a new repository

---

### Post by sillyboy on 2009-03-28
Thanks

---

