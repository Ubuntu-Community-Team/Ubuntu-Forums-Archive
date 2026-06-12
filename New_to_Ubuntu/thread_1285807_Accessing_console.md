---
title: "Accessing console"
date: 2009-10-08
forum: New to Ubuntu
---

### Post by lfpc2009 on 2009-10-08
Dear friends,

I'm a beginner in Ubuntu, and Linux. Anyway, my question is the following: I've tried to used the console and after running the command -su it asks me for a password. I've never set a  root password when I installed this distro, so I've tried to use the common password -root but it doesn't recognize it.

What shall I do?

Thanks in advance.

---

### Post by Peter09 on 2009-10-08
In Ubuntu you cannot login as root, you use sudo in the command shell to gain root privilege e.g

```
sudo cd /etc/<a directory>
```

Normally the user that is installed during the O/S installation is an admin user and their password will also work for authentication to gain privilege.

---

### Post by corncob on 2009-10-08
Its asking for your password.  Root doesn't have one.

---

