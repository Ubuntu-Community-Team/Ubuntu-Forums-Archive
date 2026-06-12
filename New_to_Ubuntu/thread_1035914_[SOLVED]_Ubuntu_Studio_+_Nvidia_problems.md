---
title: "[SOLVED] Ubuntu Studio + Nvidia problems"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by Abu_Dayya on 2009-01-10
I installed Ubuntu Studio 8.04.1 on my PC which has an Nvidia 8500GT card. Then installed the driver using EnvyNG, but I keep getting low resolution. When I try to boot my machine, xserver won't start and I get this error:

Error: API mismatch: the NVIDIA kernel module has version 173.14.12, but this NVIDIA driver component has version 169.12. Please make sure that the kernel module and all NVIDIA driver components have the same version.

So, the error seems clear. How do I fix it? Do I downgrade the kernel module or upgrade the driver? and how do I do either one?

I can see from [this link]("http://www.nvidia.com/object/linux_display_ia32_180.22.html") that nvidia has released a new driver (180.22) on the 8th of January. Will downloading this driver and running the provided installation script fix this problem? Does this script include the kernel module as well as the driver?

Thanks

---

### Post by Abu_Dayya on 2009-01-10
I found this on nvidia website:

Installing the Kernel Interface

The NVIDIA kernel module has a kernel interface layer that must be compiled specifically for each kernel. NVIDIA distributes the source code to this kernel interface layer, as well as precompiled versions for many of the kernels provided by popular Linux distributions.

When the installer is run, it will determine if it has a precompiled kernel interface for the kernel you are running. If it does not have one, it will check if there is one on the NVIDIA FTP site (assuming you have an Internet connection), and download it. If one cannot be downloaded, either because the FTP site cannot be reached or because one is not provided, the installer will check your system for the required kernel sources and compile the interface for you. You must have the source code for your kernel installed for compilation to work. On most systems, this means that you will need to locate and install the correct kernel-source, kernel-headers, or kernel-devel package; on some distributions, no additional packages are required (e.g. Fedora Core 3, Red Hat Enterprise Linux 4).

After the correct kernel interface has been identified (either included in the .run file, downloaded, or compiled from source code), the kernel interface will be linked with the closed-source portion of the NVIDIA kernel module. This requires that you have a linker installed on your system. The linker, usually /usr/bin/ld, is part of the binutils package. You must have a linker installed prior to installing the NVIDIA driver.


It looks that I'm a little stupid. Does that mean that the kernel module is included in the .run file?

---

### Post by Abu_Dayya on 2009-01-10
Ok. So I:

 ran the .run file from the shell (booted into recovery mode, then obtain root shell)
executed the .run file. The installer suggested to change the runlevel to runlevel 1 I think.
Then It said there were no kernel module for your kernel, do want to download it? ofcourse it couldn't connect to the net cause I was running from the shell and I don't know how to connect to the net from the shell.
Then it started recompiling the kernel module 
Installation was complete

Still when I booted into ubuntu, low resolution.....


please help

---

### Post by Abu_Dayya on 2009-01-11
Anyone can answer any of my questions?

---

### Post by hotweiss on 2009-01-11
I've had this problem many times before. To fix this problem you have to boot into recovery mode and reinstall your driver. If you still get an error after that, you have to rebuild xorg in recovery mode:

> sudo dpkg-reconfigure xserver-xorg

---

### Post by Abu_Dayya on 2009-01-11
> **hotweiss said:**
> I've had this problem many times before. To fix this problem you have to boot into recovery mode and reinstall your driver. If you still get an error after that, you have to rebuild xorg in recovery mode:

I already did that. And the problem still persists

---

### Post by hotweiss on 2009-01-11
> **Abu_Dayya said:**
> I already did that. And the problem still persists

This is what I would do next:

1) Go into recovery mode

2) > sudo apt-get remove nvidia*

3) reinstall the driver

4) rebuild xorg AGAIN if that fails

PS-remain strong!!! :)

---

### Post by Abu_Dayya on 2009-01-11
> **hotweiss said:**
> This is what I would do next:

1) Go into recovery mode

2) 

3) reinstall the driver

4) rebuild xorg AGAIN if that fails

PS-remain strong!!! :)

I'll do that. Hope it works this time.

By the way, how can I connect to the internet while on the recovery mode. Cause when I tried installing the driver earlier, the installer asked to connect to nvidia's ftp site to fetch something, but couldn't cause there was no connection. maybe this might help?

---

### Post by hotweiss on 2009-01-11
> **Abu_Dayya said:**
> I'll do that. Hope it works this time.

By the way, how can I connect to the internet while on the recovery mode. Cause when I tried installing the driver earlier, the installer asked to connect to nvidia's ftp site to fetch something, but couldn't cause there was no connection. maybe this might help?

Don't worry about an internet connection, it's not important.

---

### Post by Abu_Dayya on 2009-01-12
I DID IT

I followed a post here in these forums (can't remember which one) that suggested uninstalling the driver, then removing ubnutu-restricted-modules and ubuntu-restricted-modules-common packages, then install the driver again......... DIDN'T WORK


Then it just hit me... why not uninstall the driver... download a driver of the same version as the kernel module (173.14)... then install that one... Pretty simple actually.... I don't know why I didn't think of that...



I'm marking this one SOLVED.... I hope people with the same API mismatch problem can benefit from this

---

### Post by Abu_Dayya on 2009-01-12
> **hotweiss said:**
> 

PS-remain strong!!! :)

Thanks ;)

---

### Post by Abu_Dayya on 2009-01-12
P.S

I also found out how to stop xserver and still be connected to the internet

ALT+CTRL_F1
```
 sudo /etc/init.d/gdm stop
ps -ef | grep -i xserver
kill <process id of any remaining xsever process>

```

But it turned out I didn't need internet connection while installing the driver

.......................

Another P.S

now when I go to system -> Admin -> Hardware Drivers, I don't see any proprietary drivers installed. Is that because I unistalled the ubuntu-restricted-modules package?... Either way, I now have my nvidia card working

---

