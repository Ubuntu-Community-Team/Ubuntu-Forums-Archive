---
title: "Control Windows Through Ubuntu?"
date: 2011-04-11
forum: New to Ubuntu
---

### Post by doppel.ganger on 2011-04-11
I have a friend that wants to be able to control his Windows machine through his 10.10 machine with screen sharing. Is this possible and if so, how do you do it?

---

### Post by 1clue on 2011-04-11
> **doppel.ganger said:**
> I have a friend that wants to be able to control his Windows machine through his 10.10 machine with screen sharing. Is this possible and if so, how do you do it?

You mean through a script or manually?  Is there a problem with remote desktop?  There's a really good remote desktop client for Linux.

---

### Post by doppel.ganger on 2011-04-11
I mean like through the remote desktop viewer.

---

### Post by seawolf167 on 2011-04-11
TightVNC, UltraVNC, RDP in wine

---

### Post by 1clue on 2011-04-11
Or remote desktop viewer.  Exactly the same as on Windows only IMO better.

It's right in Ubuntu.  I think it comes on the default desktop install.

---

### Post by BertN45 on 2011-04-12
If you want to control the windows machine use the "terminal server client: from the Internet menu, This terminal server work together with the windows remote desktop function, which should be activated on the windows machine.
Note that Microsoft blocks the use of the windows machine locally, only one user at any time is allowed to use the windows machine. There are hacks available on the internet to allow more users on a windows machine.

If you want to share the desktop and be able to see what the other person on the other machine is doing. Install a VNC server on the windows machine. There are at least three flavors of VNC available on the Internet. Use remote desktop viewer or the same flavor of the VNC client on 10.10. Here you are sharing a single desktop and that only works if you work together in a disciplined way or if you work alone on both machines.

---

### Post by akakingess on 2011-04-12
Here is the link for [UltraVNC]("http://www.uvnc.com/") which is my personal choice/preference, but there are several out there that a google search wil bring up, and then it's just a matter of personal preference.

---

