---
title: "Looking to learn why my Samba config requires user to be in root"
date: 2009-07-09
forum: New to Ubuntu
---

### Post by filemorf on 2009-07-09
Hello,

I have just migrated a working Samba smb.conf to new server, post migration the users need to be in the root group to be allow access.

When following the steps in [http://us5.samba.org/samba/docs/man/Samba-HOWTO-Collection/diagnosis.html](http://us5.samba.org/samba/docs/man/Samba-HOWTO-Collection/diagnosis.html) to diagnose I get the following error when trying:

```
smbclient //server-name/testshare -Uusername

tree connect failed: NT_STATUS_BAD_NETWORK_NAME
```I can sucessfully use smbclient -L //server-name and if I add the user to root group then the user can connect. I am performing the smbclient commands on the same Sambe server.

I did not want to burden with verbose info dump, will glady provide more info.
Samba version 3.0.28-0.el5.8

Dave 
a.k.a filemorf

---

### Post by tarps87 on 2009-07-15
What are the permissions on the folder on the server?

---

