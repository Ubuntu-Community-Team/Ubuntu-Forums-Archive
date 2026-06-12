---
title: "Sonar xscreensaver"
date: 2010-01-01
forum: New to Ubuntu
---

### Post by jnmjr on 2010-01-01
Hi everybody and HAPPY 2010!!!!  I'm here again asking for your help, I've got Sonar screensaver running but I get this message,

SONAR MUST BE SETUID TO PING!      .... I don't know how...

It would be neat if it pinged...... Can any one help with this? You have all been so helpful, I can't say enough about the Linux community. THX. ):P

---

### Post by sylvester_0 on 2010-01-01
I believe what you're looking for is:

```
sudo chmod +s /usr/lib/xscreensaver/sonar
```

---

### Post by jnmjr on 2010-01-01
THX Sylvester, that did it.
Now if it would make a Sonar sound it 'd be awesome.:lolflag:

---

### Post by fslezak on 2010-06-23
Huh. After I did that, all it says is "Resolving hosts". How can I have the SETUID message not show up, but not use a Internet connection?

---

### Post by kainalu on 2011-01-27
Hey, I have this problem too, the screen just stays on resolving hosts

---

### Post by breem42 on 2011-01-31
These instructions worked for me.

It takes a while for the system to start up, but it does work.

---

### Post by boblizar on 2011-06-16
set it to ping known ssh clients, only pings hosts you know you hit then, runs much quicker.

---

