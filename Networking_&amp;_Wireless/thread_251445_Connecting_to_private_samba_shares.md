---
title: "Connecting to private samba shares"
date: 2006-09-05
forum: Networking &amp; Wireless
---

### Post by pwrstick on 2006-09-05
Hello,

I have two computers in server mode that need to be hidden from everyone else but can see eachother's shares.

I've successfully installed samba on both machines, and I think I have the smb.conf files set up correctly:

```
[Cottage External]
path = "/mnt/external"
valid users = backup
available = yes
browseable = no
public = no
writable = yes
```

My goal is to have a hard drive on each server shared with the other server, but with no one else.

Now I don't know how to connect via samba at command line.  I think smbclient is used but I'm not sure in what manner.

Links or code snippets are greatly appreciated!

---

### Post by pwrstick on 2006-09-05
I basically followed this thread:
[http://www.ubuntuforums.org/showthread.php?t=248656]("http://www.ubuntuforums.org/showthread.php?t=248656")

The samba shares are still private and, I believe I added samba users (not sure).  But my fstab now mounts over smbfs and seems to work just fine.

//192.x.x.x/share_name /mount_dir smbfs username=bleh,password=bleh,dmask=777,lmask=777,auto 0 0

---

