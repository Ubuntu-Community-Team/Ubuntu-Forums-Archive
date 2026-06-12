---
title: "ftp is semi-broken in Ubuntu 7.10"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by rybu on 2007-10-23
FTP seems to be highly problematic in Ubuntu 7.10.  On a website I usually connect to via FTP to upload photos, FTP crashes on about 60% of operations -- even things as simple as a change of directory.  

By "crash" I mean this:

> 
PASV

Error: Could not read from socket: Connection reset by peer
Disconnecting from site ****
Error: Remote site disconnected after trying to transfer file
Could not download ****.jpg from local filesystem
Error: Remote site local filesystem disconnected. Will reconnect in 5 seconds
Looking up ****
Trying linhostjava18.prod.mesa1.secureserver.net:21


It seems there's some difficulty with sockets.  Anyone know what might be the source?   I presume there's bug reports out there, haven't looked for any yet.

---

### Post by mafitzpatrick on 2007-12-12
Any success with this? I suspect this might be the cause of [my problems](http://ubuntuforums.org/showthread.php?t=638148&highlight=PASV+fTP) too.

---

