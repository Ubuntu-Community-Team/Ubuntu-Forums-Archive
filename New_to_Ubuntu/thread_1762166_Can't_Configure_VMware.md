---
title: "Can't Configure VMware"
date: 2011-05-18
forum: New to Ubuntu
---

### Post by pkjm17 on 2011-05-18
I installed VMware but it says it's not configured correctly. This is the output from my terminal from running /usr/bin/vmware-config.pl

Making sure services for VMware Server are stopped.

Stopping VMware autostart virtual machines:
   Virtual machines                                                   failed
Stopping VMware management services:
   VMware Virtual Infrastructure Web Access
   VMware Server Host Agent                                           failed
Stopping VMware services:
   VMware Authentication Daemon                                        done
   Virtual machine monitor                                             done

None of the pre-built vmmon modules for VMware Server is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes] yes

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.35.8/build/include]

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.35.8/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-source-2.6.35.8'

  WARNING: Symbol version dump /usr/src/linux-source-2.6.35.8/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config0/vmmon-only/linux/driver.c:31:
/tmp/vmware-config0/vmmon-only/./include/compat_wait.h:78: error: conflicting types for 'poll_initwait'
include/linux/poll.h:72: error: previous declaration of 'poll_initwait' was here
In file included from /tmp/vmware-config0/vmmon-only/./common/vmx86.h:32,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.h:29,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:101:
/tmp/vmware-config0/vmmon-only/./include/x86msr.h:164:1: warning: "MSR_THERM2_CTL" redefined
In file included from /usr/src/linux-source-2.6.35.8/arch/x86/include/asm/msr.h:4,
                 from /usr/src/linux-source-2.6.35.8/arch/x86/include/asm/processor.h:21,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /tmp/vmware-config0/vmmon-only/./include/compat_module.h:27,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:26:
/usr/src/linux-source-2.6.35.8/arch/x86/include/asm/msr-index.h:234:1: warning: this is the location of the previous definition
/tmp/vmware-config0/vmmon-only/linux/driver.c: In function 'LinuxDriverSyncCallOnEachCPU':
/tmp/vmware-config0/vmmon-only/linux/driver.c:1423: error: too many arguments to function 'smp_call_function'
/tmp/vmware-config0/vmmon-only/linux/driver.c: In function 'LinuxDriver_Ioctl':
/tmp/vmware-config0/vmmon-only/linux/driver.c:1987: error: 'struct task_struct' has no member named 'euid'
/tmp/vmware-config0/vmmon-only/linux/driver.c:1987: error: 'struct task_struct' has no member named 'uid'
/tmp/vmware-config0/vmmon-only/linux/driver.c:1988: error: 'struct task_struct' has no member named 'fsuid'
/tmp/vmware-config0/vmmon-only/linux/driver.c:1988: error: 'struct task_struct' has no member named 'uid'
/tmp/vmware-config0/vmmon-only/linux/driver.c:1989: error: 'struct task_struct' has no member named 'egid'
/tmp/vmware-config0/vmmon-only/linux/driver.c:1989: error: 'struct task_struct' has no member named 'gid'
/tmp/vmware-config0/vmmon-only/linux/driver.c:1990: error: 'struct task_struct' has no member named 'fsgid'
/tmp/vmware-config0/vmmon-only/linux/driver.c:1990: error: 'struct task_struct' has no member named 'gid'
/tmp/vmware-config0/vmmon-only/linux/driver.c:2007: error: too many arguments to function 'smp_call_function'
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.35.8'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/go/unsup-linux-products" and
"http://www.vmware.com/go/unsup-linux-tools".

Execution aborted.

---

