---
title: "JeOS as a Host for VMWare 2.0.1"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by tatodc on 2009-07-20
I was just trying to improve my home server, and while I was reading to best practices to implement VMWare, I find the JeOS option, it is not clear in any documentation if it is a good thing to put JeOS as the Host OS or it is only useful as the guest sistem for the virtual machines.

If not, what is a good thing to do, to have Ubuntu 9.04 full server install or just the minimal server install?

Thanks in advance for the replys.

---

### Post by Mighty_Joe on 2009-07-20
JeOS is a guest, not a "bare metal" OS:

> JeOS is a specialised installation of Ubuntu Server Edition with a tuned kernel that only contains the base elements needed to run within a virtualized environment. 

[Ubuntu Server Edition JeOS]("http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos")

Exactly what are you trying to "improve" by using VM's?

---

### Post by tatodc on 2009-07-20
I bought a server a year ago and have installed Ubuntu 8.04 and VMWare 2.0, now I saw that there are new versions of software so I decided to upgrade it, in that process, I realize that there are many things I didn't know. One of them was JeOS.

If anyone has a good guide with recommendations to install a Ubuntu & VMWare it will be more than appreciated

---

### Post by Mighty_Joe on 2009-07-21
> **tatodc said:**
> If anyone has a good guide with recommendations to install a Ubuntu & VMWare it will be more than appreciated

VMWare *what*?  VMWare has about a dozen products, each aimed at a different segment of the industry.  
There's information in the [Ubuntu Community Documentation]("https://help.ubuntu.com/community/VMware/Server") about installing VMWare Server and setting up a VM.

---

