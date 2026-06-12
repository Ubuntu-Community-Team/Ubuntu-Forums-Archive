---
title: "[SOLVED] java for mediamaster"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by trucker33377 on 2008-12-07
i need to upload files to mediamaster but the uploader says i'm missing java run time Recommended Version 6 Update 11 

ive installed java from spm and the add and remove still missing what it needs.

---

### Post by taurus on 2008-12-07
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
java -version
```

---

### Post by trucker33377 on 2008-12-07
> **taurus said:**
> What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
java -version
```

java version "1.6.0_0"
OpenJDK  Runtime Environment (build 1.6.0_0-b11)
OpenJDK Server VM (build 1.6.0_0-b11, mixed mode)
lonnie@lonnie-desktop:~$

---

### Post by taurus on 2008-12-07
Maybe it is looking for the Sun's version.

---

### Post by trucker33377 on 2008-12-07
that was it found jre in the spm and installed it plus the plugin rebooted 
good to go thanks now if i could remember how to mark this solved

---

