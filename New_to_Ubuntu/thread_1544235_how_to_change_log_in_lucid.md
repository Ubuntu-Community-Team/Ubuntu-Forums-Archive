---
title: "how to change log in lucid"
date: 2010-08-02
forum: New to Ubuntu
---

### Post by DarinB on 2010-08-02
I had some really cool log in screens i created in earlier versions of Ubuntu. Can that be done in Lucid?

---

### Post by LowSky on 2010-08-02
Yes it can

---

### Post by DarinB on 2010-08-06
hey low sky 
could you guide me a little more?
i have found it difficult to find a tutorial on it.

---

### Post by nick_goodfate on 2010-08-06
you can use ubuntu tweak (you can find it in Software Center) to change login screen logo, login wallpaper and choose if you want user list and restart buttons to be displayed . You can also disable/enable sounds at login .

---

### Post by DarinB on 2010-08-07
I use Linux mint 9 i can't find ubuntu tweak

---

### Post by sisco311 on 2010-08-07
> **DarinB said:**
> I use Linux mint 9 i can't find ubuntu tweak

Add gnome-appearance-properties & gconf-editor to GDM's autostart:
```
sudo  cp -t /usr/share/gdm/autostart/LoginWindow/ /usr/share/applications/gnome-appearance-properties.desktop /usr/share/applications/gconf-editor.desktop
```

Log out. Two new windows should appear. 

In gconf-editor, go to apps -> gdm -> simple-greeter, where you can change/setup the banner text, disable/enable the restart buttons and user list...

In gnome-appearance-properties you can change the theme, background, icon theme, mouse cursor...

When you are done, close the windows and log in, then remove the apps from GDM's autostart:
```
sudo rm /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow/gconf-editor.desktop
```

---

### Post by rburkartjo on 2010-08-07
dar here is the link for ubuntu tweak. and i used mint before and it works just great

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by DarinB on 2010-08-08
ubuntu tweaks does not work for me...
I see others on a google search have the same thing

---

### Post by DarinB on 2010-08-08
> Add gnome-appearance-properties & gconf-editor to GDM's autostart:
Code:

sudo  cp -t /usr/share/gdm/autostart/LoginWindow/ /usr/share/applications/gnome-appearance-properties.desktop /usr/share/applications/gconf-editor.desktop

Log out. Two new windows should appear.

In gconf-editor, go to apps -> gdm -> simple-greeter, where you can change/setup the banner text, disable/enable the restart buttons and user list...

In gnome-appearance-properties you can change the theme, background, icon theme, mouse cursor...

When you are done, close the windows and log in, then remove the apps from GDM's autostart:
Code:

sudo rm /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow/gconf-editor.desktop

Please explain how this differs from ubuntu tweak and what does the -t do
also will this give me the application from earlier versions of ubuntu to change the log in

---

### Post by DarinB on 2010-08-08
Hey sisco311 it worked great....
is there a way to change the actual log in part since it is in the middle and blocks my picture.

---

### Post by DarinB on 2010-08-09
i saw an earlier post this > sudo -u gdm gconftool-2 --set /apps/gdm/simple-greeter/disable_user_list --type bool true

what does this do? can it let me use the login windows preference from jaunty...will this cool thing come back to create themed log ins??????

---

