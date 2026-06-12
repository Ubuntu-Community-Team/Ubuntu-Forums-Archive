---
title: "Forcing group on samba share ?"
date: 2007-12-28
forum: Networking &amp; Wireless
---

### Post by erland on 2007-12-28
In previous Ubuntu releases I have been able to have a samba smb.conf file that defines a "force group" attribute to force all files created from the client to get a specific group.

Now in Gutsy I'm not able to mount that share, it just complains with the following message when mounting:
"can't read superblock"

If I remove the "force group" directive from the smb.conf on the server everything works, but it will obviously not set the goup on newly created file.

The share in smb.conf looks like this:
```

[video]
   comment = Video files
   path = /mnt/video
   valid users = erland
   force group = mythtv
   browseable = yes
   read only = No
   create mask = 0660
   directory mask = 0770
   guest ok = no
   printable = no

```

It seems to be server related, because I can't mount the share on a Gutsy server from a Dapper client. 

Mounting shares on the Dapper server from a  Gutsy client works perfectly and the group is in this case also set.

Does anyone have any clue how to solve this ?

---

