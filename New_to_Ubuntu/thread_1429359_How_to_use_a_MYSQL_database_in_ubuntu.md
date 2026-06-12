---
title: "How to use a MYSQL database in ubuntu"
date: 2010-03-14
forum: New to Ubuntu
---

### Post by amritpalpathak on 2010-03-14
Hello i have install a MYSQL on my ubuntu pc when i tried to open it ,, it ask about the 
1=server hostname 
2=username
3=password
 
## in server hostname and username wat is to be filled up ?/
plz help me

---

### Post by jpkotta on 2010-03-14
Run `hostname` in a terminal to get the machine's name.  'localhost' always works for the machine you're on.

The default user is 'root'.  The password is whatever you gave when you installed it.

```
mysql -u root -p
```

You can create additional users.

I highly recommend phpmyadmin to interact with the database.

---

### Post by iMisspell on 2010-03-14
_[COLOR="Blue"][MySQL Administrator]("http://images.google.com/images?q=mysql%20administrator")[/COLOR]_ 'mysql-admin' is another choice for a GUI.

---

### Post by kellemes on 2010-03-14
> **jpkotta said:**
> (..)
i highly recommend phpmyadmin to interact with the database.

+1

---

### Post by Slim Moe on 2010-03-14
```
mysql -h localhost -u root -p

```

**Host ( -h ):** target machine where the MysQL server is running ( in your case, localhost )
**User ( -u ):** no comments
**Password ( -p ):** no comments

---

