---
title: "ubuntu"
date: 2011-02-19
forum: New to Ubuntu
---

### Post by bigmonmulgrew on 2011-02-19
Hi guys.
I'm experimenting with ubuntu server on a VPC
Would it be possible to clone the VPC hard drive to a physical had drive and run it from a real PC.

I know if I did this with windows it would be mardy about the different drivers but I'm guessing ubuntu is more flexible.

Am I correct?

---

### Post by nickleboyblue on 2011-02-19
In order for the boot sequence to run, the computer needs to know how to find the boot loader on the hard drive.  If it can't find grub, it won't even make an attempt at booting.  So, if you load the VPC hard drive into a real, physical hard drive,  it would be really difficult to get it to boot.  I'm sure there's a way, but it would be much simpler just to install ubuntu server fresh on the physical hard drive with it connected to the mother board it will be used with, install your needed programs/libraries, and copy over all the files that you need.

---

### Post by bigmonmulgrew on 2011-02-19
Thats a good point I handt considered grub. I'm sure I read an article some time ago on how to reinstall it though.

I'm asking as I currently am experimenting with setting up a home web server which will eventually be run on a hardware server.

I'd liek to get it running now though on a VPC and transferre it later.

---

### Post by JKyleOKC on 2011-02-19
When you create it in a VM, the hardware drivers installed will be those for the VM's emulated hardware. When you clone it over to a real system via imaging software, the drivers won't change, but neither will they work with the actual hardware unless you are VERY lucky. This applies to the network card(s), video, USB interfaces, and possibly even the mouse and keyboard. Video is likely to be especially frustrating since without it working it's almost impossible to tell what is going on.

That's why you'll find it much easier to install a fresh copy of the same version of the same distro on the real hardware, and then copy over your program and data files from the VM. Installing the fresh copy of the o/s will get all of the drivers compatible with the hardware during the installation process, so that when you copy the files over they'll have a much better chance of running.

---

