---
title: "How to make one OS boot by default in Boot menu"
date: 2009-05-31
forum: New to Ubuntu
---

### Post by anchorschmidt on 2009-05-31
Some of us like to dual boot our computers. However, you come to a boot menu before booting up and want to make one OS boot by default. For example if you have Ubuntu and Windows XP, and you're sharing your computer with your someone less computer literate than you are, you would want the OS to boot into windows by default right?. If not for this reason, then just for the sake of convenience. 

To do this 
```
sudo gedit /boot/grub/menu.lst
```

in the 12/13th line you will see default followed by a number 0. This number signifies the OS that will boot by default in the boot menu. 

so if my boot menus is like this (just as an example)
Ubuntu 
Kubuntu 
Windows (loader)

Then Ubuntu is 0, Kubuntu is 1 and windows is 3. So if I want to boot into windows. I will replace 0 with 3. 

Then save and close gedit.

---

### Post by pastalavista on 2009-05-31
OR... you can install startup manager and do it with a GUI ```
sudo apt-get install startupmanager
```:D

---

### Post by anchorschmidt on 2009-05-31
Wow thanks!

---

