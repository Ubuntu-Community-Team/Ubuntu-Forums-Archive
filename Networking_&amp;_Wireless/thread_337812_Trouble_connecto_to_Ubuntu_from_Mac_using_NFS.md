---
title: "Trouble connecto to Ubuntu from Mac using NFS"
date: 2007-01-13
forum: Networking &amp; Wireless
---

### Post by threadhead on 2007-01-13
I've been hitting a wall for the past couple of hours trying to connect to my Ubuntu (Edgy) box from the Mac (10.4.7). I have read *every* message here on the board and elsewhere. Still can not get it to work.

The following packages were installed (no errors): nfs-kernel-server nfs-common portmap
Portmap was not configured for loopback

My exports file:
```
/home/karl 192.168.0.1/24(rw,sync,insecure,anonuid=1000,anongid=100)
```

Everything was restarted:
```
sudo exportfs -ra && sudo /etc/init.d/portmap restart && sudo /etc/init.d/nfs-kernel-server restart
```

From the Mac I try to connect from the Finder (Go/Connect to Server...):
```
nfs://192.168.2.3
```

I remember reading something about the UID and GUID needs to match between client and server. So I changed the UID on Ubuntu to '501'. WHOA, **that was a big mistake!** Thank god I had ssh access to change it back and reboot.

So, what am I missing? I just can't connect to Ubuntu from my Mac using NFS.

---

