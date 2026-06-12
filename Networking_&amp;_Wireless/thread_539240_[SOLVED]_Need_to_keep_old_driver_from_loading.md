---
title: "[SOLVED] Need to keep old driver from loading"
date: 2007-08-31
forum: Networking &amp; Wireless
---

### Post by uclalinux on 2007-08-31
Hi, I have the realtek rtl8111/8186b Ethernet card on my motherboard (ecsG33T-M2),  i found a thread that fixed my networking problem, but i don't know how to keep the change permanent. every time I restart I have to remove the 8169 mod, and load this other one. 

This is what I have done to get it working,

```

Code:

sudo aptitude install build-essential
sudo aptitude install linux-headers-`uname -r`


Code:

 tar xjf 8168-8.001.00.tar.bz2


Code:

cd r8168-8.001.00
make clean modules
sudo make install
sudo depmod -a


Code:

sudo modprobe -r r8169


Code:
sudo modprobe r8168
```

How do get rid of this one, and keep the other one alway loaded?

Thanks

---

### Post by noob12 on 2007-08-31
You want to blacklist r8169 and tell the system to load r8168 at boot.  This will do that:

```

echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist

echo "r8168" | sudo tee -a /etc/modules

```

---

### Post by uclalinux on 2007-08-31
Thanks, works great. 
Could you direct me to a location where I could learn more about what those  commands did?

---

### Post by noob12 on 2007-08-31
Well those commands were just a short form way of adding lines to two files.

The first file **/etc/modprobe.d/blacklist** contains blacklist lines for kernel modules that you don't want to load.  The second file **/etc/modules** contains a list of modules that aren't normally loaded but you want to load.

You can examine these files in an editor or using **cat** and you will see your added lines at the end of them.

---

### Post by uclalinux on 2007-08-31
thanks

---

