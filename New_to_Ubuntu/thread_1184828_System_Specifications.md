---
title: "System Specifications"
date: 2009-06-11
forum: New to Ubuntu
---

### Post by samh785 on 2009-06-11
How do I check my computer specs in ubuntu? I need the equivalent of going to the system properties in windows vista. Please and thank you in advance.

---

### Post by AKK9 on 2009-06-11
Try installing HardInfo:

Type this into the terminal:

```
sudo apt-get install hardinfo
```

---

### Post by owenll on 2009-06-11
Or open a terminal and type:```
sudo lshw -html > hardware.html
```A file named **hardware.html** will be created in your Home directory.

---

### Post by samh785 on 2009-06-11
Thanks guys! This is exactly why I love this forum- quick and helpful answers.

---

