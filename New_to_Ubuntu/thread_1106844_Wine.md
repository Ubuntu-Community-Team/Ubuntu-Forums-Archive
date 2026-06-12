---
title: "Wine"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by newlec on 2009-03-26
Hi, I cannot find Wine in the apt-get list. I've tried all possible options;
ie. sudo apt-get install wine but it still not available in apt-get.
I've also tried from \root but I am asked for a Unix password, which I give but still not getting anywhere. Help!

---

### Post by albandy on 2009-03-26
do apt-cache search wine and post the results

---

### Post by RedNikon on 2009-03-26
Here is the .dep file that will allow you to install and run wine on Ubuntu.

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by blazemore on 2009-03-26
```
sudo su
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add - && wget http://wine.budgetdedicated.com/apt/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/winehq.list && apt-get update && apt-get install wine -y --force-yes
```

---

