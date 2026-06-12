---
title: "NFS Mount - Strange Permission Issue?"
date: 2018-01-18
forum: Networking &amp; Wireless
---

### Post by rkillcrazy on 2018-01-18
First off, I'm not sure if this is an issue with my **Synology DS212j** (running DSM 6.1.4-15217 Update 5) or with my PC (running **Ubuntu** 17.10).  I've only recently noticed the issue and have been poking at it for the last couple days.

Basically, I've been mounting the NFS share with the command **below** for a couple of years and it has always worked - without issue.  However, recently, I've been mounting it but noticing I no longer can browse the share via **Nautilus** and **edit anything in the root**.  Basically, I can drag & drop files to it but I **_cannot_ right-click** and **rename** them, **cut** them or **move** them (see the screen-shot).  I found it to be quite curious that if I use a **terminal** session, I can do whatever I want with these same files.  More curious still, I created a subdirectory and copied some files into it.  I could then right-click these files inside that subdir and rename, move, etc. just fine!  

Has the way we mount NFS shares changed?  Can I add/remove a switch to remedy this issue?

How I mount my NFS share:
```
sudo mount -t nfs 192.168.20.49:/volume1/Movies ~/Videos/NAS/Movies
```

How it's mounted:
```

mount | grep nfs
192.168.20.49:/volume1/Movies on /home/tome/Videos/NAS/Movies type nfs4 (rw,relatime,vers=4.0,rsize=131072,wsize=131072,namlen=255,hard,proto=tcp,timeo=600,retrans=2,sec=sys,clientaddr=192.168.20.115,local_lock=none,addr=192.168.20.49)

```

---

### Post by rkillcrazy on 2018-01-31
It's likely an issue with the export on the Synology as the issue persists across multiple machines running fully updated builds of Ubuntu 17.10.  I'll send my queries their way.

---

