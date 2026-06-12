---
title: "Using WOL and VNC together"
date: 2007-12-12
forum: Networking &amp; Wireless
---

### Post by manthony121 on 2007-12-12
My Ubuntu 7.04 computer(fermi) lives downstairs; my wife has an XP
computer(ella) in the upstairs bedroom.  I would like to be able to turn
on fermi from ella, and start a VNC session, using my usual desktop.

The problem I have encountered is that Gnome's built-in VNC server, vino,
does not work until after you have logged in from the graphical login
window.  So, I can wake up fermi, and get an ssh login, but I can't start
a VNC session.

So, is there a way to login to your gnome desktop from a remote (Windows)
machine?  If I use a different VNC server, such as vnc4server, can I avoid
the need for a GUI login?

---

### Post by Original Brownster on 2007-12-13
Hi,
Although I haven't tested this, assuming you can get your pc to wake up on lan ok (never had to do this) there is no reason why you cannot install vnc server to run as a daemon on this pc. by default it will use screen:1 not screen:0 the graphical desktop used for the user at the screen. 

hth

---

### Post by m i k e on 2008-01-01
bump.

Is there any other solution to this/how would you install Ubuntu's Remote Desktop (VNC) to run as a daemon?

Thanks.

---

