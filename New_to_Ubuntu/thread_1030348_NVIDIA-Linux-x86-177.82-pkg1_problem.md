---
title: "NVIDIA-Linux-x86-177.82-pkg1 problem"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by bindkeeper on 2009-01-04
Hi 
I'm trying to install drivers for my nVIDIA GeForce 8400 GS on Ubuntu 8.04.
After installation of the driver from nVIDIA's package and starting X I'm getting: "Ubuntu is running in low-graphic mode" screen.

these my steps done so far:

download the NVIDIA-Linux-x86-177.82-pkg1.run

installed build essential from synaptic

ctrl+alt+f1

login + pass

```
sudo /etc/int.d/gdm stop
```

from the directory with the package  ```
 sudo sh NVIDIA-Linux-x86-177.82-pkg1.run

```
the menu told me that no precompiled kernel was found, but successfully completed the installation.
```
startx
```
and now I'm geting the "Low graphic mode"

the output of cat /etc/X11/xorg.conf | grep Driver is

```
 	Driver		"kbd"
	Driver		"mouse"
	Driver		"nv"

```

I'm assuming the "nv" indicates that there is no driver installed.

---

### Post by Bachstelze on 2009-01-04
First, uninstall the drivers:

```
sudo sh NVIDIA-Linux-x86-177.82-pkg1.run --uninstall
```

and then install them The Ubuntu Way&#8482;:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by sadaruwan12 on 2009-01-04
I don't think you need to install that driver from Nvidia 'cos Ubuntu repos do contain the needed driver just go to System -> Administration -> Hardware Drivers from there you can enable the proprietary drivers for your graphic card and thats it no need to run driver package from nividia 'cos it some time recs your OS.

---

### Post by Bachstelze on 2009-01-04
> **sadaruwan12 said:**
> thats it no need to run driver package from nividia 'cos it some time recs your OS.

No, it doesn't (whatever the heck "recs" means, but I don't think it's something good). It just requires a bit more knowledge of how Linux and Xorg work.

---

### Post by bindkeeper on 2009-01-04
I think I have already rec my OS because I don't have the "Hardware Drivers" in System -> Administration :) and it was there a hour ago

---

### Post by bindkeeper on 2009-01-04
OK I reinstalled the jockey-gtk and the "Hardware Drivers" is  back.
I also had to install the Linux-restricted-modules.
then did the installation from "Hardware Drivers"
now it seems that the login window "bigger" than my desktop window so I can only see the upper left part of the login window.

---

