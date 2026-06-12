---
title: "MySQL server"
date: 2009-12-17
forum: New to Ubuntu
---

### Post by vanhornd on 2009-12-17
I'm having trouble getting my Ubuntu machine to be a MySQL server.  Is it necessary to activate the package for it to work?  I downloaded the binary from the MySQL site but am having trouble getting it to work.  

When I tried to activate the package, Ubuntu wanted me to put the original Ubuntu disk in my diskdrive which was impossible because I installed from a web download.  Any ideas?

Thanks, Doug

---

### Post by leprkhn on 2009-12-17
Check /etc/apt/sources.lst and be sure to comment (#) out the CD.
Then:
```
sudo apt-get update
```
```
sudo apt-get install mysql-server mysql-client
```

---

### Post by vanhornd on 2009-12-18
Thanks!  It is working now!

---

