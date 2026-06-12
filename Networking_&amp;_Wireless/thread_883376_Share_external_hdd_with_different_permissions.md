---
title: "Share external hdd with different permissions"
date: 2008-08-07
forum: Networking &amp; Wireless
---

### Post by AncientPC on 2008-08-07
I have a USB hdd hooked up to my Ubuntu box that I want to share over the network.  It is currently formatted to NTFS and mounted into /media/mybook/ (thus 777 permissions).

What I want is read only to public (over network), and writable only by me.

Now in the /etc/samba/smb.conf, do I create two entries that conflict with each other?

Currently I have:

```
[mybook]
path = /media/mybook
browseable = yes
read only = no
guest ok = no
create mask = 0777
directory mask = 0777
#force user = me
#force group = me
#above commented out because they don't seem to work

```

---

### Post by AncientPC on 2008-08-19
bump?

---

### Post by sea_monkey987 on 2008-08-19
there are two ways you can do this:  

1. create one share with two valid users using the "valid users = " option that have the appropriate permissions for /media/mybook.  777 permissions will not work.  you will need 755 or 644 permissions.
- or -
2.create two different shares, marking one of them as read only.  I haven't used this second method so I'm not sure if samba will force read-only access even though your folder has 777 permissions.

---

