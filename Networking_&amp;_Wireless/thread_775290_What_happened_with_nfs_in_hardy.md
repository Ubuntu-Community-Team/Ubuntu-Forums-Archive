---
title: "What happened with nfs in hardy?"
date: 2008-04-30
forum: Networking &amp; Wireless
---

### Post by sergioruydavid on 2008-04-30
Hi

I installed the new ubuntu hardy heron some days ago. After that, I can't easily share folders the way I used to do in gutsy. I don't find the option to choose sharing a folder through samba or nfs, and Hardy can't see the shared folders (nfs) from other network computers with gutsy. (In gutsy gibbon version, this is automatic)

Anyone here knows how do I configure a nfs network here?

Thanks!

---

### Post by Monicker on 2008-04-30
For some reason NFS is no configurable through the gui any longer.  A ticket is open on that:  [https://bugs.launchpad.net/ubuntu/+bug/219895]("https://bugs.launchpad.net/ubuntu/+bug/219895")

You can still do Samba. Go to Places -> Sharing Options. Be warned, there is glitch with this also, but you can get around it: [http://ubuntuforums.org/showthread.php?t=773851]("http://ubuntuforums.org/showthread.php?t=773851")

---

### Post by sergioruydavid on 2008-04-30
Thanks. I already knew that I could do it via samba, but I just don't want to. But thanks anyway, now I know other people have the same opinion about the problem.

Just one detail to add: I don't have "Sharing Options" on "Places" here. In gutsy I used to have. the only way to share folders via GUI is by right clicking a over a folder in nautilus. Then I can choose "Sharing options".

regards,
Sergio

---

### Post by chriscr on 2008-04-30
Hi,

I have NFS working but not as conveniently as before.

In Gutsy, as soon as I made a mount entry in /etc/fstab it would create a "desktop configuration file" entry visible in the "machine name" nautilus window. (computer:///).
To mount that entry I just right clicked and "mount"ed it. Then an icon appeared on the desktop and the entry in nautilus got an "nfs" icon beside it. To unmount it was just as easy.

In Hardy, no entry appears under computer:/// until it is mounted and all the files listed in there are "unknown type". To mount it I have to open a terminal window and type "mount <followed by the 1st or 2nd parameter on the fstab line>. After that it is listed in computer:/// and access is OK. Unmount works fine from that entry, as before.

Perhaps I have just got some setting wrong in nautilus or the desktop, but I've been through a lot of the configuration editor and can't see anything relevant.

Chris.

---

