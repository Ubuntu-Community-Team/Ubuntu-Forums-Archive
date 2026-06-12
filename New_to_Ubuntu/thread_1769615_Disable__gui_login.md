---
title: "Disable  gui login"
date: 2011-05-28
forum: New to Ubuntu
---

### Post by konsolelover on 2011-05-28
hello everyone, i have installed ubuntu 11.04 and i want to disable gui login as it takes time to load and i really don't need it very much and i can start x server with startx when i'll need it.....so i tried something like
sudo update-rc.d -f gdm remove
which didn't work(checked while rebooting)
i read about something to edit in /boot/grub/menu.lst which i didn't find in my system.......
so guys please help!

---

### Post by konsolelover on 2011-05-28
i was looking for inittab in /etc but didn't find it yet...........guys pls help

---

### Post by munzerelli on 2011-05-28
try commenting out the first line in /etc/X11/default-display-manager

---

### Post by konsolelover on 2011-05-28
ok i'm gonna try it........

---

### Post by konsolelover on 2011-05-28
i just commented out the first and only line of /etc/X11/default-display-manager and then rebooted it...and it just got stuck with ubuntu logo.....then i had to switch recovery mode and i made the change again in default-display-manager ....did i have to select any other option???..........pls help...thnks

---

### Post by munzerelli on 2011-05-28
try:
mv /etc/rc2.d/S99gdm /etc/rc2.d/K99gdm
Changing the S(tart) to K(ill) will not let the service start, but if  you want to change it back easily, you just do the reverse, and your  service is back!

good luck!

---

### Post by konsolelover on 2011-05-28
error: no such file or directoy

---

### Post by jramshu on 2011-05-28
You can go into administration>login screen and set it for auto login, you can also set the time delay for it. 

EDIT: Or are you wanting to boot into cli?

---

### Post by munzerelli on 2011-05-28
yes, he is wanting to just boot cli

try this:
[http://www.cyberciti.biz/faq/prevent-xorg-from-starting-in-linux/](http://www.cyberciti.biz/faq/prevent-xorg-from-starting-in-linux/)

---

### Post by jramshu on 2011-05-28
Try this:
```
sudo gedit /etc/default/grub
```Change this line from this:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```to this:

```
GRUB_CMDLINE_LINUX_DEFAULT="text"
```

```
sudo update-grub
```

---

### Post by konsolelover on 2011-05-29
@jramshu
thnx dude it worked....
but still i need little help
when i logged in cli and when i had to use gui mode , i just used startx and i got gui mode but there was no ubuntu panel in upside and bottom of the screen....don't know y(even in my login screen menu, i have selected ubuntu classic)..... i had to restart the gdm......any clue

---

### Post by jramshu on 2011-05-30
You can try to restart gdm this way:

```
sudo /etc/init.d/gdm restart
```

EDIT:
It may actually be this line:
```
sudo service gdm start
```

---

### Post by FinzLeft on 2012-04-30
When i checked my DEAFULT= it was blank or ""
so i added "text" but it still booted GUI.

> **jramshu said:**
> Try this:
```
sudo gedit /etc/default/grub
```Change this line from this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```to this:
```
GRUB_CMDLINE_LINUX_DEFAULT="text"
```
```
sudo update-grub
```

---

