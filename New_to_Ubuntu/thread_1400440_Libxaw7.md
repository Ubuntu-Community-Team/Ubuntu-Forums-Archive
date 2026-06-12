---
title: "Libxaw7"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by MrChainBlueLightnin on 2010-02-06
Hello,
I am trying to install Citrix client on ubuntu 9.04 and I was hoping someone could help me determine if I have libxaw7. The tutorial says it is required for the install.

---

### Post by mushwars on 2010-02-06
```
apt-cache search libxaw7
```
I am not sure what this will return but pick the library, probably will be that, then do
```
sudo apt-get install libxaw7
```
If it says it is up to date then you have it installed, if not say yes to it asking weather to install it, then continue with whatever you were doing.

---

