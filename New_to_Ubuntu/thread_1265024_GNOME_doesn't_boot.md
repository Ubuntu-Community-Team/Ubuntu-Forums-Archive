---
title: "GNOME doesn't boot"
date: 2009-09-12
forum: New to Ubuntu
---

### Post by TRouBLe32 on 2009-09-12
I'm using 9.04 for a week now. Everything's running ok. The last couple of days i didn't turn off the PC.
So I did a restart half an hour ago, and when I came back all I could see was the desktop without the menus or anything else GNOME-related. 

Transmission was open (it's set to autostart), i could interact with the desktop (make a folder, change wallpaper) but anything else was missing. 
Tried restarting a couple times, tried booting with the previous kernel but nothing changed. I was thinking about running recovery mode but I don't wanna meke thing worse.

---

### Post by MelDJ on 2009-09-12
maybe try logging into into another session?

---

### Post by TRouBLe32 on 2009-09-12
How can I do that???

---

### Post by MelDJ on 2009-09-12
or make a launcher for terminal in the desktop with the command gnome-terminal.
then in terminal run gnome-panel

---

### Post by Vaphell on 2009-09-12
maybe solution from this thread would help
[http://ubuntuforums.org/showthread.php?t=1263990](http://ubuntuforums.org/showthread.php?t=1263990)

---

### Post by MelDJ on 2009-09-12
> **TRouBLe32 said:**
> How can I do that???

at the login screen, click on session and choose. but i think its easier to do the other way i have shown

---

### Post by TRouBLe32 on 2009-09-12
> **MelDJ said:**
> at the login screen, click on session and choose. but i think its easier to do the other way i have shown

Yeah, i did the terminal thing and it worked.Thank you.
I'm going to do a restart and see if it happens again..

EDIT: turns out it didn't work. "gnome-panel" doesn't finish...This is the output:

> ** (gnome-panel:4999): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:4999): DEBUG: Adding applet 0.
** (gnome-panel:4999): DEBUG: Adding applet 1.
** (gnome-panel:4999): DEBUG: Adding applet 2.
** (gnome-panel:4999): DEBUG: Adding applet 3.
** (gnome-panel:4999): DEBUG: Adding applet 4.
** (gnome-panel:4999): DEBUG: Adding applet 5.
** (gnome-panel:4999): DEBUG: Adding applet 6.
** (gnome-panel:4999): DEBUG: Adding applet 7.
** (gnome-panel:4999): DEBUG: Adding applet 8.
** (gnome-panel:4999): DEBUG: Adding applet 9.
** (gnome-panel:4999): DEBUG: Adding applet 10.
** (gnome-panel:4999): DEBUG: Adding applet 11.

(gnome-panel:4999): Gdk-WARNING **: /build/buildd/gtk+2.0-2.16.1/gdk/x11/gdkdrawable-x11.c:878 drawable is not a pixmap or window

(gnome-panel:4999): libglade-WARNING **: Unexpected element <requires-version> inside <glade-interface>.
** (gnome-panel:4999): DEBUG: Adding applet 12.

If I close the terminal the panel dissapears again.
I'm guessing there's a problem with an applet, but i have no idea which one..

---

### Post by MelDJ on 2009-09-12
> **TRouBLe32 said:**
> Yeah, i did the terminal thing and it worked.Thank you.
I'm going to do a restart and see if it happens again..

EDIT: turns out it didn't work. "gnome-panel" doesn't finish...This is the output:



If I close the terminal the panel dissapears again.
I'm guessing there's a problem with an applet, but i have no idea which one..

does the panel come when terminal is open only? if thats the case, it means you are running the panel from terminal. keep terminal and right click the panel and add a new panel. that might make a panel which is independent from terminal i think. try it.

---

### Post by nandemonai on 2009-09-12
Your suspicion that a panel applet is causing the crash is probably right.

If you reset gnome that should get you logging in ok.

From terminal as the user you're having trouble with:

```
mv ~/.gnome2 ~/.gnome2.backup
```

Log out and back in again.

---

### Post by TRouBLe32 on 2009-09-12
@MelDJ Nope.Didn't work either... I don't think the problem is running the panel from terminal, i think that when the terminal runs for some reason it crashes.

@nandemonai didn't work.

I also tried changing the session from last one to gnome but it didn't change anything...(probably because last session=gnome)

**EDIT: OK, so I created a new user... Logged in and everything was fine. It even reactivated the nvidia driver in my user.**

---

### Post by nandemonai on 2009-09-12
> **TRouBLe32 said:**
> @MelDJ Nope.Didn't work either... I don't think the problem is running the panel from terminal, i think that when the terminal runs for some reason it crashes.

@nandemonai didn't work.

I also tried changing the session from last one to gnome but it didn't change anything...(probably because last session=gnome)

Weird..

Something odd going on then.

You can run gnome-panel in the background from terminal by putting a & at the end of the command. That should allow you to close the terminal.

```
gnome-panel &
```

If it refuses to come back on a new login you could always add the command to startup apps.

Another thing worth a shot may be this:

```
gnome-panel --replace &
```

---

### Post by TRouBLe32 on 2009-09-13
Tried the & at the end of the command. It still errors, but the panel is working.I don't like this solution though, feels very temporary...
Anyway, thanks for the help:):)

---

### Post by MichaLuis on 2009-09-13
I had a similar problem, after doing some customization to my panel and creating one to put on the right side of the screen. After booting, the panel didnt appear. Had to use gnome-panel on the console but the panel kept open when I close the console. After a reboot the panel didnt open again so I added the gnome-panel command to the boot list. What is really weird is that I made a new panel on the right side of the screen but it always appears on the left. When I try to change that, it automatically switches to left in the options window. If I delete that panel and create a new one on the right, it goes back to left as well. I have no add-ons installed, all components in the panel are from the instalation cd.

Any idea? It doesnt bother me that the panel is on the left but there must be some explanation for this :confused:

Greets :D

Michael

---

