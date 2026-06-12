---
title: "Help! Big trouble with access rights on NFS shares."
date: 2007-12-20
forum: Networking &amp; Wireless
---

### Post by joede on 2007-12-20
I've done several installations of clients and servers with debian and ubuntu. All of these installation were only small networks, but without trouble. Now I have a problem with NFS, I've never seen before.

My server is running Breezy (yes, it's old, I know ;) ). The harddisks are exported with Samba (for the windoze clients) and with NFS. There is **no** NIS server active, so I add the user-ids and group-id allways manually. The samba daemon is configured with "force group" to ensure a unique group for each share.

And here is my problem: I've installed Gutsy for a brand new client. The UIDs and GIDs are exactly the same as on the server. I've checked this more than twice! After mounting a NFS path, I can see the access rights as expected -- the GID matches the name. But even if the group rights are matching, I can't get access to the directories! If I am the owner, all is working fine, but if I am only in the same group, it seems that I only get the rights of "other". If I create a directory on the server (with 775), all the other group members can access it (with samba). The group name (and it's ID) is equal to the older directories. 

If I mount the share with smbfs, I have access as expected.

Heres the snippet from my Gutsy /etc/fstab
```

camelot:/home/jd /media/nfs/jd nfs rw,hard,intr,user,nosuid,exec,sync 0 0
camelot:/home/Samba/ /media/nfs/lan nfs rw,hard,intr,user,nosuid,exec,sync 0 0

```

What's the reason for this behaviour?

Is it possible that features like ACL or SElinux are the reason for my problem? I neither use ACL nor SElinux (as far as I know), but maybe the default configuration of Gutsy is a problem.

Or more information: my previous server / clients was based in Woody and Warty. I've used the same configuration here without trouble.

By the way: the Midnight-Commander shows me the access rights of the filesystem (775, ...) by name (with c-x o). Nautilus seems to get more informations. Here the directories have labels showing the access limitations.

Any hints?

---

### Post by joede on 2007-12-20
A few minutes ago, I've tested another Gutsy-Client together with an NFS-Server running Debian Etch.

The /etc/fstab at the client and the /etc/exports at the server are nearly identical. In this environment, the NFS access is working as expected. A directory created by user-a (with 775) allows WR access to user-b if the group matches the GID of the directory.

So what could be the difference to the Breezy NFS-Server?

---

