---
title: "Unblocking Port 22"
date: 2007-09-30
forum: Networking &amp; Wireless
---

### Post by markk1994 on 2007-09-30
For SSH I need to unblock port 22 anybody  know how to?

---

### Post by noob12 on 2007-09-30
It depends on whether you are using firestarter or iptables directly (or something else).

Note that Ubuntu desktop doesn't come with the SSH server installed by default.  So if you're trouble connecting by SSH to an Ubuntu host, first make sure you have installed the **openssh-server** package.

This will do that:
```

sudo aptitude install openssh-server

```

---

### Post by scruff on 2007-09-30
Not sure if installing sshd adds it to the default runlevel or not. If you find ssh server not running after a reboot, open a terminal and type:

sudo update-rc.d ssh default


-Scruff

---

