---
title: "Authentifications"
date: 2011-02-28
forum: New to Ubuntu
---

### Post by fullmetallinux on 2011-02-28
I have ubuntu 10.10 and is has just as much if not more authentications then when windows 7 first came out. Even logging in to networks requires it. How do I set what needs authentications
or turn them off completely?

---

### Post by john77eipe on 2011-02-28
Welcome to the Ubuntu Forums! 

Most of the functionalities in Ubuntu requires certain privileges. It's better that way. 

Anyways if you need to change you can modify the default timer that comes with sudo. 


```
sudo visudo
```

then add this to the end of the defaults line:
```
,timestamp_timeout=
```

the value could be a positive number denoting the number of minutes till timeout. If it's -1 it is infinite. Meaning you won't be asked for password again.  

Have a loot at
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

