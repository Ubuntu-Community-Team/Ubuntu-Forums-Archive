---
title: "Limit a User to Internet only."
date: 2011-03-09
forum: New to Ubuntu
---

### Post by mn_voyageur on 2011-03-09
I have an individual who wants to use my computer when I am at work.  I tried to set him up as a user and limit his access to only the internet.  However, when I log in as him, I can still navigate to my folders.

The only box checked under "User Privileges" is Internet.  

Thanks,
MarkN

---

### Post by matt_symes on 2011-03-09
Hi

You could change the permissions of your home folder with your files in

```
chmod 700 /home/<your user name>
```

Do this when logged in as you or put sudo in front of it.

Kiind regards

---

