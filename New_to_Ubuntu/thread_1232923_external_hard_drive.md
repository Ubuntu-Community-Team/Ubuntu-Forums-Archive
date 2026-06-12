---
title: "external hard drive"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by bjhome on 2009-08-06
I bought a WD Elements external hard drive now i need to know how to install it. i am getting an error saying error starting autorun program permission denied

---

### Post by nothingspecial on 2009-08-06
It sounds like there`s some sort of windows software on it.  I would remove.

I don`t necessarily recommend you do this because you might want the software that comes with it but then I don`t have windows or a mac.

---

### Post by bjhome on 2009-08-06
I read somewhere that it can be installed for use on both windows and linux but i don't know how to do this.they said it comes withformatted with FAT32  but they reformatted it as EXT3 for linux but if they used NTFS you can use it for both operating systems.
Unfortunately i don't understand any of this.
Can any body help me. please.

---

### Post by lkraemer on 2009-08-06
bjhome,
Like nothingspecial stated, it is the Windows software on the new
External drive that is trying to run when you plug in the drive cable.

You have to make your own decisions.  Will the Drive be used on Linux
ONLY, or maybe sometimes with Windows (YUK!)?

You should already know the answer to that question.

I don't like all that extra (fancy) software running when I plug anything
in a USB port so I typically delete it, but you may need it, or want it.

I'd stick the LiveCD of your Distro in the CD Drive and boot it.
Plug in the USB Drive, then run Gparted from the System Menu.

Then I'd make double sure that I picked the correct drive from the
top right area of Gparted, and then DOUBLE CHECK IT, before formatting
the partition.  You might want a NTFS Partition if Windows/Linux will be
accessing the drive, or EXT3 if Linux ONLY. Then CHECK AGAIN!  (The size
drive should help you find the correct one.)

Just make sure you format the correct partition of the correct drive
because once it is done your data will be gone.

lkraemer

---

