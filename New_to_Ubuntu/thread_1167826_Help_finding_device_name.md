---
title: "Help finding device name"
date: 2009-05-23
forum: New to Ubuntu
---

### Post by jjmanbolero on 2009-05-23
Hi There,

I am needing to find a device name of the CCTV DVR cards I added. Is there a program that can tell me what the names are?

I know it's something like "dev/video0" or something

---

### Post by oldos2er on 2009-05-23
```
dmesg | grep video
```
or
 ```
dmesg | grep dvr
```

---

