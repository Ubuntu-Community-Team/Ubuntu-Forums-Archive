---
title: "[SOLVED] Boot disc to reinstall NTFS part from an image"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by syrusd on 2008-12-13
Total beginner here.

Been using WinPE with imagex to create recovery discs for some PCs but I've found some older hardware that simply wont boot due to Vistas requirements or other such problems, so I thought "hmmm, perhaps linux holds the solution!".

So basically what I want is to create a bootable disc with tools to make an image of a systems boot NTFS partition and store it on a USB harddrive. Then make a recovery disc that will boot and format the boot partition, restore it from the image and then restart the machine without any user intervention.

So does anyone know if there are freeware tools for such a task? I expect it will require a number of titles to be integrated into a boot disc and then some sort of scripting to complete the various tasks on the recovery disc.

Any ideas would be greatly appreciated.

Many thanks
Dan

---

### Post by mikeyphi on 2008-12-13
Have a look at partimage - available through System/Administration/synaptic package manager

---

### Post by caljohnsmith on 2008-12-13
In addition to Partimage, you might want to check out [Clonezilla]("http://www.clonezilla.org").

---

### Post by syrusd on 2008-12-13
Many thanks, will look into that

Cheers
Dan

---

