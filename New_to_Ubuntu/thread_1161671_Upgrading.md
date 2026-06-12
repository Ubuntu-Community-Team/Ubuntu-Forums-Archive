---
title: "Upgrading"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by Leshinsky on 2009-05-16
Ok,  so i have ubuntu i think lol.  but i want to go to notebook remix.  is there a way to basically upgrade or do i have to start from scrach.  and what is the difference.  does anyone know.  please fill me in.

---

### Post by x33a on 2009-05-16
[http://www.canonical.com/projects/ubuntu/unr](http://www.canonical.com/projects/ubuntu/unr)

to install netbook remix without reinstalling
```
sudo aptitude install ubuntu-netbook-remix

and then,

sudo aptitude remove ubuntu-desktop
```

---

### Post by Leshinsky on 2009-05-16
Ok, i feel stupid but i just used those commands to upgrade to laptop remix and it really screwed up my laptop.  so how do i change back to the regular ubuntu.

---

### Post by x33a on 2009-05-17
do the reverse

```
sudo aptitude remove ubuntu-netbook-remix

then sudo aptitude update && sudo aptitude install ubuntu-desktop
```

by the way, what got screwed up?

---

### Post by Leshinsky on 2009-05-17
Ok i tried those commands in terminal then restarted but it did nothing.  Any other ideas or should i just do another upgrade to server (this computer will be a server in a few weeks )

---

