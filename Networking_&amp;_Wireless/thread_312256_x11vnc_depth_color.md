---
title: "x11vnc depth color"
date: 2006-12-04
forum: Networking &amp; Wireless
---

### Post by Frunktz on 2006-12-04
Hi! Is there a way to reduce the depth color of x11vnc? Default have 32 or 24 bpp but from my office is very very slow.
Anyway to set for example 64 colors?
Thanks

---

### Post by krunge on 2006-12-12
You can usually set the depth/bpp in your VNC Viewer.

Unix RealVNC viewer allows you to do this dynamically (press F8 )
not sure about Unix TightVNC viewer  (-bgr233 on cmd line?).
I think all windows viewers allow setting dynamically.

Once the viewer communicates this pixel format (depth, bpp, etc)
to x11vnc, x11vnc will use that format for transmission to your
viewer, thereby getting a speedup if you choose low depth.

For reasons I don't understand I don't see any viewers that have
a selectable 16bpp mode. This would be a nice way to get a 2X
speedup with almost no degradation of color.

---

### Post by Frunktz on 2006-12-13
Wth X11vnc If I set the color from the client, the X11vnc close the connection...

---

### Post by krunge on 2006-12-14
Which VNC Viewer, version, and OS?  I don't see that when I change color
depth.  Posting the x11vnc message output might be useful too.

---

### Post by Frunktz on 2006-12-15
Using KRdc and setting low color.
Today I recompiled a version of x11vnc and seems to work using xvnc4viever, but with KRdc x11vnc closes connection...

---

### Post by krunge on 2006-12-15
Perhaps this is the krdc bug discussed here:

[INDENT][http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=399408]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=399408")[/INDENT]

I have uploaded a fix for this just this morning:

[INDENT][http://www.karlrunge.com/x11vnc/x11vnc-0.8.4.tar.gz]("http://www.karlrunge.com/x11vnc/x11vnc-0.8.4.tar.gz")[/INDENT]

if you could test it out, for both problems, I would appreciate it.

Karl

---

### Post by Frunktz on 2006-12-15
Ok, I try! Thanks

---

### Post by jetpeach on 2006-12-23
sweet Karl, glad you uploaded a fix for this, it has been bothering me quite a lot.  i just saw your posts on the bugs when searching google and then checked here to let others know about the tightvnc problem, but see you have done so already :)
i will try to test the fix.

EDIT: woohoo! it's fixed.  I created a DEB file using checkinstall -D for those who don't want to compile from source.  I'm a total newb at compiling from source, so I just kept adding developer libraries until ./configure didn't give any more warnings about things that wouldn't work if I compiled without installing libjpeg-dev etc first.  so anyway, the only problem with the deb though is I didn't know how to add dependencies to it using checkinstall (option 10, but what is the syntax? searched web couldn't find a guide to checkinstall so dumb...), so currently it has NO dependencies, meaning you should install x11vnc from the repositories first (that will also install the dependencies) then do "sudo dpkg -i x11vnc_0.8.4-1_i386.deb" next.  a link to the deb file is below to download. 
[http://helpthehappy.com/x11vnc_0.8.4-1_i386.deb]("http://helpthehappy.com/x11vnc_0.8.4-1_i386.deb")

---

