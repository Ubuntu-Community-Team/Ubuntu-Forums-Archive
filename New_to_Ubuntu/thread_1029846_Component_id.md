---
title: "Component id?"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by mjheagle8 on 2009-01-03
i need to find the component id of my wireless card, and i dont know how.  it is a dlink air dwl-520 rev.e and i need the component id to find the firmware to flash.  i'm using the tutorial on [http://linux.junsun.net/intersil-prism/](http://linux.junsun.net/intersil-prism/) and [http://linux.junsun.net/intersil-prism/IDtable.html](http://linux.junsun.net/intersil-prism/IDtable.html). any help is greatly appreciated! i just need to know how to find my component id so i can finish the process! thanks!

---

### Post by 73ckn797 on 2009-01-03
Open terminal and enter: ```
lspci
```

---

### Post by mjheagle8 on 2009-01-04
i'm familiar with that command. but i dont see anything that looks like a component id when i run ```
lspci
```

---

### Post by 73ckn797 on 2009-01-04
> **mjheagle8 said:**
> i'm familiar with that command. but i dont see anything that looks like a component id when i run ```
lspci
```


Try:```
sudo lshw
```

---

