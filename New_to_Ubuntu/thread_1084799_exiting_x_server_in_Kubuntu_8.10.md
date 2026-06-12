---
title: "exiting x server in Kubuntu 8.10"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by sergeyf on 2009-03-02
Hello guys,

I am trying to install nvidia drivers and to do that I need to exit the x server first. I did according to what this guy said:

"
@nite owl : do Crtl+Alt+F1 to switch to a virtual console, log in, terminate the Xserver because it is still running :

Code:

sudo /etc/init.d/gdm stop

then start the installer

Code:

sudo sh /path/to/package.run

when the install is complete, you can either

Code:

sudo reboot

or restart your xserver

Code:

sudo gdm

"

but when I try the first line "sudo /etc/init.d/gdm stop" it cannot find the path. and I checked my root/etc/init.d folder and it doesn't have the "gdm" file

what do I do???

... sorry if its a stupid question but I am new to linux

THANKS

---

### Post by taurus on 2009-03-02
For Kubuntu (KDE), it's kdm

```
sudo /etc/init.d/kdm stop
```

Gdm is for Ubuntu--Gnome.

---

### Post by sergeyf on 2009-03-02
Thanks for the quick response!!!
worked great

---

### Post by sergeyf on 2009-03-02
Spoke to soon!!! when I restart I get a Black blank screen!!!
can access the console though with Alt+Ctrl+F1.
It said the the drivers were installed correctly...

---

### Post by Sysero on 2009-03-03
> **sergeyf said:**
> Spoke to soon!!! when I restart I get a Black blank screen!!!

Is that a black screen after you login and KDE loads?  If so, Press and hold 

[COLOR="Navy"]Alt - Shift - F12[/COLOR]

If you get your desktop, then go to:

[COLOR="Navy"]System Settings - Desktop - Desktop Effects[/COLOR]

and uncheck the [COLOR="Navy"]Enable Desktop Effects[/COLOR] button.

If you mean a black screen after reboot in general, you will need to edit xorg.conf.

Reboot into recovery mode.  Choose **root terminal** option.

```
sudo nano /etc/X11/xorg.conf
``` 

Scroll down and change the line:

[COLOR="Navy"]driver nvidia[/COLOR]

to

[COLOR="Navy"]driver nv[/COLOR]

Save the file and reboot.

---

