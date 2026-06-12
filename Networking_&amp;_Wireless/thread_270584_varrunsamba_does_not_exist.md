---
title: "/var/run/samba does not exist"
date: 2006-10-03
forum: Networking &amp; Wireless
---

### Post by mihaisofti on 2006-10-03
I have just installed Ubuntu 606 on i386 architecture, and get the above error when running testparm, the full error being

ERROR: lock directory /var/run/samba does not exist
ERROR: pid directory /var/run/samba does not exist

As a fairly new newbie, I don't know what to do about it.  I can see neither my own shares nor this machine from this machine, or from any other box on the network (a mix of linux and win)

Can anyone point me in the right direction, please?

Mihai

---

### Post by bswilson on 2006-10-03
I would expect to see that error message if either 1) Samba is not installed and configured, or 2) Samba is not running.  You can confirm this with the following command:

```
$ sudo ps -ef |grep smb
```

If you get back nothing, then Samba isn't running.

---

