---
title: "Relaying sshfs over samba works, but over NFS fails"
date: 2007-07-01
forum: Networking &amp; Wireless
---

### Post by madoka on 2007-07-01
Forgive my poor text diagram:

```

/files           (sshfs)  /files             (samba)    /files
(Offsite server) -------> (gateway) ------------------> (client1)
                                          |
                                          |  (NFS)      /files
                                          ------X-----> (client2)


```

I hope it makes sense.  I'm doing this because not all client's got FUSE installed.  Relaying over samba works perfectly.  However, I couldn't get the relaying over NFS to work.  If I don't mount the remote share, then the NFS connection would work.

I have user_allow_other set in fuse.conf, and allow_other set in the mount option.  In /etc/exports, I have nohide and all_squash set.

---

