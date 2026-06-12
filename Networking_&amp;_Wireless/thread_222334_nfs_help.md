---
title: "nfs help"
date: 2006-07-24
forum: Networking &amp; Wireless
---

### Post by onlythetim on 2006-07-24
I have a gentoo server, a gentoo client, and a kubuntu client.   The gentoo client and server work fine together, but the kubuntu client has trouble integrating into the system.  What I am specifically wondering about is nfs.  I have 4 directories setup for nfs on the server, which I am currently sharing with the gentoo client.  I added the appropriate info to exports on the server, and added the directories to fstab.  However, the directories are never mounted on startup on the kubuntu client, and when I try to moutn them manually, or with a mount -a, it sometimes works.  Sometimes I type the command it doesn't work.  then, if I type it again (exactly the same... use the up arrow key)  it might work after the third or forth try.

Anyone have any idea what's going on here?

Thanks.

---

### Post by mpvano on 2006-07-25
Make sure you have portmapper installed and running, as well as any mounting daemons needed, and that they're not firewalled in such a way that they can't talk.

I was surprised to find out that under some circumstances, you can mount NFS volumes without portmapper installed on the client, but NFS mounting is only reliable if it's installed. I don't think it's part of the default install (at least it wasn't with breezy).

Caution: portmapper can have some security implications if you don't do something to restrict access to it to only your own known hosts!

Mario

---

