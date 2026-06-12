---
title: "Virutal Box help... compiling kerenel modules?"
date: 2009-10-04
forum: New to Ubuntu
---

### Post by koglaa on 2009-10-04
uhhh... Hi...  I have a problem with virtual box...
After extracting the .deb file I get the following error
```
VirtualBox will not start until this problem is fixed. Please consult /var/log/vbox-install.log to find out why the kernel module does not compile. Most probably the kernel sources were not found. Install them (the package name is probably linux-headers-<version> whereby <version> can be determined by 'uname -r') and execute

  /etc/init.d/vboxdrv setup

as root.
```

So, in terminal...
```
koglaa@baka-laptop:~$ sudo su
[sudo] password for koglaa: 
froot@baka-laptop:/home/koglaa# /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module                                             *  done.
 * Recompiling VirtualBox kernel module                                         
 * Look at /var/log/vbox-install.log to find out what went wrong
root@baka-laptop:/home/koglaa# /var/log/vbox-install.log
bash: /var/log/vbox-install.log: Permission denied
root@baka-laptop:/home/koglaa# sudo /var/log/vbox-install.log
sudo: /var/log/vbox-install.log: command not found
root@baka-laptop:/home/koglaa# 
```

And then I open the log file:
```
Attempting to install using DKMS
  removing old DKMS module vboxdrv version  3.0.6

------------------------------
Deleting module version: 3.0.6
completely from the DKMS tree.
------------------------------
Done.

Creating symlink /var/lib/dkms/vboxdrv/3.0.6/source ->
                 /usr/src/vboxdrv-3.0.6

DKMS: add Completed.

Error! Your kernel source for kernel 2.6.24-16-generic cannot be found at
/lib/modules/2.6.24-16-generic/build or /lib/modules/2.6.24-16-generic/source.
You can use the --kernelsourcedir option to tell DKMS where it's located.
Failed to install using DKMS, attempting to install without
Makefile:147: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again. Stop.
```

I'm a noob.  I need help.

---

### Post by sandyd on 2009-10-04
> **koglaa said:**
> uhhh... Hi...  I have a problem with virtual box...
After extracting the .deb file I get the following error
```
VirtualBox will not start until this problem is fixed. Please consult /var/log/vbox-install.log to find out why the kernel module does not compile. Most probably the kernel sources were not found. Install them (the package name is probably linux-headers-<version> whereby <version> can be determined by 'uname -r') and execute

  /etc/init.d/vboxdrv setup

as root.
```So, in terminal...
```
koglaa@baka-laptop:~$ sudo su
[sudo] password for koglaa: 
froot@baka-laptop:/home/koglaa# /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module                                             *  done.
 * Recompiling VirtualBox kernel module                                         
 * Look at /var/log/vbox-install.log to find out what went wrong
root@baka-laptop:/home/koglaa# /var/log/vbox-install.log
bash: /var/log/vbox-install.log: Permission denied
root@baka-laptop:/home/koglaa# sudo /var/log/vbox-install.log
sudo: /var/log/vbox-install.log: command not found
root@baka-laptop:/home/koglaa# 
```And then I open the log file:
```
Attempting to install using DKMS
  removing old DKMS module vboxdrv version  3.0.6

------------------------------
Deleting module version: 3.0.6
completely from the DKMS tree.
------------------------------
Done.

Creating symlink /var/lib/dkms/vboxdrv/3.0.6/source ->
                 /usr/src/vboxdrv-3.0.6

DKMS: add Completed.

Error! Your kernel source for kernel 2.6.24-16-generic cannot be found at
/lib/modules/2.6.24-16-generic/build or /lib/modules/2.6.24-16-generic/source.
You can use the --kernelsourcedir option to tell DKMS where it's located.
Failed to install using DKMS, attempting to install without
Makefile:147: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again. Stop.
```I'm a noob.  I need help.
sudo apt-get install linux-headers-2.6.24-16-generic

---

### Post by koglaa on 2009-10-04
```
koglaa@baka-laptop:~$ 
koglaa@baka-laptop:~$ sudo apt-get install linux-headers-2.6.24-16-generic
[sudo] password for koglaa: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers-2.6.24-16-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-headers-2.6.24-16-generic has no installation candidate
koglaa@baka-laptop:~$ 

```
Its installed on package manager

---

### Post by crispy_420 on 2009-10-04
Find your kernel version to be sure with:

uname -r

Then search the package manager for appropriate headers.

---

### Post by koglaa on 2009-10-05
I installed all the kernel packages.  That doesn't really help.  When I goto applications > system tools > Sun virtualbox I get an error
```
Effective UID is not root (euid=1001 egid=0 uid=1001 gid=0) (rc=-10)

It may help to reinstall virtual box.
```

Anyway I reinstalled, still same error.  Does this mean I have to reinstall as root?

---

### Post by koglaa on 2009-10-06
Bump

---

### Post by sandyd on 2009-10-06
what the heck is goin on there...
```

gksudo VirtualBox

```

does that work?

or try adding your user to the "virtualbox" group.

---

### Post by koglaa on 2009-10-06
omg, that works now, thanks!  I don't think its cause of that.  I had 81 broken files (which I found from the package manager via filters).  I upgraded/fixed them all, ran your command at it worked, thanks :KS

---

### Post by koglaa on 2009-10-06
ok... found out it didn't work... again <_<. 
```
The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv.  Re-setup the kernel module by execution

/etc/init.d/vboxdrv setup

as root.  Users of Ubuntu, Fedora or Mandriva should install the DKMS package first.  This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary
```

I've got DKMS and I'll get started on the root setup tomorrow.  I'm going to sleep right now though

---

### Post by Scunizi on 2009-10-06
Perhaps sudo apt-get install build-essential dkms .. and then rerun the installer.  Make sure to put yourself in the vbox group when finished.

---

### Post by koglaa on 2009-10-07
Nope.  Not that.

---

### Post by Scunizi on 2009-10-07
In your first post you said you "extracted" the .deb file.. did you actually extract it, as in decompress/expand or did you "dpkg -i <filename.deb> or did you double click it to let the system install it?

Also did you get the .deb directly from the vbox site and if so did you make sure you got the version compiled for your ubuntu version?

This is a really weird problem.  I've never had these kinds of issues.

---

### Post by koglaa on 2009-10-08
> **Scunizi said:**
> In your first post you said you "extracted" the .deb file.. did you actually extract it, as in decompress/expand or did you "dpkg -i <filename.deb> or did you double click it to let the system install it?

Also did you get the .deb directly from the vbox site and if so did you make sure you got the version compiled for your ubuntu version?

This is a really weird problem.  I've never had these kinds of issues.


Yeah, by extracted I meant I installed it by double clicking it.  I did get the .deb from the vbox site and I did get 9.04 version

---

### Post by koglaa on 2009-10-09
Bump

---

### Post by koglaa on 2009-10-10
Bump again

---

### Post by koglaa on 2009-10-12
Another bump...

---

### Post by crispy_420 on 2009-10-13
Just did a reinstall of Ubuntu so I will look into this further and see what I can do. I've been mainly in VirtualBox recently due to school.

---

### Post by koglaa on 2009-10-16
Bump

---

