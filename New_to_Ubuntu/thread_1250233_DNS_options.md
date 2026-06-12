---
title: "DNS options"
date: 2009-08-26
forum: New to Ubuntu
---

### Post by mbaybarsk on 2009-08-26
Hello again,
 
How do i change my DNS address?
 
:confused:

---

### Post by x33a on 2009-08-26
open /etc/resolv.conf with your favourite text editor (as root).

example:
```
gksudo gedit /etc/resolv.conf
```
add the dns servers in the following format.

example for opendns servers:
```
nameserver 208.67.222.222
nameserver 208.67.220.220
```

---

