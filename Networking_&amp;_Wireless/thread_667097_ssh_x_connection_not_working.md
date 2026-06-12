---
title: "ssh x connection not working"
date: 2008-01-14
forum: Networking &amp; Wireless
---

### Post by kentpend on 2008-01-14
I'm trying to configure x forwarding through ssh, but am consistently getting the same error message.

```
/usr/bin/X11/xauth:  /home/scott/.Xauthority not writable, changes will be ignored

```
appears when I first log in, and
```
X11 connection rejected because of wrong authentication.
X connection to localhost:10.0 broken (explicit kill or server shutdown).

```
does when I try to run an application that needs an x connection.

I've tried installing xauth, but that was already installed.
/etc/ssh/sshd_config already had
```

X11Forwarding yes
X11DisplayOffset 10

```
in it, 

and I added
```
X11UseLocalhost yes
```

Any ideas on what the problem is?

---

