---
title: "graphics packages for kubuntu"
date: 2011-08-07
forum: New to Ubuntu
---

### Post by aju1991 on 2011-08-07
PLEASE HELP ME ANYONE TO INSTALL 
GRAPHICS PACKAGES IN C LANGUAGE............


to work 
#include<vga.h>
header file




please help me...............

---

### Post by hailtothethief on 2011-08-07
```
sudo apt-get install linux-headers-`uname -r`
```

Assuming the vga.h you're talking about is a kernel header. Make sure you configure your include path properly. Good luck :)

---

