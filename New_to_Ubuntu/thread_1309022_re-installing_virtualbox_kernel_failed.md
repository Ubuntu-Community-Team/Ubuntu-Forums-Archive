---
title: "re-installing virtualbox kernel failed"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by pgar23 on 2009-11-01
Hello community,

I am trying to install VirtualBox with USB support following this guide:

[http://www.ghacks.net/2009/08/01/install-virtualbox-with-usb-support/](http://www.ghacks.net/2009/08/01/install-virtualbox-with-usb-support/)

I have done all steps, but now when I am try to install Windows 7, program tell me this:

```

python@python-laptop:~$ sudo /etc/init.d/vboxdrv setup
[sudo] password for python: 
 * Stopping VirtualBox kernel module                                             *  done.
 * Removing old VirtualBox kernel module                                         *  done.
 * Recompiling VirtualBox kernel module                                         
 * Look at /var/log/vbox-install.log to find out what went wrong
python@python-laptop:~$ 
```

The output of /var/log/virtualbox.log:
```

Attempting to install using DKMS
  removing old DKMS module vboxdrv version  2.2.4

-------- Uninstall Beginning --------
Module:  vboxdrv
Version: 2.2.4
Kernel:  2.6.31-14-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxdrv.ko:
 - Uninstallation
   - Deleting from: /lib/modules/2.6.31-14-generic/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod.......

DKMS: uninstall Completed.

------------------------------
Deleting module version: 2.2.4
completely from the DKMS tree.
------------------------------
Done.

Creating symlink /var/lib/dkms/vboxdrv/2.2.4/source ->
                 /usr/src/vboxdrv-2.2.4

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
su nobody -c "make KERNELRELEASE=2.6.31-14-generic -C /lib/modules/2.6.31-14-generic/build M=/var/lib/dkms/vboxdrv/2.2.4/build".......

Running the post_build script:
cleaning build area....

DKMS: build Completed.

vboxdrv.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.31-14-generic/updates/dkms/

depmod....

DKMS: install Completed.
Attempting to install using DKMS
  removing old DKMS module vboxnetflt version  2.2.4

------------------------------
Deleting module version: 2.2.4
completely from the DKMS tree.
------------------------------
Done.

Creating symlink /var/lib/dkms/vboxnetflt/2.2.4/source ->
                 /usr/src/vboxnetflt-2.2.4

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Running the pre_build script:

Building module:
cleaning build area....
su nobody -c "make KERNELRELEASE=2.6.31-14-generic -C /lib/modules/2.6.31-14-generic/build M=/var/lib/dkms/vboxnetflt/2.2.4/build"....(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.31-14-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/vboxnetflt/2.2.4/build/ for more information.
0
0
Failed to install using DKMS, attempting to install without
make KBUILD_VERBOSE=1 -C /lib/modules/2.6.31-14-generic/build SUBDIRS=/tmp/vbox.0 SRCROOT=/tmp/vbox.0 modules
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";	\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /tmp/vbox.0/.tmp_versions ; rm -f /tmp/vbox.0/.tmp_versions/*
make -f scripts/Makefile.build obj=/tmp/vbox.0
  gcc -Wp,-MD,/tmp/vbox.0/linux/.VBoxNetFlt-linux.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.1/include  -Iinclude  -I/usr/src/linux-headers-2.6.31-14-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -fstack-protector-all -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -I/lib/modules/2.6.31-14-generic/build/include -I/tmp/vbox.0/ -I/tmp/vbox.0/include -I/tmp/vbox.0/r0drv/linux -D__KERNEL__ -DMODULE -DRT_OS_LINUX -DIN_RING0 -DIN_RT_R0 -DIN_SUP_R0 -DVBOX -DRT_WITH_VBOX -DVBOX_WITH_HARDENING -DRT_ARCH_AMD64 -DVBOX_WITH_64_BITS_GUESTS  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(VBoxNetFlt_linux)"  -D"KBUILD_MODNAME=KBUILD_STR(vboxnetflt)"  -c -o /tmp/vbox.0/linux/.tmp_VBoxNetFlt-linux.o /tmp/vbox.0/linux/VBoxNetFlt-linux.c
In file included from /tmp/vbox.0/include/VBox/intnet.h:34,
                 from /tmp/vbox.0/linux/../VBoxNetFltInternal.h:26,
                 from /tmp/vbox.0/linux/VBoxNetFlt-linux.c:47:
/tmp/vbox.0/include/VBox/stam.h:69:7: warning: "_MSC_VER" is not defined
/tmp/vbox.0/linux/VBoxNetFlt-linux.c: In function &#8216;vboxNetAdpNetDevInit&#8217;:
/tmp/vbox.0/linux/VBoxNetFlt-linux.c:225: error: &#8216;struct net_device&#8217; has no member named &#8216;open&#8217;
/tmp/vbox.0/linux/VBoxNetFlt-linux.c:226: error: &#8216;struct net_device&#8217; has no member named &#8216;stop&#8217;
/tmp/vbox.0/linux/VBoxNetFlt-linux.c:227: error: &#8216;struct net_device&#8217; has no member named &#8216;hard_start_xmit&#8217;
/tmp/vbox.0/linux/VBoxNetFlt-linux.c:228: error: &#8216;struct net_device&#8217; has no member named &#8216;get_stats&#8217;
make[2]: *** [/tmp/vbox.0/linux/VBoxNetFlt-linux.o] Error 1
make[1]: *** [_module_/tmp/vbox.0] Error 2
make: *** [vboxnetflt] Error 2
```

Why is the re-installation of the kernel going wrong>??

---

### Post by miklcct on 2009-11-01
Upgrade to a new version of VirtualBox.

---

