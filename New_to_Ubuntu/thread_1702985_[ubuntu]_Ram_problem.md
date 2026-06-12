---
title: "[ubuntu] Ram problem?"
date: 2011-03-08
forum: New to Ubuntu
---

### Post by darmok47 on 2011-03-08
Hi, i think i have the same problem but... I'M RUNNING 64BIT VERSION!

lshw say that i have 4 GB ram, but system monitor say 3.2GB

Who is right?
ubuntu is using 4GB or 3.2?

Someone know the answer?

---

### Post by marin123 on 2011-03-08
```
uname -a
```

that will tell you if youre using 64 bit version, because i doubt 64 bit kernel cannot address 4 G ram.

---

### Post by Dorsenstein on 2011-03-08
The system monitor on any OS will almost never say the amount of RAM you have actually installed. I have 4GB of memory and the system monitor says 3.7

---

