---
title: "Burning DVD's???"
date: 2011-02-06
forum: New to Ubuntu
---

### Post by jimmyBoy18 on 2011-02-06
Could someone offer a new user advice on an app to burn CD's and DVD's...I want to burn an ISO of NetBeans for my Computer Science/Programming classes. Thanks in advance for your patience.

P.S. I run a 64-bit Intel Pentium Dual-Core

---

### Post by robsoles on 2011-02-06
Welcome to UF.

Brasero is in a vanilla install of Ubuntu 10.04 and it hasn't let me down for ages and ages - it is burning software.

Furious ISO mounter seems a good partner for Brasero, it allows you to access optical disk file-systems without burning them to disc and also helps burn them to disc using Brasero.

Have a browse through the Ubuntu Software Centre and grab a few different ones, see if you find anything to like better than Brasero and Furious ISO mounter.

---

### Post by Hedgehog1 on 2011-02-06
I second this recommendation!

Brasero is also carried by default in Ubuntu 10.10, in case that is the version you are running.

Applications >> Sound & Video >> Brasero Disk Burner.

:KS

---

### Post by presence1960 on 2011-02-06
Brasero works fine. You may want to look at K3B also. You can install it from terminal by running ```
sudo apt-get install k3b
```

---

### Post by tjwoosta on 2011-02-06
For a simple command line solution try

```
cdrecord -v /path/to/file.iso
```

(-v is just for verbose output so you can see whats going on)

Edit: 
AlsoI should mention that despite the name it burns any iso's including dvd's

---

