---
title: "Can´t set password for MySQL"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by G!zZm0 on 2008-12-30
I tried setting up my password using this command:

*mysqladmin -u root password yourrootsqlpassword*

But I get this error:

[I]mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'
[/I]

Can anyone help me???

---

### Post by Titan8990 on 2008-12-30
You should have set the root password up when you first installed mysql.


Try:

sudo dpkg-reconfigure mysql-server

---

### Post by Nepherte on 2008-12-30
> **G!zZm0 said:**
> I tried setting up my password using this command:

*mysqladmin -u root password yourrootsqlpassword*
[/I]
That's for logging in to mysql with the root user and the supplied password, not for setting the password.

---

### Post by stussy on 2008-12-30
I have the same problem, any success G!zZm0 ?

---

### Post by cariboo on 2008-12-30
Have you tried:

```
mysql -u root -p
```

When prompted use the password you set when installing mysql.

If you don't remember what the password was you can run:

```
sudo dpkg-reconfigure mysql-server-5.0
```

This will bring up the password dialog screen.

Jim

---

### Post by stussy on 2008-12-30
Thank you cariboo907

---

