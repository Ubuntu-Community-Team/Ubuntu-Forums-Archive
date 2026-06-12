---
title: "adding users"
date: 2010-07-17
forum: New to Ubuntu
---

### Post by rburkartjo on 2010-07-17
just had to do a clean install of ubuntu and installed 10.04. having problems adding users. any ideas

---

### Post by wojox on 2010-07-17
Don't know? Have a look [AddUsersHowto]("https://help.ubuntu.com/community/AddUsersHowto")

---

### Post by rburkartjo on 2010-07-17
wo got this what happened had some major problems with linux mint and went back to ubuntu 10.04 how would i fix
ray@ray-desktop:~$ adduser
adduser: Only root may add a user or group to the system.
ray@ray-desktop:~$

---

### Post by wojox on 2010-07-17
```
sudo adduser <username>
```

---

### Post by sisco311 on 2010-07-17
> **rburkartjo said:**
> wo got this what happened had some major problems with linux mint and went back to ubuntu 10.04 how would i fix
ray@ray-desktop:~$ adduser
adduser: Only root may add a user or group to the system.
ray@ray-desktop:~$

Please read the link posted by wojox.

Either use the GUI System > Administration > Users and Groups or run adduser as root:
```
sudo adduser **username**
```

---

### Post by rburkartjo on 2010-07-17
tks guys got it when i reinstalled ubuntu 10.04 went to ext4 and system was a little slow for a while. sometime have no patience/tks

---

