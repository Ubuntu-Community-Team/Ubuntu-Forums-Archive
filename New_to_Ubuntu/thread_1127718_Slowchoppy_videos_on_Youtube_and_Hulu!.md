---
title: "Slow/choppy videos on Youtube and Hulu!"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by sylvainrb on 2009-04-16
I recently upgraded my laptop with 2 GB of memory but there are still videos on Youtube (HQ) and Hulu that won't play well, whereas they play perfectly when I use Windows XP. Can I ameliorate this somehow or is it a problem related to Ubuntu and the websites? Or has anyone experienced/noticed the same thing with their machine?

Thanks!

---

### Post by riza hylviu on 2009-04-16
have you installed adobe flash plug in?

---

### Post by sylvainrb on 2009-04-16
Yes... I mean Youtube plays fine unless I try to watch the videos in high quality. Are there different flash plug-ins?

---

### Post by riza hylviu on 2009-04-16
i tried watching some hd videos on youtube and i can watch them fine with the  flash plug in , it means that maybe you have a graphics card issue
have configured your video card well?

---

### Post by sylvainrb on 2009-04-16
Yeah that I probably didn't do haha! How should I go about it or do you have a link with the necessary information?

Also how can I check the type/specs for my video card?

Thank you.

---

### Post by riza hylviu on 2009-04-16
gedit /etc/X11/xorg.conf 
try typing thin in the terminal and read what is written in the device section

---

### Post by sylvainrb on 2009-04-16
Here's what the device section reads:
```
Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection
```

---

### Post by Turtleman on 2009-05-10
Hey sylvainrb, have you found a solution for this? I'm having the same problem! I wanna switch out of windows completely but it's small things like that that stop me!

---

### Post by sylvainrb on 2009-05-10
> **Turtleman said:**
> Hey sylvainrb, have you found a solution for this? I'm having the same problem! I wanna switch out of windows completely but it's small things like that that stop me!

Yeah well sort of. The problem is due to Compiz being enabled so I use Fusion Icon to switch between Compiz and Metacity within a session, and videos work fine in Metacity. To get Fusion Icon:

```
sudo apt-get install fusion-icon
```

---

### Post by jimmytop on 2009-05-10
go to
System - Administration - Hardware Drivers.

Activate the recommended driver.
Reboot.

This worked wonders for my nvidia agp card, all videos and graphics are fantastic now that I'm not using the default driver ubuntu installed originally.  Using 9.04.

---

### Post by sylvainrb on 2009-05-10
Oh and also I did make the complete change from Windows to Ubuntu and it's working very well. There are issues that I've run into but with some research I was able to solve. If you're willing to struggle at times and/or have another machine with Windows on it... I say you can make the change too! ;p

PS: If you use the machine for work/school/important things, I'd keep Windows just in case...

---

