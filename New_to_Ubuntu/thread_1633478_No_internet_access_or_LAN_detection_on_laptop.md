---
title: "No internet access or LAN detection on laptop"
date: 2010-11-29
forum: New to Ubuntu
---

### Post by Satki on 2010-11-29
Hi, completely new user to Ubuntu here; I recently dual booted Ubuntu using Wubi and it starts up absolutely fine.

It cannot connect to the internet however, it doesn't seem to be able to detect the LAN cable at all, (no notifications or recognition when I unplug/plug it in). I'm at UNI,and have a friend who is running the same install as me on his laptop, but detected the internet automatically on first install, so its not a network configuration problem. I'm thinking the problem lies with the drivers for the laptop, but I'm not sure.

The laptop I'm running is a Toshiba Satellite Pro L650-165

---

### Post by madjr on 2010-11-29
thats weird, lan should work.

do you have a live-cd/dvd or live usb (1gb+ thumb drives) of ubuntu you can try?

if not , you can burn a cd (image mode) or create a live-usb pretty quick with unetbootin.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

if live works correctly then ubuntu is fine and there might be an issue with the wubi install (which like i said is rare).

You can then uninstall the wubi setup and install to a real partition from the live (not a virtual one like with wubi, since is for temporary learning anyway).

---

### Post by Kernelingus on 2010-11-29
You might also want to open up a terminal window and type:

```
ifconfig
```

Post the results here.

---

