---
title: "Issue with sharing NTFS from Ubuntu to Windows client"
date: 2016-11-15
forum: Networking &amp; Wireless
---

### Post by seejay3 on 2016-11-15
Hello all,

I read and tried a lot of things I found here but still I am facing the issue that I cannot change or create any data when I am connected to the shared drive from my windows machine.

When I try to add the network drive within Windows with a wrong user
 -> Access denied -> Correct

When I try to add the network drive within Windows with my user seejay (using windows login data, same password as linux user)
 -> Access granted -> Correct
-> See data and browse through them -> works
-> Open data -> works
-> Add new data -> does not work -> My issue
-> Change excisting data -> does not work either -> My issue

If I try to change the file name I get the following error:
You require permission from Unix User\pi to make changes to this file
even when I change the fstab to uid=1001 (my ID, seejay, see below) I get the error but "from user bananapi\seejay".

If I try to change a folder name I get this error message
The action can't be completed because the folder or a file in it is open in another program

Creating a file:
You need permission to perform this action

Even when I connect with different credentials bananapi\seejay I get these errors.

Here is what I've done so far:

Created two users
```

id seejay
uid=1001(seejay) gid=1001(seejay) groups=1001(seejay),27(sudo),1003(networkshares)

```

```

id nadine
uid=1002(nadine) gid=1002(nadine) groups=1002(nadine),1003(networkshares)


```



Added them to a new group networkshares
```

getent group networkshares
networkshares:x:1003:seejay,nadine

```

Created an entry in FSTAB:
```
UUID=xxxxxxxxxxxx   /media/shared   ntfs    defaults,uid=1000,gid=1003,umask=0002   0       0
```

Changed the permission of the mount point
```

ls -la /media/shared
total 12
drwxrwxr-x 1 pi   networkshares 4096 Nov 14 16:46 .
drwxrwxrwx 4 root networkshares 4096 Nov  9 15:52 ..
drwxrwxr-x 1 pi   networkshares 4096 Sep 27 03:27 shares

```

and 
```
ls -la /media/shared/sharestotal 132
drwxrwxr-x 1 pi networkshares  4096 Sep 27 03:27 .
drwxrwxr-x 1 pi networkshares  4096 Nov 14 16:46 ..
drwxrwxr-x 1 pi networkshares  4096 Sep 29 07:21 folder1
drwxrwxr-x 1 pi networkshares  4096 Aug 18 09:12 folder2
drwxrwxr-x 1 pi networkshares 24576 Oct 16 07:16 folder3
drwxrwxr-x 1 pi networkshares     0 Aug  6 10:31 folder4
drwxrwxr-x 1 pi networkshares     0 Sep  5 04:22 folder5
drwxrwxr-x 1 pi networkshares  4096 Aug  6 09:04 folder6
drwxrwxr-x 1 pi networkshares 77824 Aug 19 12:07 folder7
drwxrwxr-x 1 pi networkshares  4096 Oct 16 07:31 folder8
drwxrwxr-x 1 pi networkshares     0 Aug  6 09:04 folder9
drwxrwxr-x 1 pi networkshares  8192 Sep 29 10:39 folder10



```


Added this to smb.conf (left all default values as they were)
```

[shares]
comment = Filebackup
path = /media/shared/shares
valid users = @networkshares
read only = no
writable = yes
browseable = yes
create mask = 0755
directory mask = 0755
force group = networkshares
force directory mode = 2775
write list = @networkshares

```

Testparm returns the following
```

testparm -v
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "syslog" option is deprecated
Processing section "[printers]"
Processing section "[print$]"
Processing section "[shares]"
Loaded services file OK.
Server role: ROLE_STANDALONE
....
[shares]
        comment = Filebackup
        path = /media/shared/shares
        valid users = @networkshares
        write list = @networkshares
        force group = networkshares
        group = networkshares
        read only = No
        create mask = 0755
        force directory mode = 02775


```

I hope you can help me to get this fixed.
Previously I used OMV and used the NTFS share with it and it worked, so I now it is possible, but I don't know where the issue is.

Thanks already in advance
seejay

---

### Post by slickymaster on 2016-11-15
*Thread moved to **Networking & Wireless**.*

---

### Post by seejay3 on 2016-11-18
anyone an idea what I should check?

---

### Post by seejay3 on 2016-11-18
after checking now all over again, I found out, that the reason is not the share or the file permisson but rather that the ntfs hard disks are mounted read only after changing from OMV to Ubuntu.
So I have to check in this direction.

[solved]
after installing ntfs-3g it and remounting everything it works. Even though I did not change anything in fstba
[COLOR=#111111][FONT=Consolas]sudo apt-get install ntfs-3g[/FONT][/COLOR]

---

