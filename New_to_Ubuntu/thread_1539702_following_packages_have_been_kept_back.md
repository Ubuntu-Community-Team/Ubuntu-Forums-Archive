---
title: "following packages have been kept back:"
date: 2010-07-26
forum: New to Ubuntu
---

### Post by vivek40 on 2010-07-26
Hii My update manager shows  the following upgrades among many others. 
linux-generic linux-headers-generic linux-image-generic

However when I try to upgrade them through the terminal, all other upgrades happen and I get the below message for these ones.
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic

This had happened before and I had used the upgrade manager to upgrade these. However this time again this has popped up. So why does this happen and in such cases is it wise to use the upgrade manager to do the upgrades.
Thanks

---

### Post by wojox on 2010-07-26
Open your terminal and copy and paste

```
sudo apt-get update; sudo apt-get upgrade; sudo apt-get dist-upgrade
```

---

### Post by vivek40 on 2010-07-26
Thanks wojox!

---

### Post by wojox on 2010-07-26
Your Welcome. ;)

---

