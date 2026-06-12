---
title: "Installing java and updating"
date: 2009-03-12
forum: New to Ubuntu
---

### Post by Ammon Van Meter on 2009-03-12
I am wanting to install java on ubuntu now. I remember doing this once before.

1. I had to turn the .bin into an executable to ubuntu could read it.

2. Then I updated via a terminal command.

---

### Post by nateperson on 2009-03-12
?
I would just use the Synaptic Package Manage to install Java.  Just open it, then do a search for "java jdk" if you need the java compiler or "java jre" if just want to run stuff.  Select the package and select Mark for installation.  Then click apply.

---

### Post by taurus on 2009-03-12
```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```

---

