---
title: "netbook remix interface?"
date: 2010-07-15
forum: New to Ubuntu
---

### Post by ornothaloapq on 2010-07-15
i like the way the Ubuntu Netbook interface looks and i read that it is possible to have that interface on the ubuntu desktop version. does anyone know an  easy way to do that?

---

### Post by fooman on 2010-07-15
go to synaptic (system > administration > synaptic package manager) and search for and install "ubuntu-netbook-remix"

after it installs,  log out and when you get to the login window....click once on your user name,  then look down at the bottom of the screen and choose netbook remix from the menu and login.  

hope that helps.

---

### Post by kerry_s on 2010-07-15
> **ornothaloapq said:**
> i like the way the Ubuntu Netbook interface looks and i read that it is possible to have that interface on the ubuntu desktop version. does anyone know an  easy way to do that?

if you just want to add the desktop launcher, all you need is "netbook-launcher" you can add it to startup.

if you want the program that maximizes the applications, it's "maximus", i recommend you uncheck undecorate in gconf-editor if you want to keep the buttons. same thing add to startup.

---

### Post by KdotJ on 2010-07-15
or quick way,

```
sudo apt-get install netbook-launcher
```

then log out and select it from "Sessions"

---

