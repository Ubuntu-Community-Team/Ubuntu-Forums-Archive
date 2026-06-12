---
title: "cant download from software center??"
date: 2010-01-06
forum: New to Ubuntu
---

### Post by Syppli on 2010-01-06
i have a problem, i cant download from the ubuntu software center, and thats kind of bad, when i have to download my graphics driver from there, and it just keep saying "Not available in the current data"... can anyone help me??

---

### Post by plucky on 2010-01-06
**System > Administration > Software Sources** and make sure repositories are ticked then reload.(See screenshot)


Good Luck

---

### Post by Syppli on 2010-01-06
still not working :( anything else?

---

### Post by howefield on 2010-01-06
Open a terminal (Applications > Accessories > Terminal) and type 

```
sudo apt-get update
``` 

Enter your password if prompted.

Once it is finished, try downloading your software again.

---

