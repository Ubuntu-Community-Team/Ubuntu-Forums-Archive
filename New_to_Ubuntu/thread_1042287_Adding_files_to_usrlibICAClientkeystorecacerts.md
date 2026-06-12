---
title: "Adding files to /usr/lib/ICAClient/keystore/cacerts"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by Cheddardip on 2009-01-17
I need to add Citrix Certs. How do I give my self permission do add files to this directory? 

/usr/lib/ICAClient/keystore/cacerts

I'm using this tutorial 
[http://geekpete.com/blog/tech-guides/linux-citrix-client-error-61-ubuntu-810-intrepid-ibex](http://geekpete.com/blog/tech-guides/linux-citrix-client-error-61-ubuntu-810-intrepid-ibex)

---

### Post by adult swim on 2009-01-17
```
sudo cp /path/to/file.crt /usr/lib/ICAClient/keystore/cacerts
```
EDIT: or you can press alt+f2 and enter in ```
gksudo nautilus
``` to drag and drop

---

### Post by Cheddardip on 2009-01-17
I tried alt f2 I still get permission denied.

I also tried extracting the file to /usr/lib/ICAClient/keystore/cacerts and I'm denied permission.

---

### Post by Cheddardip on 2009-01-17
Sorry, reread your post and followed directions this time. It worked. Need to work on reading comprehension.

---

