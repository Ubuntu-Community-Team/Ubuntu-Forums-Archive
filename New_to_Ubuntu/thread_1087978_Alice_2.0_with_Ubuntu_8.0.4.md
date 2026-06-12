---
title: "Alice 2.0 with Ubuntu 8.0.4"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by corujask8 on 2009-03-05
Hi, I've downloaded Alice 2.0 <www.alice.org>, but I can't install or run. My notebook is Dell vostro 1000 with sempron processor.

Thank's!

---

### Post by zvacet on 2009-03-06
Let say that you downloaded package in your home directory.Type in terminal

```
 tar xvfz Alice-2.0.0.tar.gz
```

that will create folder named Alice or something similar (you can see it if you type ls in terminal;it will be with blue letters).Go to that folder with 

```
cd Alice
```

and then 

```
./run-alice
```

Instructions taken from [here.]("http://www.alice.org/index.php?page=downloads/download_alice")

Be sure that you have opengl drivers and Java installed.

---

