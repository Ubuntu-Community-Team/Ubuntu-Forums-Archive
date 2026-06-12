---
title: "[SOLVED] 8.10 wireless networking isn't working"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by Taeo243 on 2009-01-10
I installed Ubuntu 8.10 for the first time a few days ago and I can't get the wireless internet to work. A wired ethernet connection works fine, but not my wireless card. I have a Broadcom 802.11b/g WLAN card and a HP Pavillion zv6100 laptop. Above the keyboard there is a killswitch(actually a kill button),which doesn't work in ubuntu. I think this button might be turning off the wireless card when i boot into ubuntu and I don't know how to turn it back on. Any help would be appreciated.

---

### Post by ibizatunes on 2009-01-10
With broadcom wireless you need restricted drivers, have you enabled them?
in system > admin > hardware drivers

---

### Post by Taeo243 on 2009-01-10
The only driver that shows up is the ATI driver

---

### Post by cdtech on 2009-01-10
Be sure that everything but the Source code is selected under the "Ubuntu Software" tab (System > Administration > Software Sources)

---

### Post by Taeo243 on 2009-01-10
Yes, everything is selected except for the source code and "CdRom with Ubuntu 8.10 Interped Ibex"

---

### Post by cdtech on 2009-01-10
Which broadcom do you have?
```
lspci
```
Try installing the "b43-fwcutter" from the synaptic package manager if you know for sure you have the broadcom. Just type b43 in the search box and it should come up.

---

### Post by ptn107 on 2009-01-10
Installing this package is the same as enabling the broadcom drivers in the Hardware Drivers applet.

[_b43-fwcutter_011-4ubuntu1_i386.deb (32-bit)_]("http://mirrors.kernel.org/ubuntu/pool/main/b/b43-fwcutter/b43-fwcutter_011-4ubuntu1_i386.deb")

[_b43-fwcutter_011-4ubuntu1_amd64.deb (64-bit)_]("http://mirrors.kernel.org/ubuntu/pool/main/b/b43-fwcutter/b43-fwcutter_011-4ubuntu1_amd64.deb")

---

### Post by Taeo243 on 2009-01-10
the wireless card is Broadcom BCM4318. I can't find the    "b43-fwcutter" package in the synaptic package manager.

---

### Post by cdtech on 2009-01-10
Open a terminal and try:
```
sudo apt-get install b43-fwcutter
```

---

### Post by Taeo243 on 2009-01-10
It says "Couldn't find package b43-fwcutter"

---

### Post by Taeo243 on 2009-01-10
I have to go for a couple of hours.:(

---

### Post by cdtech on 2009-01-10
Then your sources.list isn't correctly configured. Post:
```
cat /etc/apt/sources.list
```

---

### Post by tom56 on 2009-01-10
First of all, if you haven't done so already, use that wired connection to install updates and then try the Hardware Drivers thing again.

I have the same card (also in an HP Pavilion laptop). I am using the "Broadcom STA wireless driver" from System->Admin->Hardware Drivers. The package you need is linux-restricted-modules, but this should already be installed. All you need to do is enable the right driver. This link should help - [http://ubuntuforums.org/showthread.php?t=1025020](http://ubuntuforums.org/showthread.php?t=1025020)

This is a different driver to the b43 cutter one, and having tried both I find it works much better (I get a better signal).

Someone has filed a bug related to your problem here - [https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/291271](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/291271)

---

### Post by Taeo243 on 2009-01-10
Ok, here is the source.list code output. I put the brakets at the beginning and end of the post for clarity.                                                                                                            
{# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse}

---

### Post by Taeo243 on 2009-01-10
I hooked up my wired connection and started downloading the updated that were there, 219 of them:(. I decided to look in the Hardware Drivers program and two new drivers, Software Modem and Broadcom B43 (I am assuming this is b43-fwcutter) were there:P. I tried activate it, but I got this error message "SystemError: Failed to lock /var/cache/apt/archives/lock"
:confused:

---

### Post by Taeo243 on 2009-01-10
Well, I downloaded the updates from my ethernet connection and I restarted the computer and now I have 4 choices of linux 2 normal and 2 recovery I guess the one that ends with a 9 is the one i should use. Anyway I tried activating B43-fwcutter and it worked. What should I do now that i have it ins.... (voice trails off) YAY!!!!:):):):) my wireless internet works now! I guess all i needed was the driver. After I installed it I pressed my wireless killswitch and it turned my network card on!!! So this is solved. Thank you for your time everyone:)

---

### Post by Taeo243 on 2009-01-10
How do you mark a thread as solved?:embarassed:

---

### Post by hotweiss on 2009-01-11
> **Taeo243 said:**
> How do you mark a thread as solved?:embarassed:

