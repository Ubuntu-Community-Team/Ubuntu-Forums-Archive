---
title: "NFS v SMB v AFP"
date: 2015-07-07
forum: Networking &amp; Wireless
---

### Post by npinn001 on 2015-07-07
I have 14.04 server installed with Webmin over the top of it, and have set up and configured some NFS shares, but the Mac just doesnt want to connect up. 

I have a mix of Linux, Windows and Apple devices on the network, but only really have a need for the Mac and the Linux boxes to connect up (the windows machines are just work related and so dont need access really).

Am I better using AFP? Or just go with SMB? I wanted NFS for the speed, but if the mac aint playing ball....

---

### Post by Morbius1 on 2015-07-07
OSX now defaults to SMB not AFP for file sharing and it's the only thing common to all the OS's in your network.
> When you connect from a Mac using OS X Mavericks or OS X Yosemite to  another computer using file sharing, your Mac automatically tries to use  the Service Message Block (SMB) protocol to communicate. If SMB is not  available, OS X tries to connect using Apple File Protocol (AFP).

---

### Post by npinn001 on 2015-07-07
Ah I see, thanks for that tip, kind of solves the issue really. I wanted to use NFS as I've alwasy read its a lot faster, but if SMB is the way to go I guess its not important.

---

