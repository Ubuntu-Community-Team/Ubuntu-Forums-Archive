---
title: "ubuntu with xp"
date: 2011-07-31
forum: New to Ubuntu
---

### Post by Aitashan on 2011-07-31
is there a way to install xp dual boot on ubuntu

---

### Post by Gone fishing on 2011-07-31
Yes

If you have XP already installed the Ubuntu installer will do everything for you including resizing your Windows partition setting up grub etc.

And there are many other options such as running XP inside Ubuntu in Virtual Box or installing Ubuntu on the Windows file system using Wubi. Personally I'd gofor the first option.

---

### Post by jerrrys on 2011-07-31
its somewhat of a pain, but yes you can.

Partition your disk with gparted.
Install Windows
Re-install Grub.
Edit Grub to List Windows

i am guessing your running grub2

[https://help.ubuntu.com/community/Grub2#Changing%20or%20Moving%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Changing%20or%20Moving%20GRUB%202")

---

### Post by Paqman on 2011-07-31
> **jerrrys said:**
> 
Edit Grub to List Windows


Grub should automatically detect Windows during setup, but if it didn't then all you'd need to do would be run the command:
```
sudo update-grub
```
You shouldn't need to edit anything.

---

### Post by jerrrys on 2011-07-31
my bad; thanks paqman

---

### Post by amjjawad on 2011-07-31
> **Aitashan said:**
> is there a way to install xp dual boot on ubuntu

[http://ubuntuforums.org/showthread.php?p=10257675](http://ubuntuforums.org/showthread.php?p=10257675)

There are 6 different scenarios, see which one fits your case :)

OR

If you didn't like the guide, try to search here: [http://www.googlubuntu.com/](http://www.googlubuntu.com/)

---

