---
title: "read/write problem with samba"
date: 2007-05-14
forum: Networking &amp; Wireless
---

### Post by rickycodie on 2007-05-14
help! i can't write to shared folder with samba. i have  two ubuntu systems and it sees the folders, but i cant write to them, what do i do?

---

### Post by ukripper on 2007-05-15
paste your smb.conf here

---

### Post by rickycodie on 2007-05-15
when i enter sudo gedit smb.conf it comes up with a blank screen!

---

### Post by rickycodie on 2007-05-31
i had to log on as root.

---

### Post by jonallport on 2007-05-31
Probably not Samba, but the filesystem permissions.  If you CHMOD 0777 a test file can you write it?

---

### Post by ukripper on 2007-06-04
type :

```
sudo gedit /etc/samba/smb.conf
```

and find out if you have enabled WINS server and with appropriate permissions.

Or paste your smb.conf here

---

### Post by rickycodie on 2007-06-04
i have the problem solved but thanks for your help.

---

