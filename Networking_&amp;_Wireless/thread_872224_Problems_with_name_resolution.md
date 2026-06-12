---
title: "Problems with name resolution"
date: 2008-07-27
forum: Networking &amp; Wireless
---

### Post by grenadeguy187 on 2008-07-27
I have recently switched to Ubuntu. I used to be a Fedora user, so I understand linux. I have installed samba and the client, but name resolution doesn't quite work. I want to be able to ping a Fedora 9 box named "hoster". I can ping  the ubuntu machine itself from Fedora, but I can't ping back. I am running Ubuntu 8, and help will be appreciated.

---

### Post by Iowan on 2008-07-28
Just a few (feeble) ideas.  Do you have WINS support enabled?  Check info on nsswitch.conf.

---

### Post by grenadeguy187 on 2008-07-29
Here is my nsswitch.conf:

```
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
```

Thanks for the help!

---

