---
title: "No network manager"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by crf450x06 on 2009-01-27
Unable to access network manager . Will not allow to add/remove from disk. Ubuntu 8.10

---

### Post by stoogiebuncho on 2009-02-01
What happens when you try to start it?  Does it give an error message, or is it just not there?

---

### Post by cariboo on 2009-02-01
You really don't need network manager to connect to a network. If you need it for peace of mind, have you tried reinstalling. Open a Applications-->Accessories--Terminal and type:

```
sudo apt-get --reinstall network-manager network-manager-gnome
```

Jim

---

