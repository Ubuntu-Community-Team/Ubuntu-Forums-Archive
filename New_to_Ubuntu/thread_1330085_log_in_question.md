---
title: "log in question"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by bob58523 on 2009-11-18
Greetings....

I have a small problem, nothing serious. I have installed Ubuntu 9.10 x64 on my HP dv9260nr laptop. As I was installing all the programs that I would need I did something that changed the login screen. Not a big deal, but now it is (what I would guess) the basic gnome log in screen. How can I change it back? I am sure that there is a program that allows someone to do this, I just can't find it.

thanks,
Bob

---

### Post by nathan726 on 2009-11-18
Open a terminal (Applications > Accessories > Terminal)
And enter the following command:
```
gksudo -u gdm dbus-launch gnome-appearance-properties
```It should allow you to change various aspects of the GDM login screen through a GUI.

---

### Post by bob58523 on 2009-11-19
> **nathan726 said:**
> Open a terminal (Applications > Accessories > Terminal)
And enter the following command:
```
gksudo -u gdm dbus-launch gnome-appearance-properties
```It should allow you to change various aspects of the GDM login screen through a GUI.
I did as you said and this is what I get

"this theme will not look as you intended because the required GTK+ theme 'Humanlogin' is not installed.'

I did a search under synaptic for all 'gtk+' themes and did not find the one mentioned. I did notice that the human theme was already installed.

thanks,
bob

---

### Post by ukripper on 2009-11-19
May help: [http://www.ubuntumini.com/2009/09/hack-karmics-gdm-login-screen.html](http://www.ubuntumini.com/2009/09/hack-karmics-gdm-login-screen.html)

---

### Post by bob58523 on 2009-11-20
thanks for the idea... but this did not do what it said it would do. It only bought me to a screen showing all the programs that are available in the menus.

thanks again

---

