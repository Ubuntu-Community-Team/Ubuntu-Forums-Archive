---
title: "jaunty screen flickering"
date: 2009-07-26
forum: New to Ubuntu
---

### Post by libihero on 2009-07-26
the only problem i have with jaunty is the screen keeps flickering.  is this a common bug in it?

---

### Post by cwsnyder on 2009-07-26
It sounds like you have set the vertical refresh rate too low on your video settings.  That can happen on Windows as well as Ubuntu and other versions of Linux.

What are your video settings (HorizontalxVertical pixels, number of colors, @ Vertical refresh rate), and which video card/monitor combination?  We might be able to make suggestions.

---

### Post by InkedScales on 2009-07-26
I have a similar problem Ive only just installed abuntu and it was fine then I installed my hardware update for it and its gone mental its flickereing all the time and when i open the display options box it only loads halfway and the flickers mroe and wont load at all so i cant really tell u the refresh rate or anything :(

---

### Post by cwsnyder on 2009-07-27
@InkedScales: Did you experience the problem first with the Live CD before install, or just after installing a proprietary display driver?

If just after the proprietary driver, you may want to un-install/disable the proprietary driver or switch to an earlier version.

If the Live CD (try without installing) works and your install does not, then you need to get to a terminal (Gnome Terminal, Konsole, etc.) from inside your install, and re-run the X-server setup program ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` You may also have to remove the proprietary driver using Synaptic.

---

### Post by InkedScales on 2009-07-27
> **cwsnyder said:**
> @InkedScales: Did you experience the problem first with the Live CD before install, or just after installing a proprietary display driver?

If just after the proprietary driver, you may want to un-install/disable the proprietary driver or switch to an earlier version.

If the Live CD (try without installing) works and your install does not, then you need to get to a terminal (Gnome Terminal, Konsole, etc.) from inside your install, and re-run the X-server setup program ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` You may also have to remove the proprietary driver using Synaptic.

thanks for the advise Ive actually sorted the problem now by reverting to ubuntu 8.04 instead of 9.04 it seems to all be working fine now thanks again

---

### Post by libihero on 2009-07-28
how do u find out what the video settings are??

---

### Post by panhandle on 2009-07-28
This should help you:

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

You can also go System-->Preferences-->Screen Resolution

---

