---
title: "X11 screw up"
date: 2009-12-12
forum: New to Ubuntu
---

### Post by dunbrokin on 2009-12-12
I screwed up my X11 and am trying to change the file using the Live CD....I have mounted the disk

sudo mount /dev/sda1 /mnt

and

sudo gedit /mnt/etc/X11/xorg.conf

But there is nothing in the file!! Gparted shows my sda1 as mounted...I have sda2 also but I am presuming the Xorg is on sda1.

HELP!

---

### Post by jacobs444 on 2009-12-12
xorg is automatically configured now, so typically there is nothing in xorg.conf anymore.

---

### Post by Physical Hook on 2009-12-12
Delete it.

---

### Post by dunbrokin on 2009-12-12
But my old system will not boot up...it just hangs...I cannot even get to the failsafe....

---

### Post by Physical Hook on 2009-12-12
Then tell us how did you screwed it up. There should be a reason behind this ..

---

### Post by jacobs444 on 2009-12-12
+1 on last comment

---

### Post by dunbrokin on 2009-12-12
I pretty much followed this for my own monitor....and changed a Virtual Space command from 2043(I think) 1024 to Virtual Space 1280 1024


[http://ubuntuforums.org/showthread.php?p=8441312#post8441312](http://ubuntuforums.org/showthread.php?p=8441312#post8441312)

---

### Post by dunbrokin on 2009-12-12
bump!

---

### Post by dunbrokin on 2009-12-12
Right I have managed to get a command line and booted up on back of that....I can now see my directories using ls....but I have no GUI....how do I start the GUI?...It I try to do gedit /boot/grub/menu.lst I get "Gtk-Warning ** cannot open display"

---

### Post by dunbrokin on 2009-12-12
OK, using "sudo startx" I get some information about errors.....

Using config file "etc/X11/xorg.conf"

Parse error on line 24 of section Monitor in file etc/X11/xorg.conf"
"Option" is not a valid keyword in this section

EE Problem parsing config file
EE Error parsing the config file

Fatal server error
no screens found

So how do I change my xorg.conf from the command line..??

---

### Post by dunbrokin on 2009-12-12
Using nano I have been able to change the xorg.conf....

I did sudo dpkg-reconfigure --phigh xserver-xorg

but it made not a jot of a difference...I cannot still get the X to work.

What am I doing wrong?

Despite having changed the xorg.conf file, when I run sudo startx I get EXCACLTY the same errors as before...suggesting that the xorg file is still the same....how can that be?

---

### Post by dunbrokin on 2009-12-12
Solve by 1. renming the xorg.conf file xorg.conf.old using the mv command (Note you have to use nano in command line mode gedit will not work in command line).

2 restart....the machine sets up a new xorg.conf file...which solves the problem.

---

