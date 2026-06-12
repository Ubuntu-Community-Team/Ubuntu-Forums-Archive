---
title: "remote reboot - network id"
date: 2007-11-08
forum: Networking &amp; Wireless
---

### Post by theonlyalterego on 2007-11-08
After poking around the forums here I haven't seen anything that describes my problem, but I find it hard to believe it's not out there somewhere...

I often manage my ubuntu machine via SSH, and VNC. Every so often I need to restart it (mostly for upgrades), but post-restart my router never finds it until I physically login to the machine.

After looking around I saw [this thread]("http://ubuntuforums.org/showthread.php?t=598880"), which leads me to believe that the the "network" is not started until you AFTER a user logs into the system. So I tried to enable auto-login (not sure if it worked yet since I can't get to the machine until this weekend) but my thought was that this would be the same as if I had physically logged into the PC.

My ubuntu machine behind a router on verizon fios,  I have a number of ports forwarded based on the machine name (SSH, VNC, CSS server ^_^ etc) so the router SHOULD identify the machine once it tries to connect. The problem is, after I send a reboot command to the ubuntu pc it never shows back up on the router; at least not until I physically login; this in turn means that I cannot SSH into the PC since the router doesn't know it's there.

anyone know how I can get around this?

---

