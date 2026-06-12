---
title: "ubuntu software center wont load software"
date: 2011-06-19
forum: New to Ubuntu
---

### Post by &lt;(-.-)&gt; on 2011-06-19
When i open the software center it opens fine but when i search something, go to one of the categories, or try to look at previously installed software, it will just show the loading animation and not any software.

---

### Post by oldos2er on 2011-06-19
Can you run ```
sudo apt-get update
``` in a terminal and post the output here?

---

### Post by &lt;(-.-)&gt; on 2011-06-19
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_restricted_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

dont know if that will help.

---

### Post by Rubi1200 on 2011-06-19
Hi,

Make sure all package managers are closed and then open a terminal (Ctrl+Alt+T) and run the following commands:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

---

### Post by &lt;(-.-)&gt; on 2011-06-19
great it worked thanks

---

### Post by Rubi1200 on 2011-06-20
Excellent! Glad you got it sorted out :-)

---

