---
title: "Approximately when would 	2.6.34 kernel?"
date: 2010-05-23
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2010-05-23
Approximately when would Lucid get the **2.6.34** kernel? Weeks, Months, Next year?

My uname

Karmic:~$ uname -a
Linux Lexington-19-Karmic **2.6.32-22**-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux

---

### Post by Talon2 on 2010-05-23
> **Mark_in_Hollywood said:**
> Approximately when would Lucid get the **2.6.34** kernel? Weeks, Months, Next year?



Probably never.  The history of Ubuntu shows that a specific kernal release is picked for a specific operating system release.  I think I saw where the plan for Ubuntu 10.10 is to use kernel 2.6.35.

---

### Post by -humanaut- on 2010-05-23
It may be backported in Lucid probably sometime right before Meerkat launches or right after. Or possibly through a PPA.

---

### Post by wojox on 2010-05-23
You could test 10.10

```
Linux wojox-desktop 2.6.34-3-generic #10-Ubuntu SMP Wed May 19 03:21:41 UTC 2010 i686 GNU/Linux
```

---

### Post by ajgreeny on 2010-05-23
You can always simply download the appropriate **image**, **headers** and **headers generic** packages from here
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc7-lucid/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-rc7-lucid/")
and try them.  Put them in an empty folder and run ```
sudo dpkg -i *
``` from that folder and they will be installed giving you the kernel in grub which you can try out.  I tried the rc4 version on a test bed partition with no ill effects at all.

If you have one of the old ATI graphics cards, you might also like to add the xorg ppa repos to get updated packages which are apparently better for the old ATI cards which cause overheating problems in Lucid
deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) lucid main

---

### Post by sgosnell on 2010-05-23
Most people don't need the headers.  If you don't plan to compile the kernel, just get the appropriate image file and install it with gdebi.  I've been running newer kernels on top of Jaunty, Karmic, and now Lucid since Jaunty was in beta, with no ill effects at all, just the linux-image files.

---

### Post by bumanie on 2010-05-23
At one point I was running kernel 2.6.34-999 generic (development kernel) as it was the only way I could get my 3g modem working - but that now works with the present 2.6.32-22-generic. sgosnell is correct that one only needs the image and not the headers if you plan to run the 2.6.34-xx kernel.

---

### Post by nhasian on 2010-05-23
dont install release candidate 7.  the stable 2.6.34 has already been released.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/)

you will need to install 3 packages.

> For 32 bit:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634_2.6.34-020634_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634_2.6.34-020634_all.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634-generic_2.6.34-020634_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634-generic_2.6.34-020634_i386.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-image-2.6.34-020634-generic_2.6.34-020634_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-image-2.6.34-020634-generic_2.6.34-020634_i386.deb)

> for 64 bit:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634_2.6.34-020634_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634_2.6.34-020634_all.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634-generic_2.6.34-020634_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634-generic_2.6.34-020634_amd64.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-image-2.6.34-020634-generic_2.6.34-020634_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-image-2.6.34-020634-generic_2.6.34-020634_amd64.deb)

please install in order listed.  Then run from a from a terminal afterwards:

```
sudo update-grub
```

reboot.  to confirm you are running the new kernel type in a terminal:

```
uname -a
```

---

### Post by Mark_in_Hollywood on 2010-05-23
My purpose in asking about the newer kernel is to obtain a -working- module for the AMD K10Temp and that will allow LM-Sensors to provide me with CPU Temp. Currently, with whatever sensors that sensors-detect can use, I have only the temps of the GPU (Evga 9500GT) and the Hard Disk (Seagate ST3400620NS).

From both an efficiency as well as a "safety" viewpoint, as end user, I want to change as little as possible to accomplish this. That makes a "safe" upgrade as well as, by doing as little as possible (meddling in my OS), and "doing no harm" first.

My (very limited) understanding of the K10Temp module is that it is in-built into the Linux kernel as of 2.6.34. Would I be wrong in thinking that it would then be in-built as well in 2.5.35?

---

### Post by sgosnell on 2010-05-23
Features seldom get dropped from later kernels.  It's perfectly safe to install newer kernels, because you can always boot from any kernel still installed.  You can install the .34 kernel, and if you have problems just boot from the default kernel.  You can easily remove kernels via Synaptic, as long as you aren't booted to the kernel you intend to remove.  I would advise installing the .34 kernel and trying it out.  I like it a lot.  If it doesn't do what you want you can always remove it, and you can also install the .35 kernel over it when it is released.  That will just result in the ability to boot to the .35 kernel in addition to the .34 kernel and whatever you already have installed.  I tend to remove older kernels after I insure that the newer kernel works ok, just to save space and remove clutter, but I usually keep the default kernel for the OS version I have installed, although I seldom boot to it.  It's just a final safety fallback.

---

### Post by Mark_in_Hollywood on 2010-05-23
To: nhasian

You seemed to innately understand what I was wanting. I followed your post. I have the last part of the K10Temp module working. Mostly.

As this is a 4-core CPU, I am seeing one core running at 262 degrees F., but that doesn't make me concerned as the other cores are running at 84 and 95 degrees F.

Fan speed is back, too, and that's an important one for me.

Thank you all, community. I'm marking this as "solved".

---

### Post by cayhorstmann on 2010-06-03
Actually, you don't need to run update-grub; the kernel install script will do that for you. 

By default, Lucid does not show your boot options if you have nothing but Linux on your machine. [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) has instructions for getting the kernel choice option on boot, so that you can boot into an older kernel and remove the newer one. (And then you will need to run update-grub :-))

---

### Post by sgosnell on 2010-06-03
Actually, if you remove the old kernel through Synaptic, it updates grub for you.  No need to run update-grub unless you do the removal manually, which I don't think is a good idea.

---

### Post by aselvan on 2010-06-13
Does anyone know when 2.6.34 will be available as part of update?
Thanks
-Arul

---

### Post by Sef on 2010-06-13
> Does anyone know when 2.6.34 will be available as part of update?

It won't be as has been noted.  Some aspects of that kernel has been backported into Ubuntu's Lucid kernel.

---

### Post by afrodeity on 2010-07-22
Just a quick question: 

I manually install my nvidia drivers and obviously installing the above kernel requires me to do a nvidia install.

The installer reports that the kernal was compiled using an earlier GCC version which is not the GCC version I have installed. 

It then asks whether I wish to overide and/or suggests I change the GCC environment variable.

Is this something I should be worried about with this kernel?

---

