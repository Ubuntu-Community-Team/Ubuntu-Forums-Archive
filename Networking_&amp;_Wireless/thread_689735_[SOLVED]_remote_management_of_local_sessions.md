---
title: "[SOLVED] remote management of local sessions"
date: 2008-02-06
forum: Networking &amp; Wireless
---

### Post by kevinfishburne on 2008-02-06
Scenerio:

Multiple Ubuntu 7.10 workstations in a public library. Users logged in have timed session limits based on which user account they log in with. Staff has ability to remotely start a session with the appropriate user account on display 0 so the user can use it.

Problem:

I found a way to log in to gdm using VNC, but only on display 1. The local display remains at the login screen. These machines are AMD64, so I am having problems getting FreeNX to do desktop sharing or shadowing (it doesn't work at all). Is there a way to use VNC or something similar to take a user from gdm to the desktop on display 0?

Kevin

---

### Post by Andrew Stone on 2008-02-06
I think the program you're looking for is "vino".  Install it using synaptic; it does vnc for screen 0.

---

### Post by kevinfishburne on 2008-02-11
I found some information here:

[http://en.gentoo-wiki.com/VNC#New_sessions]("http://en.gentoo-wiki.com/VNC#New_sessions")

but it says that vino can only connect to existing sessions, but can't connect to gdm to log in a user on display 0. I found a howto here:

[http://ubuntuforums.org/showthread.php?t=363236]("http://ubuntuforums.org/showthread.php?t=363236")

which did the trick nicely. Now I can log in remotely with gdm on display 0. The link explains how to use x11vnc, which you install and configure on the machines you want to control. After doing that you can use any regular vnc client to control those machines. If it runs insanely slow, turn off Compiz and it will be much better.

---

