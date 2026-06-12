---
title: "How to install packages with .tar.gz extensions"
date: 2010-03-13
forum: New to Ubuntu
---

### Post by amritpalpathak on 2010-03-13
Hiii i am new for linux .Recently i downloaded a mysql database  which is .tar.gz package 
please help me to install it in ubuntu 9.10 .....

---

### Post by aysiu on 2010-03-13
You don't install .tar.gz packages unless you have a special reason to.

Use the package manager to install most stuff (including MySQL):
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by amritpalpathak on 2010-03-13
Hello ...plz tell me how to install it through terminal because it is not present in ubuntu software center
?
Thanks

---

### Post by nemilar on 2010-03-13
The MySQL database is available via the repository of nearly every distro.  You might be looking for mysql-server.

---

### Post by aysiu on 2010-03-14
> **amritpalpathak said:**
> Hello ...plz tell me how to install it through terminal because it is not present in ubuntu software center
?
Thanks
```
sudo apt-get update
sudo apt-get install mysql-server-5.0
``` should do it.

---

