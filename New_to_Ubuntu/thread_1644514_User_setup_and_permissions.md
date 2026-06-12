---
title: "User setup and permissions"
date: 2010-12-13
forum: New to Ubuntu
---

### Post by sidmaster1 on 2010-12-13
User accounts question?
I have 2 accounts setup in Ubuntu 10.04 LTS, one with administrator permissions, and one as a standard user w/o admin permissions. I use the standard account for normal use.

Question:
Can I add admin permissions to the standard user account w/o causing problems with file permissions or something?

AND, the first account I setup during install was this admin account, does that make it my root account?

Thanks!

---

### Post by MrFaler on 2010-12-13
Your admin account is part of the group that is allowed to use sudo. That enables it to run certain commands or programs as superuser. You can give your normal user sudo privileges by adding him to the sudoers file:

```
sudo adduser username admin
```

will suffice. If you want to edit the sudoers file yourself take a look at this webpage: [http://benaiah41.wordpress.com/2008/08/15/37/]("http://benaiah41.wordpress.com/2008/08/15/37/")

Your admin account isn't the root account. The root account isn't availabe *by default* on Ubuntu.

---

### Post by sidmaster1 on 2010-12-13
> **MrFaler said:**
> Your admin account is part of the group that is allowed to use sudo. That enables it to run certain commands or programs as superuser. You can give your normal user sudo privileges by adding him to the sudoers file:

```
sudo adduser username admin
```

will suffice. If you want to edit the sudoers file yourself take a look at this webpage: [http://benaiah41.wordpress.com/2008/08/15/37/]("http://benaiah41.wordpress.com/2008/08/15/37/")

Your admin account isn't the root account. The root account isn't availabe *by default* on Ubuntu.
Thanks that answers my question. Can you tell me if the original account that I setup when installing is my root account? Thanks Again!

---

### Post by oldos2er on 2010-12-13
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

The root account itself is disabled in Ubuntu, as was mentioned. But your user account can gain root privileges using 'sudo', as long as your user is in the admin group.

---

### Post by sidmaster1 on 2010-12-13
Thanks a lot for the help. That solved my problem in duplicate.

---

### Post by oldos2er on 2010-12-13
You're welcome.

---

