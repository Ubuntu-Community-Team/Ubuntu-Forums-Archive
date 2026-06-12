---
title: "installing VMware"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by WinterMadness on 2009-05-26
hi, im trying to install vmware so i can run vista inside ubuntu. i get this error(i include everythingbecause i dont know what went wrong)

```


joe@joe-laptop:~/Desktop/vmware-server-distrib$ sudo /usr/bin/vmware-config.pl
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons? 
[/usr/share/icons] 

What directory contains your desktop menu entry files? These files have a 
.desktop file extension. [/usr/share/applications] 

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

/usr/share/applications/vmware-server.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
/usr/share/applications/vmware-console-uri-handler.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.28-11-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config2/vmmon-only'
make -C /lib/modules/2.6.28-11-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CC [M]  /tmp/vmware-config2/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config2/vmmon-only/./include/x86.h:20,
                 from /tmp/vmware-config2/vmmon-only/./include/machine.h:24,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:49:
/tmp/vmware-config2/vmmon-only/./include/x86apic.h:79:1: warning: "APIC_BASE_MSR" redefined
In file included from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/fixmap_32.h:29,
                 from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/fixmap.h:5,
                 from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/apic.h:8,
                 from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/smp.h:13,
                 from include/linux/smp.h:30,
                 from include/linux/topology.h:33,
                 from include/linux/mmzone.h:763,
                 from include/linux/gfp.h:4,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:12:
/usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/apicdef.h:132:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config2/vmmon-only/./include/machine.h:24,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:49:
/tmp/vmware-config2/vmmon-only/./include/x86.h:830:1: warning: "PTE_PFN_MASK" redefined
In file included from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/paravirt.h:7,
                 from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/irqflags.h:55,
                 from include/linux/irqflags.h:57,
                 from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/system.h:11,
                 from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/processor.h:17,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:12:
/usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/page.h:22:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config2/vmmon-only/linux/vmhost.h:13,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:71:
/tmp/vmware-config2/vmmon-only/./include/compat_semaphore.h:5:27: error: asm/semaphore.h: No such file or directory
/tmp/vmware-config2/vmmon-only/linux/driver.c:146: error: unknown field ‘nopage’ specified in initializer
/tmp/vmware-config2/vmmon-only/linux/driver.c:147: warning: initialization from incompatible pointer type
/tmp/vmware-config2/vmmon-only/linux/driver.c:150: error: unknown field ‘nopage’ specified in initializer
/tmp/vmware-config2/vmmon-only/linux/driver.c:151: warning: initialization from incompatible pointer type
/tmp/vmware-config2/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config2/vmmon-only/linux/driver.c:1670: error: too many arguments to function ‘smp_call_function’
make[2]: *** [/tmp/vmware-config2/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config2/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config2/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```

---

### Post by Baelus on 2009-05-27
I remember having to use a patch called "vmware-any-any-update". Might help you along.

Here's the page about it:

[http://communities.vmware.com/message/76957]("http://communities.vmware.com/message/76957")

---

### Post by hyperdude111 on 2009-05-27
Try virtualbox it has a .deb and its free.

---

### Post by Baelus on 2009-05-27
> **hyperdude111 said:**
> Try virtualbox it has a .deb and its free.

Agreed. I've found virtualbox to be less of a hassle.

Definitely worth a try:

[http://www.virtualbox.org/]("http://www.virtualbox.org/")

---

