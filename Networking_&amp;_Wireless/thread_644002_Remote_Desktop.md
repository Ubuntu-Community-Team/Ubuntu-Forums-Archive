---
title: "Remote Desktop"
date: 2007-12-18
forum: Networking &amp; Wireless
---

### Post by weaver4 on 2007-12-18
I want to set up Remote Desktop on my Ubuntu Machine in my home and get to it's desktop by using Windows.  Is it as easy as turning on Remote Desktop in Ubuntu and using Remote Desktop Connection on my windows xp machine or do I need to install something like UltraVNC?

---

### Post by weaver4 on 2007-12-19
bounce

---

### Post by yoda2031 on 2007-12-19
RDC is an entirely different protocol to VNC.  There are currently no servers for RDC under linux (or if there are, they are extremely experimental).

There are two remote management protocols in linux, essentially.  First is the one you already seem familiar with - VNC.  I'd stick with this if you already know how to get it working.  XDMCP is the better but more difficult protocol for a number of reasons.

To enable VNC, go to System>Preferences>Remote Desktop and enable Remote Desktop.

To enable XDMCP, go to System>Preferences>Login Window and click the Remote tab, then change to anything other than "Disabled" (plain with face browser works better than same as local, especially in gutsy).

To connect using VNC, download UltraVNC or Chicken of the VNC (Apple OSX) or VNCViewer 4.0, or ANY OTHER VNC CLIENT then point it at your server's FQD or IP address.

VNC is choppy in poor network conditions and there must be a user logged in on the server for it to work.

To connect using XDMCP, either tunnel X over ssh (ssh -X uname@host, in PuTTY enable X11 Tunneling in X options - not sure if this works, and you may need an X server in Windows to work properly) or query the server directly using "X -query hostname".

Remote desktop in a nutshell, hope it helped :)

Ciao

---

### Post by tech9 on 2007-12-19
I use RealVNC and it works flawlessly

---

### Post by mellowd on 2007-12-19
VNC is great and easy to use

---

