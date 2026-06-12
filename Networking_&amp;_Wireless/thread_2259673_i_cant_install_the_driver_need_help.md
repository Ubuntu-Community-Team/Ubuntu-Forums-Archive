---
title: "i cant install the driver need help"
date: 2015-01-06
forum: Networking &amp; Wireless
---

### Post by temroa on 2015-01-06
how can &#305; install this driver to my x552cl notebook

[https://github.com/tobiasBora/MT7630E_3.16](https://github.com/tobiasBora/MT7630E_3.16)

i dont know how to use that commands

**3. Use**

 To just compile the library and copy the firmware in /lib/firmware,  please run (you&#8217;ll be prompt for sudo password during the copy in  /lib/firmware):
 
make compile

To load and compile the driver (wifi and bluetooth) for the current session only, please run :
  
make load

To install the driver in order to load it every time you start your computer :
  
make install

And to uninstall it :
  
make uninstall

---

### Post by Bucky Ball on 2015-01-06
Welcome. Please give the result of this command from a terminal if you are attempting to install a wireless card driver:

```
sudo lshw -C network
```

... and the Ubuntu release and flavour you are using. Thanks.

---

