---
title: "freenx, network termination on startup"
date: 2008-06-12
forum: Networking &amp; Wireless
---

### Post by matw on 2008-06-12
Greetings,

Freenx reports a network error upon starting up (see nxclient messages below). It makes it past authentication, and I see a no machine window for a brief moment before it shuts down.

The nxserver is running on ubuntu 8.04. The client is running on XP. Both machines are connected to the same network. The same nxclient successfully connects to a different nxserver running on a Fedora linux system that is also on the same network.

Any ideas how I can go about fixing this?

Mat

______ nxclient error messages below _______

Info: Display running with pid '528' and handler '0x205be'.

NXPROXY - Version 3.1.0

Copyright (C) 2001, 2007 NoMachine.
See [http://www.nomachine.com/](http://www.nomachine.com/) for more information.

Info: Proxy running in client mode with pid '3216'.
Session: Starting session at 'Thu Jun 12 11:20:13 2008'.
Warning: Connected to remote version 2.1.0 with local version 3.1.0.
Info: Connection with remote proxy completed.
Info: Using LAN link parameters 1536/24/1/0.
Info: Using image streaming parameters 50/128/1024KB/6144/768.
Info: Using image cache parameters 1/1/65536KB.
Info: Using pack method '16m-rle-9' with session 'unix-gnome'.
Info: Not using NX delta compression.
Info: Not using ZLIB data compression.
Info: Not using ZLIB stream compression.
Info: Not using a persistent cache.
Info: Forwarding X11 connections to display ':0'.
Session: Session started at 'Thu Jun 12 11:20:13 2008'.
Info: Established X server connection.
Info: Using shared memory parameters 0/0K.
Error: Connection with remote peer broken.
Error: Please check the state of your network and retry.
Session: Terminating session at 'Thu Jun 12 11:20:14 2008'.
Session: Session terminated at 'Thu Jun 12 11:20:14 2008'.

---

### Post by MkDiR on 2008-07-03
I have the exact issue when I am trying to connect from work to home. I hope someone knows the answer to this since I have been searching the forums for a couple days now.

---

