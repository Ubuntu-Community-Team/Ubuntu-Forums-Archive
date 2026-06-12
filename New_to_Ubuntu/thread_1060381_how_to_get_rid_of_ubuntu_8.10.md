---
title: "how to get rid of ubuntu 8.10?"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by iseeclouds on 2009-02-04
i have 3 hard drive partitions (1:vista, 2:data, 3:ubuntu). how can i entirely get rid of ubuntu on my hard drive? don't worry, i won't quit using linux. i just want to replace 8.10 with ubuntu studio 8.04. because i need the rt-kernel and other audio stuff for running renoise. so, what's an easy way to do this? i don't need any backups form the ubuntu part of my hard drive. just want it gone so i can install studio.

---

### Post by taurus on 2009-02-04
Boot from the LiveCD and use gparted (System -> Administration) to delete the partitions your harddrive where Ubuntu is.

---

### Post by bgerlich on 2009-02-04
Just put in the Studio install media and install over the Ubuntu partition. The installer will create new grub system list and such, you shouldn't have any problems if you select the right partition. Check what partition your ubuntu system uses before you start the installation process.

---

