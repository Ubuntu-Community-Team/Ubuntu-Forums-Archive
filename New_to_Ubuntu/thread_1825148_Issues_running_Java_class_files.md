---
title: "Issues running Java class files"
date: 2011-08-14
forum: New to Ubuntu
---

### Post by Emora on 2011-08-14
I'm not sure what I am looking for to open one of the Java files I have. What do I need to open it?

-Emora

---

### Post by trozamon on 2011-08-14
open a command prompt and type:

```
sudo apt-get install default-jre
```

wait for it to install, then type

```
java thefilename
```

Note that the .class is not included with the file name, and that the name is case sensitive

---

### Post by SavageWolf on 2011-08-14
Remember to mark it as executable, right click > Properties > Permissions > Allow executing file as program. Then you should be able to just double-click it.

---

### Post by Emora on 2011-08-14
> **trozamon said:**
> open a command prompt and type:

```
sudo apt-get install default-jre
```wait for it to install, then type

```
java thefilename
```Note that the .class is not included with the file name, and that the name is case sensitive

> 
Package jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Unable to locate package default
E: Package 'jre' has no installation candidate


:confused::confused::confused:

What now?
-Emora

---

### Post by trozamon on 2011-08-15
Alright, open up synaptic and search for "jre", then install one.

Then complete the rest of my instructions

---

