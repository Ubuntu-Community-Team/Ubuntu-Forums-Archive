---
title: "issues this morning on my kubuntu 10.10"
date: 2011-01-03
forum: New to Ubuntu
---

### Post by nnamdi on 2011-01-03
i tried login into my computer this morning then it ran a check disk and gave errors then i rebooted and ran recovery mode from grub after which the computer booted but i noticed it did not enable some thing like my sound and co. but when ever i login i get this error message

> 

warning cannpt open console kit session: unable to opensession: cannot launch daemon file not found or permission invalid.



please how do i tackle all this issues thank you

---

### Post by Zorael on 2011-01-03
You could try and force all files in your home directory to be owned by you, I guess. They should all be to begin with, I think. Might be a few exceptions.

I have no idea what could cause this though.
```
$ sudo chown -Rc *youruser*:*yourgroup* /home/*youruser*
```
Obviously, replace *youruser* and *yourgroup* with the name of your user and your group.

In an automated form;
```
$ export GROUP=$(groups | awk '{ print $1 }'); export MYUSER=$USER; export MYHOME=$HOME; sudo chown -Rc $MYUSER:$GROUP $MYHOME && unset GROUP MYUSER MYHOME
```

---

