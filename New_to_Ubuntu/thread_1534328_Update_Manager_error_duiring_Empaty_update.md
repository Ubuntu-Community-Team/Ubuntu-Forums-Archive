---
title: "Update Manager: error duiring Empaty update"
date: 2010-07-19
forum: New to Ubuntu
---

### Post by cheetaux on 2010-07-19
Update Manager recommended the following updates:
empathy, empathy-common, and nautilis-sendto-empathy

However, during the update, I get the following errors:

```
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/empathy/nautilus-sendto-empathy_2.30.1.1-0ubuntu1_i386.deb
  404  Not Found [IP: 91.189.88.30 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/empathy/empathy_2.30.1.1-0ubuntu1_i386.deb
  404  Not Found [IP: 91.189.88.30 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/empathy/empathy-common_2.30.1.1-0ubuntu1_all.deb
  404  Not Found [IP: 91.189.88.30 80]
```

Any ideas?  Thanks

---

### Post by philinux on 2010-07-19
Try again in a while the server may be down or in Software Sources change the server to Main.

---

### Post by cheetaux on 2010-07-19
Switching the server to Main fixed it.  Thanks.

---

