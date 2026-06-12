---
title: "Ubuntu option still on Boot Menu?"
date: 2010-06-07
forum: New to Ubuntu
---

### Post by IBUA on 2010-06-07
Hey,

I installed ubuntu 10.04 and everything was fine for a day. But after trying to mount a NAS to it, I had problems in both Ubuntu and Windows 7 where nothing would work or would freeze. (I had dual-booted it, installed using WUBI).

The problem is, is that when Windows 7 booted, it went into a recovery mode and did the 'restore point' thing.

Windows 7 now works fine, however the Ubuntu option is still on the Boot Menu, despite no files remaining on the computer.

I want to reinstall Ubuntu (but I won't try mounting the NAS again) but the old Ubuntu option bugs me.

Could anyone suggest ways of removing the Ubuntu option off the Boot menu before I reinstall Ubuntu?

Thanks

---

### Post by Mariane on 2010-06-07
I would suggest reinstalling Ubuntu first and then editing the grub file. 

Mariane

---

### Post by sydbat on 2010-06-07
I would suggest never using wubi, as it almost always causes problems...at least IMO.

---

### Post by IBUA on 2010-06-07
> **Mariane said:**
> I would suggest reinstalling Ubuntu first and then editing the grub file. 

Mariane

Thank you, will do :)

Could you direct me in how i'd edit the grub file once i've reinstalled it?

---

### Post by anewguy on 2010-06-07
A couple of suggestions:

+1 on not using wubi.  Try to install Ubuntu in it's own partition for a true dual-boot.

When you do install Ubuntu to it's own partition and not use wubi, it will create a grub menu for you.


Dave ;)

---

### Post by Mariane on 2010-06-07
> **IBUA said:**
> 
Could you direct me in how i'd edit the grub file once i've reinstalled it?


Edit /boot/grub/menu.lst by typing in a terminal one of the following:

gksudo gedit /boot/grub/menu.lst
or 
sudo vi /boot/grub/menu.lst
or
sudo kwrite - and then you browse for the file if you are using kde. 

You can comment out the unwanted option by putting a # at the beginning of the corresponding line. Then you save and you're done. It is still advisable to do a backup first:

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.save

Mariane

---

### Post by IBUA on 2010-06-07
Ahh don't worry. I found the solution. It wasn't Grub which was the problem, it was just the boot menu. I had to delete an entry using the bcdedit.exe on windows.

Thanks for your help though :)

---

### Post by anewguy on 2010-06-07
> **Mariane said:**
> Edit /boot/grub/menu.lst by typing in a terminal one of the following:

gksudo gedit /boot/grub/menu.lst
or 
sudo vi /boot/grub/menu.lst
or
sudo kwrite - and then you browse for the file if you are using kde. 

You can comment out the unwanted option by putting a # at the beginning of the corresponding line. Then you save and you're done. It is still advisable to do a backup first:

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.save

Mariane

Hey, just so you know - they changed the default grub to grub 2, and it doesn't use the menu.lst file.  There are some other steps you have to do instead (including update-grub to rebuild the menu).  If you're interested, let me know and I'll point you to some info on it.  But menu.lst still applies for the older releases.

Dave ;)

---

