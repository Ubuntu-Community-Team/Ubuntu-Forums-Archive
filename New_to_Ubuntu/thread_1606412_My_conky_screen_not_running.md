---
title: "My conky screen not running"
date: 2010-10-26
forum: New to Ubuntu
---

### Post by karthick87 on 2010-10-26
I have changed my home directory [COLOR=DarkRed]permission to 700[/COLOR] after that i couldn't find conky screen running in my desktop..Someone help me to get it back...

---

### Post by Quackers on 2010-10-26
Is it a permission error or did recent updates run?
Recent updates have caused a problem with Python.
Try running 
```
sudo ln -s /usr/bin/python2.6 /usr/bin/python2
```

---

### Post by karthick87 on 2010-10-26
> **Quackers said:**
> Is it a permission error or did recent updates run?
Recent updates have caused a problem with Python.
Try running 
```
sudo ln -s /usr/bin/python2.6 /usr/bin/python2
```

```

karthick@Ubuntu-desktop:~$ sudo ln -s /usr/bin/python2.6 /usr/bin/python2
ln: creating symbolic link `/usr/bin/python2': File exists

```

---

### Post by Quackers on 2010-10-26
Oh, when I tried that it just ran.
It may be a permission thing then, but I don't know enough to comment. Incidentally, why did you change permissions?

---

### Post by karthick87 on 2010-10-26
I have two more users in my ubuntu system,changing the permission would restrict other users to view my home dirtectory.Thats why i changed the permission..

---

### Post by Verbeck on 2010-10-26
maybe killing the process and starting conky again might help

---

### Post by karthick87 on 2010-10-27
Changed the permission back to 755,now its working..Thank you :)

---

