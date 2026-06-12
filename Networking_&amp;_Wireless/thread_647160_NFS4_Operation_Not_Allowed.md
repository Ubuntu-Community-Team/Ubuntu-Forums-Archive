---
title: "NFS4 Operation Not Allowed"
date: 2007-12-22
forum: Networking &amp; Wireless
---

### Post by MichaelBKK on 2007-12-22
I've read and tried everything in recent (and not so recent) posts on this, but I haven't seen the same problems described or found any solution that works.  Here's the problem:

I upgraded my server to Fedora 8 (been running Red Hat/Fedora on it for years, and FWIW Fedora seems to be catching up to Ubuntu in usability).  I had been working fine with an NFS mount from my Ubuntu 7.10 desktop to Fedora 6 before the upgrade.

The problem seems to be that the NFS in F8 is now v4, so I have to make some changes.  Having followed the instructions for both systems, I now get the following message when I try to mount the remote directory:

```
sudo mount -t nfs4 server:/exports/html /home/myhome/html
mount.nfs4: Operation not permitted
```

Anybody have any suggestions?  I'm kind of dead without the mount.

---

