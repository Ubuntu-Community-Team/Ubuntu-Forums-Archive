---
title: "different user permissions in Samba"
date: 2008-08-29
forum: Networking &amp; Wireless
---

### Post by jjohns63 on 2008-08-29
I'm trying to make multiple users with different access permissions to a samba share.

I currently have 2 UNIX users:
user
public

I have added them to samba using ```
smbpasswd -a <username>
```

My current directory permissions are set to 
```
drwxr-x---  11 user   public
```

however the "public" user is still able to write to the directory. This is not what I want, I want the user "user" to be the only user with permission to write. I saw in a couple places that setting the sticky bit would cause Samba to follow the UNIX permissions but this did not work. Anyone have any suggestions?

---

