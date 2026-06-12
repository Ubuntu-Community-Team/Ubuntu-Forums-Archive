---
title: "Failed to retrieve share list from server (windows)"
date: 2010-12-15
forum: New to Ubuntu
---

### Post by hunter99507 on 2010-12-15
I have a windows wireless drive but i cant open it. I see it but not open. How can i fix this issue?

---

### Post by seawolf167 on 2010-12-16
First, ensure samba is installed (open a terminal, type the commands in there)

```
sudo apt-get install samba
```Next, open Nautilus (the file manager), i.e. any folder, then type the following, but replace the XXX's with the IP address of the server you are trying to access

```
smb://XXX.XXX.XXX.XXX
```(This is usually something like 192.168.X.X)

---

