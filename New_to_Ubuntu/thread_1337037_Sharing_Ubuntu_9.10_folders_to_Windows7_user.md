---
title: "Sharing Ubuntu 9.10 folders to Windows7 user"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by khaosgott on 2009-11-25
Hi guys/girls,

im trying to configure a shared folder on Ubuntu machine for Win7 user. I can get to the login window, but no luck actually logging in.

the workgroup name is default, basically it should work.

what do I do wrong?

Thanks in advance,
K.

:popcorn:

---

### Post by braete on 2009-11-25
you could tick guest access in folder properties or check if permissions are ok

---

### Post by khaosgott on 2009-11-25
Hi braete, 
thanks for the reply.

even after ticking "guest access" the problem wont go away.

---

### Post by ukripper on 2009-11-25
ok you can try this then:

this will install samba server if not already installed:
```
sudo apt-get install samba
```

then just run these commands:
```
sudo /etc/init.d/samba stop
```

Use your username to give access for samba:
```
sudo smbpasswd -L -a **your_username**
```
```
sudo smbpasswd -L -e **your_username**
```

now start samba service:
```
sudo /etc/init.d/samba start
```

Go to windows 7 and look for share you created and access it by using the username you just entered.

---

