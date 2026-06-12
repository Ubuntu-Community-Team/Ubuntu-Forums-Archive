---
title: "Dual Boot problem after install windows"
date: 2010-03-18
forum: New to Ubuntu
---

### Post by Brutus2006 on 2010-03-18
First of all I should appologize for installing anything widows related, but what the heck never known to be to smart.

I have 2 hard drives one with Ubuntu the second with XP. I got hold of a copy of Windows 7 thought Id install try it out. Now after install Grub does not come up to select Ubuntu instead goes direct to Windows. 

Any help would be appreiated

Thanks

---

### Post by J V on 2010-03-18
> 1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot.this

---

### Post by Brutus2006 on 2010-03-18
Not to sure what my hard drive numbers would be?

---

### Post by J V on 2010-03-18
What is the drive with linux on it?

it will show up as for example "sda2" - the SD stands for sata disc (could be hd for ide) the A means the first hard drive (0), and the 2 means the second partition (1, grub counts from 0)

---

### Post by Brutus2006 on 2010-03-18
all it shows is windows C: thats it I know I have 2 seperate hard drives. Do I have to reinstall Ubuntu now?

---

