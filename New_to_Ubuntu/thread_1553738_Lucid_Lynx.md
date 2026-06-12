---
title: "Lucid Lynx"
date: 2010-08-15
forum: New to Ubuntu
---

### Post by CosmicFlux on 2010-08-15
Hi,

I've been away from Ubuntu for a while and I've just installed 10.4 (Lynx) on my desktop system. I understand there has been a change to the login framework, from usplash to plymouth?

What does this mean with regard to changing the login screen theme? I've managed to change the background of the login screen and also the boot splash screen with no issues, but I would like to change the actual login theme. 

Is this possible?


Cosmic

---

### Post by limestone on 2010-08-15
It's open source so it is possible but there is no easy way.. I think?
They say you also can't uninstall plymouth because it's baked in so much in Ubuntu.

---

### Post by TheWeakSleep on 2010-08-15
Are you talking about applying a different gtk theme to the login window? if so you can try this 
```
sudo -u gdm dbus-launch gnome-appearance-properties
```or
```
sudo -u gdm dbus-launch gconf-editor
```and set it using the gconf-editor. Edit the value of desktop--gnome--interface--gtk_theme key

or if you create a launcher for gnome-appearance-properties, you could move it to the /usr/share/gdm/autostart/LoginWindow and it would start automatically, though you would have to remove it after.

---

### Post by CosmicFlux on 2010-08-15
Thanks, I will give it a try. 

I don't understand why they would make this so hard in the later versions, it used to be so easy to do - just drag and drop the package.

Cosmic

---

### Post by 3rdalbum on 2010-08-16
Firstly, the login screen is GDM, not Plymouth. (Plymouth is the splash screen).

Secondly, the version of GDM in Ubuntu 9.10 and later are completely different to earlier ones. It's a complete rewrite. It does not support the old themes.

---

