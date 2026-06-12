---
title: "List of connected hardware."
date: 2009-07-07
forum: New to Ubuntu
---

### Post by SG3 on 2009-07-07
How can i get via terminal the list of connected hardware.

---

### Post by Boondoklife on 2009-07-07
try sudo lshw

---

### Post by damis648 on 2009-07-07
> **Boondoklife said:**
> try sudo lshw

```
sudo lshw
``` should get you all you need; if not try
```
sudo lspci
sudo lsusb
sudo lspcmcia
```

---

### Post by SG3 on 2009-07-07
thanks :)

---

