---
title: "Graphics Driver - 8800GTX"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by NayC on 2009-05-02
Hi,

Absolute beginner with ubuntu! I have just installed it recently in a VMWare VPC to have a play as I really want to learn how to use linux.

Basically I have an nVidia GeForce 8800GTX and I'm trying to install drivers. I believe I have installed the NVIDIA Binary.Org X 173 which installed fine, but after thoughouly looking at the list of supported GPU's I dont think it actually supports mine, although supports every other form of 8800 card I can think of!

So I did a little search and have downloaded (I think) the driver for 32-bit linux from the official nVidia site. It told me to download it, which has opened a page with a lot of code and then firefox says in the bottom right "Done". It then tells me to type (which I assume is in the terminal?) "sh NVIDIA-Linux-x86-180.51-pkg1.run". I tried this and the terminal is saying cannot open "(the file name)"...

Am I doing this correctly? I just want to play with the desktop features...

Is there a way to properly check what drivers are installed, look for updates etc?

Cheers, Nay.

---

### Post by NayC on 2009-05-02
I accidentally ran into this just now in the Ubuntu Pocket Guide pdf. It says under a VPC like VMware, although great for testing and even using linux, some features such as desktop visual effects wont work? I take it this is why then.

May have to try on a partitioned dual boot then!

---

### Post by Cheesemill on 2009-05-02
If you've got Ubuntu installed on a VM, then it cannot see your graphics card at all. Instead it sees the virtual graphics card presented to it by VMware, the drivers for this can be installed by installing VMware Tools on the virtual Ubuntu OS.

If you do go for the dual-boot option, you *shouldn't* have to download anything from the  nVidia website. All you need to do is go to System > Administration > Hardware Drivers and select the appropriate driver.

Cheesemill

---

