---
title: "uid and gid for NFS"
date: 2006-08-21
forum: Networking &amp; Wireless
---

### Post by microserf on 2006-08-21
Hi

I have an account on a desktop machine running Ubuntu and I need my home directory to be on an NFS filesystem. The directory and all my files exists on the NFS system, I just need to be able to read and write it from my account on my Ubuntu desktop. I can mount the NFS filesystem OK.

I can create an account on the Ubuntu desktop with the correct uid (for the NFS dir), but I need to set the gid of my user account to the correct value. However, the gid value in question (101) is already in use by my Ubuntu desktop. 

So, what I'd like to do is change the conflicting gid on the Ubuntu desktop to a different number, to free up the required gid. I'd then create a new gid of 101 and then assign it to my account on the Ubuntu box. Can anyone tell me how to do this cleanly?

Alternatively, I've read that I could use ugidd to do the required mapping. However I can't find any documentation on how to do this (that makes any sense to me). If this is the better approach, can you point me to a "for idiots" tutorial?

One constraint is that I have no control over the NFS server---that's out of my hands. I have little idea of what its running.

Thanks in advance

C

---

### Post by ohgod on 2006-08-21
You can change the group id of a group with the groupmod command:

```
sudo groupmod -g 150 dhcp
```

The above command would change the group id of the dhcp group to 150 (that's the group that has an id of 101 on my Ubuntu box).

**I should point out that while I've run this command on my box, I don't use the dhcp client so I'm not sure if this will cause you any problems.  Files that have a group ownership of 101 before you change group ids will need to have their ownership updated after you change the dhcp group id to something else.**

---

### Post by microserf on 2006-08-22
OK, thanks ohgod.

---

