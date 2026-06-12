---
title: "Help in setting up D-Link DWL-G510"
date: 2007-02-22
forum: Networking &amp; Wireless
---

### Post by tinyang on 2007-02-22
I am using Ubuntu 6.06 and have tried following the installation instructions on [[color=blue]ndiswrapper wiki[/color]](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation) and has never got passed the stage on compiling and installing.

The terminal gives me this error when I tried using the make command:

bash: make command not found

What should I do?

Thanks.  :)

---

### Post by spd106 on 2007-02-22
To answer your question directly, you need to install the 'build-essential' package in order to use make. There are a few dependencies so it is best to install via synaptic.

---

### Post by tinyang on 2007-02-22
Is there an offline way of installing?

build-essential package is not in Synaptic, so I had downloaded it from [[color=blue]here[/color]](http://packages.ubuntu.com/hoary/devel/build-essential).

After this, I tried installing, but it needed internet connections, which I don't have. Currently running to and from my cousin's house for all my needs.

---

### Post by zanglang on 2007-02-22
1. Actually, isn't ndiswrapper already in the repository? 'apt-get install ndiswrapper-utils ndiswrapper-utils-1.8' (<-- off the top of my head, package name might be wrong) and you can move straight to the install windows driver step.

2. That's odd, build-essential ought to be included. Make sure you update your package lists first. 'apt-get update'.

3. You can offline-install by downloading the deb for ndiswrapper straight from the repositories but that's pretty much highly not recommended, so be careful there. ;)
[http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/](http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/)

---

### Post by tinyang on 2007-02-22
It wasn't included. Both the terminal and Synaptic couldn't find both of these packages.

> 2. That's odd, build-essential ought to be included. Make sure you update your package lists first. 'apt-get update'.

Er... that's impossible, because I'm still trying to set it up. Now at my cousin's house.

---

### Post by tinyang on 2007-02-23
The packages have installed successfully, but now I am getting funny errors.

First, following the article, I tried to link up the kernel and got this error:

```
root@tinyang-desktop:/home/tinyang# ln -s /usr/src/linux-2.6.15-26-386 /lib/modules/2.6.15-26-386/build
bash: kernel-version: No such file or directory
```

When I restart the computer and tried without linking, here's what I got:

```
root@tinyang-desktop:/home/tinyang/Desktop/ndiswrapper-1.37# make distclean
make -C driver clean
make[1]: Entering directory `/home/tinyang/Desktop/ndiswrapper-1.37/driver'rm -rf ndiswrapper.ko ndiswrapper.o crt.o hal.o iw_ndis.o loader.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o rtl.o wrapmem.o wrapndis.o wrapper.o divdi3.o usb.o win2lin_stubs.o \
           divdi3.o workqueue.o .*.ko.cmd .*.o.cmd \
           ndiswrapper.mod.[oc] *~ .tmp_versions Modules.symvers Module.symvers
make[1]: Leaving directory `/home/tinyang/Desktop/ndiswrapper-1.37/driver'
make -C utils clean
make[1]: Entering directory `/home/tinyang/Desktop/ndiswrapper-1.37/utils'
rm -f *~ *.o loadndisdriver
make[1]: Leaving directory `/home/tinyang/Desktop/ndiswrapper-1.37/utils'
rm -f *~
rm -fr ndiswrapper-1.37 ndiswrapper-1.37.tar.gz patch-stamp
make -C driver distclean
make[1]: Entering directory `/home/tinyang/Desktop/ndiswrapper-1.37/driver'rm -rf ndiswrapper.ko ndiswrapper.o crt.o hal.o iw_ndis.o loader.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o rtl.o wrapmem.o wrapndis.o wrapper.o divdi3.o usb.o win2lin_stubs.o \
           divdi3.o workqueue.o .*.ko.cmd .*.o.cmd \
           ndiswrapper.mod.[oc] *~ .tmp_versions Modules.symvers Module.symvers
rm -f *_exports.h .\#* win2lin_stubs.h
make[1]: Leaving directory `/home/tinyang/Desktop/ndiswrapper-1.37/driver'
make -C utils distclean
make[1]: Entering directory `/home/tinyang/Desktop/ndiswrapper-1.37/utils'
rm -f *~ *.o loadndisdriver
rm -f .\#*
make[1]: Leaving directory `/home/tinyang/Desktop/ndiswrapper-1.37/utils'
rm -f .\#*
root@tinyang-desktop:/home/tinyang/Desktop/ndiswrapper-1.37# make
make -C driver
make[1]: Entering directory `/home/tinyang/Desktop/ndiswrapper-1.37/driver'Can't find kernel build files in /lib/modules/2.6.15-26-386/build;
  give the path to kernel build directory with
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/tinyang/Desktop/ndiswrapper-1.37/driver'
make: *** [all] Error 2
```

---

### Post by durty_dawg on 2007-02-23
I was having problems with my d-link dwl-g650 at first then i was like oh updates. I updated then it was like almost immediate plug and play. So I would suggest updating your repos, and stuff first.

---

### Post by tinyang on 2007-02-23
I would love to, but without internet, I can't.

---

### Post by zanglang on 2007-02-25
Check if your kernel already has the ndiswrapper module, type 'modprobe -l' and search for 'ndiswrapper.ko'.

Is there any way you can bring the computer somewhere and update it? Or at the very least, download the ndiswrapper debs and install them instead of manually compiling...

Alternatively, if possible get the latest Edgy ISO that would've got newer driver updates.

---

### Post by tinyang on 2007-02-25
> Check if your kernel already has the ndiswrapper module, type 'modprobe -l' and search for 'ndiswrapper.ko'.

I will do this.

> Is there any way you can bring the computer somewhere and update it? Or at the very least, download the ndiswrapper debs and install them instead of manually compiling...

Downloading ndiswrapper debs and installing isn't a problem. I have installed Windows and got it to connect to the Net. The only problem now is the compilation, which is really frustrating.

> Alternatively, if possible get the latest Edgy ISO that would've got newer driver updates.

Good idea. If nothing works, I am going to download Edgy. I am giving up. 5 hours of downloading is better than 5 days of troubleshooting. Haha...

---

