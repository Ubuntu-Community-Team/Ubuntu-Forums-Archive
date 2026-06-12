---
title: "Setting jdk1.6.0_18 as default"
date: 2010-02-11
forum: New to Ubuntu
---

### Post by infestor on 2010-02-11
i have jdk-6u18-linux-x64 installed in here: /opt/java/64/jdk1.6.0_18

but how do i set this jdk as system default?
netbeans stopped working.

---

### Post by raffaele181188 on 2010-02-11
'cause your NetBeans javahome points to older directory.
Launch netbeans from terminal with
```

netbeans --jdkhome /opt/java/64/jdk1.6.0_18

```
then change preferences from options dialog

---

