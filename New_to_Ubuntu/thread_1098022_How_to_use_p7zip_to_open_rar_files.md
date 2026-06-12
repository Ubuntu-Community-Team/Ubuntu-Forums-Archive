---
title: "How to use p7zip to open rar files?"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by babloo75 on 2009-03-16
I have p7zip installed on my system. And synaptic package manager states that it can be used to open rar files. How can i do it.? when i open any rar file, it says "archive type not supported"
please help.

---

### Post by stchman on 2009-03-16
> **babloo75 said:**
> I have p7zip installed on my system. And synaptic package manager states that it can be used to open rar files. How can i do it.? when i open any rar file, it says "archive type not supported"
please help.

All you need to create and unpack .7z archives is the proper packages.

```
sudo apt-get -y install rar unrar p7zip p7zip-full

```

This will install the rar and 7zip stuff for File Roller.

---

### Post by babloo75 on 2009-03-16
Thanks. Now I can open them.

---

