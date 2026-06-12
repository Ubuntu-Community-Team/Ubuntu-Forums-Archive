---
title: "how to burn .iso.vdi image on DVD?"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by eshant_engineer on 2009-01-01
I have downloaded virtualbox from mininova on ubuntu. After extracting it is now in .iso.vdi format. But Brasero is not able to burn this image....what should i do?

---

### Post by eshant_engineer on 2009-01-01
anybody........

---

### Post by steveneddy on 2009-01-01
I always use K3b for burning.

It should handle DVD or CD .iso just fine.

And just a little hint, it's really not a good idea to bump your thread in less than 30 minutes.

Actually you should give it a few hours before attempting a bump. It is just good forum etiquette.

Remember that **we are all volunteers here**. If you need an answer in less than 30 minutes, paid support is available.

---

### Post by eshant_engineer on 2009-01-01
sorry......
 I found it in add/remove, there it is showing that it's a cd writing program but the image is of around 2.4 GB! would it finally work for this?

---

### Post by nhasian on 2009-01-01
actually .vdi is the VirtualBox Hard-Drive Interface File.  You will need to install virtualbox in order to boot a virtual computer with a .vdi file.  for instructions on how to install the latest virtualbox follow my thread:

[http://ubuntuforums.org/showthread.php?t=1015045](http://ubuntuforums.org/showthread.php?t=1015045)

---

### Post by eshant_engineer on 2009-01-01
it's free or not?

---

### Post by Delever on 2009-01-01
VirtualBox is free, there is open source version in repositories, but I recommend Sun's closed version (follow previous poster's thread), which is free too.

Once it is installed, you can create new virtual machine and attach this file (which is disk image) as disk to it, so when you start, it boots from that image.

---

### Post by steveneddy on 2009-01-01
> **nhasian said:**
> actually .vdi is the VirtualBox Hard-Drive Interface File.  You will need to install virtualbox in order to boot a virtual computer with a .vdi file.  for instructions on how to install the latest virtualbox follow my thread:

[http://ubuntuforums.org/showthread.php?t=1015045](http://ubuntuforums.org/showthread.php?t=1015045)

I didn't que in on the fact that there was a .vdi extension on the end of that.

That's what i get for posting at 6:am

---

