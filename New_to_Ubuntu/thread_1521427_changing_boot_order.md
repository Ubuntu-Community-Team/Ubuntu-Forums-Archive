---
title: "changing boot order"
date: 2010-06-30
forum: New to Ubuntu
---

### Post by manny43 on 2010-06-30
Hello friends

I have pc running Ubuntu 9.10 on sda1 and linuxmint 8 on sda6 i also have ubuntu 10.04 on sdb.Ubuntu 10.04 was installed after installing 9.10 and mint 8 now when boot the first choice is Ubuntu 10.04 and if i want 9.10 or mint 8 i have to scrool down and choose which one to boot.Can i change boot order as to make
Ubuntu 9.10 the first choice automaticaally since 9.10 is the OS i use all the time?Do i have to restore GRUB2 to Ubuntu 9.10?Thanks

---

### Post by ubunterooster on 2010-06-30
Using Synaptic, get the program called "startup-manager"

It will be placed into System>Administration>Startup-manager

---

### Post by hansdown on 2010-06-30
Hi manny43.

Boot the 10.04 system, and install 

```
startup-manager
```

from synaptic.

Click system> administration> startup-manager.

Under boot options, you can change the default to 9.10, or which one you prefer.

---

### Post by manny43 on 2010-06-30
Thank you very much that was easy.Thanks again great support

---

