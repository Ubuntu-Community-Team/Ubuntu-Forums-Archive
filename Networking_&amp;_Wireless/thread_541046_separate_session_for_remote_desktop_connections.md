---
title: "separate session for remote desktop connections"
date: 2007-09-02
forum: Networking &amp; Wireless
---

### Post by dgrafix on 2007-09-02
Is there a way of having two users on my pc at the same time? one via vnc on the LAN and one local user?

The reason I want to do this is whenever i use VNC on my laptop it has the horrible scrolling resolution mode.

---

### Post by Haegin on 2007-09-02
Well VNC just connects to an already running session which isn't what you want. You probably want to look into XDMCP which lets you login to a new session. You may also want [sabayon]("http://www.gnome.org/projects/sabayon/") to create different user profiles so you can have a different resolution. I haven't used sabayon so I'm not totally sure but XDMCP should be what you want.

---

