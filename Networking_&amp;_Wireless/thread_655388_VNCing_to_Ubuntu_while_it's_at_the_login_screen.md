---
title: "VNCing to Ubuntu while it's at the login screen"
date: 2008-01-01
forum: Networking &amp; Wireless
---

### Post by m i k e on 2008-01-01
I am going to be using wake-on-lan to power up my computer remotely.  Then I would like to be able to connect via VNC.  However, Ubuntu doesn't start the remote desktop service (VNC) until after you log in so my questions are:  How can I log in through VNC while Ubuntu is at the login screen?  Is there a way to set it so that Ubuntu starts the remote desktop service before one logs in?  Thanks.

---

### Post by Chayak on 2008-01-01
I don't know about VNC but FreeNX should work much better, but be warned it sometimes takes a bit of tweaking to get it to work correctly.  Then again so does VNC

Interesting question though.  It could be possible to add the VNC server to your system runlevels right after it starts X and GDM it would start the VNC server.   You might also want to look around on the net for doing VNC over SSH if you plan to do this over the internet.

---

