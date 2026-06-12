---
title: "Fluxbox, setting up system tray, gtk etc"
date: 2010-03-21
forum: New to Ubuntu
---

### Post by Twiggeh on 2010-03-21
So, i've finally begun my switch from xfce to fluxbox.. its working ok so far, just a few snags.

Namely :
I do know know the names of the system tray applets xfce/xubuntu uses, so i cant put them in autostart.. I'd like to know the name of the network, sound/volume, and battery applets.

Also, my gtk theme looks horrible, i think it reverted back to some fugly default setting.. how do use the gtk theme i had from xfce? I guess its also just some program that needs to be put in autostart..

---

### Post by roccity1 on 2010-03-21
I think that you can load xfce-mixer and nm-applet like this in ~/.fluxbox/startup

xfce-mixer &
nm-applet &

(the "&" tells fluxbox to keep it open but run it in the background)

I don't know of any battery applet for fluxbox though.
As for the gtk themes you can try using lxapperance for gtk and then in the fluxbox menu there should be a option for styles this will change the border and colors.

---

### Post by kerry_s on 2010-03-21
theme = install lxapperance
network = nm-applet
sound, volume & battery = you can't use those, there're xfce4-panel applets made for xfce4-panel.

you should come over to the lxde side, you'll get all those features. ;)

---

### Post by roccity1 on 2010-03-21
You can use xfce-mixer and nm-applet in fluxbox I have many times before. You just have to install them.

---

### Post by Twiggeh on 2010-03-21
Thanks for the replies =)
But xfce-mixer doesnt seem to work properly, its not showing up in my system tray.. is there a separate command/flag/something to start the actual systray program?

---

### Post by kerry_s on 2010-03-21
if it's not a system tray program, you can't use it, fluxbox panel has no launchers or applets, it only has a system tray. xfce4-mixer is not usable as a icon.

if your looking for something light with the traditional panel, lxde is the one. it has all the settings, plugins & you can use more the 1 panel, i use 3 on mine.

---

### Post by Twiggeh on 2010-03-21
> **kerry_s said:**
> if it's not a system tray program, you can't use it, fluxbox panel has no launchers or applets, it only has a system tray. xfce4-mixer is not usable as a icon.

if your looking for something light with the traditional panel, lxde is the one. it has all the settings, plugins & you can use more the 1 panel, i use 3 on mine.

Thanks, but no thanks.. in that case i could just as well stay in Xfce.
I've always had a special love for fluxbox, i even use bblean for my gaming pc. So i specifically want this wm to work.. And if it doesnt then i already have xfce configured and ready to go.

Is there any systray-plugin for alsa i could download?
or make my volume knob on my laptop work without using whatever xfce is using?

---

### Post by kerry_s on 2010-03-21
yeah, you can do keyboard shortcuts.

the commands are:

```
amixer set Master 3+
amixer set Master 3-
amixer set Master toggle

```

in the old wm's, i used percentage instead, cause anything in between you couldn't really tell on my laptop speakers. i just had a volume section in the menu.

```
amixer set Master 25%
amixer set Master 50%
amixer set Master 75%
amixer set Master 100%
```

there also the option of docks, little applets that dock to a certain area of the screen, there use to be some volume wheels. i think it can use bbox & wmaker docks there's some in the repo. wmix?,asmixer?,etc... just type "mixer" in synaptic quick search.

---

