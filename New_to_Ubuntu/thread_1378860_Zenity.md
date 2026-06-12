---
title: "Zenity"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by Dibjibjub on 2010-01-11
Hi, this is my first thread in the forums, so please be nice.  
I am new to Ubuntu, or Linux for that matter, and I installed it on my old laptop as a side experiment.  I am now trying to install Zenity.  I know how to work it and what it does, but I can't find out how to install it.  I have read several guides and they don't help at all so I was wondering if you all can help me. 
In advance, thank you.... and sorry if this is in the wrong place.

EDIT:  I have the .tar.gz folder.

---

### Post by marshmallow1304 on 2010-01-11
Hello and welcome. :D


[This Zenity]("http://en.wikipedia.org/wiki/Zenity")?

2 methods:

1) Applications->Accessories->Terminal
```
sudo apt-get install zenity
```

2) System->Administration->Synaptic Package Manager
Search for zenity, right-click it, mark for installation, click Apply.

---

### Post by Dibjibjub on 2010-01-12
I tried the Synaptic Package Manager, it registered that I had it to install, but it didn't offer to install it.

---

### Post by marshmallow1304 on 2010-01-12
> **Dibjibjub said:**
> I tried the Synaptic Package Manager, it registered that I had it to install, but it didn't offer to install it.

It might be already installed.  It was for me.  If you open a terminal and issue
```
which zenity
```
and it returns
```
/usr/bin/zenity
```
then zenity is already installed.

---

