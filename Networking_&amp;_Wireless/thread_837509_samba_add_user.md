---
title: "samba add user"
date: 2008-06-22
forum: Networking &amp; Wireless
---

### Post by Mr. Win on 2008-06-22
I'm trying to create a user account for samba so that I can connect to it via Windows XP.  How do I do this?

I'm on 07.04

---

### Post by sisco311 on 2008-06-22
To setup a password for your ubuntu user:
```
sudo smbpasswd -a your-user-name
```

To create a new samba user:
```
sudo useradd username
sudo smbpasswd -a username
```

---

### Post by dmizer on 2008-06-23
you're probably better off adding samba users that don't have shell access like so:
```
sudo useradd -s /bin/true username
sudo smbpasswd -L -a username
sudo smbpasswd -L -e username
```

---

