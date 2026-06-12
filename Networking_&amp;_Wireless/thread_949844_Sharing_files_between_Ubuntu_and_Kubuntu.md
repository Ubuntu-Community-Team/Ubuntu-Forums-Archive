---
title: "Sharing files between Ubuntu and Kubuntu"
date: 2008-10-16
forum: Networking &amp; Wireless
---

### Post by jacko8686 on 2008-10-16
It's been a few months I have installed Linux and I was wondering how do I share files between Ubuntu 8.04 and Kubuntu Hardy Heron (on my laptop). I have installed Sampa on both but how do I manage to make the pcs see each other?

THe pc are connected to a LAn with a TpLink router ..

---

### Post by Iowan on 2008-10-16
Someone is bound to suggest that NFS is better for Unix-Unix filesharing (or even SSHFS), but Samba should still work. First question is whether machines can see (ping) each other. **smbtree** should show the servers available.  Next, is Samba-server installed - and running? (Samba client came pre-installed).  Some threads say SMBFS must also be installed (although CIFS is actually being used).  Are both machines in the same workgroup? Does either (or both) machine(s) have a firewall blocking Samba ports? There are pros and cons to installing Winbind. (The service provided by winbindd is called `winbind' and can be used to resolve user and group information from a
Windows NT server... from  Synaptic Package Manager). With Winbind, **/etc/nsswitch.conf** may need to be edited.

---

