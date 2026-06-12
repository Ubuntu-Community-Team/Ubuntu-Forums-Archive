---
title: "Cannot remove a device file"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by sergiodlc on 2009-11-09
Hi:
I'm rying to delete a file as root but I get 
```
>> sudo rm -fr /opt/ltsp/_i386/
rm: cannot remove `/opt/ltsp/_i386/dev/pts/0': Operation not permitted
>> ls -lh /opt/ltsp/_i386/dev/pts/
crw--w---- 1 pepitos tty 136, 0 2009-11-09 16:10 0

```

Any idea?

---

### Post by teward on 2009-11-09
i think the 0 is the hard drive you're using.  but I'm not sure.  killing it might nuke your system though, so thats probably why its denying you from deleting it.

---

### Post by egalvan on 2009-11-09
One possible explanation is that it is locked by another user.

ltsp stands for Linux Terminal Server Project.

Which implies other users may exist.

---

### Post by The Cog on 2009-11-09
The c in the permissions means it is a character device, not a normal file. Not that I know how to get rid of it. Perhaps do it from a live CD?

---

