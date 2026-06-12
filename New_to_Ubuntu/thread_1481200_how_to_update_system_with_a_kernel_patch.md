---
title: "how to update system with a kernel patch"
date: 2010-05-12
forum: New to Ubuntu
---

### Post by molar on 2010-05-12
I've encounterd a bug with an ATI radeon and S video:
[https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/563983](https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/563983)

Since the bug is solved I wanted to know how can i update my system with it. I've done system update but it's not there. this is the only thing that bothers me in Ubuntu since this computer is only used for playing videos.

any help will be appreciated. thx guys.

---

### Post by luscinius on 2010-05-12
Hi 
The bug report says the ``patch applied to linux-image-2.6.32-21-generic_2.6.32-21.32 sources and kernel recompilation fixes the problem''.
Then you should recompile the kernel ([https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)) --- install the ubuntu kernel source package, apply the patch (from the bugreport) to it and rebuild.
The patch can be applied to the source code only, as it is universal; probably it is impossible to patch the kernel binary in a universal way.
The patch itself is a text file showing the differences to be made to the sources.

---

### Post by molar on 2010-05-12
I see that there is a way to use the synaptic package manager to install the updated kernel. could someone guide me through the process?

i've opened the package manager, found the package i want to install "linux-image-2.6.32.21-generic", it says that the installed version is 2.6.32-21.32.

what should I do next? should I mark it for reinstallation? for removal? thx for help. after installation should I recompile it or is it already done for me?

---

### Post by luscinius on 2010-05-12
When you install linux-image-*** via synaptic, you get the standard binary ubuntu kernel, already built for you. As far as I understand, it does not include the patch you need yet. When you installing this package you get the binaries only --- and they do not have the update you need.

That is why you need to compile the kernel on you computer from the C source code (mere text files), and this will produce the binaries. To do this you can follow instructions given here: [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)
First do
```
sudo apt-get build-dep linux
```
Then
```
sudo apt-get build-dep --no-install-recommends linux-image-$(uname -r)
```
This will install dependencies needed for building the binary kernel (linux-image package) on you computer. Finally, get the source:
```
sudo apt-get source linux-ubuntu-modules-$(uname -r)
```
Then find where the sources are (probaly somewhere in /usr/src/), apply the patch and proceed with the compilation instructions.

---

### Post by molar on 2010-05-13
thank you for your answer. I think that I might just go back to 9.10 and  wait until all of this is sorted our properly. this bug will be patched  into the kernel eventually.

---

