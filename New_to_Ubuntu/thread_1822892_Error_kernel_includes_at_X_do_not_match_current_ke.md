---
title: "Error: kernel includes at X do not match current kernels"
date: 2011-08-11
forum: New to Ubuntu
---

### Post by ole1 on 2011-08-11
Hi. I am new to Ubuntu and currently using Ubuntu 10.04.3 (kernel: 2.6.38-10-generic). I tried to install the fglrx driver for my ATI Radeon HD 4200 video card. The installation failed and referred me to a make.log which tells me:

"
Error: kernel includes at /lib/modules/2.6.38-10-generic/build/include do not match current kernel.
they are versioned as "" instead of "2.6.38-10-generic".
you might need to adjust your symlinks:
- /usr/include
- /usr/src/linux
"

Which brings me to the question: how do i adjust these symlinks? Also: /usr/src/linux does not exist on my machine.

Thank you in advance.

---

### Post by matt_symes on 2011-08-11
Hi

How are you trying to install the drivers ? What guide are you following ?

Have you checked in System->Administration->Hardware drivers and looked for the driver there ?

Kind regards

---

### Post by ole1 on 2011-08-11
Hi.

I went to System->Administration->Hardware Drivers and chose the proprietary driver. The system then downloaded the driver and tried to install it, resulting in the error message below. This now happens every time I run 'sudo apt-get upgrade'.

Thanks

PS: Here is the aforementioned error message. Some of it is in german. If translating those parts would help, I can try but my technical english probably is not up to par.

fglrx (2:8.723.1-0ubuntu5) wird eingerichtet ...
Removing old fglrx-8.723.1 DKMS files...

------------------------------
Deleting module version: 8.723.1
completely from the DKMS tree.
------------------------------
Done.
Loading new fglrx-8.723.1 DKMS files...
Building only for 2.6.38-10-generic
Building for architecture i686
Building initial module for 2.6.38-10-generic

Error! Bad return status for module build on kernel: 2.6.38-10-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/fglrx/8.723.1/build/ for more information.
dpkg: Fehler beim Bearbeiten von fglrx (--configure):
 Unterprozess installiertes post-installation-Skript gab den Fehlerwert 10 zurück
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von fglrx-amdcccle:
 fglrx-amdcccle hängt ab von fglrx; aber:
  Paket fglrx ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von fglrx-amdcccle (--configure):
 Abhängigkeitsprobleme - verbleibt unkonfiguriert

---

### Post by matt_symes on 2011-08-12
Hi

Please post the output of 

```
ls -l /lib/modules/2.6.38-10-generic/build/
```

(that is a small L above) and 

```
ls /usr/src/
```

Kind regards

---

### Post by ole1 on 2011-08-16
Hi.


$ ls -l /lib/modules/2.6.38-10-generic/build/
File or folder not found.


$ ls /usr/src/
fglrx-8.723.1
linux-headers-2.6.32-32
linux-headers-2.6.32-33
linux-headers-2.6.32-33-generic
linux-headers-2.6.38-10
linux-headers-2.6.38-10-generic


Kind Regards.

---

### Post by matt_symes on 2011-08-18
Hi

Sorry for my delay in responding. 

> $ ls -l /lib/modules/2.6.38-10-generic/build/
File or folder not found.

The above is telling.

Can you post the output of.

```
ls -l /lib/modules
```

and

```
ls -l /lib/modules/2.6.38-10-generic
```

That is a small L as before.

Kind regards

---

### Post by ole1 on 2011-08-22
Hi.

Here it is:

~$ ls -l /lib/modules
insgesamt (total) 16
drwxr-xr-x 3 root root 4096 2011-07-23 11:18 2.6.32-28-generic
drwxr-xr-x 3 root root 4096 2011-07-23 11:18 2.6.32-32-generic
drwxr-xr-x 5 root root 4096 2011-08-11 12:54 2.6.32-33-generic
drwxr-xr-x 4 root root 4096 2011-08-11 12:31 2.6.38-10-generic

