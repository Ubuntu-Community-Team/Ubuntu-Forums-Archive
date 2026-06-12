---
title: "No access to Vista on a dual boot fresh install of Lucid"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by Berean on 2010-04-29
Hi, I've recently installed Lucid on a dual boot of my Vista machine.  All went well until I got to the screen where I can select Ubuntu/memory test/Vista and found there was no vista available!  I panicked and logged on to Ubuntu regardless, thinking that perhaps I'd inadvertently done an install of Ubuntu overwriting my Vista.  But when I looked at Places>Computer>Vista I can clearly see all the program files there, and assume there is a problem with Grub.  Can anyone help please?  Many thanks.

---

### Post by Paqman on 2010-04-29
Grub should have detected Vista when it installed, but in case it hasn't, try forcing it to update. Go to Applications > Accesories > Terminal and enter:
```
sudo update-grub
```
Enter your password when prompted. This will get Grub to scan your drives.

If that doesn't work we'll need more info. Let us know how many hard drives you've got, and exactly how you installed Ubuntu. If you could post the output of this command as well:
```
sudo fdisk -l
```
It would be very helpful.

---

### Post by Berean on 2010-04-29
[QUOTE=Paqman;9191260]try forcing it to update. Go to Applications > Accesories > Terminal and enter:
```
sudo update-grub
```
Why didn't I think of that? :lolflag: Grub updated and now it works fine.  Thank you so much.  Ian.

---

