---
title: "e100 intel driver"
date: 2005-08-21
forum: Networking &amp; Wireless
---

### Post by tieflingrogue on 2005-08-21
I had exactly the same problem with fedora core 4: my ethernet card isn't being detected.  I'm running a dell 5100c with an Intel PRO/100 VE adapter.   With FC4, I just downloaded the updated e100 driver from Intel along with kernel source and everything worked.

With ubuntu,  I do the "make install"  command for driver, it says "kernel source not found". I can't seem to find all of the kernel source files.  I did find linux-headers-2.6.10-5-686, but seems like i need linux-headers-2.6.10-5.  I can't access the internet via ubuntu, so i can't do something like sudo apt-get kernel-source.

---

### Post by h4rdc0d3 on 2005-08-23
Sorry, I don't know enough to tell you which packages you need... but you can browse and search ubuntu packages at [http://packages.ubuntu.com/]("http://packages.ubuntu.com/"). Also, you can use that site to download the .deb files. Once you have the .deb's you can install them with (in order to bypass apt):
 ```
dpkg -i package.deb
```

---

### Post by chili555 on 2005-08-23
[QUOTE=tieflingrogue]I had exactly the same problem with fedora core 4: my ethernet card isn't being detected.  I'm running a dell 5100c with an Intel PRO/100 VE adapter.   With FC4, I just downloaded the updated e100 driver from Intel along with kernel source and everything worked.

With ubuntu,  I do the "make install"  command for driver, it says "kernel source not found". I can't seem to find all of the kernel source files.  I did find linux-headers-2.6.10-5-686, but seems like i need linux-headers-2.6.10-5.  I can't access the internet via ubuntu, so i can't do something like sudo apt-get kernel-source.[/QUOTE]
 After sudo updatedb, when I do locate e100 on my freshly installed system, I see that the e100 module seems to be present already!

I suggest trying to load it with modprobe e100 and then see if  you can activate eth0 through System => Administration => Networking.

---

