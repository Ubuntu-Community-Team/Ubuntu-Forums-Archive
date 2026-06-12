---
title: "Best way to achive my goal?"
date: 2006-11-13
forum: Networking &amp; Wireless
---

### Post by Crooksey on 2006-11-13
Hey,

I am looking to set up a "file server" on an ubuntu x86 machine, mainly for music movies and photos.

There will be one ubuntu box accessing this and 1 mac (Macbook brand new), whats the best type of file sharing protocol for me to use and methods i can do to use it?

The server will most likely be running X.

---

### Post by Crooksey on 2006-11-14
bump ](*,)

---

### Post by FrodoB on 2006-11-14
I think that the issue may be that most folks are not familiar with the networking capability of the Mac. I am assuming that this is using OS-X, BSD UNIX based.

The options are:

NFS - Works on all UNIX variants

SMB - Works on Windows and Linux, probably OS-X

HTTP - Share off of a web server and ftp files around or use one of the above

NFS probably work really well if the server is on all of the time. The clients do not like it when the server goes down on them.  It makes the network look like the file system. I would probably go with NFS if there were no Windows machines involved.

---

### Post by Crooksey on 2006-11-14
Ill go with NFS then, any good howtos?

---

### Post by FrodoB on 2006-11-14
Ubuntu Docs:
[https://help.ubuntu.com/community/UserDocumentation?action=fullsearch&context=180&value=NFS](https://help.ubuntu.com/community/UserDocumentation?action=fullsearch&context=180&value=NFS)

Linux Howto:
[http://www.tldp.org/HOWTO/NFS-HOWTO/index.html](http://www.tldp.org/HOWTO/NFS-HOWTO/index.html)


Also see:
[http://www.howtoforge.com/high_availability_nfs_drbd_heartbeat](http://www.howtoforge.com/high_availability_nfs_drbd_heartbeat)

---

