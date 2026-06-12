---
title: "Steal X window?"
date: 2007-12-20
forum: Networking &amp; Wireless
---

### Post by Dragon45 on 2007-12-20
Lets say I start a windowed application (say, gedit) from the physical box. Then, I go somewhere and remotely log onto the box via SSH with X11 forwarding enabled. Is there a way to forward the already existing gedit window over ssh, by stealing or diverting or cloning it?

(Posted in networking because this is over a network...)

---

### Post by jonallport on 2007-12-20
I suppose you could export a new DISPLAY env variable  from the original shell and re-spawn the window.  I'm gonna have a try.

---

### Post by jonallport on 2007-12-20
Doesn't look practical to me.  I've had new windows spawned to a remote X server but I can't get existing ones to move, sorry.

I really think this is more of a 'Desktop Environments' question as you're going to need to tinker with GDM et al.

---

