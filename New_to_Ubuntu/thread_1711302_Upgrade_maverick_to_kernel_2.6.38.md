---
title: "Upgrade maverick to kernel 2.6.38"
date: 2011-03-21
forum: New to Ubuntu
---

### Post by krishna.988 on 2011-03-21
Is it possible to upgrade maverick to 2.6.38?

Is it ok to follow the steps mentioned here:

[http://translate.googleusercontent.com/translate_c?hl=en&ie=UTF-8&sl=auto&tl=en&u=http://www.lffl.org/2011/03/ubuntu-installiamo-il-nuovo-kernel-2638.html&prev=_t&rurl=translate.google.com&twu=1&usg=ALkJrhiUclIhJvIraWS2KRnzbmSfS7jFfw#more](http://translate.googleusercontent.com/translate_c?hl=en&ie=UTF-8&sl=auto&tl=en&u=http://www.lffl.org/2011/03/ubuntu-installiamo-il-nuovo-kernel-2638.html&prev=_t&rurl=translate.google.com&twu=1&usg=ALkJrhiUclIhJvIraWS2KRnzbmSfS7jFfw#more)

---

### Post by Paqman on 2011-03-21
I wouldn't install a kernel from an untrusted source, no. You have no way of knowing how it's been modified.

You can get the newer kernel safely by upgrading to Ubuntu 11.04 when it's released on 28th April. Is there some reason you were wanting to get a new kernel sooner?

---

### Post by rvchari on 2011-03-21
> **krishna.988 said:**
> Is it possible to upgrade maverick to 2.6.38?

Is it ok to follow the steps mentioned here:

[http://translate.googleusercontent.com/translate_c?hl=en&ie=UTF-8&sl=auto&tl=en&u=http://www.lffl.org/2011/03/ubuntu-installiamo-il-nuovo-kernel-2638.html&prev=_t&rurl=translate.google.com&twu=1&usg=ALkJrhiUclIhJvIraWS2KRnzbmSfS7jFfw#more](http://translate.googleusercontent.com/translate_c?hl=en&ie=UTF-8&sl=auto&tl=en&u=http://www.lffl.org/2011/03/ubuntu-installiamo-il-nuovo-kernel-2638.html&prev=_t&rurl=translate.google.com&twu=1&usg=ALkJrhiUclIhJvIraWS2KRnzbmSfS7jFfw#more)

i could do it with update manager (2.6.35-28-generic) (which pops up whenever newer updates r available)

---

### Post by krishna.988 on 2011-03-21
> **rvchari said:**
> i could do it with update manager (2.6.35-28-generic) (which pops up whenever newer updates r available)


It is 2.6.35-28 and not 2.6.38

---

### Post by krishna.988 on 2011-03-21
> **Paqman said:**
> I wouldn't install a kernel from an untrusted source, no. You have no way of knowing how it's been modified.

You can get the newer kernel safely by upgrading to Ubuntu 11.04 when it's released on 28th April. Is there some reason you were wanting to get a new kernel sooner?


Is there any other way of installing the new kernel without upgrading the OS..What is the difference b'w 2.6.35-28 which is the latest update for maverick and 2.6.38??

---

### Post by NightwishFan on 2011-03-21
To be honest I would just wait until Ubuntu 11.04 is released. Unless you know of a specific reason to get a newer one there really is no reason. Best wait until you have Canonical's engineers to sort out the problems with it. :)

---

### Post by Paqman on 2011-03-21
> **krishna.988 said:**
> Is there any other way of installing the new kernel without upgrading the OS..


Not really, no. 

You *could* download a completely vanilla kernel from kernel.org and compile it yourself, but it's annoying to do and you'd miss out on all the patches that Ubuntu provides with their kernels. Pointless exercise IMO.

> 
What is the difference b'w 2.6.35-28 which is the latest update for maverick and 2.6.38??

If 2.6.35 is working fine then just keep using it. It's a perfectly good kernel.

---

### Post by rvchari on 2011-03-21
> **krishna.988 said:**
> Is it possible to upgrade maverick to 2.6.38?

Is it ok to follow the steps mentioned here:

[http://translate.googleusercontent.com/translate_c?hl=en&ie=UTF-8&sl=auto&tl=en&u=http://www.lffl.org/2011/03/ubuntu-installiamo-il-nuovo-kernel-2638.html&prev=_t&rurl=translate.google.com&twu=1&usg=ALkJrhiUclIhJvIraWS2KRnzbmSfS7jFfw#more](http://translate.googleusercontent.com/translate_c?hl=en&ie=UTF-8&sl=auto&tl=en&u=http://www.lffl.org/2011/03/ubuntu-installiamo-il-nuovo-kernel-2638.html&prev=_t&rurl=translate.google.com&twu=1&usg=ALkJrhiUclIhJvIraWS2KRnzbmSfS7jFfw#more)

i updated using the link successfully.... then removed it by reverting back to gud ol 2.6.35-28.
Y ? coz my vbox kernel module wont compile ! says there is a version clash between 2.6.38 and 2.6.38-200XXX something. So no point in holding on to keep fiddling around when 2.6.35-28 seems to take care of my needs !

another lesson i learnt, better upgrade from update manager where ubuntu has tried, tested and then offered for upgrade so no re-compiling issues will be found (its my opinion)

---

### Post by messie on 2011-03-21
Except if your laptop doesn't go into sleep mode (fixed with kernel 2.6.36) and your bluetooth mouse doesn't connect (fixed with kernel 2.6.37). If you google it there are pre-compiled kernels for ubuntu maverick 2.6.36 and 2.6.37...
and for 2.6.38:
[http://www.ramoonus.nl/2011/03/linux-kernel-2-6-38-installation-guide-for-ubuntu-linux/](http://www.ramoonus.nl/2011/03/linux-kernel-2-6-38-installation-guide-for-ubuntu-linux/)

(the 2.6.36 and 2.6.37 worked perfectly for my Ubuntu 10.10 x64 compiled by this guy, going to try 2.6.38 just now :D)

---

### Post by carvic on 2011-03-31
Installed 2.6.38-2 precompiled image  ([http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38.2-natty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38.2-natty/)) and  suitable header on maverick meerkat , via dpkg -i. The system (asus  eeepc) is apparently ok, with WLAN, audio etc functions fine and general  performance apparently better than 2.6.35-28.

Greets.

---

### Post by rvchari on 2011-03-31
> **carvic said:**
> Installed 2.6.38-2 precompiled image  ([http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38.2-natty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38.2-natty/)) and  suitable header on maverick meerkat , via dpkg -i. The system (asus  eeepc) is apparently ok, with WLAN, audio etc functions fine and general  performance apparently better than 2.6.35-28.

Greets.

is vbox functioning well ? coz when i did it earlier, vbox kernel modules cudnt load even after re-compiling !!! so i had no choice but to revert back to prev kernel...

---

### Post by brianread on 2011-04-04
> **rvchari said:**
> is vbox functioning well ? coz when i did it earlier, vbox kernel modules cudnt load even after re-compiling !!! so i had no choice but to revert back to prev kernel...

I am also keen to upgrade to 2.6.38 while still on meerkat, as I could use the new desktop scheduling fix, as I drive my system pretty hard, however I also need vbox, so I'd need to know whether it works or not.

---

### Post by krishna.988 on 2011-04-05
> **carvic said:**
> Installed 2.6.38-2 precompiled image  ([http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38.2-natty/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.38.2-natty/")) and  suitable header on maverick meerkat , via dpkg -i. The system (asus  eeepc) is apparently ok, with WLAN, audio etc functions fine and general  performance apparently better than 2.6.35-28.

Greets.

Can you please elaborate the steps on how to update this? As I'm a novice to Linux..

Thanks

---

### Post by beew on 2011-04-05
> **krishna.988 said:**
> Can you please elaborate the steps on how to update this? As I'm a novice to Linux..

Thanks

If you are a novice is there a reason why you want to attempt a risky operation by all accounts that may break your system?

---

### Post by krishna.988 on 2011-04-05
> **beew said:**
> If you are a novice is there a reason why you want to attempt a risky operation by all accounts that may break your system?


As I'm a novice, I want to learn things, so that I will transition from a Novice user to advanced

---

### Post by beew on 2011-04-05
> **krishna.988 said:**
> As I'm a novice, I want to learn things, so that I will transition from a Novice user to advanced

Why don't you try it on an external drive? Install Maverick in an external drive then you can experiment without breaking your functioning system.

---

### Post by krishna.988 on 2011-04-05
> **beew said:**
> Why don't you try it on an external drive? Install Maverick in an external drive then you can experiment without breaking your functioning system.


yes you are right ..I have Windows 7 installed which is my primary OS ..and ubuntu on another drive as Secondary OS to learn Linux

---

### Post by beew on 2011-04-05
I am not sure what you may "learn" in this undertaking other than how to add a ppa. It is not like you are compiling the kernel yourself. There is much more to learn than to do something like that.

---

### Post by krishna.988 on 2011-04-05
> **beew said:**
> I am not sure what you may "learn" in this undertaking other than how to add a ppa. It is not like you are compiling the kernel yourself. There is much more to learn than to do something like that.

Ok please tell me how to do that.. Thanks!

---

### Post by beew on 2011-04-05
The link points to a collection of .deb files. If you don't even know how to install a .deb file, then no offence, I don't think you should be messing with unsupported kernels.

---

### Post by MountainX on 2011-04-24
> **messie said:**
> Except if your laptop doesn't go into sleep mode (fixed with kernel 2.6.36) and your bluetooth mouse doesn't connect (fixed with kernel 2.6.37). If you google it there are pre-compiled kernels for ubuntu maverick 2.6.36 and 2.6.37...
and for 2.6.38:
[http://www.ramoonus.nl/2011/03/linux-kernel-2-6-38-installation-guide-for-ubuntu-linux/](http://www.ramoonus.nl/2011/03/linux-kernel-2-6-38-installation-guide-for-ubuntu-linux/)

(the 2.6.36 and 2.6.37 worked perfectly for my Ubuntu 10.10 x64 compiled by this guy, going to try 2.6.38 just now :D)

With Maverick and kernel 2.6.35-28 I'm also have USB 3.0 errors in addition to the suspend-resume errors you mentioned. I tested Natty beta 2 LiveCD and it seems to solve most of my errors. I don't want to switch to Natty (it has other bugs), but I would like to use kernel 2.6.38-4 ([http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)).

How did it work for you?

---

### Post by jcolyn on 2011-04-24
I used this method to upgrade my kernel to 2.6.38 which is the Ubuntu kernel.

Go to the link and scroll toward the bottom of the list and pick the latest kernel. I would however stay away from the RC kernels.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")

For the 32 bit kernel download the linux-headers all.deb and i386.deb and linux-image i386.deb

For the 64 bit kernel download the linux-headers all.deb and amd64.deb and linux-image amd64.deb

Now go to the download folder where you downloaded the files and double-click the .deb files in this order.

First the linux-header ending in all.deb once installed double-click the linux-header ending in i386.deb (or amd64.deb if 64 bit)

Last double-click the linux-image ending in i386.deb (or amd64.deb if 64 bit)

Be sure to install in the above order and i386 or amd64 whichever your computer is.

Once it installs reboot and your computer will boot on the 2.6.38 kernel

Kernel 2.6.39 may be out in a week or two..

---

### Post by MountainX on 2011-04-24
I tried it too. Here are my results (including an error and how I resolved it)

```

uname -a
Linux desktop 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 18:42:20 UTC 2011 x86_64 GNU/Linux

Browse this website http://kernel.ubuntu.com/ 
I want v2.6.38.4-natty (there are some for 2.6.39 too)

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38.4-natty/linux-headers-2.6.38-02063804_2.6.38-02063804.201104221009_all.deb

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38.4-natty/linux-headers-2.6.38-02063804-generic_2.6.38-02063804.201104221009_amd64.deb

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38.4-natty/linux-image-2.6.38-02063804-generic_2.6.38-02063804.201104221009_amd64.deb

Make absolutely sure that you install them in this order : 

sudo dpkg -i linux-headers-2.6.38-02063804_2.6.38-02063804.201104221009_all.deb

sudo dpkg -i linux-headers-2.6.38-02063804-generic_2.6.38-02063804.201104221009_amd64.deb

sudo dpkg -i linux-image-2.6.38-02063804-generic_2.6.38-02063804.201104221009_amd64.deb

```OOOPS - errors!!!
Actually, they are warnings, but they are imporant and I needed to fix them:
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168d-2.fw for module r8169
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168d-1.fw for module r8169

Here's how to fix firmware for 8169 using linux-firmware package from natty:
```

wget https://launchpad.net/ubuntu/+archive/primary/+files/linux-firmware_1.49_all.deb
sudo dpkg -i linux-firmware_1.49_all.deb 
sudo update-initramfs -u

sudo update-grub

reboot

uname -a
Linux desktop 2.6.38-02063804-generic #201104221009 SMP Fri Apr 22 10:11:24 UTC 2011 x86_64 GNU/Linux

```Seems to have fixed my problems! So far this is a huge improvement :D
(I'll do more testing over the next few days...)

---

### Post by MountainX on 2011-04-24
> **rvchari said:**
> is vbox functioning well ? coz when i did it earlier, vbox kernel modules cudnt load even after re-compiling !!! so i had no choice but to revert back to prev kernel...

It is not a problem for me, but in response to your question, no, VBox isn't working...

 * dkms: running auto installation service for kernel 2.6.38-02063804-generic                                                                                   
 *       virtualbox-ose (3.2.8)...                                       [fail] 

 * dkms: running auto installation service for kernel 2.6.38-02063804-generic                                                                                   
 *       virtualbox-ose (3.2.8)...                                       [fail] 

I don't care about it right now. I'll probably fix it after Natty is released. But I suspect you could fix it the same way I fixed the modules for r8169 (see post above). You'll probably just have to download some packages from the VirtualBox site or a PPA... 
Maybe you can start here: [http://www.ubuntuupdates.org/packages/show/292938](http://www.ubuntuupdates.org/packages/show/292938)

Let me know if you fix it...

---

### Post by mathgeek2000 on 2011-04-24
I've played with upgrading the kernel, a few times following the instructions here:

[How To Compile A Kernel - The Ubuntu Way - Page 2 | HowtoForge - Linux Howtos and Tutorials]("http://www.howtoforge.com/kernel_compilation_ubuntu_p2") 

It works, ok -- But I've had issues getting VirtualBox to work with the custom kernel. & there's not a big improvement at least on my hardware. (HP 6910p - Intel Graphics, SATA 160GB HDD, 2GB Memory)

---

### Post by sandyd on 2011-04-24
> **MountainX said:**
> It is not a problem for me, but in response to your question, no, VBox isn't working...

 * dkms: running auto installation service for kernel 2.6.38-02063804-generic                                                                                   
 *       virtualbox-ose (3.2.8)...                                       [fail] 

 * dkms: running auto installation service for kernel 2.6.38-02063804-generic                                                                                   
 *       virtualbox-ose (3.2.8)...                                       [fail] 

I don't care about it right now. I'll probably fix it after Natty is released. But I suspect you could fix it the same way I fixed the modules for r8169 (see post above). You'll probably just have to download some packages from the VirtualBox site or a PPA... 
Maybe you can start here: [http://www.ubuntuupdates.org/packages/show/292938](http://www.ubuntuupdates.org/packages/show/292938)

Let me know if you fix it...
VirtualBox 4.04 r70112 works with the Vanilla kernel (on gentoo).
Upgrade (or download) the latest virtualbox from the virtualbox site and see if it works.

---

