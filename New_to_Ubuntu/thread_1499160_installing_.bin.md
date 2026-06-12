---
title: "installing .bin"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by paul88 on 2010-06-01
I'm trying to install j2ee.bin but keep getting the following message.
```
./java_ee_sdk-5_08-jdk-6u20-linux.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

```

i have tried chmod +x j2ee.bin

any ideas?

---

### Post by collinp on 2010-06-01
Try installing the libstdc++6 package through the following terminal command:
```
sudo apt-get install libstdc++6
```

---

### Post by paul88 on 2010-06-01
```
libstdc++6 is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-21 linux-headers-2.6.32-21-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Gave me the above and

```
./java_ee_sdk-5_08-jdk-6u20-linux.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

```

---

### Post by paul88 on 2010-06-01
Problem solved. I downloaded the following

[http://packages.ubuntu.com/en/jaunty/libstdc++5](http://packages.ubuntu.com/en/jaunty/libstdc++5)

---

