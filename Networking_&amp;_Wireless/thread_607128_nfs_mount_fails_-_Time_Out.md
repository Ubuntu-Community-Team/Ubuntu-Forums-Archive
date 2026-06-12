---
title: "nfs mount fails - Time Out"
date: 2007-11-08
forum: Networking &amp; Wireless
---

### Post by William_in_Kanata on 2007-11-08
I am trying to mount an nfs share, that was working fine yesterday, but now fails with the message

mount: RPC: timed out

Haveing worked through the trouble shooting guide for nfs at sourceforge, and everything is OK, except that when I look at the contents of /proc/fs/nfs/export all I get is

# Version 1.1
# Path Client(Flags) # IPs 

Reading between the lines of the guide, I would expect to then see a list of the exported file systems. I haven't changed anything on the server, but it was rebooted earlier to-day. I do see the client connecting, and being authenticated in the server logs.

Both machines are running Ubuntu Server 6.06.1, with all patches current. The Files system is mounted, and has appropriate permissions. ( it is physicaly on /dev/md0 with is a two drive raid 1 set up).

Any suggestions as to where to look now, or what to tweek will be most greatfully received.

---

