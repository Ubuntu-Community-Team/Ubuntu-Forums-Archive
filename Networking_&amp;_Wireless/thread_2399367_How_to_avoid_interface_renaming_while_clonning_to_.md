---
title: "How to avoid interface renaming while clonning to another PC with the same HW"
date: 2018-08-24
forum: Networking &amp; Wireless
---

### Post by jirkarck on 2018-08-24
Please, could anyone give me an advice how to avoid network interface renaming on Ubuntu 16.04+? I have maden the binary copy of system hard drive and I need to clone it to more computers with exactly the same HW (but with different MAC addresses, ofcourse). In older Ubuntu, I solved it by deleting file:
```
/etc/*udev*/*rules*.*d*/70-persistent-*net*.rules
```

But this file does not exist on newer Ubuntu systems.

Many thanks in advance!

---

### Post by TheFu on 2018-08-24
[https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/](https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/)

---

