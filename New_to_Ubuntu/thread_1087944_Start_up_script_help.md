---
title: "Start up script? help"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by ericeclifford on 2009-03-05
I do this 

root@eric:~/live# update-rc.d edit/etc/init.d/FOO start 51 S .
update-rc.d: /etc/init.d/edit/etc/init.d/FOO: file does not exist
root@eric:~/live# update-rc.d edit/etc/init.d/FOO
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults|multiuser [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
		-n: not really
		-f: force



BTW The edit foldier is considered the root because I am customizing a cd?

---

### Post by Bodsda on 2009-03-05
try putting a slash before the edit

```

/edit/etc/init.d/FOO

```

---

