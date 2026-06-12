---
title: "nvidia graphic card"
date: 2010-11-18
forum: New to Ubuntu
---

### Post by amitpokhrel on 2010-11-18
how can i find which nvidia graphic card i have??

---

### Post by Hippytaff on 2010-11-18
```

lspci

```
will list all pci devices
```

lspci | grep -i nvidia

```
will list pci devices with nvidia in the line ( -i so it's not case sensitive)
:-)

---

