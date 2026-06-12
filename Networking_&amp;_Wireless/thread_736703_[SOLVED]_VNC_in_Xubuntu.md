---
title: "[SOLVED] VNC in Xubuntu"
date: 2008-03-26
forum: Networking &amp; Wireless
---

### Post by CaesarLike on 2008-03-26
I am trying to remotely access a pc with Xubuntu installed on it.  Xubuntu has been used instead of Ubuntu on this machine as it is a bit old now, and Ubuntu stresses it a bit too much.  I can run a VNC client from Xubuntu, but cannot access the machine via vnc from another pc running Ubuntu.  The error I recieve is that the connection has been refused. My router is pointing to the Xubuntu machine for vnc connections, yet even using the internal lan ip's I still cannot connect.  I suspect that I do not have the right VNC server installed, as I can access the Xubuntu pc with SSH.
I have installed vnc4server, but this has made no difference.  I do notice that Xubuntu does not have the Remote Access screen, to enable remote connections, that Ubuntu has.  Does anyone know what I need to download, either to get the Remote Access screen or to enable remote access using VNC?

---

### Post by chewearn on 2008-03-27
[http://ubuntuforums.org/showthread.php?t=726789](http://ubuntuforums.org/showthread.php?t=726789)

---

### Post by CaesarLike on 2008-03-27
Thanks AstalaVista, your previous post was exactly what I needed.
I already had Vino installed, but as it wasn't starting at boot up, I had no remote connection.  Its also good to know how to start the interface window too. :)

---

