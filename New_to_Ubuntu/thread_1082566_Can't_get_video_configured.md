---
title: "Can't get video configured"
date: 2009-02-27
forum: New to Ubuntu
---

### Post by Vunutus on 2009-02-27
I'm using Ubuntu 8.10 and am having some troubles getting my video configured. I use an NVIDIA card, and any time I try to activate a driver, it defaults to low graphics mode and I have to run xfix to get things back. I've tried installing several different driver versions using both EnvyNG and the Hardware Drivers utility.

What gives?

---

### Post by overdrank on 2009-02-27
> **Vunutus said:**
> I'm using Ubuntu 8.10 and am having some troubles getting my video configured. I use an NVIDIA card, and any time I try to activate a driver, it defaults to low graphics mode and I have to run xfix to get things back. I've tried installing several different driver versions using both EnvyNG and the Hardware Drivers utility.

What gives?

What is the model of the nvidia graphics? I have seen threads on intrepid with the older nvidia cards.

---

### Post by Vunutus on 2009-02-28
My card is the nvidia 6800

---

### Post by overdrank on 2009-02-28
> **Vunutus said:**
> My card is the nvidia 6800

Ok after installing the drivers and using the xfix option you are still left without the nvidia drivers? 
Have you tried to install the nvidia driver manually? 
The only downfall to this is if the kernel is updated then you will have to reinstall the nvidia drivers.

---

### Post by Vunutus on 2009-02-28
Doing a manual install apparently worked. Either it was that or the fact that the downloaded version from nvidia was 180, while the highest offered by the graphical utilities was 177.

Oh well, thanks.

---

