---
title: "CIFS mounts as wrong user/group"
date: 2006-11-27
forum: Networking &amp; Wireless
---

### Post by gushy on 2006-11-27
I've got a Linksys NSLU2 and I'm mounting a share on it from my server using CIFS.

The problem is that even though I am specifying uid=root and gid=root, it's mounting the directory as owned by one of my users, and the group is one of my user groups.

I think this has something to do with extended attributes, and therefore unix extensions must be on in the samba config on the NSLU2.  As I can't change that I need to be able to override / ignore those attributes when mounting the drive.

Anyone know of a solution?

Thanks,

---

