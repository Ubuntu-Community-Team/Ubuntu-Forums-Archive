---
title: "Uninstalling a software installed from deb"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by Rany Albeg on 2009-03-19
Hi all ,

I was always installing softwares with apt-get .
yesterday I installed 'LimeWire' from a deb file.

Now i want to remove it and i dont know how.

Thanks.

---

### Post by bruno9779 on 2009-03-19
You should be able to see the .deb package for limewire in synaptic

---

### Post by khelben1979 on 2009-03-19
```
sudo apt-get remove limewire
```

---

### Post by mikewhatever on 2009-03-19
It's **sudo dpkg -r limewire**, or whatever the package is named.

---

### Post by sahabcse on 2009-03-19
Hi

For permanently removing the packages run

suod apt-get purge package-name

For more information follow below url

[http://sahabm.blogspot.com/2009/01/package-management-debian-and-ubuntu.html](http://sahabm.blogspot.com/2009/01/package-management-debian-and-ubuntu.html)

---

### Post by khelben1979 on 2009-03-19
> **mikewhatever said:**
> It's **sudo dpkg -r limewire**, or whatever the package is named.

Hey, you! My solution also works. :popcorn:

---

### Post by billgoldberg on 2009-03-19
> **khelben1979 said:**
> ```
sudo apt-get remove limewire
```

Yep, or just search for it in synaptic.

---

### Post by Rany Albeg on 2009-03-27
Thanks for helping.
have a nice day.

---

