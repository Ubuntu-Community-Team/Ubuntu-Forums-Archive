---
title: "can't start vncserver"
date: 2007-02-22
forum: Networking &amp; Wireless
---

### Post by Pollywoggy on 2007-02-22
When I start a vncserver, I get this:

Fri Feb 23 02:23:40 2007
 vncext:      VNC extension running!
 vncext:      Listening for VNC connections on port 5901
 vncext:      created VNC server for screen 0
error opening security policy file /etc/X11/xserver/SecurityPolicy
Could not init font path element /usr/share/X11/fonts/misc/, removing from list!
Could not init font path element /usr/share/X11/fonts/TTF/, removing from list!
Could not init font path element /usr/share/X11/fonts/OTF, removing from list!
Could not init font path element /usr/share/X11/fonts/Type1/, removing from list!
Could not init font path element /usr/share/X11/fonts/CID/, removing from list!
Could not init font path element /usr/share/X11/fonts/100dpi/, removing from list!
Could not init font path element /usr/share/X11/fonts/75dpi/, removing from list!

Fatal server error:
could not open default font 'fixed'

I installed the vnc4server and xvnc4viewer packages and also twm.

Any ideas on what is wrong?

---

### Post by grumpymole on 2007-03-26
Pollywoggy,

There was a problem with the fontpath.  Try using /usr/share/fonts/X11/misc instead.  If you are starting with Xvnc, use the -fp option.  See [here]("http://grumpymole.blogspot.com/2006/12/xubuntu-remote-desktop-with-vnc4server.html") for more detail.

Regards

---

