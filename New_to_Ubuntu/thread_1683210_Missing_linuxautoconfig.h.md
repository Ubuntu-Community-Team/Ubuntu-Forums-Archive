---
title: "Missing linux/autoconfig.h"
date: 2011-02-07
forum: New to Ubuntu
---

### Post by Sancho_Panza on 2011-02-07
Hey,

i tried to install cisco vpn client to the /bin folder. I have the latest version of ubuntu running and this is my very first package to install. But when i want to start the script vpn_install i get this:

Making module
make -C /lib/modules/2.5.35-25-generic/build SUBDIRS=/bin/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-25-generic'
  CC [M]  /bin/vpnclient/linuxcniapi.o
/bin/vpnclient/linuxcniapi.c:14: fatal error: linux/autoconf.h: No such file or directory
compilation terminated.
make[2]: *** [/bin/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/bin/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-25-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

I already installed the mentioned linux header and still getting this error message. Ok, this linux/autoconf.h file is not traceable, but i don't really know how to fix this. 

I would be graceful if anybody could give me a hint.forum ubuntu

---

### Post by anglican on 2011-02-07
> **Sancho_Panza said:**
> Hey,

i tried to install cisco vpn client to the /bin folder. I have the latest version of ubuntu running and this is my very first package to install. But when i want to start the script vpn_install i get this:

Making module
make -C /lib/modules/2.5.35-25-generic/build SUBDIRS=/bin/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-25-generic'
  CC [M]  /bin/vpnclient/linuxcniapi.o
/bin/vpnclient/linuxcniapi.c:14: fatal error: linux/autoconf.h: No such file or directory
compilation terminated.
make[2]: *** [/bin/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/bin/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-25-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

I already installed the mentioned linux header and still getting this error message. Ok, this linux/autoconf.h file is not traceable, but i don't really know how to fix this. 

I would be graceful if anybody could give me a hint.forum ubuntuThat file is generated dynamically when you configure the kernel,  run: ```
make menuconfig
``` in /usr/src/linux/ & save the  kernel configuration, this will generate the  /usr/include/linux/autoconf.h file according to the kernel  configuration.

H

---

### Post by Sancho_Panza on 2011-02-07
Hey anglican

thanks very much for your reply. I went to /usr/src/liniux-headers-2.6.35-25. (This is my kernel version) I opend the kernel menu and saved it, but still no autoconfig.h  :confused: 
You said this file should be in usr/includ/linux ? 

Does anybody know how i get this file in the directory ?? I already reinstalled the linux-header.... no success...

regards
Panza

---

### Post by anglican on 2011-02-08
> **Sancho_Panza said:**
> Hey anglican

thanks very much for your reply. I went to /usr/src/liniux-headers-2.6.35-25. (This is my kernel version) I opend the kernel menu and saved it, but still no autoconfig.h  :confused: 
You said this file should be in usr/includ/linux ? No that should be /usr/src/linux/include/linux/autoconf.h - I think.
> **Sancho_Panza said:**
> 
Does anybody know how i get this file in the directory ?? I already reinstalled the linux-header.... no success...

regards
PanzaReinstalling isn't going to help - it would delete the file if it existed. Configuring/compiling a kernel is what's needed. Try the following:
```
uname -r
```which should report a <version>-<nn>-generic to be used in the following
```
sudo apt-get install linux-source-<version> kernel-package libncurses5-dev fakeroot
sudo /bin/bash
cd /usr/src
bunzip2 linux-source-<version>.tar.bz2
tar xvf linux-source-<version>.tar
ln -s linux-source-<version> linux
cp /boot/config-`uname -r` /usr/src/linux/.config
cd /usr/src/linux
make menuconfig
```then choose "Load an alternative Configuration File" and load the .config file (just hit enter). Then choose "Exit" and save the configuration when prompted. It shouldn't be necessary to actually compile the kernel, to do so you'd do (still as root):
```
make-kpkg clean
fakeroot make-kpkg --initrd --append-to-versio=-custom kernel_image kernel_headers
```Which after a _**very**_ long time would create two .deb files in /usr/src. (to actually install these you would also need to create an initrd.img and add that initrd.img to the grub menu for the custom kernel).

H

---

### Post by Sancho_Panza on 2011-02-13
Hey,

i was absence for some days.. Meanwhile i have followed your instructions up to creation of the two deb files. There is a file Initrd.img in the root directory. Is this file you have mentioned? If not how do i create it and is grubmenu == boot directory. Do i just paste it there? There are right now tow files in the boot directory:  initrd.img-2.6.35-22-generic  &  initrd.img-2.6.35-25-generic.

Funny thing: I reinstalled ubuntu 10.10 and still the same thing. Something i'm doing very wrong i guess. Hmm when i installed ubuntu there was version 2.6.35-22 displayed at startup, after updating both the 2.6.35-22 and 2.6.35-25 are displayed.

What do you suggest what to do next?

regards

---

### Post by anglican on 2011-02-14
> **Sancho_Panza said:**
> Hey,

i was absence for some days.. Meanwhile i have followed your instructions up to creation of the two deb files. There is a file Initrd.img in the root directory. Is this file you have mentioned? If not how do i create it and is grubmenu == boot directory. Do i just paste it there? There are right now tow files in the boot directory:  initrd.img-2.6.35-22-generic  &  initrd.img-2.6.35-25-generic.

Funny thing: I reinstalled ubuntu 10.10 and still the same thing. Something i'm doing very wrong i guess. Hmm when i installed ubuntu there was version 2.6.35-22 displayed at startup, after updating both the 2.6.35-22 and 2.6.35-25 are displayed.

What do you suggest what to do next?

regardsDo you have the file linux/autoconf.h now?

H

---

### Post by zooey on 2011-10-29
Hi guys,

just in case someone has same problem as you and also i had this problem you can find autoconf.h in /usr/src/linux-headers-$YOUR NUMBER/include/generated so if you have problem with compiling just change in that file where is the error to generated/autoconf.h   . Nice day :)

---

