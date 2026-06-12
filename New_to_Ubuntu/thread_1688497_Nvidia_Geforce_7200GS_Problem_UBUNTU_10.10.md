---
title: "Nvidia Geforce 7200GS Problem UBUNTU 10.10"
date: 2011-02-15
forum: New to Ubuntu
---

### Post by prob70 on 2011-02-15
Hi Guys,

I am very new to UBUNTU and need your help with this really annoying problem I have with this graphics card. I have just installed Ubuntu 10.10 and the maximum screen resolution I get is 1024 x 768 and unable to use any of the fancy graphics options.
When I boot up I get a small cicuit board icon in the top right hand corner of the screen which is telling me a driver is required and it gives me 2 options.
Option 1: Driver version 173
Option 2: Driver version 96 (recommended)

I have first installed the recommended one and re-booted. The startup sound is heard but the monitor switches off and I get NO SIGNAL on the screen. I re-installed UBUNTU from scratch as I could not see anything on the screen and then installed version 173. Exactly the same problem occured. 
I have been to the Nvidia web site and selected all the details for the driver. If I click on agree and download, all i get is a new web page of text. If I right click and save as (using widows so I can download the file) i get NVIDIA-Linux-x86-260.19.36.run.
How do I install this driver???
A step by step idiots guide would be useful to get the above problem sorted.

Many Thanks

Paul Roberts

---

### Post by roelpaulo on 2011-05-19
> **prob70 said:**
> Hi Guys,

I am very new to UBUNTU and need your help with this really annoying problem I have with this graphics card. I have just installed Ubuntu 10.10 and the maximum screen resolution I get is 1024 x 768 and unable to use any of the fancy graphics options.
When I boot up I get a small cicuit board icon in the top right hand corner of the screen which is telling me a driver is required and it gives me 2 options.
Option 1: Driver version 173
Option 2: Driver version 96 (recommended)

I have first installed the recommended one and re-booted. The startup sound is heard but the monitor switches off and I get NO SIGNAL on the screen. I re-installed UBUNTU from scratch as I could not see anything on the screen and then installed version 173. Exactly the same problem occured. 
I have been to the Nvidia web site and selected all the details for the driver. If I click on agree and download, all i get is a new web page of text. If I right click and save as (using widows so I can download the file) i get NVIDIA-Linux-x86-260.19.36.run.
How do I install this driver???
A step by step idiots guide would be useful to get the above problem sorted.

Many Thanks

Paul Roberts

Download this 3 stuff... Install it according in order...

dkms_2.0.20.4-0ubuntu2_all.deb
nvidia-173-kernel-source_173.14.12-1-0ubuntu4_i386.deb
nvidia-glx-173_173.14.12-1-0ubuntu4_i386.deb

---

