---
title: "Booting W/ Recovery Menu, Authentication Failed @ GDM"
date: 2009-06-15
forum: New to Ubuntu
---

### Post by Game Over on 2009-06-15
[SIZE="3"]Hello! I am having a bit of trouble here... 

I just customized my grub splash, log in screen and turned off auto login. I need to edit /etc/gdm/gdm.conf and / or /etc/pam.d/gdm OR grub.lst but I can not get these to sudo gedit, even in the root, and obviously I can't fix it from the desktop because the Authentication Fails before I even have the chance to enter my password. 

I have cited many of the threads relating to this but nothing quite fits. I'm runny Jaunty on HP Pavilion 6000.

A HUGE thanks in advance,
Alva [/SIZE]

---

### Post by Game Over on 2009-06-15
[SIZE="3"]Bump.

Any help? Please and tanks.[/SIZE]

---

### Post by Azrael3000 on 2009-06-15
well from what I figure you have to edit these files in console mode. To do that press
CTRL + ALT + F1

log in with your username and password. Then type
```
sudo nano /etc/gdm/gdm.conf
```
(replace by any other file you want), save by pressing
CTRL + O
and quit with
CTRL + X
then you probably want to restart X by typing
```
sudo /etc/init.d/gdm restart
```
and you should be fine.
Edit: Maybe you need to press
CTRL + ALT + F7
to get back to tty7

HTH
Arno

---

### Post by Game Over on 2009-06-15
[SIZE="3"]It worked! You, my friend, are a life saver![/SIZE]

---

### Post by Azrael3000 on 2009-06-15
well I'm happy to hear that, thanks ;)

---

