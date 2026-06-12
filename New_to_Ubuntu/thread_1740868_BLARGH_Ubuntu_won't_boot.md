---
title: "BLARGH Ubuntu won't boot"
date: 2011-04-27
forum: New to Ubuntu
---

### Post by Visvalor on 2011-04-27
Hey, I'm trying to install libmobiledevice and in doing so I removed libimobiledevice (the one with I) and after I did this the desktop crashed into a black login screen and now I'm stuck there. 

I tried typing startx but it just boots into a black screen with a mouse cursor.

I've gotta say, installing the latest libmobiledevice from ppa is turning out to be an enormous pita.

---

### Post by dniMretsaM on 2011-04-27
I don't see how removing libimobiledevice1 could cause that (I'm not sure why you would want to remove it anyway since it's the latest version). You must have accidentally removed something major along with it.

---

### Post by Visvalor on 2011-04-27
Yes it had some stuff tied to it that had to be removed. I would'nt have thought Ubuntu would have pulled out something that couldn't be removed.

Any way I can get it back in?

Also now the thing won't boot at all, it's just got a black cursor blinking. How the hell do I get into some form of safemode?

---

### Post by Rubi1200 on 2011-04-27
You don't say what version you are running, but if you removed that package it likely took out the following essential files:

> [COLOR=Red]gnome-power-manager[/COLOR]
[COLOR=Red] gvfs-backends[/COLOR]
[COLOR=Red] indicator-session[/COLOR]
libgpod4
rhythmbox-plugins

---

### Post by Visvalor on 2011-04-27
Why on earth would it take anything out? Ok so I'm running 10.10, how do I get my essential files back? It now boots to "Ubuntu is running in low-graphics mode"

---

### Post by dniMretsaM on 2011-04-27
Do you have access to a command line? If so, just re-install the packages that were deleted.

> **Visvalor said:**
> Why on earth would it take anything out?

Because they are not necessary for the system to actually run.

---

### Post by Visvalor on 2011-04-27
Did that, rebooted, then it does teh same low graphics nonsense. I get back to the login and startx. It goes right back to the black screen and mouse.

Any other suggestions :\? I really don't want to have to reinstall ubuntu again.

---

### Post by dniMretsaM on 2011-04-27
You could try reinstalling a desktop environment (GNOME, XFCE, KDE, LXDE, Unity, etc.). Look up the necessary command for which ever you want to install (I believe it would just be sudo apt-get install gnome/xfce/kde/lxde/unity). However, I don't know if this will actually fix your problem so you may want to wait for some more advice.

---

### Post by Visvalor on 2011-04-27
Ok, is there any way I can just repair from the CD WITHOUT losing all my files and installs again?

---

### Post by dniMretsaM on 2011-04-27
You mean the Live CD that you used to install Ubuntu with?

---

### Post by dniMretsaM on 2011-04-27
Take a look at [this](http://www.dharwadkar.com/weblog/ubuntu06). It's for an older version, but it may work.

I know that's not from the LiveCD, but it seems easier. And if it doesn't work, I'll look for something else.

---

### Post by Visvalor on 2011-04-27
Yes that one

---

### Post by Visvalor on 2011-04-27
Ok so upon reboot what buttoms do I press to get into a recovery mode situation?

---

### Post by Visvalor on 2011-04-27
Also in my X11 folder in my main HD I have some folders, but no xorg.conf. I have xorg.conf.failsafe, xorg.conf-backup-#'s

---

### Post by dniMretsaM on 2011-04-27
> **Visvalor said:**
> Ok so upon reboot what buttoms do I press to get into a recovery mode situation?

Try holding ESC. I read that that will get you to a menu where you can select it.

> **Visvalor said:**
> Also in my X11 folder in my main HD I have some folders, but no xorg.conf. I have xorg.conf.failsafe, xorg.conf-backup-#'s

Are hidden files enabled (Ctrl+H)? If they aren't there, I'm not sure, I'll have to do some more looking.

---

### Post by Visvalor on 2011-04-27
Yea I hit ctrl+h to look (while on the live cd browsing) and still nothing.

Let me reboot and try the esc key.

---

### Post by dniMretsaM on 2011-04-27
Just to clarify, which version of Ubuntu are you running?

---

### Post by dniMretsaM on 2011-04-27
In 10.04 and 10.10 there is no xorg.conf file. [This thread](http://ubuntuforums.org/showthread.php?t=1662305) seems to be a similar problem to yours, give it a read. Although no fix is mentioned, it may give you some ideas. I'll keep looking.

Also, if ESC doesn't work, try Shift.

---

