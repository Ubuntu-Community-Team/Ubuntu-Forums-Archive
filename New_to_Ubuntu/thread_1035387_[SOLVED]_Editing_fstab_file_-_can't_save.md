---
title: "[SOLVED] Editing fstab file - can't save"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by jrsc109 on 2009-01-09
Hi

I am trying to save a change to the fstab file, but I am told "Error while moving fstab" - Permission Denied.

How do i give myself the rights to amend.  I could do this on 8.04, but now I've upgraded I don't seem to be able to do this.

Thanks

---

### Post by taurus on 2009-01-09
You need to edit it with root privilege.

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by tech9 on 2009-01-09
> **jrsc109 said:**
> Hi

I am trying to save a change to the fstab file, but I am told "Error while moving fstab" - Permission Denied.

How do i give myself the rights to amend.  I could do this on 8.04, but now I've upgraded I don't seem to be able to do this.

Thanks

try this....

hit Alt-F2

type in gksu nautilus

Then browse to your fstab file, open, edit - now you should be able to save it - because you have root privileges with gksu

hope this helps,

T9

---

### Post by jrsc109 on 2009-01-09
That certainly let me save - thank you.  Now to check the changes have the desired effect.  Many thanks.

---

### Post by tech9 on 2009-01-12
> **jrsc109 said:**
> That certainly let me save - thank you.  Now to check the changes have the desired effect.  Many thanks.

your welcome! :)

---