Click on Thread Tools at the top...

---

### Post by tom56 on 2009-01-11
> **Taeo243 said:**
> Well, I downloaded the updates from my ethernet connection and I restarted the computer and now I have 4 choices of linux 2 normal and 2 recovery I guess the one that ends with a 9 is the one i should use. Anyway I tried activating B43-fwcutter and it worked. What should I do now that i have it ins.... (voice trails off) YAY!!!!:):):):) my wireless internet works now! I guess all i needed was the driver. After I installed it I pressed my wireless killswitch and it turned my network card on!!! So this is solved. Thank you for your time everyone:)

Glad you solved the problem! As for the two choices at boot, they are different kernel versions...

Whenever you install a new kernel (e.g. through an update), it gets added to the boot choices. You should always use the newest one (this will usually be the one listed at the top). The old choices are there so that if the new one doesn't work, you have the option of going back the old one.

---

### Post by Taeo243 on 2009-01-11
Ok, thanks

---

### Post by _self on 2009-01-11
Hello, would you help me to solve the similar question?
I use Dell Inspiron 1525 laptop with wireless card BCM4312 802.11b/g. After installing Ubuntu 8.10 it works fine.
Now i want to compile new kernel, 2.6.28 and turn off some helpless modules. For the beginning, I've downloaded the source of the kernel and used my current config to compile it and check its work. I was surprised when discovered that the wireless card couldn't be found. Config was absolutely identical, but it's something wrong with modules. What exactly - i cannot find while.
Now i have two text files with 'lsmod' output. I found module 'wl' in current stable kernel, and it's absent in 2.6.28. Also I couldn't find any file with such a name in /lib/modules/2.6.27-9-generic (current kernel).
In 27 kernel I can see restricted driver in 'System-Administration-Hardware Drivers', but in 28 - no way. There's an empty list there. I have installed b43-fwcutter from repository, then after reading [this]("http://linuxwireless.org/en/users/Drivers/b43#devicefirmware") tried to build it from source - no effect. Any ideas how to make it work? Thanks in advance! :)

---

### Post by tom56 on 2009-01-12
> **_self said:**
> Hello, would you help me to solve the similar question?
I use Dell Inspiron 1525 laptop with wireless card BCM4312 802.11b/g. After installing Ubuntu 8.10 it works fine.
Now i want to compile new kernel, 2.6.28 and turn off some helpless modules. For the beginning, I've downloaded the source of the kernel and used my current config to compile it and check its work. I was surprised when discovered that the wireless card couldn't be found. Config was absolutely identical, but it's something wrong with modules. What exactly - i cannot find while.
Now i have two text files with 'lsmod' output. I found module 'wl' in current stable kernel, and it's absent in 2.6.28. Also I couldn't find any file with such a name in /lib/modules/2.6.27-9-generic (current kernel).
In 27 kernel I can see restricted driver in 'System-Administration-Hardware Drivers', but in 28 - no way. There's an empty list there. I have installed b43-fwcutter from repository, then after reading [this]("http://linuxwireless.org/en/users/Drivers/b43#devicefirmware") tried to build it from source - no effect. Any ideas how to make it work? Thanks in advance! :)

I don't mean to sound harsh, but why are you compiling a new kernel? It sounds like you aren't clear on what you are doing. When you compile the kernel you need to make sure the module is enabled and also compiled. There's lots of guides on the internet for how to do this.

---

### Post by _self on 2009-01-12
Well, firstly i'm compiling new kernel to get more expirience with Linux. Secondly - to have my computer work better.
I can presume i configure new kernel wrong if i do that with the config written by myself. But here's another case - i copied working config (it means all modules are built in the same way that while installing the system from CD, isn't it?) and installed built kernel. I tried to do it using "make bzImage..." or using "fakeroot make-kpkg...". So the only variant i can understand is that new kernel has no supptor of that hardware. Of course, I'm not so clear on this, otherwise i would not ask for help :)

---

### Post by tom56 on 2009-01-14
> **_self said:**
> Well, firstly i'm compiling new kernel to get more expirience with Linux. Secondly - to have my computer work better.
I can presume i configure new kernel wrong if i do that with the config written by myself. But here's another case - i copied working config (it means all modules are built in the same way that while installing the system from CD, isn't it?) and installed built kernel. I tried to do it using "make bzImage..." or using "fakeroot make-kpkg...". So the only variant i can understand is that new kernel has no supptor of that hardware. Of course, I'm not so clear on this, otherwise i would not ask for help :)

It's been several years since I last compiled a kernel and my memory is a little hazy. Clearly, you need to built the right module. I used to use
```
make menuconfig
```
to do this, and make sure it is being built as a module and not built into the kernel.

---

