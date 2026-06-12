---
title: "SMBFS / CIFS problems"
date: 2007-02-10
forum: Networking &amp; Wireless
---

### Post by floof on 2007-02-10
Hi all,

My first post on ubuntu forums.

I'm posting because i'm having problems with smbfs and cifs mounts.

I have a home LAN, on which three computers are running plus a Thecus n2100 NAS (by the way, never buy this product, it has very low quality). I have been using pam_mount to mount the NAS on logons with smbfs protocol. It works almost fine, except that the smb client will freeze when multiple processes access the mounted files at the same time. This issue completely freezes nautilus and any other app accessing the share.

I have read that it is a known problem with smbfs, and I have been advised to switch to cifs, which I've done. The problem is, when I switch to cifs, that my uid and gid parameters don't work : the share is mounted with wrong owner. The command I've used to mount is :

mount -t cifs //192.168.1.XXX/share /home/user/share -o user=user, uid=user, gid=user

The mount command succeeds, but when I try to access the share, I realise that it's owner is not that which I asked for :

> ls -l
...
drwxr-xr-x 2 1001 dhcp        0 2007-02-24 13:20 share
...

it's owned by user 1001 group dhcp :shock: 

Why is that so ? why isn't the folder owned by user:user ? I can't manage to understand what happens ](*,) . Any help welcome.

thanks,
Florent

[edit]

I found info on this issue on another post :
[http://www.ubuntuforums.org/showthread.php?t=188027]("http://www.ubuntuforums.org/showthread.php?t=188027")

This did not solve everything, but it got me a bit further.

The share is mounted with proper owner/group, but I can't manage to access the files :
for example :
```

user@host> xmms Mp3/Mills\ Brothers\ -\ Till\ Then.mp3 
Message: device: default
Error id3.c, line 285: fread() failed

```

Also, the files in the share all have the setuid and setgid bit set :
```

 user@host> ls -l
total 279076
-rwxrwSrwt 1 floof floof 2851886 2007-01-07 17:18 DSC_1335.JPG
-rwxrwSrwt 1 floof floof 2406734 2007-01-07 17:18 DSC_1336.JPG
-rwxrwSrwt 1 floof floof 2680759 2007-01-07 17:18 DSC_1337.JPG
-rwxrwSrwt 1 floof floof 2580211 2007-01-07 17:18 DSC_1338.JPG
-rwxrwSrwt 1 floof floof 2643307 2007-01-07 17:18 DSC_1339.JPG
-rwxrwSrwt 1 floof floof 2949917 2007-01-07 17:18 DSC_1340.JPG
-rwxrwSrwt 1 floof floof 2553467 2007-01-07 17:18 DSC_1341.JPG
-rwxrwSrwt 1 floof floof 2564068 2007-01-07 17:18 DSC_1342.JPG
-rwxrwSrwt 1 floof floof 2872360 2007-01-07 17:18 DSC_1343.JPG
-rwxrwSrwt 1 floof floof 3372981 2007-01-07 17:18 DSC_1344.JPG
-rwxrwSrwt 1 floof floof 2090565 2007-01-07 17:18 DSC_1345.JPG

```

how to change this ?

---

### Post by floof on 2007-02-12
Hello,

I got a little further (or not) concerning this issue. I have installed an NFS module on my NAS, so it would export directories. My problem is again concerning files beeing owned by inexistant UIDs. I looked at "man mount" and "man nfs" but unfortunately there does not appear to be any info on how to mount with specific UID.

It is important for m to mount with consistent UID/GID, because share are mounted on session openings for each user, in their home directory.

Any idea anyone ?

Thanks.

---

### Post by LordYama on 2007-02-17
By default, the cifs kernel module is loaded dynamically as required. We need it to load it manually on boot.
[LIST=1]
[*]In **/etc/modules**, add a line that reads *cifs*.
[*]In **/etc/rc.local**, add a line that reads *echo 0 > /proc/fs/cifs/LinuxExtensionsEnabled*. This line needs to be before the *exit 0*
[/LIST]
Since we are turning off support for UNIX filesystem features, things like symlinks will not work. There is a [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/48418") covering this matter.

---

