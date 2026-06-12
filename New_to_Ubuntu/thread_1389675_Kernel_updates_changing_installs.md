---
title: "Kernel updates changing installs"
date: 2010-01-24
forum: New to Ubuntu
---

### Post by carbonbased on 2010-01-24
Is there a way that I can go about installing my video card drivers so that when a kernel update gets installed I don't have to start over again with the driver installation?

---

### Post by Greenwidth on 2010-01-24
What card and driver is it?

For Nvidia - add the ppa:
[https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa)

---

### Post by carbonbased on 2010-01-24
> **Greenwidth said:**
> What card and driver is it?

For Nvidia - add the ppa:
[https://launchpad.net/~nvidia-vdpau/+archive/ppa]("https://launchpad.net/%7Envidia-vdpau/+archive/ppa")

Card: Nvidia GTS 250
Nvidia driver: NVIDIA-Linux-x86-190.53-pkg1.run

Drive came form Nvidia's website. What's from Ubuntu is not up to date, I guess, as it doesn't work.
-------

---

### Post by Greenwidth on 2010-01-24
Add the ppa as a software source in System > Admin > Software Sources, dkms will rebuild modules when you get a new kernel.

There's 195.30 in there too, which might be good for you as you have a recent card. They are beta, but work fine for me (not the same card), might be worth a go, prob best to have a look at the changelog on the Nvidia site.

---

