---
title: "Update repository list?"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by Treeh on 2009-10-29
How can I update my repository list/add more to it?

When I type "sudo apt-get install wine" it doesn't find the package. 

Thanks.

---

### Post by arochester on 2009-10-29
Go to [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by sisco311 on 2009-10-29
wine is in the universe repos:
```
sudo software-properties-gtk -e universe
sudo apt-get update
sudo apt-get install wine
```

or go to System -> Administration -> Software Sources to enable the universe repo.

---

