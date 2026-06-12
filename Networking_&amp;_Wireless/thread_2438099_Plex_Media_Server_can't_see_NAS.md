---
title: "Plex Media Server can't see NAS"
date: 2020-03-05
forum: Networking &amp; Wireless
---

### Post by darthlinux2 on 2020-03-05
Hi

I am new to ubuntu, so far it has everything I need but I have ran in to a problem when trying to set up plex media server, all my media is on my NAS drive but Plex doesn't see the NAS drive, I have tried to follow instructions online but seem to get stuck.
Does anyone have a dummys guide to mounting a NAS drive.

---

### Post by TheFu on 2020-03-06
Depends.

a) does the NAS have a static IP?  Desktops, servers, and devices that aren't portable (like a laptop) should have static IPs.

b) what protocols does the NAS support?  CIFS, NFS, DLNA, Something else?  Cheap NAS use CIFS only.  Better NAS support NFS too.  NFS tends to work better than CIFS for streaming needs.

c) the exact model of the NAS would be helpful, since some of them have odd configurations.

d) Avoid using non-wired connections for any streaming server.

My plex server is also my NFS server for the other 15 systems on the network. If the network is GigE, it shouldn't matter.

---

### Post by darthlinux2 on 2020-03-06
Yes the NAS box has a static IP address
Its supports CIFS/NFS
the model is D-Link ShareCenter DNS-323

---

### Post by TheFu on 2020-03-06
Does the NAS "export" the NFS shares?  I've only done that on Unix/Linux systems, not non-enterprise NAS boxes.
Did you mount the NFS share on the plex machine?  A single line in the fstab is the method many people use.

A simple version will mount the storage always, not just on-demand:
```
romulus:/Data/r2     /S      nfs      proto=tcp      0      2
```
If you use this version, the /S directory needs to already exist - meaning you must create it.  That's it.  Run **sudo mount -a** and the storage should mount assuming the NAS has properly exported the /Data/r2 share.

_**OR**_

Something like this will use systemd-automount capabilities to mount the storage on-demand.
```
romulus:/Data/r2     /S      nfs      x-systemd.automount,x-systemd.idle-timeout=5min,proto=tcp,noauto     0      2
```
where:
* /S is the local mount point
* x-systemd.automount            appears to HAVE TO BE first in the options
* x-systemd.idle-timeout=600s    is optional 5m works too
* proto=tcp                      is a best practice for NFS on fast networks
* noauto              is there to prevent mounting before a request was made

Then run:
```
sudo systemctl daemon-reload
sudo systemctl start S.automount
```
The "S.automount" maps directly to the name of the mount point selected by you in the fstab.  If the mount point was /data/stuff/movies, then the command would be:
```
sudo systemctl start data-stuff-movies.automount
```
Leave it to the systemd team to make things harder than needed.

Some manpages: *systemd.automount*  *systemd.mount* to learn more.

If your plex server cannot ping the NAS by name, use the LAN IP address instead of "romulus".

Someone else will need to help with any needed NAS-side configuration. Sorry.

---

