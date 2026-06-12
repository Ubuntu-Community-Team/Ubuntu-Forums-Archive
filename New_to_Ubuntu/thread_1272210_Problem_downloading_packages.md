---
title: "Problem downloading packages"
date: 2009-09-21
forum: New to Ubuntu
---

### Post by grifan526 on 2009-09-21
I was trying to download some new apps using Add/remove Application and with everything I tried to download it gave me this error:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/qt4-qtconfig_4.5.0-0ubuntu4.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/qt4-qtconfig_4.5.0-0ubuntu4.1_i386.deb)
  404 Not Found [IP: 91.189.88.45 80]

I am pretty sure they are all the same this particular one is for KOffice though. Any help would be greatly appreciated.

---

### Post by zkriesse on 2009-09-21
Have you updated the system? If not run these two commands in the terminal. . 
```
sudo apt-get update
```
NOTE: you will have to type your password which you will not see. This is normal.
```
sudo apt-get upgrade
```

---

