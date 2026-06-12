---
title: "vlc full screen in dual monitor setup"
date: 2010-06-04
forum: New to Ubuntu
---

### Post by Mariane on 2010-06-04
Hi, 

vlc works fine on my laptop. 

I have another monitor plugged in with a larger screen. 

Double-clicking on the vlc display, or telling it to go to full screen, always sends it full screen on my laptop screen. 

Do you know how I could get vlc to play full screen on the other monitor without setting this other monitor as the primary display for everything? 

I am using TwinView so both monitors form some kind of single display and I can drag stuff from one display to the other with the mouse. 

Mariane

---

### Post by madverb on 2010-06-04
So if you drag VLC to the second display and double click it, it moves to display 1?
In my setup I just drag VLC across and double click and it opens up in the display I double click it on.

---

### Post by Mariane on 2010-06-07
Mine jumps back to the laptop monitor. 

Mariane

---

### Post by Mariane on 2010-06-07
Editing /.vlc/vlcrc does not work.
When I run vlc it overwrites the settings there so even if I tell it the default fullscreen monitor is monitor 1 it sets it back to being monitor 0 (the cheek!). 

Stopping it from modifying this configuration file (chown root vlcrc) stops vlc from changing the file but does not stop vlc from ignoring what is written in the file. 

Mariane

---

