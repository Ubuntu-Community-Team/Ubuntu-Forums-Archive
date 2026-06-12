---
title: "virtual box"
date: 2009-10-26
forum: New to Ubuntu
---

### Post by misswham on 2009-10-26
i tried to log onto virtual box and i got this message

Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Re-setup the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.

i am a novice.  what is it asking me to actually DO?

---

### Post by blur xc on 2009-10-26
A simple possible solution is to uninstall it, and try reinstalling.  Sometimes you get a problem on installation.  Other than that, try the Vbox forums.  There are some VBox guru's over there that can be of help.

BM

---

### Post by misswham on 2009-10-26
i have been using it for 2 mths now and this just popped up today

---

### Post by clive littlewood on 2009-10-26
Hi

If you had an kernal update this will cause this problem.

If you dowloaded the .deb file to install VB then reinstall from the .deb

All your machines and settings will be saved and it will install the kernal mod for the latest kernal.

Hope this helps

Clive

---

### Post by alphaniner on 2009-10-26
I run VBox on 9.04 and I don't know anything about DKMS, but the other bit is asking is to open a terminal and enter

```
sudo /etc/init.d/vboxdrv setup
```

Edit: Now I think about it I must have DKMS installed, because I never need to re-configure after kernel updates.

---

### Post by BQAggie2006 on 2009-10-26
It's asking you to run the following command to re-setup the VirtualBox kernel driver:

```
sudo /etc/init.d/vboxdrv setup
```If that does not work, I would then suggest uninstalling it as blur did, but before re-installing it, install the DKMS (Dynamic Kernel Module Support) package with the following command:

```
sudo apt-get install dkms
```

---

### Post by alphaniner on 2009-10-26
And if you aren't confused enough already, consider using the information [here]("http://www.virtualbox.org/wiki/Linux_Downloads") to allow VBox to be downloaded & updated through the package manager (scroll down to "Debian-based Linux distributions").

---

### Post by misswham on 2009-10-26
BRAVO and thanks this worked

sudo /etc/init.d/vboxdrv setup

---

