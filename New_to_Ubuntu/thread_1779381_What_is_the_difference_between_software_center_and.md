---
title: "What is the difference between software center and synaptic pkg manager?"
date: 2011-06-10
forum: New to Ubuntu
---

### Post by TAspr on 2011-06-10
Ad stated above, what is the difference between using the Ubuntu sofware center and the synaptic package manager, and what things could you use them for?  I know that the software center gets you software, but the package manager seems difficult to use for sure.  

Maybe someone can layout the steps on using the package manager??  Please?

---

### Post by oldos2er on 2011-06-10
They're both graphical front-ends for the APT system ([http://en.wikipedia.org/wiki/Advanced_Packaging_Tool](http://en.wikipedia.org/wiki/Advanced_Packaging_Tool)), so they have similar functions. The Software Center has a dumbed-down (if you will) interface which hides info from its user and chokes on certain errors (e.g. authentication errors); Synaptic doesn't have these problems.

---

### Post by mcduck on 2011-06-10
The Software Center is intended as user-friendly tool for installing and uninstalling packages, while Synaptic s a full-featured package management tool that gives you better way to browse through all packages instead of just programs, and handles more advanced package management tasks like fixing broken packages, pinning packages to a certain version or forcing the install of older version. And of course shows detailed information about the package status, contents, dependencies, installed files and so on. 

Both, like oldos2er said, are frontends to the same package management system, apt. Only built for different purposes, one to make installing and uninstalling your desktop software as easy as possible, and one to serve as powerful tool for all your package management needs. :)

---

