---
title: "how to install crypt manager or any other encryption software"
date: 2011-04-03
forum: New to Ubuntu
---

### Post by zaafar on 2011-04-03
hi, i was looking to install an encryption software and came across these 


sudo addgroup your-login fuse
 sudo apt-get install encfs python2.6-dev python-nautilus subversion
 svn checkout [http://crypt-manager.googlecode.com/svn/trunk/](http://crypt-manager.googlecode.com/svn/trunk/) crypt-manager
 cd crypt-manager
 sudo ./install.sh


but in the end it says


sudo: ./install.sh: command not found

can anybody please help me or suggest any other alternative . thanx !

---

### Post by hakermania on 2011-04-03
truecrypt, I use it and it's the best!

---

### Post by Dry Lips on 2011-04-03
Cryptkeeper is a nice program for encrypting files or folders.  
  You can install it from the Ubuntu Software Center
 or:
 ```
sudo apt-get install cryptkeeper
```

---

### Post by bodhi.zazen on 2011-04-03
See also :

[https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)

---

