---
title: "NFS: Error Msg - &quot;Server is down&quot;"
date: 2007-06-03
forum: Networking &amp; Wireless
---

### Post by badman3k on 2007-06-03
I've been trying to mount my NFS, which is hosted on a Fedora c6 box, onto my Ubuntu Linux box, but to no avail.

I keep getting the following message when I run the command "sudo mount /mnt/Dell":
mount to NFS server '192.168.1.107' failed: server is down.

Now I've checked to see whether the services are running on both the local and server machines and they are.

The config files have the following:

/etc/exports:
/home/rich 192.168.1.100(rw,sync,no_root_squash)

/etc/hosts.allow:
ALL:192.168.1.100

/etc/hosts.deny:
<no entries>

Any help would be much appreciated.

Richard

---

