---
title: "log file viewer problem"
date: 2011-09-02
forum: New to Ubuntu
---

### Post by werty2010 on 2011-09-02
since a while ago whenever i open "log file viewer" on the top i have a message:

```

/var/log/btmp
You don't have enough permissions to read the file.

```what is it for?
how can i fix it?

---

### Post by Azdour on 2011-09-02
Hi,

If I understand correctly the btmp is a log of failed login attempts. The log is not readable to everyone which is why the log viewer cannot open it.

It's a known bug:

[https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/374320](https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/374320)

---

