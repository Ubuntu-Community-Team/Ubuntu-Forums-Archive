---
title: "Resolution and xorg.conf"
date: 2010-10-15
forum: New to Ubuntu
---

### Post by david_huang on 2010-10-15
Hi all, 

I've just install my ubuntu 10.10 and want to adjust my screen resolution. I've tried using "preference/monitor" but it lack 1024*768 one, so I tried to edit the xorg.conf file but it do not exist, and Xorg --configure doesn't work with error:

Server is already active for display 0
	If this server is no longer running, remove /tmp/.X0-lock
	and start again.

What's the problem? Thanks for any tips, and be reminded I'm just a newbie to ubuntu.

---

### Post by khelben1979 on 2010-10-16
xorg.conf has been removed in newer versions of Ubuntu by the default. Start with doing an output of your hardware by typing **lspci** from a text terminal.

Once we know something about your hardware, it will be easy to see if the system are going to use open source graphics or non-free drivers. With a decent graphics card, non-free drivers give you faster 3D performance.

---

