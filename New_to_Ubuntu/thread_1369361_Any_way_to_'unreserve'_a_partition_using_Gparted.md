---
title: "Any way to 'unreserve' a partition using Gparted?"
date: 2009-12-31
forum: New to Ubuntu
---

### Post by listerdl on 2009-12-31
Hi I have successfully dual booted windows 7 and ubuntu on a new laptop - the only issue is that it came with Vista pre-installed. I am unable to overwrite or unreserve its partition called winRE - which is the RECOVERY partiton for Vista should anything go wrong. Thing is, Id like to get rid of that completely. Any ideas?

THANKS and happy new year.

Lister

---

### Post by Sef on 2009-12-31
I used [GParted]("http://gparted.sourceforge.net") itself and was able to reformat the whole disk.   My computer is a Dell.

---

### Post by listerdl on 2009-12-31
> **Sef said:**
> I used [GParted]("http://gparted.sourceforge.net") itself and was able to reformat the whole disk.   My computer is a Dell.

thanks...i tried gparted but it doesnt allow me to remove winRE. I guess it isnt doing any harm there and in fact, perhaps it is better to keep this? (Thing is though that the winRE relates to Vista, an OS that I do not want anyway.... - this came pre-isntalled with the laptop).

Thanks ;)

---

### Post by durand on 2009-12-31
If a backup disk came with your computer, then you wouldn't need the WinRE partition. I deleted mine with gparted. Maybe you have it mounted, which could explain why you can't reformat it.

---

### Post by lisati on 2009-12-31
> **durand said:**
> If a backup disk came with your computer, then you wouldn't need the WinRE partition. I deleted mine with gparted. Maybe you have it mounted, which could explain why you can't reformat it.

+1 
Neither my current laptop nor my main desktop came with recovery disks, but both came with software to make them. Before you go deleting your recovery partition, it might be good to make sure you have a set of recovery disks - just in case you need to reinstall Windows for some reason, e.g. if your machine needs servicing under warranty.

---

### Post by listerdl on 2009-12-31
ok thanks...

but having a Vista winRE isnt doing any harm is it? - I have dual booted Windows 7 and Ubuntu and have no need for the Vista Loader....but is it ok just to keep it there?

thanks ;)

---

### Post by durand on 2010-01-01
Oh yeah, there won't be any problems.

---

