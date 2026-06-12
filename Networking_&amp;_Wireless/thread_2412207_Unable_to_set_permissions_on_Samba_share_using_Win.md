---
title: "Unable to set permissions on Samba share using Windows ACL's"
date: 2019-02-09
forum: Networking &amp; Wireless
---

### Post by brownatron on 2019-02-09
Hi All,

I'm relatively new to Linux having been a Windows guy for most of my life (for all my sins).

I've recently installed Ubuntu 18.04 on a machine and joined it to my Windows domain and I am using the Ubuntu box to share out a bunch of stuff using Samba.
I've followed [the guide on the Samba Wiki]("https://wiki.samba.org/index.php/Setting_up_a_Share_Using_Windows_ACLs") about configuring Windows ACL's but it doesn't seem to be working as I can't modify the permissions on the share :(
The error I get on Windows is: > Failed to enumerate objects in the container. Access is denied.

I can browse to the share and even create files/folders in it I just cannot set any permissions on it :(

I'd really appreciate any help you can give on this one.

I've tried to include everything I think will be useful in debugging this but please let me know if you need anything else. :) (have substituted my actual domain for MYDOMAIN.COM in all the below examples)

smb.conf:
```

[global]
        security = ads
        realm = MYDOMAIN.COM
# If the system doesn't find the domain controller automatically, you may need the following line
#        password server = 192.168.1.25
# note that workgroup is the 'short' domain name
        workgroup = MYDOMAIN
#       winbind separator = +
        idmap uid = 10000-20000
        idmap gid = 10000-20000
        winbind enum users = yes
        winbind enum groups = yes
        template homedir = /home/%D/%U
        template shell = /bin/bash
        client use spnego = yes
        client ntlmv2 auth = yes
        encrypt passwords = yes
        winbind use default domain = yes
        restrict anonymous = 2


[testshare]
        path = /zstorage/testshare/
        read only = no
        vfs objects = acl_xattr streams_xattr
        map acl inherit = yes
        store dos attributes = yes
        inherit permissions = yes

```

Result from getfacl:
```

root@mekanenko:/home/administrator# getfacl /zstorage/testshare/
getfacl: Removing leading '/' from absolute path names
# file: zstorage/testshare/
# owner: root
# group: domain\040admins
user::rwx
group::rwx
other::---

```

Sharing from Windows - trying to add the "TestPerms" group to the share:
[IMG]https://img.photobucket.com/albums/v675/steveori/perms_zpswjwlmqnk.png[/IMG]

This is using Windows Server 2016.

---

### Post by brownatron on 2019-02-09
Solved!

I hate to be "that guy" who solves his own question but after an afternoon of troubleshooting I've worked out that it was actually down to my filesystem not Samba.

I'm using ZFS as the underlying storage for the server and I forgot that ACL support isn't enable by default /facepalm

so by running the following few commands:
```
root@mekanenko:~# zfs set acltype=posixacl zstorage/testshare
root@mekanenko:~# zfs set aclinherit=passthrough zstorage/testshare
root@mekanenko:~# zfs set xattr=sa zstorage/testshare

```

I was able to get the file permissions working.
Hopefully this helps someone else in the future.

---

### Post by albert41 on 2020-01-26
Bro just wanted to say thank you so much had this issue was going crazy

---

### Post by wildmanne39 on 2020-01-26
Old thread back to sleep.

---

