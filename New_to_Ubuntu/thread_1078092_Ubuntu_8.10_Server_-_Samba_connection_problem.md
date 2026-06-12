---
title: "Ubuntu 8.10 Server - Samba connection problem"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by Hunterjelly on 2009-02-23
When I try to connect to my Samba share I get this error:

> \\ubuntu\share is not accessible. You might not have permission to use this network resource. Contact the administrator of the server to find out if you have access permissions.

The network path was not found.

Connecting from an XP x64 system.

My smb.conf is as follows:

> [share]
 comment = Storage
 path = /mnt/Storage
 browsable = yes
 guest ok = no
 read only = no
 create mask = 0755

with security set to user.

I've used smbpasswd to add the "ftp" user that I intend to use for connecting with. I added the ftp user to the "sambashare" group (the only other group it is in is "ftp").

I;ve tried a lot of stuff, and I'm out of ideas. I need help!

---

### Post by Hunterjelly on 2009-02-23
I ended getting help from a friend, heres what fixed it:
> 
[all]
   comment = All
   path = /mnt/storage/ftp
   browseable = yes
   read only = no
   guest ok = no

Edit: Looks like it was pretty much just a spelling mistake on browseable.

---

