---
title: "Compiling error"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by tombom62 on 2009-04-29
Whenever I get to ./configure on compiling anything, I get a error telling me that my C compiler cannot create executables.  I have no idea and have never compiled anything before, so I need help. ubuntu intrepid, openbox, btw.



Has anyone come across this?

---

### Post by tahnok on 2009-04-29
You generally need a package called build-essentials if you want to compile anything. Also you need the linux headers for your kernel. You can install both of these with this command

```
 sudo apt-get install linux-headers-$(uname -r) build-essentials 
```

---

### Post by taurus on 2009-04-29
There is no "s" in the build-essential package.

---

### Post by andrew.46 on 2009-04-29
Hi taurus,

> **taurus said:**
> There is no "s" in the build-essential package.

Well strictly speaking there are 2 :-).

Andrew

---

