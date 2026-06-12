---
title: "NX Client crashes when I try to connect to an Ubuntu FreeNX server"
date: 2013-09-05
forum: Networking &amp; Wireless
---

### Post by nwngeek212 on 2013-09-05
I'm using NoMachine Enterprise Client Beta 4 on my Mac to try to connect to my FreeNX server at home. I am able to connect and log in, but when I choose a desktop environment (Gnome), the client crashes. I don't think this is a problem with the Enterprise Client Beta, as this same problem happened using NX Player.

Other info: I'm using Ubuntu Desktop 13.04, ssh works, http server works

---

### Post by TheFu on 2013-09-05
Rather than running a full desktop, try running an xterm, then starting the DE you want.  Custom settings needed.

Thanks for mentioning that ssh works.  Does access to the freenx work from inside the LAN?

---

### Post by nwngeek212 on 2013-09-05
No I encountered the same error when connecting from within the LAN.

When I try to open an xterm, my all my keyboard inputs are wrong, there doesn't seem to be any correlation between what I input and what shows up on the terminal

---

### Post by TheFu on 2013-09-06
> **nwngeek212 said:**
> No I encountered the same error when connecting from within the LAN.

When I try to open an xterm, my all my keyboard inputs are wrong, there doesn't seem to be any correlation between what I input and what shows up on the terminal

I'm not a Mac guy. Tried it for 2 weeks, never "felt" right.
The only time I've seen keyboard stuff go wrong is when using VNC from an ARM tablet to connect to a chroot Ubuntu install running on the same tablet. That doesn't really apply here.

I can completely confirm that FreeNX from the Ubuntu repos works with the NoMachine clients for Windows and Debian just fine. I kick off an xterm and then run either a full DE if the bandwidth is great or a pure WM if bandwidth/distance make the connection slow.

I'd guess that the problem lies with the FreeNX server setup - possibly the NX public key hasn't been exchanged with all the clients? In my FreeNX setup, the apt-get install was just 1 step in about 5 that was necessary.  
* replace the default ssh keys with newly created keys for the nx userid.
* share the nx ssh public key with each client
* ensure that ssh works for both the nx userid AND my personal account.
The nx userid ssh key is used for the initial connection, but my personal login credentials are used after the login screen is shown.

Clear as mud?

OTOH, you probably handled all this already, so those steps are for lurkers.

---

