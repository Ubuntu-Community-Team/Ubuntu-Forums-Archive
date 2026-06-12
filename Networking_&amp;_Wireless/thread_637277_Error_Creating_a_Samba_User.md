---
title: "Error Creating a Samba User"
date: 2007-12-10
forum: Networking &amp; Wireless
---

### Post by ususim on 2007-12-10
hi there,

  i've already created a user in Administration but having problem to create a samba user. the following are the details:

[INDENT]ususim@ususim-ubuntu:~$ sudo smbpasswd -a KC[/INDENT]
[INDENT]Can't load /etc/samba/smb.conf - run testparm to debug it[/INDENT]

  what's wrong with that? and how to run test parm? Please guide me.

  Thanks in advance

---

### Post by jetsam on 2007-12-10
```
testparm /etc/samba/smb.conf
```

..should run testparm.  Testparm is a syntax checking utility for smb.conf that comes with samba.  Hopefully it will give you some useful output regarding what the problem is in your smb.conf.  Smbpasswd seems unhappy with it...

---

