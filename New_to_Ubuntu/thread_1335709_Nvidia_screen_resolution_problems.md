---
title: "Nvidia screen resolution problems"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by Gary Nored on 2009-11-23
Running 9.10 (which is totally awesome!).
Installed nvidia driver. Nvidia is correctly aware of my monitor size (1920x1200), but Ubuntu isn't. 
When I try to save nvidia settings, it reports that it cannot parse /etc/X11/xorg.conf. So the configuration is never saved. 

I'm pasting the contents of this file below. Shouldn't there be more to it?

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

---

### Post by wrgb2 on 2009-11-23
I am running an Nvidia card also, and mine looks just like yours except for the following line at the end of the "Screen" section :

Option	"AddARGBGLXVisuals"	"True"

Also, my Nvidia X Server Dispaly Congiguration is set to Auto and correctly recognizes my maximum resolution.

---

### Post by Sealbhach on 2009-11-23
Try running nvidia-xconfig.

So just go to another terminal: Ctrl+Alt+F1

Log in.

Bring down the X server

```
sudo service gdm stop
```

Then

```
sudo nvidia-xconfig
```

Then

```
sudo service gdm start
```

.

---

### Post by Madel on 2009-11-23
Probably, the problem is in monitor detection and not nvidia.

I have just installed Ubuntu on 2 different machines. Actually, both system unit have the same contents. Same motherboard brand, same model, same nvidia card and model. The only different is it's monitor.

The 1st PC have a LCD monitor. No problem after installing nvidia proprietary drivers.
The 2nd PC have a CRT monitor. Working with the nv driver. But after installing nvidia proprietary drivers, I can't get to the GUI. Im stuck in the terminal. Though, i have a friend of mine who have experienced this same problem, yet, he's still not around. Still waiting for him to fix it. He was talking about configuring x.org manually. But he said he's not sure if it works with 9.10. He just said that it did work with 6.06 and 8.04, LTS versions.

---

### Post by mechro on 2009-11-23
> **Gary Nored said:**
> 
When I try to save nvidia settings, it reports that it cannot parse /etc/X11/xorg.conf. So the configuration is never saved. 


To be able to save the configuration you have to do **gksudo nvidia-settings **.

---

### Post by Gary Nored on 2009-11-24
Thanks to all. The console instructions worked. Round things are round and desktop effects worked for the first time. 

When I went to run Virtualbox, however, it's broken after this morning's update, so I still don't know if the system will report the correct screen resolution to the guest system. 

Sigh ...

---

