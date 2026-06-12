---
title: "Samba Shared Folders"
date: 2007-12-09
forum: Networking &amp; Wireless
---

### Post by dj_penguin on 2007-12-09
Hi all,

I have a small home network setup with a few users and three computers, one using Gutsy and the other two on WinXP.  I've created shared folders in some of the user's home directories and can access them if I login as that user using samba.  However, if I login as a different user I cannot access the shares and samba says that it can' mount the shares.  I want each user to have their own share but for other users to be able to browse the shares.  I've created a new group called netusers and added the networked users to this group.  However, I still get the same message that samba is unable to mount the share unless I login as the user who owns the share.  An example of the shared section in my smb.conf file is shown below;

```

[DanielPublic]
path = /home/daniel/DanielPublic
valid users = @netusers
available = yes
browsable = yes
public = yes
writable = no
create mask = 0765

```

Any advice would be much appreciated.

**[COLOR="Red"][SOLVED][/COLOR]**

---

