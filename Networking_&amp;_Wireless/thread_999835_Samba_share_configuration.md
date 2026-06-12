---
title: "Samba share configuration"
date: 2008-12-02
forum: Networking &amp; Wireless
---

### Post by Rolaco on 2008-12-02
Hi,

I'm trying to configure my Samba shares in the following way:

Shares:
Folder1
Folder2
Folder3
Folder4

Users:
user1
user2
user3
user4

Folder1 should be accessed with r/w permissions by user1 and user4, access should be forbidden to user2 and user3

Folder2 should be accessed with r/w permissions by user1 and read-only by other users

Folder3 accessed by user1 and user2 only

Folder4 accessed by user1 and user3 only

I've tried a lot of different ways but either I get folder1 to be accessed by all or by none!

Can anyone help?

Thanks,

Rolaco

---

### Post by Iowan on 2008-12-02
Post your */etc/samba/smb.conf*.

---

### Post by bab1 on 2008-12-02
> **Rolaco said:**
> Hi,

I'm trying to configure my Samba shares in the following way:

Shares:
Folder1
Folder2
Folder3
Folder4

Users:
user1
user2
user3
user4

Folder1 should be accessed with r/w permissions by user1 and user4, access should be forbidden to user2 and user3

Folder2 should be accessed with r/w permissions by user1 and read-only by other users

Folder3 accessed by user1 and user2 only

Folder4 accessed by user1 and user3 only

I've tried a lot of different ways but either I get folder1 to be accessed by all or by none!

Can anyone help?

Thanks,

Rolaco

In your share definitions use the "valid user" directive to limit who can access the folder.  You can use "create mask" directives to insure proper file permissions any files or directories created in the folder.

See [**here**]("http://us1.samba.org/samba/docs/") for specific information

---

