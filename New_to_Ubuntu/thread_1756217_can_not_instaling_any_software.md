---
title: "can not instaling any software"
date: 2011-05-12
forum: New to Ubuntu
---

### Post by Abdika on 2011-05-12
Hello, i need help about my ubuntu 11.04. i can't install & upgrade software from ubuntu repository after removing clamav.i installed all clamav package & removing it with synaptic package manager.i realy need to solving it. 
thank you:confused:

---

### Post by Rubi1200 on 2011-05-12
Hi,
try the following commands in the terminal and see if it resolves the problem. If there are errors reported, post them here please:

```
sudo apt-get install -f

sudo dpkg --configure -a

sudo apt-get update
```

---

