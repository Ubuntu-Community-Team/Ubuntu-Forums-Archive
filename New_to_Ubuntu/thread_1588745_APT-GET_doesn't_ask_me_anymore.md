---
title: "APT-GET doesn't ask me anymore"
date: 2010-10-05
forum: New to Ubuntu
---

### Post by Blutkoete on 2010-10-05
Hello!

Two or three days ago, APT-GET stopped asking me whether I want to proceed or not when I run "sudo apt-get install <...>". Normally it showed me what to install and how much to download for that and asked me whether that's fine with me or not.

What has happened?

Thank you,

Blutkoete

---

### Post by andrewthomas on 2010-10-05
You get asked if you do an 

```
sudo apt-get update && sudo apt-get upgrade
```or 

if an 

```
sudo apt-get update && sudo apt-get install **pkgname**
```requires additional packages to satisfy dependencies, but otherwise it will just do what you tell it.

---

### Post by Blutkoete on 2010-10-07
Sorry for my late response.

Thank you very much, that explains it! But I'm a little bit ashamed that I haven't noticed that in two years of Ubuntu/Kubuntu experience.

---

