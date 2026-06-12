---
title: "nforce drivers"
date: 2008-02-10
forum: Networking &amp; Wireless
---

### Post by fouadk on 2008-02-10
hi everyone...

i have an hp pavilion dv6650 that comes with an nvidia ethernet controller....

it does not work out of the box....

i tried the nvidia site to get the drivers but they are made only for fedora,,,,

does anyone know how to make this work for ubuntu

please help

thanks in advance

---

### Post by madmetal on 2008-02-10
open terminal and give 
```
lspci
```
and see if you can find ethernet controler and which is it...
mine is 
00:05.0 Bridge: nVidia Corporation CK8S Ethernet Controller (rev a2)
and works out of the box...

---

### Post by fouadk on 2008-02-11
lspci shows concerning the networkin is :

```

00:06.0 Ethernet controller: nVidia Corporation MCP65 Ethernet (rev a3)

```

---

