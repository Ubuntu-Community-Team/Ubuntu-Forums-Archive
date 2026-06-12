---
title: "NFS help, permissions"
date: 2008-07-26
forum: Networking &amp; Wireless
---

### Post by tobias_84 on 2008-07-26
Hi all.

Got NFS to work directly but the problem is when I want to create files from the client. If I do 'ls -l' on the client it seem correct but it's the wrong user and group on the server side.

Exempel:
```

//client-user = a (non_root)
//server-user = b (non_root)


a@client:nfs_mount/path/folder$ mkdir test
a@client:nfs_mount/path/folder$ ls -l
drwxr-xr-x  2 a   a   4096 2008-07-05 13:55 test

b@server:nfs_share/path/folder$ ls -l
drwxr-xr-x  2 b   b   4096 2008-07-05 13:55 test

```

The user B doesn't exist on the client, only at the server but user A does exist on both sides.


/etc/passwd
On client:
```

a:x:1000:1000:a,,,:/home/a:/bin/bash

```

On server:
```

b:x:1000:1000:b,,,:/home/b:/bin/bash
a:x:1007:1007:a,,,:/home/a:/bin/bash

```


Is there a way to specify in /etc/exports witch user that owns it?

/share_a-folder x.x.x.x/x(rw,no_root_squash,async)
/share_b-folder x.x.x.x/x(rw,no_root_squash,async)
/share_c-folder x.x.x.x/x(rw,no_root_squash,async)

so if any user adds something to share_b-folder user b is the owner?



Thanx for any help!

---

