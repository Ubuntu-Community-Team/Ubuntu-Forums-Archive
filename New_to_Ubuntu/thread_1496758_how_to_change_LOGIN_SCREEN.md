---
title: "how to change LOGIN SCREEN"
date: 2010-05-29
forum: New to Ubuntu
---

### Post by frozenflames on 2010-05-29
i am using Ubuntu 10.4 and i was wondering how can i change my login box theme

---

### Post by sydbat on 2010-05-29
Should be the same as 9,10 - go to Synaptic, find and install Start-up Manager.

---

### Post by frozenflames on 2010-05-29
in synaptic i searched and there is no Start-up Manage :confused:

---

### Post by sydbat on 2010-05-29
> **frozenflames said:**
> in synaptic i searched and there is no Start-up Manage :confused:Sorry, I mistyped...it is all one word startupmanager.

---

### Post by wojox on 2010-05-29
> **frozenflames said:**
> in synaptic i searched and there is no Start-up Manage :confused:

It's in there. Search startupmanager

---

### Post by frozenflames on 2010-05-29
ok startupmanager is installed but when i open it  it got only two tabs [boot options] and [Advanced] nothing else no config for loing screen or theme :confused:

---

### Post by wojox on 2010-05-29
[Read this]("http://www.ubun2.com/question/293/how_ubuntu_change_login_screen_window_appearance_910") it's the procedure I use to change the wallpaper and windows.

---

### Post by frozenflames on 2010-05-29
yeah that didnt work
tty crt-alt-f1 took me to black screen like terminal
Login in ok
export DISPLAY=:0.0 worked ok
:confused: sudo -u gdm gnome-control-center this line gives  3 error

first one i couldnt copy but it was similar to below

warning **: get -actions-list()-problem cant load gtk-theme-selector.desktop

warning **: get -actions-list()-problem cant load gnome-cups-manager-selector.desktop
 then switch back alt-f7 it didnt work also :confused:

---

### Post by wojox on 2010-05-29
> **frozenflames said:**
> yeah that didnt work
tty crt-alt-f1 took me to black screen like terminal
Login in ok
export DISPLAY=:0.0 worked ok
:confused: sudo -u gdm gnome-control-center this line gives  3 error

first one i couldnt copy but it was similar to below

warning **: get -actions-list()-problem cant load gtk-theme-selector.desktop

warning **: get -actions-list()-problem cant load gnome-cups-manager-selector.desktop
 then switch back alt-f7 it didnt work also :confused:

Sorry about that. I get those errors as well. To get back to the login screen use Ctrl+Alt+F8

---

### Post by frozenflames on 2010-05-29
these warning came up 
warning **: get -actions-list()-problem cant load  gtk-theme-selector.desktop
.
.
.
.
.
.
  
nothing elese no new window to change the themes r any thing:confused: so that didnt wok:confused: so more help needed :)

---

### Post by hok00age on 2010-05-29
> **frozenflames said:**
> i am using Ubuntu 10.4 and i was wondering how can i change my login box theme

Download this tutorial:
[http://dl.dropbox.com/u/6786897/ubuntu_customization.tar.gz]("http://dl.dropbox.com/u/6786897/ubuntu_customization.tar.gz")

It covers customization of Ubuntu GDM too.

Hope it helps you.
Regards :)

---

### Post by frozenflames on 2010-05-29
:KSThan you that really helped and also i founf Gnome Art and it rocks:KS

---

### Post by robertrose6 on 2010-07-28
> **wojox said:**
> [Read this]("http://www.ubun2.com/question/293/how_ubuntu_change_login_screen_window_appearance_910") it's the procedure I use to change the wallpaper and windows.

I should have read the whole tread but anyways. I fallowed the link and ran the commands now appearance preferences shows up at ever login. Can someone help?

---

