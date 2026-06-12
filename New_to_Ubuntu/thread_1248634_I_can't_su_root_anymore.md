---
title: "I can't su root anymore"
date: 2009-08-24
forum: New to Ubuntu
---

### Post by Grifulkin on 2009-08-24
I was trying to use Aircrack-ng just to see if I could do it and instead of typing sudo for every command I wanted to su to root and then run the commands.

So ```
ryan@Ubuntu:~$ groups
ryan adm dialout cdrom video plugdev lpadmin netdev admin sambashare

```

And ```
ryan@Ubuntu:~$ su
Password: 
su: Authentication failure

```

So any help would be great, but whenever you get around to it.

---

### Post by jrothwell97 on 2009-08-24
su asks for root's password, and as root is locked (i.e. you can't *log in* as root), you can't use su.

Instead, try using

```
sudo -i
```

which runs sudo interactively.

---

### Post by gldearman on 2009-08-24
Another option would be:

```
sudo /bin/bash
```

which will spawn a new bash shell as root.

---

### Post by Grifulkin on 2009-08-24
Thank you, I never thought of doing sudo /bin/bash though, makes sense though.

---

