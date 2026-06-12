---
title: "Query apt-get for program version"
date: 2009-10-08
forum: New to Ubuntu
---

### Post by Limitlesschannels on 2009-10-08
Hey all,

Is there a way to ask apt-get for the program version within the repos before installing it?

---

### Post by halitech on 2009-10-08
this should work
```
sudo apt-cache policy <package_name>
```

---

### Post by diesch on 2009-10-08
```
apt-cache policy PACKAGE_NAME
```

---

