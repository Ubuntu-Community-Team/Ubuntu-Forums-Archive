---
title: "Inbound Remote Desktop into Ubunto desktop"
date: 2007-02-12
forum: Networking &amp; Wireless
---

### Post by T.Anderson on 2007-02-12
Remote Desktop inbound to Ubuntu 

--------------------------------------------------------------------------------

Am running Ubuntu 6.1 desktop.
I can connect remotely to Ubuntu desktop from my PC using the VNC client from my PC.  I adjsted the built in Remote Desktop program on Ubuntu, to allow for this inbound connection.
HOWEVER, I must first be logged into the Ubuntu desktop BEFORE Ubuntu will accept any RealVNC desktop connections.  Why?  Seems strange.
Q.) How to set Ubuntu desktop to accept a RealVNC connection without first having to login on Ubuntu? If I do remote work on Ubuntu that requires a remote reboot of Ubuntu, I can no longer RealVNC into Ubuntu, not until someone at remote Ubuntu logs in first...

What is the trick to having Ubuntu accept connections at all times?

---

### Post by Sqwishy on 2007-02-12
Please don't post 2 threads asking the same question.
[http://ubuntuforums.org/showthread.php?t=359730](http://ubuntuforums.org/showthread.php?t=359730)

---

### Post by Yoooder on 2007-02-12
This isn't a guaranteed answer, but it sounds like your VNC server isn't being started until you login (which I think might be the only way for it to start under Linux).

What you want is a server/daemon running that runs at system start-up, versus a server that runs when you log in.

Do some research to see if it's possible to start the server at boot (and remove it from your desktop startup-apps)

---

