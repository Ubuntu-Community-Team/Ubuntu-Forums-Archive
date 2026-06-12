---
title: "Reformat Flash Drive"
date: 2009-12-02
forum: New to Ubuntu
---

### Post by Dullstar on 2009-12-02
I need to reformat my flash drive, but I don't know how to do it.  I'm guessing it has something to do with our favorite hard-drive eraser command (see announcement).

---

### Post by Aearenda on 2009-12-02
In Karmic, the 'Disk Utility' in System->Administration will do that for you; or you can install gparted, which is a little more intuitive. The drive must be unmounted before it can be formatted.

---

### Post by ramjet_1953 on 2009-12-02
1. Plug in the Flash drive.

2. When the icon appears on your desktop, right-click on it and choose the format option.

NOTE: If you want maximum compatibility, use the 'Compatible with all systems (FAT)' option.

Regards,
Roger :D

---

### Post by Aearenda on 2009-12-02
> **ramjet_1953 said:**
> 1. Plug in the Flash drive.

2. When the icon appears on your desktop, right-click on it and choose the format option.
....

Doh! I use that menu every other day and never noticed 'format' there before! Doesn't work on older systems though. And this is with Gnome - the OP has Kubuntu in the profile - YMMV.

---

### Post by Chame_Wizard on 2009-12-02
Install Gparted from the repositories and you can format your flash drive.:popcorn:

---

### Post by Dullstar on 2009-12-02
Technically, I have Ubuntu, but I installed the kubuntu-desktop package and then stopped using Gnome!  Though when I install 9.10, I'm just installing Kubuntu.

---

### Post by mkvnmtr on 2009-12-02
If you have erased everything on your disk when you use Gparted you might need to create a new partition table before a new format will work. Tryto just format first. If you can not use it under Device you will find the option to create the partition table.

---

