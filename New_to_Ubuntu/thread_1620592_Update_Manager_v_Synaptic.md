---
title: "Update Manager v Synaptic"
date: 2010-11-13
forum: New to Ubuntu
---

### Post by mn_voyageur on 2010-11-13
On my other machine, Update Manager shows that updates are available.  However, when I try to update, nothing happens.

The update list does not change.  

Any suggestions?

MarkN

---

### Post by 73ckn797 on 2010-11-13
Use terminal and enter:
```
sudo apt-get update
```

Then enter:
```
sudo apt-get upgrade
```

I was having the same issue on one computer and that fixed it.

---

