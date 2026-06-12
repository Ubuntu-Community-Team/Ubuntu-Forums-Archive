---
title: "URGHH!@! video driver problems"
date: 2009-06-10
forum: New to Ubuntu
---

### Post by ptviperz on 2009-06-10
This morning I had a perfectly good working copy of 9.04 running at 1680x1050 with full compiz effects. Nvidia 7950GT card, etc etc. 

I was playing around trying to install Xen, computer needed a reboot and suddenly I'm down to base effects running in low resolution mode. 

I can see the right drivers in the restricted list but can't activate them, manual install of the newest drivers wouldn't install, nvidia xserver settings tells me to run some command and restart X, but when I do, nothing has changed. 

I'm stumped at this point and a little frustrated, can any of you super fly guru's out there give me some pointers? Thanks in advance.

---

### Post by ptviperz on 2009-06-11
Anyone? Please?

---

### Post by gamblor01 on 2009-06-11
You could try running the installer from the command line instead of clicking on the restricted drivers to install them:

```
sudo apt-get install nvidia-glx-new
sudo nvidia-xconfig
```You could try that and then restart X to see if it makes any difference.  You might need to manually update your /etc/X11/xorg.conf file however.  The installer is supposed to do that for you but maybe Xen messed it up somehow?  You might post the contents of your xorg.conf file.  It *should* contain these lines somewhere in it:

```
Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
EndSection
```

---

### Post by ptviperz on 2009-06-11
When I run apt-get from the CLI I get the following

Doing initial module build

Error! Your kernel source for kernel 2.6.28-13-server cannot be found at
/lib/modules/2.6.28-13-server/build or /lib/modules/2.6.28-13-server/source.
Installing initial module

Error! Could not locate nvidia.ko for module nvidia in the DKMS tree.
You must run a dkms build for kernel 2.6.28-13-server (x86_64) first.
Done.

and my xorg.conf is definitely missing the nvidia section, it does contain this

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

---

### Post by gradinaruvasile on 2009-06-11
Try installing the driver from nvidia.com. You must do it in single user mode (restart, boot with the recovery option, select root prompt from the list.
But first you should uninstall the existing driver
sudo apt-get remove --purge nvidia-glx-*
sudo dpkg-reconfigure -phigh xserver-xorg
reboot in recovery mode, select root prompt from the list, run the nvidia installer (from their site).
if successful, press ctrl-d, select "resume normal boot".

---

### Post by ptviperz on 2009-06-11
> **gradinaruvasile said:**
> Try installing the driver from nvidia.com. You must do it in single user mode (restart, boot with the recovery option, select root prompt from the list.
But first you should uninstall the existing driver
sudo apt-get remove --purge nvidia-glx-*
sudo dpkg-reconfigure -phigh xserver-xorg
reboot in recovery mode, select root prompt from the list, run the nvidia installer (from their site).
if successful, press ctrl-d, select "resume normal boot".

Ok, when I did this, the module got rebuilt, booted into the GUI and bingo, everything works again.

However, when I reboot, everything is back to low resolution mode. So something is going on with my kernel I guess? I had 3 options at the grub menu for the current kernel...did I pick the wrong one to repair?

---

### Post by gamblor01 on 2009-06-11
```

When I run apt-get from the CLI I get the following

Doing initial module build

Error! Your kernel source for kernel 2.6.28-13-server cannot be found at
/lib/modules/2.6.28-13-server/build or /lib/modules/2.6.28-13-server/source.
Installing initial module

Error! Could not locate nvidia.ko for module nvidia in the DKMS tree.
You must run a dkms build for kernel 2.6.28-13-server (x86_64) first.
Done.

```
I guess perhaps this is because you are missing the kernel development package?  Try issuing the command:

```

sudo apt-get install linux-kernel-devel

```

then see if you can install the package from the command line after that?

---

### Post by ptviperz on 2009-06-12
After two days of fighting this issue I finally reinstalled Ubuntu. I couldn't find any way to fix the problem.

Be warned, Xen will break your install.

---

### Post by vancouverite on 2009-06-22
Hi all,
I had the same error as ptviperz when I tried to convert to the server kernel.  I fought with it for a bit before I realized that I didn't have the current headers and that's why the kernel source was missing. 

As soon as I installed "linux-headers-2.6.28-13-server" the nvida and virtual box drivers were automatically recompiled.

Hope this helps!

---

### Post by Arup on 2009-06-22
If you are into compiling your own kernel or tweaking it, best way for installing drivers would be to download from manufacturers site, do a sudo apt-get build-essential and remove linux restricted modules and linux restricted modules common and install the drivers in tty with gdm stopped.

---

