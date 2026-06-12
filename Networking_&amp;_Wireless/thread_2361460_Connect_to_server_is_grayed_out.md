---
title: "Connect to server is grayed out"
date: 2017-05-16
forum: Networking &amp; Wireless
---

### Post by jpro6363 on 2017-05-16
I am trying to connect to my NAS and for some reason the when I open the connect to server and type in anything from  afp://LS-NAS.local,  //10.0.0.x/, to  smb://10.0.0.x  the connect button is grayed out. 

uname -a
Linux jason-WS1 4.4.0-77-generic #98-Ubuntu SMP Wed Apr 26 08:34:02 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

   
lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.2 LTS
Release:	16.04
Codename:	xenial

---

### Post by jpro6363 on 2017-05-19
The Server is a NAS device.

---

### Post by Morbius1 on 2017-05-20
It almost sounds like you have a package missing. Try installing it:
```
sudo apt install gvfs-backends
```
If it says it's already installed try reinstalling it:
```
sudo apt --reinstall install gvfs-backends
```

---

