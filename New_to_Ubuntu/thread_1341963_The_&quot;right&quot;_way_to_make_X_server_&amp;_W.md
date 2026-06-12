---
title: "The &quot;right&quot; way to make X server &amp; WM start at boot?"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by 0xABC123 on 2009-11-30
I installed Ubuntu 9.10 Server Edition in virtual machine, so I can learn about Linux without getting my PC unbootable.

The first thing I typed into the terminal (after username and password) was:
```

sudo apt-get install xorg fluxbox

```How to make X server and fluxbox start by default when booting up (and auto-login)?

---

### Post by ajgreeny on 2009-11-30
Add gdm or xdm.  I have never used xdm so can not comment on that, but the newer version of gdm with karmic, is not configurable at the moment, so xdm may be the better choice.

---

### Post by 0xABC123 on 2009-11-30
[s]
I added XDM. It starts X11 + Fluxbox automatically.

Then it greets me with a grotesque 8-bit login screen which makes my eyes hurt. How to disable login screen and automatically log in? 

(didn't find anything with google and ubuntu doesn't have /etc/inittab nor /etc/events.d)
[/s]

EDIT: XDM doesn't have an option for autologin. Got rid of it. Now what?

---

### Post by 0xABC123 on 2009-11-30
I want automatic login without a display manager.

This is my /etc/rc.local:
```

#!/bin/sh -e
su -l alex -c startx
exit 0

```Permissions:
```

alex@ubuntu:/etc$ ls -l rc.local
-rwxr-xr-x 1 root root 41 2009-11-30 22:25 rc.local

```The script doesn't get executed at boot. What might be problem?

---

### Post by ajgreeny on 2009-11-30
I'm not sure, but I don't think you need the "su" in the script.

---

### Post by 0xABC123 on 2009-12-01
> **ajgreeny said:**
> I'm not sure, but I don't think you need the "su" in the script.

But "su -l username" is the command to auto-login (see manual page of su). Without su it would be just the arguments and no program to execute.

---

### Post by wojox on 2009-12-01
Server editions don't come with X. That's what they make Desktop editions for. If you really want to learn Linux stick with the shell.

---

### Post by 0xABC123 on 2009-12-01
I want a system, which can run a graphical web browser, and boot up in less than 10 seconds (same for shutdown). The system only needs to run a web browser, period. Desktop Editions are bloated with useless junk and take ages to boot up.

---

### Post by Drone86 on 2009-12-01
> **wojox said:**
> Server editions don't come with X. That's what they make Desktop editions for. If you really want to learn Linux stick with the shell.

I'm looking for something similar to what 0xABC123 is - bare bones, rock solid. 

I'm putting in some computers at remote locations and I want them to just start up and go straight to a GUI desktop - passive displays, no input devices.

I've got LXDE working but have no idea how to make the server auto-login. Sure, I could use the desktop edition and strip it back down, but that's time consuming and I don't know what it'll do to the reliability of the system.

I'm also trying to get wvdial to work without leaving it logged in as root and not requiring any user input, so it can dial out on boot by itself.

I just joined here after a lot of searching and experimenting, so I'll do a little more searching and post anything useful I find here...don't let that stop you from jumping in with info though :-)

---

### Post by wojox on 2009-12-01
> **0xABC123 said:**
> I want a system, which can run a graphical web browser, and boot up in less than 10 seconds (same for shutdown). The system only needs to run a web browser, period. Desktop Editions are bloated with useless junk and take ages to boot up.

Install

```

sudo apt-get update && sudo apt-get gnome-core gdm x11-xserver-utils gnome-themes-ubuntu jockey-gtk gnome-utils

```

Thats what I use. And build it from there. Boots in ten seconds, shuts down in 2. Open Synaptic and install what you want. From the minimal disk.

---

### Post by tweaksource on 2010-01-22
I build ubuntu cli system from a minimal cd and add fluxbox. I use slim to auto-login.

This uses generic kernel rather than server kernel.

[http://www.linux4all.net/slim_auto_login](http://www.linux4all.net/slim_auto_login)

---