~$ ls -l /lib/modules/2.6.38-10-generic
insgesamt 4224
lrwxrwxrwx  1 root root     40 2011-07-07 02:37 build -> /usr/src/linux-headers-2.6.38-10-generic
drwxr-xr-x  2 root root   4096 2011-07-22 19:47 initrd
drwxr-xr-x 11 root root   4096 2011-07-22 19:47 kernel
-rw-r--r--  1 root root 677943 2011-07-22 19:48 modules.alias
-rw-r--r--  1 root root 655892 2011-07-22 19:48 modules.alias.bin
-rw-r--r--  1 root root   6097 2011-07-07 02:28 modules.builtin
-rw-r--r--  1 root root   7438 2011-07-22 19:48 modules.builtin.bin
-rw-r--r--  1 root root     69 2011-07-22 19:47 modules.ccwmap
-rw-r--r--  1 root root 309073 2011-07-22 19:47 modules.dep
-rw-r--r--  1 root root 459000 2011-07-22 19:47 modules.dep.bin
-rw-r--r--  1 root root    186 2011-07-22 19:48 modules.devname
-rw-r--r--  1 root root    665 2011-07-22 19:47 modules.ieee1394map
-rw-r--r--  1 root root    218 2011-07-22 19:47 modules.inputmap
-rw-r--r--  1 root root  21509 2011-07-22 19:47 modules.isapnpmap
-rw-r--r--  1 root root    610 2011-07-22 19:47 modules.ofmap
-rw-r--r--  1 root root 126391 2011-07-07 02:28 modules.order
-rw-r--r--  1 root root 438901 2011-07-22 19:47 modules.pcimap
-rw-r--r--  1 root root   1723 2011-07-22 19:47 modules.seriomap
-rw-r--r--  1 root root    131 2011-07-22 19:48 modules.softdep
-rw-r--r--  1 root root 244918 2011-07-22 19:48 modules.symbols
-rw-r--r--  1 root root 313418 2011-07-22 19:48 modules.symbols.bin
-rw-r--r--  1 root root 999852 2011-07-22 19:47 modules.usbmap

---

### Post by click170 on 2011-08-31
Any progress? I'm having the same problem on a diskless Ubuntu 11.04 client.

---

### Post by click170 on 2011-08-31
To troubleshoot this I tried going to '/var/lib/dkms/fglrx/8.593/build' and executing 'sudo ./make.sh' but then I got this;

```
jeff@stan:/var/lib/dkms/fglrx/8.593/build$ sudo ./make.sh 
AMD kernel module generator version 2.1
cat: /lib/modules/2.6.38-11-generic/build/include/linux/utsrelease.h: No such file or directory
Error:
kernel includes at /lib/modules/2.6.38-11-generic/build/include do not match current kernel.
they are versioned as ""
instead of "2.6.38-11-generic".
you might need to adjust your symlinks:
- /usr/include
- /usr/src/linux

```

Which seems to indicate a problem locating utsrelease.h.  So, I did "find / | grep 'utsrelease.h'" and found a copy and symlinked that into place, and ran it again.  Now, the output is different, but I can't make heads or tails of it;

