---
title: "need a noobish tutorial on making a webserver..."
date: 2009-01-30
forum: New to Ubuntu
---

### Post by mudrain911 on 2009-01-30
I recently got a hold of someones old computer after they bought a new one, and i would like to turn it into a server for a website. I have no idea how the Ubuntu server edition even works, so i was wondering if anyone could help me with it any.

thanks in advance, 
-MuD

---

### Post by cosmotron on 2009-01-30
You really just need to install

[LIST]
[*]Apache
[*]PHP
[*]MySQL
[/LIST]

---

### Post by cariboo on 2009-01-30
A quick google search found [this]("http://www.howtoforge.com/perfect-server-ubuntu8.04-lts"). You probably don't need a mailserver, and you definitely don't need DNS, so ignore those sections.

Jim

---

### Post by mudrain911 on 2009-01-31
so i dont need anything special other than those 3 to set up a webserver... cool ill go try it and see how it works out, anyone have any warnings for me or anything let me know...

---

### Post by nandemonai on 2009-01-31
[https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html) ;)

---

### Post by lykwydchykyn on 2009-01-31
> **mudrain911 said:**
> so i dont need anything special other than those 3 to set up a webserver... cool ill go try it and see how it works out, anyone have any warnings for me or anything let me know...

Actually, there's a bit more to it, as you need some "bridge" packages to make those three things talk to one another.  Fortunately, you can just do:
```

sudo tasksel

```
And select "LAMP".  Or just select "LAMP server" during installation.

---

