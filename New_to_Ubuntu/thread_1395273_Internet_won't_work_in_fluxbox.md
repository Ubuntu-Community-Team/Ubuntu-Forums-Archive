---
title: "Internet won't work in fluxbox"
date: 2010-01-31
forum: New to Ubuntu
---

### Post by ppk on 2010-01-31
I was curious to try out fluxbox and I can't figure out how to get it to connect to the internet. It's been working flawlessly in both gnome and xfce4 so clearly it's a minor issue like turning wireless on but I can't figure it out. I have ubuntu karmic by the way.

---

### Post by Barriehie on 2010-01-31
When you're running fluxbox what does:
```

ifconfig

```
show???

Barrie

---

### Post by m_duck on 2010-01-31
I would imagine this is because Gnome and XFCE both have network manager set to autostart when they are starting, triggering the network connection. I assume fluxbox does not by default do this. If you have been using the standard network manager from Gnome (assuming it hasn't changed recently), you could add the following to your ***~/.fluxbox/startup***:```
nm-applet --sm-disable
```This should start Gnome's network manager when fluxbox starts.

Linky: [Fluxbox startup]("http://fluxbox-wiki.org/index.php?title=Editing_the_startup_file")

---

### Post by ppk on 2010-01-31
Wow that was easy. It works, thanks!

---

