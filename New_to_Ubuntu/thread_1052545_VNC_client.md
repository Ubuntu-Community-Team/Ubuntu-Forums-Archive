---
title: "VNC client"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by fugaki on 2009-01-27
Does anyone know of a good vnc client to use in windows to connect to the built in remote desktop server (with encryption)?

---

### Post by Cypher on 2009-01-28
Not sure if any VNC client supports encryption and if it does if it's compatible with the VNC server in Ubuntu. The best way ot encrypt your VNC connection so that you can use one of many different clients is to [connect over SSH]("http://ubuntu-tutorials.com/2007/06/12/vnc-over-ssh-securing-the-remote-desktop/").

---

### Post by HermanAB on 2009-01-28
From Windows to Linux, it is actually best to use SSH through Xming and PuTTY.  You could use TightVNC or UltraVNC, but on Linux VNC is almost always the wrong answer, since SSH can do everything VNC does and more.

From Linux to Windows, it is best to use Windows RDP with rdesktop.

Cheers,

Herman

---

### Post by Peter09 on 2009-01-28
Yes,
Freenx is a good option, it has a client for windows, thats if you want to see a full desktop.

---

