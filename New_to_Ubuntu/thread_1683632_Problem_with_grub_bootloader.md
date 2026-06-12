---
title: "Problem with grub bootloader"
date: 2011-02-07
forum: New to Ubuntu
---

### Post by sarrfriend on 2011-02-07
Hi
   I have installed Ubuntu along with Windows XP and by default the bootloader loads Ubuntu. I want to change it to load Windows by default. I searched the forum for ways to do this and found that I have to edit menu.lst file. When I opened the file using sudo gedit /boot/grub/menu.lst an empty gedit screen opened. Please help.

---

### Post by Quackers on 2011-02-07
Welcome to UF.
If you have Ubuntu 10.04 or 10.10 installed you will be using grub2. This later version of grub does not use the menu.lst file.
To change the default OS you can read the guide below for details, in particular section 5
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

OR

in the first paragraph of that guide there is a link to the new GUI utility (Grub Customizer) which may be a simpler method for you.

---

### Post by Johnce on 2011-02-07
Greetings!

if you want to go the GUI way . . .

In the software center you can get 'Start Up Manager'. After you install it, it will be under System => Admin. from there you can change the basic look and feel of Grub, including default OS.

Hope this helps!

-johnce

---

### Post by patrick281981 on 2011-02-09
Hi,

Go to /boot/grub/grub.cfg file and edit "GRUB_DEFAULT=0" Sets the default menu entry by menu position. As in GRUB, the first "menuentry" in grub.cfg is 0, the second is 1, etc. So if your Windows entry menu is for example 5th the default will be 4.. 

Read more on the 
[https://help.ubuntu.com/community/Grub2#/boot/grub/grub.cfg](https://help.ubuntu.com/community/Grub2#/boot/grub/grub.cfg)

Regards..

---

