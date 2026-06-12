---
title: "how to calculate dependencies for a package"
date: 2009-07-03
forum: New to Ubuntu
---

### Post by mangologin on 2009-07-03
HI guys,

How do you calculate dependencies for a package that is yet to be installed on the system,by command line.??PLz help

---

### Post by HotShotDJ on 2009-07-03
Try the -s option, for example:  sudo apt-get install -s <packagename>
> -s  No-act. Perform ordering simulation

---

### Post by mangologin on 2009-07-03
thanks for the reply,but i am having custom build packages...So it wud be a problem to use apt-get install -s for them right?

---

### Post by Rubicon_82 on 2009-07-03
[quote="mangologin"]
...i am having custom build packages...
[/quote]

Assuming this means you have obtained a *.deb package from some project's website:
```

dpkg -I <packagename>

```

---

### Post by mangologin on 2009-07-04
It basically prints the control file right?Actually am working on a project where I am planning to generate the control file ,and for that I will be needin the dependencies :D

---

### Post by austinpsycho on 2009-07-04
You're writing the software yourself?  Did you use any special libraries?

---

