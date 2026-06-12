---
title: "How to get package installation locations"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by jpongin on 2009-01-21
I'd like to know the location of each installed packaged file after installing the package via apt-get.  

And, I would like to do all of this from the command line only.

For example, if I run the following command:
> sudo apt-get install apache2.2-common

After installation, where can I go back to find all files and its locations for a apache2.2-common via the command line?

Thanks in advance.

---

### Post by Michael.Godawski on 2009-01-21
some nice commands:
```
dpkg --get-selections
``````
dpkg --get-selections | grep package
``````
dpkg -L nameofpackage
```

---

### Post by jpongin on 2009-01-21
Fabulous!

dpkg -L nameofpackage

was exactly what I was looking for.

Thanks again.

---

