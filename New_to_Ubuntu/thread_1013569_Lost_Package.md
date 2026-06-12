---
title: "Lost Package"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by Drezard on 2008-12-17
Im trying to follow this tutorial here:

> 
[http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu8.04](http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu8.04)


And its asking to install a package called postfix-tls. 

Whenever I run this command:

```

apt-get install postfix-tls

```

It says it cant find postfix-tls. Is there anything I can substitute it with? or anyway I can get it from another Repo or something?

Daniel

---

### Post by starcannon on 2008-12-17
The command you want is just:
```
sudo apt-get install postfix
```
for more information on postfix tls see here:
[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

GL and have fun

---

