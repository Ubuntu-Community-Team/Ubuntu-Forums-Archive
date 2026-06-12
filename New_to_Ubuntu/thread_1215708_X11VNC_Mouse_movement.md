---
title: "X11VNC Mouse movement"
date: 2009-07-17
forum: New to Ubuntu
---

### Post by High Camp on 2009-07-17
Hi All

I've got X11VNC up and running without problems. I'm having an issue though, while logged in the mouse keeps moving to a certain spot on the screen and clicking. It's a fairly big issue becuase I'm editing text files so the curor keeps moving.

At first I thought this was related to the physical mouse on the laptop since the lid was closed but I'm since opened the lid and am still having the same issues. Has anyone seen this before? Do you have any solutions?

Thanks so much,

---

### Post by krunge on 2009-07-17
Add the "-debug_pointer" option to the x11vnc cmd line (include more than one for more verbose output.)

This way you will see every mouse event (motion and clicks) that x11vnc injects into the X server.  When the strange mouse events happen see if it is x11vnc injecting them or not (my guess is not, but it should be ruled out.)

Also try logging into a failsafe session (xterm failsafe, not gnome failsafe)  Start twm if you want a window manager.  See if the problem still occurs. This will try to see if it is the window-manager/desktop causing the problem.

Please also indicate the version of the Xorg server running (check /var/log/Xorg.log, xdpyinfo, or Xorg -version)

---

### Post by High Camp on 2009-07-19
Hey Karl

I did as you suggested without any luck, although I did notice that the mouse buttons often got locked in the down position when debugging was on. Mostly while dragging windows, which was a bit frustrating. Since I couldn't duplicate the behaviour I went back to my original thought that it was the laptop screen being closed. Sure enough! I opened the screen, wide enough that its not touching the mouse but closed enough that the screen is turned off and that solved all my problems. 

When starting X11vnc from the terminal I noticed the website [www.karlfrunge.com](www.karlfrunge.com), I can only assume you're the developer. Thanks so much for providing personalized support on forums outside your website!

---

