---
title: "Is there a Reverse-VNC equivalent for the terminal window?"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by diablo75 on 2008-12-20
I often use Reverse-VNC connections to assist clients with their PCs.  This basicly consists of my PC listening on port 5500 for their PC to make a connection request to my PC, and after that I have remote view and control of their desktop.

But on occasion they can't get to a GUI.  They can of course get to a terminal.  Is there a way they can throw their terminal to me so I can fix their PC via their terminal by remote instead of slowly spelling every letter of every command out for them over the phone and waiting for them to read back whatever output they see, etc.?

Edit:  Turns out starting a "Failsafe Terminal" session and running x11vnc (as usual) actually works... but I have another problem.  x11vnc is running in the only failsafe terminal that is available.  I need to have a second one open...

---

### Post by krunge on 2008-12-21
> **diablo75 said:**
> I often use Reverse-VNC connections to assist clients with their PCs.  This basicly consists of my PC listening on port 5500 for their PC to make a connection request to my PC, and after that I have remote view and control of their desktop.

But on occasion they can't get to a GUI.  They can of course get to a terminal.  Is there a way they can throw their terminal to me so I can fix their PC via their terminal by remote instead of slowly spelling every letter of every command out for them over the phone and waiting for them to read back whatever output they see, etc.?

If their kernel has the framebuffer device enabled, e.g. /dev/fb0, (unfortunately most installs don't seem to enable it), then x11vnc can export the linux console:
```

sudo x11vnc -rawfb console -connect your.ip -bg

```
It works fairly well, but not as well as exporting an X display.

There is also the LinuxVNC program that exports the linux consoles even if there is no framebuffer device.  I don't think it can do reverse connections though.
> 

Edit:  Turns out starting a "Failsafe Terminal" session and running x11vnc (as usual) actually works... but I have another problem.  x11vnc is running in the only failsafe terminal that is available.  I need to have a second one open...

Just have them add '&' to the end of the command or use the x11vnc '-bg' option to run it in the background.  They could also run 'xterm -geometry +0+0 &' in the failsafe terminal before starting x11vnc.

---

