---
title: "can I change a user's forgotten password with sudo somehow?"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by jimmy the saint on 2009-02-04
I have a server and I forgot the media account's password.  I could create another user I guess, but is it possible to change the user password somehow with sudo without remembering the old one?  
Oh yeah, the server is headless.

thanks

JTS

---

### Post by adult swim on 2009-02-04
i think you can just do
```
sudo passwd media
```

---

### Post by SuperSonic4 on 2009-02-04
You should, assuming you know your own

```
sudo passwd <user>
```

---

### Post by jimmy the saint on 2009-02-05
Excellent!  thanks guys, i figured it was something simple like that, I was just worried it would require me to know the old one or something.

---

