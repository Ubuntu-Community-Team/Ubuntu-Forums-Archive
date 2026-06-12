---
title: "Transient NFS"
date: 2008-08-31
forum: Networking &amp; Wireless
---

### Post by lgbr on 2008-08-31
I have a laptop on wireless that I would like to have connected to an NFS server. Only problem is that this laptop comes and goes from the network.

Typically NFS would mount at boot, and fail if not connected, remaining disconnected until the system reboots again. If NFS successfully mounts at boot, and then leaves the network for a while, and comes back, the NFS mount becomes stale.

I'm looking for something that tries to mount NFS as it is used. Any ideas? Please note that this is a setup for someone who isn't capable of using the terminal.

---

### Post by dmizer on 2008-08-31
You can use autofs to mount NFS shares. I haven't put a whole lot of research and effort into this because I don't really have a need for it and that's why I don't have a specific howto for you. But, here are a couple threads that might get you started in the right direction:

[http://ubuntuforums.org/showthread.php?t=621266](http://ubuntuforums.org/showthread.php?t=621266)
[http://ubuntuforums.org/showthread.php?t=155330](http://ubuntuforums.org/showthread.php?t=155330)

---

