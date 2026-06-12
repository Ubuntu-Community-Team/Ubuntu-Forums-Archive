---
title: "Where are applications stored"
date: 2010-11-04
forum: New to Ubuntu
---

### Post by wannabeterminalpro on 2010-11-04
Where are the ubunutu software center applications physically stored? I can't find them physically anywhere in my /home drive or by using the search tool.

---

### Post by Paul820 on 2010-11-04
The main file goes in /usr/bin, all the rest are in other folders in / (root). If you want to find a specific program, open a terminal and enter
> whereis nameOfFile
Changing nameOfFile to the name of your file.

---

### Post by oldos2er on 2010-11-04
I don't know about Software Center, but in Synaptic Package Manager you can see where each file in a package is installed by right-clicking on one, Properties, Installed Files.

---

