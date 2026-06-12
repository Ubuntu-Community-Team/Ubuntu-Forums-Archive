---
title: "Graphic Card not being found anymore?"
date: 2009-09-21
forum: New to Ubuntu
---

### Post by Rave Gloves on 2009-09-21
After having some problems i decided to get a fresh install of ubuntu 9.04. After everything was installed and stuff i went to activate my NVidia 9300 drivers but the recommended drivers werent there, is there any way i can acitvate these maualy?

---

### Post by hal10000 on 2009-09-22
You may install the needed packages manually:
```

sudo apt-get install nvidia-180-kernel-source nvidia-common nvidia-kernel-common nvidia-glx-180 nvidia-180-libvdpau nvidia-settings

```
You then have to reboot

---

### Post by NoaHall on 2009-09-22
Or try updating your system, then rebooting. I had the same problem on a computer, updating/rebooting worked for me

---

### Post by Rave Gloves on 2009-09-22
> **hal10000 said:**
> You may install the needed packages manually:
```

sudo apt-get install nvidia-180-kernel-source nvidia-common nvidia-kernel-common nvidia-glx-180 nvidia-180-libvdpau nvidia-settings

```
You then have to reboot

> **NoaHall said:**
> Or try updating your system, then rebooting. I had the same problem on a computer, updating/rebooting worked for me


im going to do the first one, the reason i dont want to update my system is beacuse whenever i do my internet stops working, so i have set my updates to security only.

Cheers guys, i will tell you if it works when i get back from work.

---

### Post by Rave Gloves on 2009-09-22
> **hal10000 said:**
> You may install the needed packages manually:
```

sudo apt-get install nvidia-180-kernel-source nvidia-common nvidia-kernel-common nvidia-glx-180 nvidia-180-libvdpau nvidia-settings

```
You then have to reboot

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nvidia-180-kernel-source

```  

Any ideas?

---

### Post by 3rdalbum on 2009-09-22
> **Rave Gloves said:**
> ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nvidia-180-kernel-source

```  

Any ideas?

Connect to the Internet, and click the Reload button in Synaptic (or do sudo apt-get update).

---

### Post by Rave Gloves on 2009-09-22
> **3rdalbum said:**
> Connect to the Internet, and click the Reload button in Synaptic (or do sudo apt-get update).

I done both , i reloaded my synaptic and it downloaded some stuff i also sudo apt-get update and it also downloaded stuff, then i tried the code again and im getting the same error/

---

### Post by Rave Gloves on 2009-09-23
Bump, still need help

---

### Post by Rave Gloves on 2009-09-23
I fixed it, i just went for it and updated my drivers, Luckily my internet is still working. :]

---

