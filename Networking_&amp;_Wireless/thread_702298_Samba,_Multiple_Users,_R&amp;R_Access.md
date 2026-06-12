---
title: "Samba, Multiple Users, R&amp;R Access?"
date: 2008-02-20
forum: Networking &amp; Wireless
---

### Post by distortedecho on 2008-02-20
Hi.

I was wondering if someone could advise me on the following.

I have set up an NFS Share using Samba.
The directory is hidden, but at the moment is open to all users.

i want to make this more secure.

So I have tired adding Users and granting them the rights etc etc.
This auto authenticates when the user access the share from their own Windows PC.
I faced a problem where the user could create folders on the root of the share. But not in sub directories.

Now,I can allow the permissions. I've even thought of using chmod 777 *
But the issue I have is that the folders/files created are only accessible by the user that created them. 

How can I have multiple users to have the same access rights as each other?

---

### Post by ruy_lopez on 2008-02-20
Create a group <share_group>. Add your users to the group. Then add this to smb.conf:

```
force group = <share_group>
```

Then you can adjust your permissions to control the access the group users have. The owner will still own the file/folder.

---

### Post by distortedecho on 2008-02-24
Thank you!

---

