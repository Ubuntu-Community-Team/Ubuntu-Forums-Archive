---
title: "Networking with Windows"
date: 2010-07-27
forum: New to Ubuntu
---

### Post by Failboat88 on 2010-07-27
Lets say I have a ubuntu server, with some downloaded files that potentially have windows viruses. What all can my windows box do without the viruses infecting it. 

VNC,streaming media, using files on the server that aren't infected, or even just connecting to the file share.

---

### Post by Deiz on 2010-07-28
If you're serving potentially malware-laden files, you should install ClamAV on the server and run periodic scans of the directory you share with the Windows system.

The only security issue occurs once you download and run binaries on the Windows host, which shouldn't be an issue in most cases if you're running ClamAV on the server with up-to-date definitions.

---

