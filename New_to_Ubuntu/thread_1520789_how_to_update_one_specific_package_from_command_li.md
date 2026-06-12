---
title: "how to update one specific package from command line?"
date: 2010-06-30
forum: New to Ubuntu
---

### Post by legolas_w on 2010-06-30
Hi
is there any way to only update one package using the apt-get commands?

for example I have 100 packages waiting to be updated and I only want to update dockbar, is that doable from command line?

thanks.

---

### Post by teejaybee on 2010-06-30
Does "apt-get upgrade <package name>" not work for you?

I just did it with firefox, and it only upgraded firefox when I have more it could be doing.

---

### Post by Yarui on 2010-06-30
I believe you just do apt-get install for whatever package you want to update, if there is a newer version it is installed, if you have the newest version it tells you that it's already installed.

---

### Post by ankspo71 on 2010-06-30
Hi,
the only command I know for this would be: 
```
sudo apt-get install dockbar
```
if there is no update available, it will say something like "you already have the latest version installed"
if there is an update, that command will update the package with the newer version. 
Hope that helps.

(sorry - not quick enough, duplicate answer)

---

