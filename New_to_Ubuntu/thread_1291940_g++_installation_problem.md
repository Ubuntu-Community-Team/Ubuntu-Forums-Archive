---
title: "g++ installation problem"
date: 2009-10-15
forum: New to Ubuntu
---

### Post by nislamce on 2009-10-15
Hi,
I am using Ubuntu 8.10.I need to install g++ and followed two method but failed. Any co-operations will be appreciable. My internet connection is now disabled also and tried to use static ip but unfortunately failed. Then using Ubuntu CD I have followed method 2

Method 1:
--------
Installed following using ([http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.3/](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.3/))

cpp-3.3_3.3.6-15ubuntu2_i386.deb
g++-3.3_3.3.6-15ubuntu2_i386.deb
gcc-3.3-base_3.3.6-15ubuntu2_i386.deb
gcc-3.3_3.3.6-15ubuntu2_i386.deb
libstdc++5_3.3.6-15ubuntu2_i386.deb
libstdc++5-3.3-dev_3.3.6-15ubuntu2_i386.deb

cd Desktop/gcc

sudo dpkg -i --force-depends gcc-3.3-base_3.3.6-15ubuntu2_i386.deb
sudo dpkg -i --force-depends cpp-3.3_3.3.6-15ubuntu2_i386.deb
sudo dpkg -i --force-depends gcc-3.3_3.3.6-15ubuntu2_i386.deb
sudo dpkg -i --force-depends g++-3.3_3.3.6-15ubuntu2_i386.deb
sudo dpkg -i --force-depends libstdc++5_3.3.6-15ubuntu2_i386.deb
sudo dpkg -i --force-depends libstdc++5-3.3-dev_3.3.6-15ubuntu2_i386.deb

Regards,
MNI

---

### Post by kavon89 on 2009-10-15
If you can get an internet connection the machine, simply issue this command:

```
sudo apt-get install build-essential
```

---

