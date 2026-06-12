---
title: "How to get Realtek rtl8812au driver to compile on Ubuntu 18.04"
date: 2018-07-26
forum: Networking &amp; Wireless
---

### Post by ChildOfMana on 2018-07-26
Hi,

I'm having an absolute nightmate trying to get my [TP-Link Archer T4U AC1300 V2]("https://www.tp-link.com/uk/products/details/cat-11_Archer-T4U.html") USB WiFi adapter working with Ubuntu 18.04, kernel 4.15.

It was working fine on a previous Linux Mint install on this same PC, though it was an earlier kernel (I forget precisely which version now).

The official driver on the product page only supports up to kernel 4.7. I tried it anyway but no joy.

I've tried [this]("https://github.com/mk-fg/rtl8812au"), [this]("https://github.com/gnab/rtl8812au"), [this]("https://github.com/gordboy/rtl8812au") and [this]("https://github.com/yahont/rtl8812au"), as well as a couple of others that I've now lost the links to. I can't get any of them to compile. Here's the errors I'm coming up against for the last two respectively...

([https://github.com/gordboy/rtl8812au](https://github.com/gordboy/rtl8812au)) trying to install with dkms:
```

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area...
'make' -j4 KVER=4.15.0-20-generic KSRC=/lib/modules/4.15.0-20-generic/build...(bad exit status: 2)
ERROR (dkms apport): binary package for rtl8812au: 5.2.9 not found
Error! Bad return status for module build on kernel: 4.15.0-20-generic (x86_64)
Consult /var/lib/dkms/rtl8812au/5.2.9/build/make.log for more information.

```

and...

([https://github.com/yahont/rtl8812au](https://github.com/yahont/rtl8812au)) trying to compile and install with make && sudo make install:
```

compilation terminated.
scripts/Makefile.build:332: recipe for target '/home/dave/Desktop/newdrivers/rtl8812au-master/core/rtw_cmd.o' failed
make[2]: *** [/home/dave/Desktop/newdrivers/rtl8812au-master/core/rtw_cmd.o] Error 1
Makefile:1552: recipe for target '_module_/home/dave/Desktop/newdrivers/rtl8812au-master' failed
make[1]: *** [_module_/home/dave/Desktop/newdrivers/rtl8812au-master] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.15.0-20-generic'
Makefile:1639: recipe for target 'modules' failed
make: *** [modules] Error 2

```

Both of these *should* work with kernel ver. 4.15 and anecdotally people seem to be having success with them, but I just can't seem to get anywhere.

Any help will be greatly appreciated.

Cheers.

---

### Post by jeremy31 on 2018-07-26
What result for```
mokutil --sb-state
```

---

### Post by ChildOfMana on 2018-07-26
mokutil isn't installed. I've been using cube to install packages offline but it takes an age due to having to ferry the data back and forth on a usb stick. I'll get it done as soon as I can and post the output back here though.

---

### Post by ChildOfMana on 2018-07-26
> **jeremy31 said:**
> What result for```
mokutil --sb-state
```

Output:
```

EFI variables are not supported on this system

```

---

### Post by jeremy31 on 2018-07-26
Try [https://github.com/abperiasamy/rtl8812AU_8821AU_linux](https://github.com/abperiasamy/rtl8812AU_8821AU_linux)
after ```
sudo apt install build-essential
```

---

### Post by ChildOfMana on 2018-07-26
> **jeremy31 said:**
> Try [https://github.com/abperiasamy/rtl8812AU_8821AU_linux](https://github.com/abperiasamy/rtl8812AU_8821AU_linux)
after ```
sudo apt install build-essential
```

I already have the build-essential package installed and that driver is one I've already tried. I can't remember specifically why it failed now though and I didn't take a copy of the output at the time so I'll try it again and post back here. It'll have to be tomorrow evening now though unfortunately but I'll let you know how I get on.

Thanks for the help so far.

---

### Post by ChildOfMana on 2018-07-27
Okay here's the output when trying to install [https://github.com/abperiasamy/rtl8812AU_8821AU_linux](https://github.com/abperiasamy/rtl8812AU_8821AU_linux)

```

make clean
make[1]: Entering directory '/home/dave/Desktop/newdrivers/abperiasamy-rtl8812AU_8821AU_linux-master/rtl8812AU_8821AU_linux-master'
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.15.0-20-generic/build M=/home/dave/Desktop/newdrivers/abperiasamy-rtl8812AU_8821AU_linux-master/rtl8812AU_8821AU_linux-master clean
make[2]: Entering directory '/usr/src/linux-headers-4.15.0-20-generic'
make[2]: Leaving directory '/usr/src/linux-headers-4.15.0-20-generic'
make[1]: Leaving directory '/home/dave/Desktop/newdrivers/abperiasamy-rtl8812AU_8821AU_linux-master/rtl8812AU_8821AU_linux-master'
mkdir -p '/usr/src/rtl8812au-4.3.14'
cp -r dkms.conf Kconfig Makefile.dkms Makefile platform core hal include os_dep '/usr/src/rtl8812au-4.3.14'
cp Makefile '/usr/src/rtl8812au-4.3.14/Makefile'
sed 's/#MODULE_VERSION#/4.3.14/' dkms.conf > '/usr/src/rtl8812au-4.3.14/dkms.conf'
dkms add -m rtl8812au -v 4.3.14 2>/dev/null || true
dkms build -m rtl8812au -v 4.3.14

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area...
make -j4 KERNELRELEASE=4.15.0-20-generic KVER=4.15.0-20-generic...(bad exit status: 2)
ERROR (dkms apport): binary package for rtl8812au: 4.3.14 not found
Error! Bad return status for module build on kernel: 4.15.0-20-generic (x86_64)
Consult /var/lib/dkms/rtl8812au/4.3.14/build/make.log for more information.
Makefile.dkms:18: recipe for target 'build' failed
make: *** [build] Error 10

```

**Edit:** Urgh! Turns out build-essential isn't installed, even though cube says it is. I can't get cube to install it. I don't know why. This is so, SO frustrating ](*,)

**Edit 2:** So turns out I can't get build-essential installed at all. There are way too many dependencies to resolve manually, cube isn't working and I have no idea why and trying to install from the Live CD is throwing all sorts of errors about unresolved dependencies but then trying to install the needed dependencies throws all sorts of errors and so on... after 5 whole days of working on this damn installation I'm about ready to give up. It really shouldn't be this hard to get a WiFi dongle up and running. It's a sad, sad day indeed when Windows out-classes Linux :mad:

---

### Post by ChildOfMana on 2018-07-28
Well I took some very extreme measures and FINALLY got it working... but now it's broke again ](*,)](*,)](*,)](*,)

Here's what happened:

I figured the only way to get everything necessary installed was to get this damn machine temporarily online. The PC is located 2 floors away from the nearest router so ethernet is out of the question so to get it hooked up I figured I'd use USB tethering from my phone... but my network provider doesn't allow tethering on my price plan :x So, I went to the trouble of rooting my phone and installing a custom ROM on it just so I could share it's data connection via USB. Yes, *that's* how far I had to go just to install build-essentials and resolve all necessary dependencies so I could compile a driver. Unbelievable!

Anyway, the driver (finally!) compiled and installed. I was online. At last.

So... I ran a software update...

...and after a restart the wireless card isn't detected. Again. Well hello square one, I wish I could say it's been a while!!

This is the output from dkms status:

```

rtl8812au, 4.3.14, 4.15.0-20-generic, x86_64: installed
rtl8812au, 4.3.14, 4.15.0-29-generic, x86_64: installed

```

It looks like the software update installed a new kernel version (I'm used to Mint where a new kernel version isn't automatically flagged for installation). Clearly the driver, though installed, is not compatible with the newer kernel.

It's official; I give up!

Any suggestions?

---

### Post by jeremy31 on 2018-07-28
[ATTACH]280539[/ATTACH]
Download the file, copy it to Ubuntu Desktop, right click choose extract here, then in terminal
```
cd Desktop
sudo cp rtl8812au.ko /lib/modules/$(uname -r)/kernel/drivers/net/wireless/
sudo depmod -a
```
See if it works after reboot

The file will only work with the 4.15.0-29 kernel

---

### Post by ChildOfMana on 2018-07-28
Well this is weird. I logged on to carry out your instructions and the WiFi adaptor is back again!!! It seems to be fully functional as far as I can tell. I've rebooted a couple of times and it's still up. I wonder why it disappeared after the update and several reboots still failed to bring it back yet now all of a sudden here it is? Random! :confused:

Nothing has been installed or updated since it went down.

Anyway, I've kept a copy of the file you posted jeremy31 and if the adaptor goes down again I'll try your suggestion.

In the mean time is there a way I can prevent Ubuntu automatically installing new kernel versions? If this one turns out to be stable then, major security patches aside, I see no reason to upset the equilibrium by moving to a newer kernel version. Not if it's going to cause another round of headaches with the WiFi driver.

Thank you very much for your help in this, I very much appreciate it.

---

### Post by jeremy31 on 2018-07-28
Post results for ```
dkms status
```
It is not really safe to put a hold on kernel updates as they contain the security patches.  If you have an issue after a kernel update, check ```
modinfo rtl8812au | egrep 'filename|vermagic'
```
See if the vermagic kernel info matches the filename info

---

### Post by ChildOfMana on 2018-07-29
dkms status output:

```

nvidia, 390.48, 4.15.0-29-generic, x86_64: installed
rtl8812au, 4.3.14, 4.15.0-20-generic, x86_64: installed
rtl8812au, 4.3.14, 4.15.0-29-generic, x86_64: installed

```

(the nvidia driver is something I've added *since* the rtl8812au driver started working again)

[quote="jeremy31"]It is not really safe to put a hold on kernel updates as they contain the security patches.[/quote]

I know, I guess I'm just used to Mint which notifies of kernel updates and then lets you manually flag them for install so there are no nasty surprises.

Thank again.

---

