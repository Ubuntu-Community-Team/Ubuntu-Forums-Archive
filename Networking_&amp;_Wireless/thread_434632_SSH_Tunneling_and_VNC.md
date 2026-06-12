---
title: "SSH Tunneling and VNC"
date: 2007-05-06
forum: Networking &amp; Wireless
---

### Post by nuclearpidgeon on 2007-05-06
Hi everyone

I have Ubuntu 7.04 - I installed last year via 'Atomic-MPC's (the magazine) brilliant guide. It's the best thing I have done - Ubuntu ROCKS!

In the guide, there was a section on SSH tunneling and Remote Desktops. I have another XP machine and can SSH via LAN into my Ubuntu pc just fine - and I also can use VNC to have complete control over my desktop (that is especially cool, I must admit)
-BUT-
I want to use SSH tunneling so I can use VNC to access my Ubuntu PC over the 'Net
Now in the guide here's what was written...
[FONT="Comic Sans MS"][COLOR="Red"]A neat trick is to access your VNC desktop from oustide your LAN, across the Internet. You could do this by opening the VNC port (5901 in our case) on the firewall, but a better idea is to use SSH tunneling. Using SSH not only means that you need a valid SSH login to connect, but it also encrypts, and optionally compresses, the traffic.
The tunnel listens on a port on the local machine, and forwards any connections through a specified host and port at the other end, relative to the host running the SSH daemon. Here we SSH in to the Ubuntu PC and forward port 5901 on the client system to the same port on the Ubuntu PC
```
ssh -C -L 5901:localhost:5901 my.ubuntu.pc
```
If your client is a Windows box, you can configure tunnels in PuTTY from the 'Tunnels' settings Pane.[/COLOR][/FONT]

That last bit - using PuTTY. That's what I want to do, but I'm not sure how. Could someone advise me?

---

### Post by Endolith on 2007-05-07
I don't know, but PuTTY is [here](http://www.chiark.greenend.org.uk/~sgtatham/putty/).

From one Linux machine to another, I just use -X and run the programs remotely.  I don't completely understand it (I guess the processing is taking place on the remote computer?), but I can use it.  I think Xming will do the same thing from Windows?

---

