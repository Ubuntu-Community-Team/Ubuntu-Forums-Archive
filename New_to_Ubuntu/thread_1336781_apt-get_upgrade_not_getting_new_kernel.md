---
title: "apt-get upgrade not getting new kernel"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by rideburton56 on 2009-11-24
I am running kubuntu 9.10 on this machine, and today i got this.

```
#@#:~$ sudo apt-get upgrade
[sudo] password for #:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

```

Why is it holding back the new kernel?

---

### Post by Buuntu on 2009-11-24
Don't know if I can answer your question since I had the same issue, but to solve it you can either run```
sudo apt-get install <package1> <package2> <package3>
```
or do it like I did and just run Update Manager - that should install the held back packages.

---

### Post by sandyd on 2009-11-24
> **rideburton56 said:**
> I am running kubuntu 9.10 on this machine, and today i got this.

```
#@#:~$ sudo apt-get upgrade
[sudo] password for #:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

```Why is it holding back the new kernel?
It is holding it back according to the package rules that the package/repo maintainer has.
you have to manually install them by
```

sudo apt-get install 
linux-generic linux-headers-generic linux-image-generic

```

---

### Post by rideburton56 on 2009-11-25
is this happening to everyone or is it just a select few?

---

### Post by mgranet on 2009-11-25
I had that problem when updating with Kpackagekit. Synaptic seemed to install everything just fine though.

---

### Post by t.rei on 2009-11-25
it's not a problem, it's added safety.

```
sudo apt-get dist-upgrade
``` 
Running this should resolve any dependencies that will probably cause removal of some package. That is usually the reason for a regula upgrade holding back something.

---

### Post by x C0MMAND0 x on 2009-11-25
I guess I never paid much attention to the fact that certain packages were held back.  I'm running a manual install of my particular held back packages right now...

---

### Post by rideburton56 on 2009-11-25
> **t.rei said:**
> it's not a problem, it's added safety.

```
sudo apt-get dist-upgrade
``` 
Running this should resolve any dependencies that will probably cause removal of some package. That is usually the reason for a regula upgrade holding back something.

I don't bother with kpackagekit when possible, i prefer apt CLI updates/upgrades.  This was a fresh install of 9.10, so why would there be missing dependencies?

P.S.  I will try this when I get home, I just like understanding why this would happen unless something is broken, or the dreaded OPERATOR ERROR!!!  Not trying to give you a hard time.  Thanks!

---

### Post by abcuser on 2009-11-25
> **t.rei said:**
> it's not a problem, it's added safety.

```
sudo apt-get dist-upgrade
``` 
Running this should resolve any dependencies that will probably cause removal of some package. That is usually the reason for a regula upgrade holding back something.
t.rei,
this is done for safety reasons. But it is not necessary this would trigger removal of some packages. Installing new kernel can be dangerous, because new modules must be compiled (modules are something similar like operating system drivers on Windows).

For example VMWare modules or VirtualBox modules or other modules... When kernel is upgraded this kind of modules must be recompiled and this can be dangerous if admin does not know how to solve the problem. So when normal update is done there should most probably be no problem at all, but when dist-upgrade is done admin must understand that some modules must be recompiled and so this upgrade is done with care.

In some cases like on server, it is not desired to install new kernels if this is not already well tested on some testing computers.

Some programs may stop working if new kernel is installed and so manually installing kernel modules must be done.

In most of the cases this can be avoided if [DKMS package](http://packages.ubuntu.com/karmic/dkms) is installed which takes care of automatic compiling new kernel modules when new kernel is installed.

I recommend installing DKMS package before installing kernel updates to avoid having manually compiling modules if required.

Install dkms package:
```
sudo apt-get install dkms
```
and then after this package is installed then use:
```
sudo apt-get dist-upgrade
```
Regards

---

