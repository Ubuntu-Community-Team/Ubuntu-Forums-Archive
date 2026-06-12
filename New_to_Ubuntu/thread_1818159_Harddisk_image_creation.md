---
title: "Harddisk image creation"
date: 2011-08-04
forum: New to Ubuntu
---

### Post by fbr02 on 2011-08-04
Is there anyway to clone or image a harddisk using a ubuntu live CD and then reimage a harddisk using a live CD?

---

### Post by haqking on 2011-08-04
> **fbr02 said:**
> Is there anyway to clone or image a harddisk using a ubuntu live CD and then reimage a harddisk using a live CD?


[www.clonezilla.org]("http://www.clonezilla.org")

not sure about using the ubunut liveCD to do it though

---

### Post by Matt__ on 2011-08-04
try [remastersys]("http://www.geekconnection.org/remastersys/repository/"), creates its own live disk with all your apps, settings and files as you specify.

one caveat: final squash image must be less than 4Gb (my 4.8Gb new install squashed to 1.05Gb), but I still find this the best tool to backup a modified install as I keep files on another partition.

---

### Post by lykwydchykyn on 2011-08-04
> **fbr02 said:**
> Is there anyway to clone or image a harddisk using a ubuntu live CD and then reimage a harddisk using a live CD?

If you must use the Ubuntu live CD, there are some terminal commands you can use; see this tutorial:

[http://www.howtogeek.com/howto/19141/clone-a-hard-drive-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/19141/clone-a-hard-drive-using-an-ubuntu-live-cd/)

However, there are much more user-friendly options available.  Clonezilla was mentioned, but there is also G4L, which can be used as a standalone disc or as part of the PartedMagic CD.

What are you trying to image it to?  A second attached disk, or a file on a network share, or something else?

---

