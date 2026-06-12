---
title: "NxServer can't locate KDE environment"
date: 2008-06-24
forum: Networking &amp; Wireless
---

### Post by DapperMe17 on 2008-06-24
Hi,

I just updated Kubuntu Gutsy to Hardy 8.04. 

After the upgrade, when I try to sign on to the NoMachines NxServer(home PC) from my NoMachines NxClient(remote PC), I am able to connect & establish a session on the NxServer machine, however I receive a small box that states that NxServer cannot find the KDE envoronment.

Could the upgrade to Hardy have moved the KDE location, so that NXServer just can't locate the new location?

Any help would be great!
Thanks

Here is the NxClient output from the session...

[[I]I]NXPROXY - Version 3.1.0

Copyright (C) 2001, 2007 NoMachine.
See [http://www.nomachine.com/](http://www.nomachine.com/) for more information.

Info: Proxy running in client mode with pid '10637'.
Session: Starting session at 'Tue Jun 24 16:42:36 2008'.
Warning: Connected to remote version 3.0.0 with local version 3.1.0.
Info: Connection with remote proxy completed.
Info: Using WAN link parameters 768/24/1/0.
Info: Using cache parameters 4/4096KB/16384KB/16384KB.
Info: Using pack method 'adaptive-9' with session 'kde'.
Info: Using product 'LFE/None/LFEN/None'.
Info: Using ZLIB data compression 1/1/32.
Info: Using ZLIB stream compression 1/1.
Info: Using cache file '/home/dad/.nx/cache-kde/S-######################'.
Info: Forwarding X11 connections to display ':0.0'.
Info: Listening to font server connections on port '11061'.
Session: Session started at 'Tue Jun 24 16:42:36 2008'.
Info: Established X server connection.
Info: Using shared memory parameters 1/4096K.
Session: Terminating session at 'Tue Jun 24 16:42:49 2008'.
Session: Session terminated at 'Tue Jun 24 16:42:49 2008'.
[/I][/I]

---

### Post by DapperMe17 on 2008-06-25
Anyone care to take a shot?

Thanks!

---

### Post by kford on 2008-11-26
I had the same error.  In the client configuration screen, under the "advanced" tab I changed system cache memory from 16 MB to 32 MB and I was able to get a session started.  For whatever it's worth, I'm running KDE4.  Now I'm just hoping it sticks.

Good luck.

---

### Post by SANITI on 2008-12-03
I'm having the same problem using Ubuntu 8.04.1. I've tried changing the Cache: In memory from 16 Mb to 32 Mb, but that didn't work. I have had it working at one time. Any suggestions on what to check that might be the problem.

---

