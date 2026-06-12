---
title: "Cannot connect VNC when network-interface set to 'lo'"
date: 2013-12-10
forum: Networking &amp; Wireless
---

### Post by Ouroborus777 on 2013-12-10
I've been trying to setup Vino over OpenSSH. Part of that is making Vino only accept local connections.

In dconf, clearing /desktop/gnome/remote-access/network-interface works as expected. I can connect from either 127.0.0.1 or eth0's IP, both locally and remotely.
Setting /desktop/gnome/remote-access/network-interface to 'eth0' works as expected. I can connect both locally and remotely using the eth0's IP, but not from 127.0.0.1.

But setting /desktop/gnome/remote-access/network-interface to 'lo' doesn't work properly. Trying to connect via 127.0.0.1 hangs while connecting (both locally and over ssh tunneling). Based on Vino's logging, it appears to be binding to the right address and port, 127.0.0.1:5900.

How do I get this working?

---

