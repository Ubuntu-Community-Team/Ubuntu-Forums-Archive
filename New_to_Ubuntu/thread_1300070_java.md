---
title: "java"
date: 2009-10-24
forum: New to Ubuntu
---

### Post by donaldshelton on 2009-10-24
What packages do I need to install to get Java based web sites like Pogo.com to work?

---

### Post by ajgreeny on 2009-10-24
```
sudo apt-get install sun-java-jre sun-java-plugin
``` should do it.

---

### Post by donaldshelton on 2009-10-24
> **ajgreeny said:**
> ```
sudo apt-get install sun-java-jre sun-java-plugin
``` should do it.

E: Couldn't find package sun-java-jre

Don

---

### Post by ajgreeny on 2009-10-25
Sorry, its **sun-java6-jre** and **sun-java6-plugin**

My fault, as I just searched for sun-java to find them and forgot the figure 6. Make sure you have universe and multiverse repos enabled, which I think they should be by default nowadays.

---

