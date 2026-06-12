---
title: "Help! Can't start VirtualBox"
date: 2009-05-27
forum: New to Ubuntu
---

### Post by jlbr21 on 2009-05-27
Hello,

I did a stupid thing, I ran the app called "Computer Janitor", and I inadvertently must have erased some virtualbox files I shouldn't have erased. Anyway, the .VirtualBox folder in home is intact, so I went ahead and downloaded the latest virtualbox deb package from the Sun site. I started Vbox and when i try to start my windoze xp virtual machine I get the following message:

> Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Re-setup the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.

I try to run that command as indicated by the message, and get a "command not found" message in the terminal.

I do have DKMS installed and I have reinstalled it, restarted the computer, and nothing is happening.

Please help, I need to use that virtual machine for work.

Thanks.

---

### Post by kpkeerthi on 2009-05-27
Add yourself to **vboxusers **group. Reboot.
```
sudo gpasswd -a <your-user-id> vboxusers
```

---

### Post by jlbr21 on 2009-05-27
Thanks kpkeerthi,

Did it, still I get the same result. Any more ideas?

---

### Post by hashimoto on 2009-05-27
Do as it says, but run it with sudo, since you are touching the system
```
sudo /etc/init.d/vboxdrv setup
```

---

### Post by jlbr21 on 2009-05-27
Thanks Hashimoto,
I do run it as root, but still I get the message "command not found", I have upgraded, updated the linux kernel headers, rebooted, still there is a file missing and despite the fact my VBox folder is intact, some file(s) is stopping me from starting it and it is very frustrating.

---

### Post by albinootje on 2009-05-27
> **jlbr21 said:**
> still I get the message "command not found"

Please post the output of the following :
```

dpkg -l|grep -i virtualbox
ls -la /etc/init.d/vb*

```

---

### Post by xebian on 2009-05-27
> **jlbr21 said:**
> Thanks Hashimoto,
I do run it as root, but still I get the message "command not found", I have upgraded, updated the linux kernel headers, rebooted, still there is a file missing and despite the fact my VBox folder is intact, some file(s) is stopping me from starting it and it is very frustrating.

Did you install the deb file you downloaded?  If not then do

sudo dpkg -i virtual...deb file you downloaded

---

### Post by jlbr21 on 2009-05-27
> Please post the output of the following :
Code:

dpkg -l|grep -i virtualbox
ls -la /etc/init.d/vb*

juanluis@juanluis-laptop:~$ dpkg -l|grep -i virtualbox
rc  virtualbox-2.2                             2.2.2-46594_Ubuntu_jaunty            Sun VirtualBox
juanluis@juanluis-laptop:~$ ls -la /etc/init.d/vb*
-rwxr-xr-x 1 root root 9566 2009-04-07 15:56 /etc/init.d/vboxdrv.dpkg-bak

Clearly, the file doesn't exist, however, I have reinstalled 3 times the deb package, and I am posting the log file of the install, you can see there were no mistakes in the install. 

** Compiling vboxdrv
Attempting to install using DKMS

Creating symlink /var/lib/dkms/vboxdrv/2.2.2/source ->
                 /usr/src/vboxdrv-2.2.2

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=2.6.28-11-generic -C /lib/modules/2.6.28-11-generic/build M=/var/lib/dkms/vboxdrv/2.2.2/build........

Running the post_build script:
cleaning build area....

DKMS: build Completed.

vboxdrv.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.28-11-generic/updates/dkms/

depmod....

DKMS: install Completed.
** Compiling vboxnetflt
Attempting to install using DKMS

Creating symlink /var/lib/dkms/vboxnetflt/2.2.2/source ->
                 /usr/src/vboxnetflt-2.2.2

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Running the pre_build script:

Building module:
cleaning build area....
make KERNELRELEASE=2.6.28-11-generic -C /lib/modules/2.6.28-11-generic/build M=/var/lib/dkms/vboxnetflt/2.2.2/build.......
cleaning build area....

DKMS: build Completed.

vboxnetflt.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.28-11-generic/updates/dkms/

depmod....

DKMS: install Completed.

---

### Post by xebian on 2009-05-27
Pls try sudo modprobe vboxdrv

---

### Post by jlbr21 on 2009-05-27
xebian:

I did, nothing happens.

---

### Post by xebian on 2009-05-27
> **jlbr21 said:**
> xebian:

I did, nothing happens.

Can't think of anything else but have you tried re-booting?  It might but not sure.

I don't have dkms and I install directly from the debs.  If you don't change kernel that often I think dkms is an overkill.  In any case when I install new kernel, recompiling is easy once you booted to the new kernel by issuing /etc/init.d/vboxdrv setup on the terminal.

---

### Post by philinux on 2009-05-27
Dont know if this will help but attached is my copy of vboxdrv. It is only a text file. You could try using it. Just remove the .txt extension.

---

### Post by jlbr21 on 2009-05-27
OK, got it, I had uninstalled virtualbox ose and virtualbox ose source due to the fact that when trying to install the deb package, it told me that it was conflicting with the ose package. I did not realize that I needed to have virtualbox ose source installed though.

That fixed the problem.

pheeewww!!!

Thanks for your help.

---

