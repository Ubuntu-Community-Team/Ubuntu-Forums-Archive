---
title: "vnc and terminal server client"
date: 2007-05-28
forum: Networking &amp; Wireless
---

### Post by z-vap on 2007-05-28
Hey all,

I was curious about the tsclient's behavior as opposed to vncviewer.  

The popups in tsclient say if you change the protocol to VNC put the path to the passwd file in the "Username" field.  When I do this, and attempt a connection it still prompts me for a password on connect.

However if I simply use a terminal session and: ```
$ vncviewer -passwd ~/.vnc/passwd machinename
```that works fine without an additional prompt for a password.

Is this a known bug/issue, or have I missed something?

---

