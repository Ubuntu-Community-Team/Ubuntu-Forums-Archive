---
title: "where are dev libs stored"
date: 2009-05-31
forum: New to Ubuntu
---

### Post by ryanmills on 2009-05-31
I'm new to both ubuntu and code::blocks. I am working on a small project that uses cURL and I have to set the lib path but have no idea where that is. Is there a normal spot for the "-dev" files to be stored?

using 8.10

*edit - forgot to add I am looking for the C++ libs

---

### Post by asmoore82 on 2009-05-31
do you have the *-dev package(s) installed for what you need?

they are separated out and must be installed explicitly on Debian based distros.

---

### Post by ryanmills on 2009-05-31
Yes the packages are installed, I just dont know where they are installed. Its the location of the files installed by the .deb I need.

---

### Post by RedSquirrel on 2009-05-31
```
dpkg -L *package-name*
```

---

### Post by oldos2er on 2009-05-31
You can use Synaptic Package Manager to find out where each file in a package is installed to. Click Status (in the lower left corner), Installed; right-click on a package, Properties, Installed Files.

---

### Post by ryanmills on 2009-05-31
thanks thats what I was looking for

---

### Post by Tibuda on 2009-05-31
My /usr/include got many *.h files

---

