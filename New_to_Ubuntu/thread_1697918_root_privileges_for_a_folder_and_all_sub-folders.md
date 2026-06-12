---
title: "root privileges for a folder and all sub-folders?"
date: 2011-03-01
forum: New to Ubuntu
---

### Post by poisonborz on 2011-03-01
Hola,

I've recently installed ISPConfig, but noticed that when I create a new user/folder in the var/www folder, it is created with specific permissions.
I want some users to have root privileges over all the content of var/www. I've tried to add this line to sudoers

```
username ALL= NOPASSWD: /var/www
```

But I suppose this only covers /www not its contents...

---

### Post by Hakunka-Matata on 2011-03-01
[http://ubuntuforums.org/showthread.php?t=445213]("http://ubuntuforums.org/showthread.php?t=445213")

Have a look

---

