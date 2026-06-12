---
title: "Syncronization of files across LAN"
date: 2014-01-27
forum: Networking &amp; Wireless
---

### Post by DuskDN on 2014-01-27
Forgive me if this is the wrong section, it seemed appropriate.
For a while now I've been trying to figure out how to synchronize files between my laptop and my tower, and maybe even a little with my Android (which I'm sure would be the tricky part in any scenario and I'm not entirely concerned with). I've tried things like hosting ownCloud and Tonido on my tower but this seems like the wrong methodology because synchronization by these ways seems to require the duplication of data which is already present on the hard drive, rather than just using it at it's original location. I should think it could just be possible to have the machines connect to each-other and exchange the data, without the host machine creating a duplicate of the directories (in it's own system) I wish to synchronize. I don't really know a lot about networking beyond what it has taken me to host LAN parties however, so I'm a little in the dark as to how to go about doing this.
I thank the community for any information you might be able to provide.

---

### Post by ian-weisser on 2014-01-27
I think you're looking for NFS.  [https://help.ubuntu.com/13.10/serverguide/network-file-system.html](https://help.ubuntu.com/13.10/serverguide/network-file-system.html)

Samba and sshfs seems like good candidates, too.

---

