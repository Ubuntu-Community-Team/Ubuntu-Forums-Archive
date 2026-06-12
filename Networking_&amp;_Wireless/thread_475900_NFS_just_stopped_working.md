---
title: "NFS just stopped working"
date: 2007-06-16
forum: Networking &amp; Wireless
---

### Post by chrisod on 2007-06-16
NFS to a Simpleshare NAS drive has worked flawlessly for months. Today it stopped, and I stumped as to why. If I try to mount the drive manually I get the following error.

*mount to NFS server 'mediaserver' failed: server is down.*

I've rebooted the NAS device and it appears to be working properly. I can ping it and I can get to it from my XP boxes. I've checked /etc/export and /etc/fstab and all appears to be fine there. I guess its possible that the NFS server on the Simpleshare has failed, but I'm not getting any sort of error from it on a reboot. I did a portscan on the Simpleshare and it does report nfs on port 2049. rpcinfo shows that nfs is running on port 2049 on my Ubuntu Feisty box also.

In case its not clear - Ubuntu is the NFS client in this case.

Any ideas what I should try next?

---

### Post by dmizer on 2007-06-17
boot to a live cd and see if you can mount the nfs nas drive that way.  preferably something not ubuntu, or of a different release of ubuntu.

knoppix would be my first choice.

---

### Post by chrisod on 2007-06-18
Update: I assigned a static IP to the NAS drive and edited /etc/exports and /etc/fstab to point to the IP address instead of the server name. Everything is working again.

---

