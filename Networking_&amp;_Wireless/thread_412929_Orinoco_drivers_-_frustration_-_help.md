---
title: "Orinoco drivers - frustration - help?"
date: 2007-04-18
forum: Networking &amp; Wireless
---

### Post by gevans on 2007-04-18
I looked around the forums, and then some google searches but found nothing that was helpful....

I posted this in the Apple PPC area originally, and thought that it probably made more sense to post it here, so I am reposting it....needing a bit of help

I followed the guide at :
[https://help.ubuntu.com/community/Wi...t=%28kismet%29](https://help.ubuntu.com/community/Wi...t=%28kismet%29)

Got to the part where I type make and this is what happened.

#cd /usr/src/orinoco-0.15
# make
make -C /usr/src/linux-headers-2.6.20-15-powerpc M=/usr/src/orinoco-0.15 KERNELRELEASE=2.6.20-15-powerpc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-powerpc'
/usr/src/orinoco-0.15/Kbuild:38: *** This driver is already enabled in the kernel. Stop.
make[1]: *** [_module_/usr/src/orinoco-0.15] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-powerpc'
make: *** [modules] Error 2
#

can anyone tell me what I need to do to get this to compile?

So I looked around and was told I needed to rmmod the modules so it would compile. I did this and I get the same error :/

doing an lsmod reveals that the modules are indeed uninstalled. I moved the old orinoco files and the hermes file to a directory that I made in case something broke.

So, can anyone tell me why this is happening?? maybe I need to post this in the networking section? so I will do that as well.

---

### Post by chili555 on 2007-04-18
Your link is broken, so we can't examine your reference. Why are you trying to compile a tarball when a perfectly good orinoco module that works perfectly with kismet is in your kernel? 

You may have a great reason, but my laptop uses the in-built orinoco module and works well with kismet.

---

### Post by gevans on 2007-04-18
Sorry, about the bad reference. Try this one..

[https://help.ubuntu.com/community/WifiDocs/OrinocoKismet](https://help.ubuntu.com/community/WifiDocs/OrinocoKismet)

I am compiling it, because I get the following error when I try to run kismet:

FATAL: Could not find 'monitor' private ioctl or use the newer style 'mode monitor' command. This typically means that the drivers have not been patched or the correct drivers are being loaded. See the troubleshoting section of the README for more information
[1] + Done(1)            ${BIN}/kismet_server --silent ${server}

Machine and card:
Machine: Powerbook G3/500 firewire (Pismo)
Card: Apple Airport (original)

So, sadly for me,the orinoco driver doesn't just work with the original airport card :/

Greg

---

### Post by tturrisi on 2007-04-18
see [http://ubuntuforums.org/showthread.php?t=286621&highlight=orinoco](http://ubuntuforums.org/showthread.php?t=286621&highlight=orinoco)

---

### Post by gevans on 2007-04-19
> **tturrisi said:**
> see [http://ubuntuforums.org/showthread.php?t=286621&highlight=orinoco](http://ubuntuforums.org/showthread.php?t=286621&highlight=orinoco)

I appreciate the response, but I don't see anything related to the problem that I am having...Maybe I missed it??

---

### Post by tturrisi on 2007-04-19
> **gevans said:**
> I appreciate the response, but I don't see anything related to the problem that I am having...Maybe I missed it??

You need to patch the stock orinoco drivers because they don't natively support monitor mode w/ certain chipests.  The message you receive from kismet means that the drivers you have loaded do not support monitor mode.

---

### Post by gevans on 2007-04-19
> **tturrisi said:**
> You need to patch the stock orinoco drivers because they don't natively support monitor mode w/ certain chipests.  The message you receive from kismet means that the drivers you have loaded do not support monitor mode.

Yes, I understand this, and that is the reason I am attempting to compile the patched drivers and getting the error that I mentioned earlier, where I get THIS error:

#cd /usr/src/orinoco-0.15
# make
make -C /usr/src/linux-headers-2.6.20-15-powerpc M=/usr/src/orinoco-0.15 KERNELRELEASE=2.6.20-15-powerpc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-powerpc'
/usr/src/orinoco-0.15/Kbuild:38: *** This driver is already enabled in the kernel. Stop.
make[1]: *** [_module_/usr/src/orinoco-0.15] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-powerpc'
make: *** [modules] Error 2
#

---

### Post by chili555 on 2007-04-19
I suggest *sudo gedit Kbuild * to comment out this section:```
ifdef CONFIG_HERMES
$(error This driver is already enabled in the kernel)
endif
```Put # in front of each line, save, close and re-run make.

---

### Post by gevans on 2007-04-19
$ su -
Password: xxxxxxxxxxxx
# pico Kbuild
<edit lines as per instructions and my thinking last night>

/usr/src/orinoco-0.15# make
make -C /usr/src/linux-headers-2.6.20-15-powerpc M=/usr/src/orinoco-0.15 KERNELRELEASE=2.6.20-15-powerpc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-powerpc '
  CC [M]  /usr/src/orinoco-0.15/airport.o
/usr/src/orinoco-0.15/airport.c: In function 'airport_attach':
/usr/src/orinoco-0.15/airport.c:225: warning: passing argument 2 of 'request_irq' from incompatible pointer type
  CC [M]  /usr/src/orinoco-0.15/orinoco_nortel.o
In file included from /usr/src/orinoco-0.15/orinoco_nortel.c:51:
/usr/src/orinoco-0.15/orinoco_pci.h: In function 'orinoco_pci_resume':
/usr/src/orinoco-0.15/orinoco_pci.h:67: warning: passing argument 2 of 'request_irq' from incompatible pointer type
/usr/src/orinoco-0.15/orinoco_nortel.c: In function 'orinoco_nortel_init_one':
/usr/src/orinoco-0.15/orinoco_nortel.c:202: warning: passing argument 2 of 'request_irq' from incompatible pointer type
  CC [M]  /usr/src/orinoco- 0.15/orinoco_pci.o
In file included from /usr/src/orinoco-0.15/orinoco_pci.c:54:
/usr/src/orinoco-0.15/orinoco_pci.h: In function 'orinoco_pci_resume':
/usr/src/orinoco-0.15/orinoco_pci.h:67: warning: passing argument 2 of 'request_irq' from incompatible pointer type
/usr/src/orinoco-0.15/orinoco_pci.c: In function 'orinoco_pci_init_one':
/usr/src/orinoco-0.15/orinoco_pci.c:157: warning: passing argument 2 of 'request_irq' from incompatible pointer type
  CC [M]  /usr/src/orinoco- 0.15/orinoco_plx.o
In file included from /usr/src/orinoco-0.15/orinoco_plx.c:97:
/usr/src/orinoco-0.15/orinoco_pci.h: In function 'orinoco_pci_resume':
/usr/src/orinoco-0.15/orinoco_pci.h:67: warning: passing argument 2 of 'request_irq' from incompatible pointer type
/usr/src/orinoco-0.15/orinoco_plx.c: In function 'orinoco_plx_init_one':
/usr/src/orinoco-0.15/orinoco_plx.c:241: warning: passing argument 2 of 'request_irq' from incompatible pointer type
  CC [M]  /usr/src/orinoco- 0.15/orinoco_tmd.o
In file included from /usr/src/orinoco-0.15/orinoco_tmd.c:51:
/usr/src/orinoco-0.15/orinoco_pci.h: In function 'orinoco_pci_resume':
/usr/src/orinoco-0.15/orinoco_pci.h:67: warning: passing argument 2 of 'request_irq' from incompatible pointer type
/usr/src/orinoco-0.15/orinoco_tmd.c: In function 'orinoco_tmd_init_one':
/usr/src/orinoco-0.15/orinoco_tmd.c:143: warning: passing argument 2 of 'request_irq' from incompatible pointer type
  CC [M]  /usr/src/orinoco- 0.15/hermes.o
  CC [M]  /usr/src/orinoco-0.15/orinoco.o
/usr/src/orinoco-0.15/orinoco.c:2466:67: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/usr/src/orinoco-0.15/orinoco.c: In function 'alloc_orinocodev':
/usr/src/orinoco-0.15/orinoco.c:2466: error: 'INIT_WORK' undeclared (first use in this function)
/usr/src/orinoco-0.15/orinoco.c:2466: error: (Each undeclared identifier is reported only once
/usr/src/orinoco-0.15 /orinoco.c:2466: error: for each function it appears in.)
/usr/src/orinoco-0.15/orinoco.c:2467:68: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/usr/src/orinoco-0.15/orinoco.c:2468:75: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
make[2]: *** [/usr/src/orinoco-0.15/orinoco.o] Error 1
make[1]: *** [_module_/usr/src/orinoco-0.15] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-powerpc'
make: *** [modules] Error 2 

Grumble complain whine (grabs cheese to go with wine) grumble complain whine

ideas?

---

### Post by gevans on 2007-04-20
Just thought I would update this to see if anyone knows how to fix the compile errors I get now.

---

