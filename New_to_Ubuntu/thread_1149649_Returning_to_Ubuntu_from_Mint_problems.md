---
title: "Returning to Ubuntu from Mint problems"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by Timpotten on 2009-05-05
I have been having endless silly problems with my new Jaunty Jacalope -  (which I find as different from my stable 8.04 as the jackrabbit is from an antelope, and much more sluggish than before)

Mint (an Ubuntu branch) seemed faster and more user-friendly, so installed that.

When I finally decided to restore my old 8.04, the zip files were all corrupt (unexpected EOF) soo it was back to the live disk

Mint has a special version of Grub called gfxgrub. This enables the nice Grub eye-candy, but apparently bypasses the load from DVD or f8 boot-media selector !

There is no obvious way around it but to delete it with the mint partition editor and start again (maybe one could edit the grub menu at /boot/grub/menu.lsr?)

The distributor admits that some hardware "does not like" this version of grub, notably Mac(book).  

There is some help here, but it did not work for me
[http://www.linuxmint.com/wiki/index.php/How_to_repair_your_grub](http://www.linuxmint.com/wiki/index.php/How_to_repair_your_grub)

---

### Post by girishsasikumar on 2009-05-05
Booting from a CD/DVD or flash drive is a feature built into the hardware of your computer and there is no reason u cannot get the CD/DVD to boot even with gfx-grub ...

and by the way if u want to c the plain old grub, at gfx-grub menu press esc

---

