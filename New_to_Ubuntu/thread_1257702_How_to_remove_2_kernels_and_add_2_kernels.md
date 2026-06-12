---
title: "How to remove 2 kernels and add 2 kernels"
date: 2009-09-04
forum: New to Ubuntu
---

### Post by eddski on 2009-09-04
I have kernel dirs in my /etc/src dir and would like to take the 2 older ones out of my menu.lst file and the 2 newer ones. I know how to edit menu.lst, but I just don't know what information to put in there. I know to do only one at a time to make sure it works, but like I said I don't know what info to put in menu.lst. Thanks

---

### Post by xir_ on 2009-09-04
> **eddski said:**
> I have kernel dirs in my /etc/src dir and would like to take the 2 older ones out of my menu.lst file and the 2 newer ones. I know how to edit menu.lst, but I just don't know what information to put in there. I know to do only one at a time to make sure it works, but like I said I don't know what info to put in menu.lst. Thanks


Try and remove them from synaptics first, this would be a much cleaner way of removal (including automatic reconfiguration of your menu.lst). 

If they aren't in synaptics and you have compiled them yourself then in future try and compile to a .deb, this really can reduce headaches.

---

### Post by oldos2er on 2009-09-04
You can use the program checkinstall to create a deb package, which can then be installed with dpkg. See [https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

---

### Post by LewRockwell on 2009-09-04
sometimes when we edit the menu.lst file all we need to do is change one or two digits

for example, recently the kernel went from "14" to "15"

make sure you double check your work or you'll be coming back...lol!

.

---

