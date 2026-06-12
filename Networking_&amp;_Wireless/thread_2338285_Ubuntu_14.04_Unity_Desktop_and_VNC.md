---
title: "Ubuntu 14.04 Unity Desktop and VNC"
date: 2016-09-26
forum: Networking &amp; Wireless
---

### Post by georgia-linux on 2016-09-26
I am running Ubuntu 14.04 (32-bit) with the original Unity desktop (desktop version, not the server version).  I have set up SSH and can connect to my Linux box from my Dell laptop (Windows). I want to set up a VNC connection between the two computers.
I already have a client (SSH and VNC) on my Dell Laptop.(MobaXterm) which works well.  All the information that I can find specifies Ubuntu SERVER software; if this is necessary, what packages do I need to install to satisfy this requirement?
I have not used the Desktop Sharing software already installed; is this equivalent to other VNC server software that I would need to install in lieu of this package?
Any help and suggestions would be appreciated.

---

### Post by TheFu on 2016-09-26
You shouldn't use Unity or any desktop environment that requires direct access to the GPU. 
Actually, I use x2go, which works over the ssh port with ssh keys by default.  There are clients for the main 3 desktops - performance is about 2-3x faster than any VNC.

Use the x2go PPA to install - follow their instructures for the client and the server installation. Use xfce, lxde, or a straight openbox environment to start. You'll need to install those desktops on the remote server. After you get that working, then screw around with whatever desktop you want to try, but I don't think Unity is supported. The x2go FAQ has specifics.

If the first connection doesn't seem reasonably fast, turn down the network settings and turn up the compression.  Also, the remote printing, audio and local mounting probably won't work through most internet firewalls; after all, that coffee shop router doesn't have any open ports. They do work great on the same LAN.

---

