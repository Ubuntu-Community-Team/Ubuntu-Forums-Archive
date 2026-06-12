---
title: "Sharing Files between Ubuntu and OS X"
date: 2006-10-11
forum: Networking &amp; Wireless
---

### Post by scrook on 2006-10-11
Hi all,

I've recently been given a G4 tower with OS X and I thought that it would be a cool project to have the Mac be able to access the ubuntu machine as a file server. 

All the files that I want to access from OS X are either in my home directory (which is in it's own partition of type EXT3) or my files partition (Also EXT3).

The two machines will be connected via a LAN.

Does anybody have any guides I can read or suggestions for getting started on this?

Thanks

Scott

---

### Post by Kateikyoushi on 2006-10-11
There are a solutions in [this thread]("http://ubuntuforums.org/showthread.php?t=240563").

---

### Post by TheCelloFellow on 2006-10-12
It's mentioned in the above thread, but I'd suggest Zeroconf myself. It's basically AppleTalk, polished though, over TCP/IP using Multicasting (serverless) DNS. Because of its roots in AppleTalk, it's native in Mac, they call it Bonjour. Kubuntu has better support for Zeroconf than Ubuntu, but Ubuntu works too. :)

---

