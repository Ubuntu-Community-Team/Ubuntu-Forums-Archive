---
title: "Google Earth flickers and not just that"
date: 2009-08-16
forum: New to Ubuntu
---

### Post by al.adab on 2009-08-16
Just installed Google Earth (followed directions given at the Ubuntu 9.04 guide 

[I]sudo apt-get install googleearth-package
make-googleearth-package --force[/I]

I turned off the Atmosphere setting and I don't have Compiz enabled. Google Earth flickers, white boxes appear and disappear in the middle of it, and it even "takes over" my browser or open office (it just occupies part of the screen while I'm using another application, but just occasionally). 

Under "troubleshooting" in the same guide (and I'm not sure this is related to my problem) it's suggested renaming libcrypto.so.0.9.8 into libcrypto.so.0.9.8.bak (?). The thing is that - if this were a solution - when I give the command *cd ~/google-earth* I get "no such "no such file or directory". Google Earth is indeed in File System...

---

### Post by 3rdalbum on 2009-08-16
~/ means "your home directory". Just a / means "the filesystem".

I think Google Earth generally installs into /opt, so you'd do:

```
cd /opt/google-earth
```

---

### Post by al.adab on 2009-08-17
sorry neither *cd ~/google-earth* nor *cd /opt/google-earth* seem to work (I did replace the *~* with my home directory name in every possible fashion I could think of, but still it doesn't work. Say the name of my home directory is *amr*, what should the command in terminal look like to rename that file?

---

### Post by Technoviking on 2009-08-17
medibuntu has a Google Earth package that fix many problems I have had in the past with Google Earth.

T-V

---

### Post by al.adab on 2009-08-20
tried the medibuntu...I'm afraid it made no difference. It still flickers and the whole thing. Graphics are working correctly on this computers, so I don't understand what's going on.

---

### Post by philinux on 2009-08-20
Flickering is due to the graphics card and driver. 

Sometimes compiz. Try turning it off.

What are your pc specs?

---

### Post by Grenage on 2009-08-20
Do you get any graphical glitches on anything else 'graphically intensive'?  Games or full-screen video, etc?  I'd personally be thinking drivers here.

---

### Post by al.adab on 2009-08-20
If it's the graphic card the only solution is to replace it, I guess?
The (relevant) specs are: 

Dell Vostro 1310
Processor: Intel Core 2 Duo T8100 (2.1GHz)
Memory: 2GB - 2 DIMM (DDR2-667) (4GB max) 
HDD: 160GB 5400RPM HDD 
Graphics: 128MB NVIDIA GeForce 8400M G

---

### Post by LowSky on 2009-08-20
what driver are you using for your graphics card?

Are you using compiz?

I suggest using the ewest driver and turning off desktop effects like compiz to stop the problem

---

