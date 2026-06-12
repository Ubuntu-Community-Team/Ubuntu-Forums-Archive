---
title: "Remote login at login screen?"
date: 2007-09-30
forum: Networking &amp; Wireless
---

### Post by Pusur on 2007-09-30
How do I make it possible to connect to my PC when it's at the login screen? I just get an error now, but as soon as I log in, it works perfectly fine. I'm using Wake on Lan, so I can start the PC from anywhere, but if remote login doesn't work, the point goes away...

---

### Post by Pusur on 2007-09-30
Anyone?

---

### Post by conjur3r on 2007-09-30
What are you using to connect to your computer?

Examples:
* Remote Desktop
* VNC
* SSH

---

### Post by Pusur on 2007-09-30
VNC. It works with SSH, but I would prefer a GUI.

---

### Post by Pusur on 2007-09-30
Is there really noone who knows the answer to this problem?

---

### Post by conjur3r on 2007-09-30
I've had this exact same issue.  There are a few other threads on this and some suggested to use a X11 module/plugin of some sort which would enable it.  My workaround was simply to get it to automatically login.  Works for me as I now have persistent sessions - meaning I can close down the VNC session, and not have the remote session logout (as what happens with Remote Desktop).

---

### Post by TomH4th on 2007-10-15
Bump. I too would like the VNC server to be running at login soIi can remotely reboot a machine, then come back and login from the X login screen. I'm a serious newb to Ubuntu, and Linux in general, but have been thrilled with it so far. Surely theres a way to do this?

---

