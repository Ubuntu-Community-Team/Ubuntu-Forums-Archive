---
title: "WIFI help"
date: 2008-08-04
forum: Networking &amp; Wireless
---

### Post by majorgoodshotpayne on 2008-08-04
Im using Ubuntu 8.04 and have a linksys wmp54gs/broadcom 4318 wifi card.  I really need help using it as i am new to Linux and just switched from Windows Xp, which i hated with a passion.  Any help would be greatly appreciated, ive tried using Ndiswrapper 1.53 but i dont know how and there are no user frienly insrtuctions i can find.

---

### Post by swisscow on 2008-08-04
I am no expert on ndiswrapper, though someone will I'm sure be along in a moment who is to help. However if you still get nowhere give anpther distro such as pclinuxos a go. The reason I say is they have a very user friendly ndiswrapper set up in the install routine.

Of course you should stay with Ubuntu.................but if you can't pclinuxos is a hell of a lot better than xp

---

### Post by Ryadt on 2008-08-04
Try see if it is in System > Administration > Hardware Drivers. Enable it if its there.

---

### Post by majorgoodshotpayne on 2008-08-04
its not their, how do i get it there?

---

### Post by Ryadt on 2008-08-04
Try this tutorial
[http://ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+4318](http://ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+4318)
hope this helps u.

---

### Post by mb_webguy on 2008-08-04
Install ndisgtk.  It's a GUI front-end for ndiswrapper, and makes it much easier to use.

The hardest part of using ndiswrapper is getting the Windows driver, but once you have the .inf file, if you have ndisgtk, it's just a couple of clicks.

---

### Post by majorgoodshotpayne on 2008-08-04
thanks guys im gonna try the one link first and then the other if it doesnt work, i hope it does, get back with the results later

---

### Post by majorgoodshotpayne on 2008-08-04
ok i looked in hardware drivers, all that i have listed in nvidia legacy my video drivers, there is no wifi card listed

---

### Post by majorgoodshotpayne on 2008-08-04
ok i got the card to show up under device drivers but it says its in use and its unchecked.  every time i try to enable it it says to reboot.

---

### Post by jpeddicord on 2008-08-04
Moved to Networking & Wireless.

---

### Post by majorgoodshotpayne on 2008-08-04
Ok so when i rebbot it still isnt enabled and when i check enable it tells me to reboot again, i really dont wanna switch back to Xp, i used ndisgtk to get the drivers and then used the Lynksis disk for the ini file, in the install proocess their was a firmware error so i had to cancel, how do i fix it or delete the space in hardware drivers so i can try and redo it?

---

