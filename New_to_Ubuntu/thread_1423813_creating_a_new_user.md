---
title: "creating a new user"
date: 2010-03-07
forum: New to Ubuntu
---

### Post by 1991sudarshan on 2010-03-07
i deleted all the user by mistake. and how to login as root in kubuntu and create a new account???

---

### Post by PX9 on 2010-03-07
I would run live CD, chroot to the system root partition and run useradd.

---

### Post by inobe on 2010-03-07
start the computer, hit escape during grub countdown, select recovery mode, choose command line.

run

```
adduser username
```

replace **username** with actual user name.

to assign new password run

```
passwd username
```

you will need to enter a password twice, you may not be able to see the password when typed.

remember to replace **username** with actual user name.

---

