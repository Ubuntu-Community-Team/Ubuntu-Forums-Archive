---
title: "Using tsclient to XDMCP into another ubuntu box - session issue"
date: 2008-04-11
forum: Networking &amp; Wireless
---

### Post by Jethro_uk on 2008-04-11
I've managed to connect from one machine I have (with ubuntu) to another with tsclient and the XDMCP protocol. However every time it runs it seems to create a new session.

Is there any way to get it to reconnect to the last session ?

---

### Post by devurandom77 on 2008-04-15
The XDMCP protocol dates back to the days of brainless X stations that acted like terminals connecting to a larger, multi-user *nix system.  It's not a a remote desktop protocol, rather it is used to negotiate a remote Xserver session startup (remember in a network setup, the Xserver is what your keyboard, mouse, and displays connect to -- not the system running the applications.  Xorg running on your local system is the Xserver).  After the startup, all of the application communication is via native X protocols.

If you're familiar with the function of "gdm" (Gnome Display Manager) on your system, then XDMCP (X Display Manager Control Protocol) is basically what allows an orphan Xserver to find, connect to, and request display management from a gdm-like process running on another system.

If you want to connect into an existing session, you should look at something like VNC.  There may be a way to configure VNC to run against a phantom X server on your host box, which you can then connect to from a client box.  I haven't tried this though.  You can also use applications like xmove to move X applications between X servers, though last I tried it it was a bit kludgy.

Hope that helps.

---

