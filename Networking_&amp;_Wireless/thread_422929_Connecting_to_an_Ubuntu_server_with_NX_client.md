---
title: "Connecting to an Ubuntu server with NX client"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by Muttonz on 2007-04-25
Hi, I'm trying to remotely connect to an Ubuntu server using the free NoMachine NX client.  I am running on an XP machine.  I've tried both NX versions 1.5 and 2.0 (I read somewhere that 1.5 was more successful, but no luck).  The session authenticates fine - a window opens up showing the NX logo for a second and then closes.  Another window pops up saying "session failed."  Here is the log:

NXPROXY - Version 1.5.0

Copyright (C) 2001, 2005 NoMachine.
See [http://www.nomachine.com/](http://www.nomachine.com/) for more information.

Info: Proxy running in client mode with pid '112'.
Info: Synchronizing local and remote caches.
Info: Handshaking with remote proxy completed.
Info: Using cache parameters 4/262144/8192KB/8192KB.
Info: Using image cache parameters 1/1/32768KB.
Info: Using isdn link parameters 4096/8/20/100.
Info: Using pack method '16m-jpeg-5' with session 'unix-gnome'.
Info: Using ZLIB data compression level 6.
Info: Using ZLIB data threshold set to 32.
Info: Using ZLIB stream compression level 9.
Info: Using remote ZLIB data compression level 6.
Info: Using remote ZLIB stream compression level 9.
Info: No suitable cache file found.
Info: Starting X protocol compression.
Info: Established X server connection.
Info: Using shared memory support in X server.
Info: End of session requested by remote proxy.
Info: Shutting down the link and exiting.

For some reason it is forcing an end of session request.  I don't know why.  I hope I am posting this to the right place, my apologies if not.  I would appreciate any help.

Thanks,
Andrew

---

### Post by gurgle on 2007-04-25
I would appreciate knowing this as well.

---

### Post by Muttonz on 2007-04-25
OK, well I had a fellow admin that could connect to the server to simply remove my account and make a new one.  That seemed to fix it - apparently there was nothing wrong on my end.

- Andrew

---