```
AMD kernel module generator version 2.1
doing Makefile based build for kernel 2.6.x and higher
rm -rf *.c *.h *.o *.ko *.GCC* .??* *.symvers
make -C /lib/modules/2.6.38-11-generic/build SUBDIRS=/var/lib/dkms/fglrx/8.593/build/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-11-generic'
  CC [M]  /var/lib/dkms/fglrx/8.593/build/2.6.x/firegl_public.o
/var/lib/dkms/fglrx/8.593/build/2.6.x/firegl_public.c:41:2: error: #error unknown or undefined architecture configured
In file included from /var/lib/dkms/fglrx/8.593/build/2.6.x/firegl_public.c:169:0:
/var/lib/dkms/fglrx/8.593/build/2.6.x/firegl_public.h:164:0: warning: "PM_EVENT_SUSPEND" redefined
include/linux/pm.h:331:0: note: this is the location of the previous definition
/var/lib/dkms/fglrx/8.593/build/2.6.x/firegl_public.c:390:5: error: unknown field ‘ioctl’ specified in initializer
/var/lib/dkms/fglrx/8.593/build/2.6.x/firegl_public.c:390:5: warning: initialization from incompatible pointer type
In file included from /var/lib/dkms/fglrx/8.593/build/2.6.x/drmP.h:86:0,
                 from /var/lib/dkms/fglrx/8.593/build/2.6.x/drm_proc.h:41,
                 from /var/lib/dkms/fglrx/8.593/build/2.6.x/firegl_public.c:431:
/var/lib/dkms/fglrx/8.593/build/2.6.x/drm_os_linux.h:45:14: error: conflicting types for ‘irqreturn_t’
include/linux/irqreturn.h:16:24: note: previous declaration of ‘irqreturn_t’ was here
In file included from /var/lib/dkms/fglrx/8.593/build/2.6.x/firegl_public.c:431:0:
/var/lib/dkms/fglrx/8.593/build/2.6.x/drm_proc.h: In function ‘FGLDRM__vma_info’:
/var/lib/dkms/fglrx/8.593/build/2.6.x/drm_proc.h:497:2: warning: format ‘%08lx’ expects type ‘long unsigned int’, but argument 5 has type ‘phys_addr_t’
/var/lib/dkms/fglrx/8.593/build/2.6.x/firegl_public.c: In function ‘fglrx_pci_suspend’:
/var/lib/dkms/fglrx/8.593/build/2.6.x/firegl_public.c:773:9: error: implicit declaration of function ‘acquire_console_sem’
/var/lib/dkms/fglrx/8.593/build/2.6.x/firegl_public.c:795:9: error: implicit declaration of function ‘release_console_sem’
/var/lib/dkms/fglrx/8.593/build/2.6.x/firegl_public.c: In function ‘__ke__cmpxchg’:
/var/lib/dkms/fglrx/8.593/build/2.6.x/firegl_public.c:1363:12: error: variable or field ‘__ret’ declared void
/var/lib/dkms/fglrx/8.593/build/2.6.x/firegl_public.c:1363:12: error: variable or field ‘__old’ declared void
/var/lib/dkms/fglrx/8.593/build/2.6.x/firegl_public.c:1363:12: error: variable or field ‘__new’ declared void
/var/lib/dkms/fglrx/8.593/build/2.6.x/firegl_public.c: In function ‘KCL_GetEffectiveUid’:
/var/lib/dkms/fglrx/8.593/build/2.6.x/firegl_public.c:1405:19: error: ‘struct task_struct’ has no member named ‘euid’
/var/lib/dkms/fglrx/8.593/build/2.6.x/firegl_public.c: In function ‘KCL_PosixSecurityCapSetIPCLock’:
/var/lib/dkms/fglrx/8.593/build/2.6.x/firegl_public.c:1779:9: error: ‘struct task_struct’ has no member named ‘cap_effective’
/var/lib/dkms/fglrx/8.593/build/2.6.x/firegl_public.c:1783:9: error: ‘struct task_struct’ has no member named ‘cap_effective’
/var/lib/dkms/fglrx/8.593/build/2.6.x/firegl_public.c: In function ‘KCL_InstallInterruptHandler’:
/var/lib/dkms/fglrx/8.593/build/2.6.x/firegl_public.c:2661:9: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
include/linux/interrupt.h:136:1: note: expected ‘irq_handler_t’ but argument is of type ‘irqreturn_t (*)(int,  void *)’
/var/lib/dkms/fglrx/8.593/build/2.6.x/firegl_public.c: In function ‘KCL_MEM_VM_GetRegionPhysAddrStr’:
/var/lib/dkms/fglrx/8.593/build/2.6.x/firegl_public.c:3223:5: warning: return makes pointer from integer without a cast
/var/lib/dkms/fglrx/8.593/build/2.6.x/firegl_public.c:3224:5: warning: return makes pointer from integer without a cast
/var/lib/dkms/fglrx/8.593/build/2.6.x/firegl_public.c:3225:5: warning: return makes pointer from integer without a cast
/var/lib/dkms/fglrx/8.593/build/2.6.x/firegl_public.c:3227:5: warning: return makes pointer from integer without a cast
/var/lib/dkms/fglrx/8.593/build/2.6.x/firegl_public.c: In function ‘KAS_Ih_Execute’:
/var/lib/dkms/fglrx/8.593/build/2.6.x/firegl_public.c:4202:9: warning: ‘return’ with no value, in function returning non-void
/var/lib/dkms/fglrx/8.593/build/2.6.x/firegl_public.c: In function ‘KAS_Mutex_Initialize’:
/var/lib/dkms/fglrx/8.593/build/2.6.x/firegl_public.c:4898:5: error: implicit declaration of function ‘init_MUTEX’
/var/lib/dkms/fglrx/8.593/build/2.6.x/firegl_public.c: In function ‘KCL_GetEffectiveUid’:
/var/lib/dkms/fglrx/8.593/build/2.6.x/firegl_public.c:1406:1: warning: control reaches end of non-void function
make[2]: *** [/var/lib/dkms/fglrx/8.593/build/2.6.x/firegl_public.o] Error 1
make[1]: *** [_module_/var/lib/dkms/fglrx/8.593/build/2.6.x] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-11-generic'
make: *** [kmod_build] Error 2
build failed with return value 2
```

Should I not have symlinked that file? I made sure it had the write kernel version in it before symlinking it..

Does anybody know how to get this to work? I just want to be able to watch a simply video without my CPU spiking lol

---

