---
title: "need to purge some applications"
date: 2010-07-17
forum: New to Ubuntu
---

### Post by AndyP79 on 2010-07-17
Hi Ya'll,
 Can someone tell me what I need to type in the terminal to purge both DockbarX and Avant Window Navigator please. I am going to remove the PPAs, but I want to make sure all associated files are gone so I can start them clean.
Thanks

---

### Post by Linye on 2010-07-17
Check this.

[http://www.webupd8.org/2010/04/ppa-purge-now-available-via-getdeb.html](http://www.webupd8.org/2010/04/ppa-purge-now-available-via-getdeb.html)

---

### Post by sad_iq on 2010-07-17
From Synaptic...use the search box to find your package, right click on it and select "Mark for complete removal"
From the terminal: sudo apt-get remove --purge <insert_name_of_package_here>

---

### Post by cariboo on 2010-07-17
You can use ppa-purge to remove the programs and their files, as well as removing the ppa. Ppa-purge is in the repositories. Usage:

```
ppa-purge -p <ppa name>
```

---

