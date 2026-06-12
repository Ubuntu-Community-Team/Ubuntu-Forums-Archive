---
title: "Default Permissions for /etc/apache2?"
date: 2009-10-11
forum: New to Ubuntu
---

### Post by fatgeek on 2009-10-11
I was following a tutorial to enable .htaccess passwords in apache and it had me change the permissions for /etc/apache2.  Well, it caused some problems, and now I can't get into it at all  Can someone please tell me how to get the permissions back to what they're supposed to be?

Thanks in advance.

EDIT

when I try to cd into /etc/apache2 I get the following:

-bash: cd: /etc/apache2: Permission denied

---

### Post by sandyd on 2009-10-11
```

sudo chown root /etc/apache2
sudo chmod -R 744 /etc/apache2

```

---

### Post by fatgeek on 2009-10-11
I tried your advice and when using the second command I get:

sudo chmod drwxr-xr-x /etc/apache2
chmod: invalid mode: `drwxr-xr-x'
Try `chmod --help' for more information.

---

### Post by unutbu on 2009-10-11
I ran
```

ls -lR /etc/apache2/ > ~/test/perms
```

Manually looking through the output, it looks like all files have 644 permissions and all directories have 755 permissions. So I suggest:
```

find /etc/apache2/ -type f -exec sudo chmod 644 {} \;
find /etc/apache2/ -type d -exec sudo chmod 755 {} \;
sudo chown -R root:root /etc/apache2
```

---

### Post by fatgeek on 2009-10-11
> **unutbu said:**
> I ran
```

ls -lR /etc/apache2/ > ~/test/perms
```

Manually looking through the output, it looks like all files have 644 permissions and all directories have 755 permissions. So I suggest:
```

find /etc/apache2/ -type f -exec sudo chmod 644 {} \;
find /etc/apache2/ -type d -exec sudo chmod 755 {} \;
sudo chown -R root:root /etc/apache2
```

That did it, thanks!

---

