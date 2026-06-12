---
title: "How to install tar.bz2 files"
date: 2010-08-31
forum: New to Ubuntu
---

### Post by calolo_nc on 2010-08-31
Hello,
I'm new to Ubuntu also to this forum

I have recently installed Ubuntu 10.04 LTS on my laptop COMPAQ Evo N800v
Everything works perfectly.

I downloaded the latest drivers from Ralink Technology RT61 (RT2561) to update my Dlink DWL-G630 PCMCIA which uses a Ralink Chipset (RT61)

Is a tar.bz2 file but I don't know what to do next ???

Can someone help me please ? Step by Step

1. How to create a folder to extract all these files into it and where to create it ??? For example /var,  /home and so on

2. After creating and extracting all the files, what to do next ???

3. How to update my Wifi Card  ??? and where to go to find the files ???

I would appreciate if you told me what to do ???

I'm looking forward to hearing from you soon     :):):)


Love Linux

---

### Post by limestone on 2010-08-31
Extract the tarball, you can do it from the terminal with
tar -xf file.tar.gz
you can create it were ever you want practically. use your desktop for easy access.

go in the new folder using 'cd' and do
./configure
make
sudo make install

You will need to have the proper dependencies installed to compile the code.

---

### Post by 3rdalbum on 2010-08-31
> **calolo_nc said:**
> Hello,
I'm new to Ubuntu also to this forum

I have recently installed Ubuntu 10.04 LTS on my laptop COMPAQ Evo N800v
Everything works perfectly.

I downloaded the latest drivers from Ralink Technology RT61 (RT2561) to update my Dlink DWL-G630 PCMCIA which uses a Ralink Chipset (RT61)

If everything works perfectly, then don't install different drivers for your hardware. If you install a driver manually rather than use the one in the kernel, then you will need to reinstall it every time there's a kernel update.

---

### Post by ilovelinux33467 on 2010-08-31
if you are installing things manually then you have to make sure that the build-essential package is installed by doing

```
sudo apt-get install build-essential
```

---

