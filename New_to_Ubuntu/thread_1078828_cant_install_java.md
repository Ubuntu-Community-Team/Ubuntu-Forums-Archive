---
title: "cant install java"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by patchido on 2009-02-23
i cant install java :S dont know why can anyone give me an easy how to - for jdk? cause ive tried for 2 days know

---

### Post by sandyd on 2009-02-23
tried the jdk bins from sun microsystems themselves?

whats the problem anyways?

---

### Post by patchido on 2009-02-23
that i did but i cant run javac on terminal

---

### Post by taurus on 2009-02-23
Which release are you running?

Have you tried installing it from a terminal with

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install sun-java6-jdk
```

---

### Post by patchido on 2009-02-24
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

thats what i get :s

---

### Post by patchido on 2009-02-24
anyone?

---

### Post by 3rdalbum on 2009-02-24
> **patchido said:**
> E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

thats what i get :s

You can only run one package manager at a time. If Synaptic is running, quit it. If Update Manager is working, wait for it to finish. If you're already using "apt-get", wait for it to finish.

---

### Post by stchman on 2009-02-24
For Hardy:

[http://www.stchman.com/essen_pack.html](http://www.stchman.com/essen_pack.html)

Look for Java.

---

