---
title: "doubts regarding installing softwares"
date: 2010-09-23
forum: New to Ubuntu
---

### Post by manish411 on 2010-09-23
there r many ways to install a software -using UBUNTU SOFTWARE,SYNAPTIC PACKAGE MANAGE or through shell using APT-GET INSTALL command. I installed MINITUBE through SYNAPTIC  ,it is installed but does not play anything after searching results are coming and showing error. Is it that it requires external
libraries or dependencies . I am experiencing the same problem with LINGOT(guitar tuner) TUXGUITAR(tabs editor). My doubt is that if we install any software do  we have to download dependencies separately. IF yes how do we know what to download.

---

### Post by coffeecat on 2010-09-23
> **manish411 said:**
> My doubt is that if we install any software do  we have to download dependencies separately. IF yes how do we know what to download.

No. If you install using Synaptic, Software Centre or apt-get from the command line, all dependencies are taken care of for you. 

If you are having problems running any apps, post details, including any error message you get, and someone should be able to help you.

---

### Post by beew on 2010-09-23
Add this ppa to your sources list then update and install the latest minitube. [https://launchpad.net/~nilarimogard/+archive/webupd8]("https://launchpad.net/~nilarimogard/+archive/webupd8")

The version in the Ubuntu repo (1.1.1?) is old and probably has a bug. I remember it didn't quite work either when I installed it from the official repo. But version 1.2 works beautifully (from the ppa)

---

