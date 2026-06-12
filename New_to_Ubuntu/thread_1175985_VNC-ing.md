---
title: "VNC-ing"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by jaceh14 on 2009-06-01
hey all, i'm trying to figure out how to VNC from my laptop (Ubuntu 9.04) to my HTPC (Windows Vista). the HTPC is hooked up to the tv and while i put dvds on the hard drive, i would like to watch tv too. i figure i could just vnc into it. i've tried to google it and have tried to search on here, but no luck for me so far. do i have to download a program to do this (i'm thinking realVNC) or can i do it with the pre-installed program on Ubuntu? and how would i go about doing these?

jace

---

### Post by bswilson on 2009-06-01
Jace,

Connecting to a remote system with VNC requires both a client application (the viewer), and a server application (such as RealVNC) on the server to which you're connecting.

Ubuntu already has the client you need, under Applications --> Internet --> Remote Desktop Viewer.  The application is actually called [Vinagre]("http://projects.gnome.org/vinagre/").

It sounds like what you really need is to ensure that your Vista system has RealVNC or a similar program installed and running, and that the Vista system does not have a firewall program blocking tcp/5900.  I might also recommend some of the more secure VNC server programs, such as [TightVNC]("http://www.tightvnc.com/") or [UltraVNC]("http://www.uvnc.com/").

---

### Post by glennric on 2009-06-01
You could also try using rdesktop.  With that you can connect to the windows remote desktop.  You will have to enable remote desktop in windows.  A convenient way to use rdesktop is from tsclient (which shows up in the menu under Applications->Internet->Terminal Server Client once the tsclient package is installed)

---

### Post by Volt9000 on 2009-06-01
> **bswilson said:**
> Jace,

Connecting to a remote system with VNC requires both a client application (the viewer), and a server application (such as RealVNC) on the server to which you're connecting.

Ubuntu already has the client you need, under Applications --> Internet --> Remote Desktop Viewer.  The application is actually called [Vinagre]("http://projects.gnome.org/vinagre/").

It sounds like what you really need is to ensure that your Vista system has RealVNC or a similar program installed and running, and that the Vista system does not have a firewall program blocking tcp/5900.  I might also recommend some of the more secure VNC server programs, such as [TightVNC]("http://www.tightvnc.com/") or [UltraVNC]("http://www.uvnc.com/").

+1

Just today I used Vinagre to log into a friend's computer, running UltraVNC under Windows XP. It worked very well, and seemed quite fast, although I don't know if viewing video through a VNC connection is the best idea. VNC is great for remote control but not really suited for watching video.

---

### Post by jaceh14 on 2009-06-02
thanks all for the info. i'm not going to be watching video through vnc, i want vnc while i set up my htpc because i don't have another monitor to use besides my television, and we only have one tv in the house. thanks again for all the input. i will try one of the other more secure vnc server programs and we'll see how that goes.

jace

Update: got it working with ultraVNC. it works great and thank you all again for the tips

---

### Post by RGPerson on 2009-07-12
I haven't got it working through UltraVNC.  I could use some help here.  I can't see what I click or type on my XP screen.  I can only see it on my TV, which is the monitor for the linux box I'm trying to connect to.

Update: I got rid of compiz (copied something like this from a site that help: sudo aptitude remove compiz-core..... and more I wasn't sure if I even had.

But it did seem to get rid of stuff. I saw that compiz was still in my processes so I rebooted and it's gone!  And now I can see on my laptop AND Tv what I click from my laptop!

Gabrielle

---

### Post by nhasian on 2009-07-12
the issue is with the vnc server on vista.  i know that vista broke a lot of the vnc servers and i dont know if they got fixed yet.  last i checked only ultraVNC claimed to be working under vista but i still never got it working for me.

---

