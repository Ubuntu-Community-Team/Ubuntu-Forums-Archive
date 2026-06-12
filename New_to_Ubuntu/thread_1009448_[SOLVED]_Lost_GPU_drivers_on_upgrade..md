---
title: "[SOLVED] Lost GPU drivers on upgrade."
date: 2008-12-12
forum: New to Ubuntu
---

### Post by joemacnz on 2008-12-12
I have lost my nVidia drivers on my move from Hardy to Intrepid. 


It is a GE Force FX 5700, and I have had no issues to date.

I have tried downloading the 177 driver via synaptic, but when I look at system>administration > hardware drivers, I am only offered the 173 and 96 drivers. I have selected the 173 driver to install, but on reboot I am still getting the error messages telling me that the drivers are not found.

---

### Post by tomtom1982 on 2008-12-12
Did you try to install the package with

```
sudo apt-get update && sudo apt-get install nvidia-glx-173
```

?

---

### Post by Sarmacid on 2008-12-12
Use envyng to download and update your drivers instead of synaptic.

---

### Post by joemacnz on 2008-12-12
This is what I get

>  Reading state information... Done
nvidia-glx-173 is already the newest version. 


The error message on start up says :
 Ubuntu is running in low graphics mode

The following error wass encountered. You may need to update your configuration to solve this.


> (EE) NVIVIA(o) Failed to initialise the NVIVIA kernel module. Please ensure that there is a supported NVIDIA GPU in this system and that the NVIDIA device files have been created properly. Please consult the NVIDIA readme for details ****aborting *** 
Screens found, but none have usable configureation. 

---

### Post by joemacnz on 2008-12-12
Envyng returns 

>  EnvyNG has detected that the headers for your kernel are missing and cannot be installed 

---

### Post by joemacnz on 2008-12-12
Okay, I think that may have sorted it. The error message was from EnvyNG -g.

EnvyNG -k seemed to have no issues.

No error messages on reboot, so fingers crossed.

The screen looks quite different, but I can live with that.

---

### Post by tomtom1982 on 2008-12-12
If you get message that the kernel source is missing, try to install with

```
sudo apt-get install nvidia-173-kernel-source
```

---

