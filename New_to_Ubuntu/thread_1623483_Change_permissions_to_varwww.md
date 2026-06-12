---
title: "Change permissions to var/www"
date: 2010-11-16
forum: New to Ubuntu
---

### Post by alan89 on 2010-11-16
Hey eveyone,

I am currently learning php in college. I have the php files saved to my USB so I can work from them at home. I know I have to save them to the www folder in var but the permissions is set to the root. 

Is there a way for me to add read, write and execute permissions for my login so I can save the files from my USB to the www folder?

Its only for testing purposes so no one is connecting to the server.

Thanks,
A

---

### Post by Verbeck on 2010-11-16
from a terminal (Applications>Accessories>Terminal), run
```
sudo chown -R **username**:**usergroup** /var/www
```in most cases, the user name and user group is the same i think

---

### Post by 3rdalbum on 2010-11-16
That's the wrong way to go about it, because it causes a loosening of security policy. The better way is to copy the files across as root. The easiest way to do that is to open the file browser as root:

```
gksudo nautilus
```

And then you can drag.across the files to the folder using this root file browser window.

---

### Post by wojox on 2010-11-16
Are you using the server install or Desktop?

---

### Post by Verbeck on 2010-11-17
> **3rdalbum said:**
> That's the wrong way to go about it, because it causes a loosening of security policy.

well.. he did say that its only for testing and no one is connecting to the server..

---

