---
title: "Setting Permissions for USB HD"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by Dave B on 2008-12-05
im trying to set the permissions for an external USB HDD 

can someone please help?

Dave

---

### Post by handydan918 on 2008-12-05
yes.

---

### Post by nandemonai on 2008-12-05
Really depends on what your actually trying to accomplish.

Is the drive mounted? Can you not access it? etc

Generally you can set permissions on a drive by using chmod/chown in terminal or by right clicking the mount point in the gui and adjusting the permissions that way.

Of course it helps if the drive is mounted in the first place. ;)

---

### Post by kd7swh on 2008-12-05
Assuming its mounted, you can use chmod to change file permissions. 

```
man chmod
```

should explain the usage of chmod.

sudo chmod +x foo.sh

makes foo.sh executable and so forth.

or you can just right click on a file in nautilus and change the permissions in the properties tab.

---

### Post by kd7swh on 2008-12-05
> **handydan918 said:**
> yes.

This doesn't help anyone, please don't waste peoples time.

---

### Post by psusi on 2008-12-05
> **kd7swh said:**
> This doesn't help anyone, please don't waste peoples time.

I got a good laugh out of it.  Ask a vague question, get a vague answer.

---

