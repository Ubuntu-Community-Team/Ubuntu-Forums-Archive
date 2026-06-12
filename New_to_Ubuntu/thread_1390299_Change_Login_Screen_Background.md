---
title: "Change Login Screen Background?"
date: 2010-01-25
forum: New to Ubuntu
---

### Post by 416inversed on 2010-01-25
In 9.10, I recently changed my Usplash to 'usplash-theme-ubuntu-color' on start-up, but the login screen still has that brown spotlight background.

How can I change it to a background that better matches the Usplash theme?

---

### Post by NCLI on 2010-01-25
How about [this]("http://www.omgubuntu.co.uk/2010/01/easy-gui-xslpash-background-changer.html")?

---

### Post by sisco311 on 2010-01-25
try this python script: [thread=1358026]GDM2 Configuration Tool[/thread]

or

run the theme manager as user gdm:
```
sudo -u gdm dbus-launch gnome-appearance-properties
```
or set the theme in gconf editor:
```
sudo -u gdm dbus-launch gconf-editor
```
edit the value of the /desktop/gnome/background/picture_filename key

---

### Post by 416inversed on 2010-01-25
> **NCLI said:**
> How about [this]("http://www.omgubuntu.co.uk/2010/01/easy-gui-xslpash-background-changer.html")?
Unfortunately, this didn't work for me because in changing my usplash theme, I turned off Xsplash. 

> **sisco311 said:**
> try this python script: [thread=1358026]GDM2 Configuration Tool[/thread]
Worked like a charm. I just created a black PNG and swapped images.

Thanks.

---

