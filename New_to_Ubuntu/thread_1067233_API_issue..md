---
title: "API issue."
date: 2009-02-11
forum: New to Ubuntu
---

### Post by SplinterOfChaos on 2009-02-11
Hi. I run epsxe with Wine and one of my applications spits this message onto the command line:

> Error: API mismatch: the NVIDIA kernel module has version 180.27,
but this NVIDIA driver component has version 180.29.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.

I don't understand how to upgrade my NVIDIA kernel or driver. I did find Applications > System > Hardware Drivers, which seems to exclusively list the NVIDIA drivers, but I can only chose between version 180 and 177, not sub-versions, it seems.

---

### Post by RomeReactor on 2009-02-11
Hi. The 180 driver in the repositories (the one that shows up in Hardware Drivers) is version 180.11; you seem to have previously installed 180.27 and 180.29. Did you uninstall 180.27 before installing the new driver?

---

### Post by SplinterOfChaos on 2009-02-11
All I ever did was go to Applications > System > Hardware Drivers and click 180. Beyond that, I didn't do a thing. I wouldn't know how to manage my drivers any other way.

Although, I did find the nvidia kernal source in the Synaptic Package Manager. Wouldn't know what to do with them, though.

---

### Post by RomeReactor on 2009-02-11
Ah, hadn't noticed you're using Jaunty; the nVidia driver version available for it is indeed 180.29.

Did you upgrade your system from Intrepid? If so, while in Intrepid, did you download and install a driver from nVidia's site?

Try running dmesg and see if you get any information regarding the modules--possibly a similar output to the error you're getting:
```
dmesg | grep NVRM
```
and post back the result.

---

### Post by SplinterOfChaos on 2009-02-11
Actually, I started with Jaunty. And yestarday, this error didn't exist. I (my package manager) installed some upgrades, but I don't know if any of them are related.

> scott@scott-laptop:~$ dmesg | grep NVRM
[   31.786550] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.27  Tue Jan 27 12:16:07 PST 2009
[ 7368.819750] NVRM: API mismatch: the client has the version 180.29, but
[ 7368.819754] NVRM: this kernel module has the version 180.27.  Please
[ 7368.819756] NVRM: make sure that this kernel module and all NVIDIA driver
[ 7368.819759] NVRM: components have the same version.
[ 7369.300257] NVRM: API mismatch: the client has the version 180.29, but
[ 7369.300262] NVRM: this kernel module has the version 180.27.  Please
[ 7369.300264] NVRM: make sure that this kernel module and all NVIDIA driver
[ 7369.300267] NVRM: components have the same version.

...

[16156.773279] NVRM: API mismatch: the client has the version 180.29, but
[16156.773283] NVRM: this kernel module has the version 180.27.  Please
[16156.773285] NVRM: make sure that this kernel module and all NVIDIA driver
[16156.773287] NVRM: components have the same version.
scott@scott-laptop:~$ 


Uh, yeah.

---

### Post by RomeReactor on 2009-02-11
So it looks like there *was* an update to the nVidia driver, and the previous driver's module wasn't properly removed. You could try switching to a console by pressing CTRL+ALT+F1, then stop the display:
```
sudo /etc/init.d/gdm stop
```
see if the module is still loaded:
```
lsmod | grep nvidia
```
if it is, remove it:
```
sudo rmmod nvidia
```
purge the driver:
```
sudo aptitude purge nvidia-glx-180
```
then start your display again:
```
sudo /etc/init.d/gdm start
```
and choose to run in low graphics mode; then you can install the driver again in 'System->Administration->Hardware Drivers' to see if the problem is fixed.

Note that I haven't used Jaunty, so this solution may not work for you, and it may be a bug yet to be solved.

---

### Post by SplinterOfChaos on 2009-02-11
That did it! I'll have to remember this.

---

### Post by RomeReactor on 2009-02-11
Glad you got it sorted out. :popcorn:

Please add [SOLVED] to the thread's name so others know where to look, in case they have the same problem.

---

