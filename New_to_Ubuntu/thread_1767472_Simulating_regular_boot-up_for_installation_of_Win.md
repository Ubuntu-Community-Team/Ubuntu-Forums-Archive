---
title: "Simulating regular boot-up for installation of Windows"
date: 2011-05-25
forum: New to Ubuntu
---

### Post by HrKristian on 2011-05-25
Hi! 
I'm curious, is there a way to -as the title says- simulate a computer boot-up, so as to install in this case Windows 7 while in the OS. 

I've been reading up on VMware, and there's some... interesting stuff there, but I couldn't find anything specific on emulating a boot-up with a mounted, bootable, .iso.

If the above is at all possible, or if I didn't make it clear what it is I want exactly, here it is:

I have partitioned my HDD, an ext4 partition for my Ubuntu system, a swap space, an NTFS "stuff" disk (guess what's on it, yep, stuff) to be shared by both OSs, and one NTFS partition for Windows 7.
I would install w7 the regular way, but the DVD-reader on my laptop is f*ed up, and I don't have a USB stick with sufficient space.

So, what I wish to do -if at all possible- is to install Windows 7 from a .iso file, while in Ubuntu, onto the separate NTFS partition.

So, is this possible?

Regards,
Kristian

---

### Post by psusi on 2011-05-25
If you want to install and run windows in a virtual machine, then VMware or another virtual machine like virtualbox or qemu is the way to go.  I've not used vmware in years so I'm not sure of the details, but somehow you configure it to emulate a cdrom and either point it to /dev/cdrom to present your actual cdrom to the virtual machine, or you can point it to an iso file instead.

It sounds like you don't want to run it in a vm though, but actually install it to the hard drive so you can dual boot.  In that case you will need to get a working dvd drive.

---

### Post by Mark Phelps on 2011-05-26
I went to a Win7 forum to look this up for you and while they had a tutorial on installing Win7 without requiring an optical drive or USB stick, they did require Win7 installed in order to do this.  

So, I don't believe it's possible to install Win7 from an ISO -- but I've not actually tried it, so I could be wrong.

---

### Post by seawolf167 on 2011-05-26
> **HrKristian said:**
> So, what I wish to do -if at all possible- is to install Windows 7 from a  .iso file, while in Ubuntu, onto the separate NTFS partition.

See the previous posts for the other answers, as to this, Mark Phelps has it correct. In order to install Windows 7 from an iso while booted, you would have to be inside a Windows environment, extract the iso file, then run the setup.exe program contained within the extracted directory. This wouldn't work while booted into Ubuntu unless you used a program like VirtualBox to mount the iso as the installation medium (i.e. install dvd) and install a full virtual OS.

---

