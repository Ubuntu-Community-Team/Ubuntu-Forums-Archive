---
title: "Need help finding drivers for my Intel Graphics Card"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by cheese123 on 2009-02-11
I'm currently trying to install Compiz Fusion, I've already enter the command in the terminal to install it, but I need to find drivers for my graphics card. When I got to System>Admin>Hardware Drivers I have nothing listed. Help would be appreciated.

---

### Post by avtolle on 2009-02-11
Generally, for intel graphics cards the drivers are included within the kernel, thus no listing. Which card do you have?

---

### Post by BDNiner on 2009-02-11
Yes they are included in the kernel. And since they are not closed source drivers they would not show up in the 'hardware' tool. Are you getting any specific error messages?

---

### Post by avtolle on 2009-02-11
Does [http://www.ubuntu.com/getubuntu/releasenotes/810#Hangs%20with%20desktop%20effects%20on%20Intel%20830MG%20and%20845G%20video%20cards](http://www.ubuntu.com/getubuntu/releasenotes/810#Hangs%20with%20desktop%20effects%20on%20Intel%20830MG%20and%20845G%20video%20cards) apply to you?

---

### Post by kevmitch on 2009-02-11
Unless you have one of the new GMA500 chips found in some of the newer subnotebooks, the drivers should be included with the kernel/X11 by default. The Ubuntu "graphics card drivers" really refer to the proprietary nvida or ati drivers.

Though they may not have the raw horsepower craved by gamers, Intel chips are the only ones that have free and open drivers. As a result, they are usually the best supported and the first to see new features like the GEM kernel graphics memory manager, or kernel mode setting. So give yourself a pat on the back for buying Intel and supporting open source.

---

### Post by cheese123 on 2009-02-11
I have an Intel Mobile 965 Express Chipset, Intel 3100

---

### Post by BDNiner on 2009-02-11
Yes, your chipset should be supported. are you getting any specific error messages when you try to start compiz? Try typing 
```

compiz --replace

```
from a terminal window and post the output.

---

### Post by cheese123 on 2009-02-11
> **BDNiner said:**
> Yes, your chipset should be supported. are you getting any specific error messages when you try to start compiz? Try typing 
```

compiz --replace

```
from a terminal window and post the output.

It says 
```

Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz: 423: /usr/bin/compiz.real: not found

```

---

### Post by BDNiner on 2009-02-12
sorry about the delay in getting back to you. It seems like compiz is no longer installed. Can you open Synaptic and search for compiz and install/reinstall the software.

---

