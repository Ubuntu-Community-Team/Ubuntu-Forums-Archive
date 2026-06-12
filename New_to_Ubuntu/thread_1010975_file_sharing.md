---
title: "file sharing"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by will11 on 2008-12-14
i have a duel boot with windows xp and ubuntu 8.10. i would like to get some music of my windows and on to ubuntu but i dont nkow apart from saving the files to a usb drive transfering them over.

thanks
will11

---

### Post by Michael.Godawski on 2008-12-14
What you probably need is a samba share. Have a look here and report back when you encounter difficulties.

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)


edit:   sorry missed the point, but taurus comes and rescues me... :)
it is getting late here...

---

### Post by taurus on 2008-12-14
If you want to access your windows partition from Ubuntu, just mount it.  You can install ntfs-config and use it to configure your windows partition.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

p.s.  You don't need samba.

---

### Post by will11 on 2008-12-14
is there not an easy way of doing it. ive just started using ubuntu.

---

### Post by will11 on 2008-12-14
i used wubi to install unbuntu inside windows i think

---

### Post by will11 on 2008-12-14
theres also a problem with my ubuntu. everytime i try and download something it says " dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem." i looked up what i had to do and i did it but everytime i try it my pc freezes.
HELP!

---

### Post by taurus on 2008-12-14
Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
```

---

### Post by bodhi.zazen on 2008-12-14
First , welcome to Ubuntu.

In general, try to keep one topic per thread. Fixing dpkg is not the same as file sharing.

First to fix your problem :

```
sudo dpkg --configure -a
```

If that fails, we need you to post the error message.

Second, ntfs-config is the easy way. It takes some time to learn a new OS and we are here to help, but it is a bit of an adjustment.

If you want to know how it works, see:

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018") 

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by theozzlives on 2008-12-14
> **will11 said:**
> is there not an easy way of doing it. ive just started using ubuntu.

just go to places>xx.x GB Media and presto you can copy your music

---

### Post by will11 on 2008-12-14
i dont understand how post an error message and it didnt work  bodhi.zazen

---

### Post by will11 on 2008-12-14
everytime i type in dpkg configure a i says dpkg: error processing vinagre (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Setting up libgnutls26 (2.4.1-1ubuntu0.2) ...

---

### Post by bodhi.zazen on 2008-12-14
You can copy and paste from the terminal.

Highlight the text, move the mouse to firefox, and press the wheel down.

Try :

```
sudo apt-get install vinagre
```

---

