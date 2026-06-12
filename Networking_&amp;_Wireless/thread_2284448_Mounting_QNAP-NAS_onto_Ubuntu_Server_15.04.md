---
title: "Mounting QNAP-NAS onto Ubuntu Server 15.04"
date: 2015-06-29
forum: Networking &amp; Wireless
---

### Post by Single_Entity on 2015-06-29
Dear all,

I'm having no success mounting a NAS onto my Ubuntu server.   The person who set the NAS up has left the company, so i don't know whether to use cifs or nfs. I have tried the following:

mount -t nfs -o nfsvers=3 192.168.168.200:/home NAS

But this just hangs and eventually times out.

I know that the IP address is correct as I can FTP onto the NAS using it.  I know the NAS has a folder called home, which is shared because I have a windows machine connected to the network which sees the home directory as a share.

The NAS folder exists and has 777 permissions.

If I run the above as cifs instead of nfs I get an error saying:

wrong fs type, bad option, bad superblock, missing codepage or helper program.

This is what led to me assuming the file system share is NFS.

Any help would be very much appreciated.

---

