---
title: "Wireless does not work on Xubuntu 15.10 (Acer Aspire 5020)"
date: 2015-10-25
forum: Networking &amp; Wireless
---

### Post by tony0000-ac on 2015-10-25
Hi all!

I've finally upgraded to Xubuntu 15.10 on my Aspire 5020, and it works really great(!), but I have a problem with wireless PCI card (is important for me to have this working)

In 15.04, I successfully installed 'acerhk' module from a Launchpad PPA, but this PPA seems to be abandoned and last update is for Vivid; so I contacted PPA owner but no reply..

Actually I have acerhk-source files from 15.04 and I tried to compile them but compilation fails.

What can I do? Can I manually fix wrong code? How can I do it?

I really need wireless :(

EDIT: Solved! I did ```
sudo apt-get install firmware-b43-installer
``` and it works!

---

### Post by praseodym on 2015-10-25
Please try if this one compiles:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget media.cdn.ubuntu-de.org/forum/attachments/07/20/6674857-acerhk-0.5.6_dkms.tar.gz
sudo tar xvf 6674857-acerhk-0.5.6_dkms.tar.gz -C /usr/src
sudo dkms add -m acerhk -v 0.5.6
sudo dkms build -m acerhk -v 0.5.6
sudo dkms install -m acerhk -v 0.5.6 
```

---

### Post by tony0000-ac on 2015-10-25
> **praseodym said:**
> Please try if this one compiles:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget media.cdn.ubuntu-de.org/forum/attachments/07/20/6674857-acerhk-0.5.6_dkms.tar.gz
sudo tar xvf 6674857-acerhk-0.5.6_dkms.tar.gz -C /usr/src
sudo dkms add -m acerhk -v 0.5.6
sudo dkms build -m acerhk -v 0.5.6
sudo dkms install -m acerhk -v 0.5.6 
```

It does not work.

```
anthony@Aspire-5020:~$ sudo dkms build -m acerhk -v 0.5.6

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
'make' -C src/ all......(bad exit status: 2)
ERROR (dkms apport): binary package for acerhk: 0.5.6 not found
Error! Bad return status for module build on kernel: 4.2.0-17-generic (i686)
Consult /var/lib/dkms/acerhk/0.5.6/build/make.log for more information.
```

And in /var/lib/dkms/acerhk/0.5.6/build/make.log:

```
DKMS make.log for acerhk-0.5.6 for kernel 4.2.0-17-generic (i686)
dom 25 ott 2015, 18.50.07, CET
make: ingresso nella directory (entering to directory) "/var/lib/dkms/acerhk/0.5.6/build/src"
make -C /lib/modules/`uname -r`/build SUBDIRS=/var/lib/dkms/acerhk/0.5.6/build/src CONFIG_FUNCTION_TRACER= modules
make[1]: ingresso nella directory (entering to directory) "/usr/src/linux-headers-4.2.0-17-generic"
  CC [M]  /var/lib/dkms/acerhk/0.5.6/build/src/acerhk.o
/var/lib/dkms/acerhk/0.5.6/build/src/acerhk.c: In function ‘send_kbd_cmd’:
/var/lib/dkms/acerhk/0.5.6/build/src/acerhk.c:242:5: error: implicit declaration of function ‘preempt_enable_no_resched’ [-Werror=implicit-function-declaration]
     preempt_enable_no_resched();
     ^
/var/lib/dkms/acerhk/0.5.6/build/src/acerhk.c: In function ‘set_mail_led’:
/var/lib/dkms/acerhk/0.5.6/build/src/acerhk.c:817:26: warning: ‘regs.eax’ may be used uninitialized in this function [-Wmaybe-uninitialized]
   struct register_buffer regs;
                          ^
cc1: some warnings being treated as errors
scripts/Makefile.build:264: set di istruzioni per l'obiettivo (instructions set for objective) "/var/lib/dkms/acerhk/0.5.6/build/src/acerhk.o" non riuscito (failed)
make[2]: *** [/var/lib/dkms/acerhk/0.5.6/build/src/acerhk.o] Error 1
Makefile:1398: set di istruzioni per l'obiettivo (instructions set for objective) "_module_/var/lib/dkms/acerhk/0.5.6/build/src" non riuscito (failed)
make[1]: *** [_module_/var/lib/dkms/acerhk/0.5.6/build/src] Error 2
make[1]: uscita dalla directory (exit from directory) "/usr/src/linux-headers-4.2.0-17-generic"
Makefile:55: set di istruzioni per l'obiettivo (instructions set for objective) "acerhk.ko" non riuscito (failed)
make: *** [acerhk.ko] Error 2
make: uscita dalla directory (exit from directory) "/var/lib/dkms/acerhk/0.5.6/build/src"
```

I'm italian so I translated to english in '()'

---

### Post by praseodym on 2015-10-25
Was it this PPA? It was necessary from 13.04:

[https://launchpad.net/~gruenertee/+archive/ubuntu/acerhk](https://launchpad.net/~gruenertee/+archive/ubuntu/acerhk)

Lets try the old one which worked until 12.10 

[https://launchpad.net/~cogito-16/+archive/ubuntu/ppa](https://launchpad.net/~cogito-16/+archive/ubuntu/ppa)

---

### Post by tony0000-ac on 2015-10-25
> **praseodym said:**
> Was it this PPA? It was necessary from 13.04:

[https://launchpad.net/~gruenertee/+archive/ubuntu/acerhk](https://launchpad.net/~gruenertee/+archive/ubuntu/acerhk)

Lets try the old one which worked until 12.10 

[https://launchpad.net/~cogito-16/+archive/ubuntu/ppa](https://launchpad.net/~cogito-16/+archive/ubuntu/ppa)

Yes, was GruenerTee's PPA. I sent a mail to him but no reply. Still waiting.

Cogito-16's PPA does not work for 15.10.


Edit: *What if I compile Acerhk in 15.04, then I copy compiled 'acerhk.o' in 15.10? Can it work? *[B]It was a bad idea.

Edit 2: Solved!
[/B]

---

