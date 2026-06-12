---
title: "changed username cant login"
date: 2009-09-29
forum: New to Ubuntu
---

### Post by amarumayo on 2009-09-29
I am trying to help out a friend.  She has changed her username and now she cannot login.  Ubuntu will no longer recognize her old username/password nor will it recognize her new one.  Any fixes to this?
Thanks,

---

### Post by diesch on 2009-09-29
How did she change her username? With the usual tools you can not change the username but have to create a new user and remove the old one (but you can edit /etc/passwd and /etc/shadow by hand).

---

### Post by Iowan on 2009-09-29
Hopefully, [this]("http://www.psychocats.net/ubuntu/fixsudo") one can help ... somehow.

---

### Post by cariboo on 2009-09-29
It probably would be faster to restart in recovery mode and at the prompt type:

```
useradd -m -g adm dialout cdrom plugdev lpadmin admin <username>
```

then:

```
password <username>
```

---

