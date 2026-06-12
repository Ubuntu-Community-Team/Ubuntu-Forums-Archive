---
title: "NVIDIA GeForce 6100 / nForce 430 Driver"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by Akumos on 2008-12-12
Hi all

I'm looking for a Linux driver for NVIDIA GeForce 6100 / nForce 430 onboard graphics chipset. Any ideas?

Thanks

---

### Post by overdrank on 2008-12-12
> **Akumos said:**
> Hi all

I'm looking for a Linux driver for NVIDIA GeForce 6100 / nForce 430 onboard graphics chipset. Any ideas?

Thanks

Hi and you can look under system, administration, hardware drivers :)

---

### Post by tomtom1982 on 2008-12-12
You need the nvidia-driver for this (I also have the same chipset).

On Hardy Heron you type in console:

```
sudo apt-get install nvidia-glx-new
```

on Inteprid Ibex you type

```
sudo apt-get install nvidia-glx-173
```

or

```
sudo apt-get install nvidia-glx-177
```

(Both are working wiht GeForce6100).

You also can install it via Synaptic/Adept. Just search for "nvidia-glx-new" on hardy or nvidia-glx-173 or -177 on inteprid.

---

### Post by Akumos on 2008-12-12
Will try it out, thanks.

---

