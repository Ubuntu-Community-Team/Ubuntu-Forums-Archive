---
title: "Error while instaling vmware serer 1.0 in Ubuntu 10.04"
date: 2011-04-24
forum: New to Ubuntu
---

### Post by sureshkumarak on 2011-04-24
Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config5/vmmon-only'
make -C /lib/modules/2.6.32-30-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-30-generic'
  CC [M]  /tmp/vmware-config5/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config5/vmmon-only/./include/vmware.h:25,
                 from /tmp/vmware-config5/vmmon-only/linux/driver.c:48:
/tmp/vmware-config5/vmmon-only/./include/vm_basic_types.h:104:7: warning: "__FreeBSD__" is not defined
In file included from /tmp/vmware-config5/vmmon-only/./include/x86.h:20,
                 from /tmp/vmware-config5/vmmon-only/./include/machine.h:24,
                 from /tmp/vmware-config5/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config5/vmmon-only/linux/driver.c:49:
/tmp/vmware-config5/vmmon-only/./include/x86apic.h:79:1: warning: "APIC_BASE_MSR" redefined
In file included from /usr/src/linux-headers-2.6.32-30-generic/arch/x86/include/asm/apic.h:11,
                 from /usr/src/linux-headers-2.6.32-30-generic/arch/x86/include/asm/smp.h:13,
                 from include/linux/smp.h:36,
                 from include/linux/topology.h:33,
                 from include/linux/gfp.h:7,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from /tmp/vmware-config5/vmmon-only/linux/driver.c:12:
/usr/src/linux-headers-2.6.32-30-generic/arch/x86/include/asm/apicdef.h:136:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config5/vmmon-only/./include/x86.h:21,
                 from /tmp/vmware-config5/vmmon-only/./include/machine.h:24,
                 from /tmp/vmware-config5/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config5/vmmon-only/linux/driver.c:49:
/tmp/vmware-config5/vmmon-only/./include/x86desc.h:593:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config5/vmmon-only/./include/machine.h:24,
                 from /tmp/vmware-config5/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config5/vmmon-only/linux/driver.c:49:
/tmp/vmware-config5/vmmon-only/./include/x86.h:830:1: warning: "PTE_PFN_MASK" redefined
In file included from /usr/src/linux-headers-2.6.32-30-generic/arch/x86/include/asm/paravirt.h:7,
                 from /usr/src/linux-headers-2.6.32-30-generic/arch/x86/include/asm/irqflags.h:60,
                 from include/linux/irqflags.h:57,
                 from /usr/src/linux-headers-2.6.32-30-generic/arch/x86/include/asm/system.h:11,
                 from /usr/src/linux-headers-2.6.32-30-generic/arch/x86/include/asm/processor.h:17,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /tmp/vmware-config5/vmmon-only/linux/driver.c:12:
/usr/src/linux-headers-2.6.32-30-generic/arch/x86/include/asm/pgtable_types.h:182:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config5/vmmon-only/./include/vcpuset.h:78,
                 from /tmp/vmware-config5/vmmon-only/./include/modulecall.h:22,
                 from /tmp/vmware-config5/vmmon-only/./common/vmx86.h:18,
                 from /tmp/vmware-config5/vmmon-only/linux/driver.h:16,
                 from /tmp/vmware-config5/vmmon-only/linux/driver.c:49:
/tmp/vmware-config5/vmmon-only/./include/vm_atomic.h:226:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config5/vmmon-only/./include/vm_atomic.h:230:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config5/vmmon-only/./include/vm_atomic.h:298:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config5/vmmon-only/./include/vm_atomic.h:304:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config5/vmmon-only/./include/vm_atomic.h:402:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config5/vmmon-only/./include/vm_atomic.h:489:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config5/vmmon-only/./include/vm_atomic.h:576:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config5/vmmon-only/./include/vm_atomic.h:663:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config5/vmmon-only/./include/vm_atomic.h:665:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config5/vmmon-only/./include/vm_atomic.h:748:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config5/vmmon-only/./include/vm_atomic.h:750:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config5/vmmon-only/./include/vm_atomic.h:831:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config5/vmmon-only/./include/vm_atomic.h:833:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config5/vmmon-only/./include/vm_atomic.h:912:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config5/vmmon-only/./include/vm_atomic.h:914:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config5/vmmon-only/./include/vm_atomic.h:1073:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config5/vmmon-only/./include/vm_atomic.h:1077:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config5/vmmon-only/./include/vm_atomic.h:1329:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config5/vmmon-only/./include/vm_atomic.h:1454:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config5/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config5/vmmon-only/linux/driver.c:49:
/tmp/vmware-config5/vmmon-only/./include/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config5/vmmon-only/./include/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config5/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config5/vmmon-only/linux/driver.c:49:
/tmp/vmware-config5/vmmon-only/./include/compat_wait.h:60: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:70: note: previous declaration of ‘poll_initwait’ was here
In file included from /tmp/vmware-config5/vmmon-only/./include/vm_basic_asm.h:32,
                 from /tmp/vmware-config5/vmmon-only/./include/vm_asm.h:25,
                 from /tmp/vmware-config5/vmmon-only/linux/driver.c:52:
/tmp/vmware-config5/vmmon-only/./include/vm_basic_asm_x86.h:48:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config5/vmmon-only/./include/vm_basic_asm_x86.h:109:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config5/vmmon-only/./include/vm_basic_asm_x86.h:278:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config5/vmmon-only/./include/vm_basic_asm_x86.h:385:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config5/vmmon-only/./include/vm_asm.h:30,
                 from /tmp/vmware-config5/vmmon-only/linux/driver.c:52:
/tmp/vmware-config5/vmmon-only/./include/vm_asm_x86.h:430:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config5/vmmon-only/./include/vm_asm_x86.h:676:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config5/vmmon-only/./include/vm_asm_x86.h:716:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config5/vmmon-only/linux/vmhost.h:13,
                 from /tmp/vmware-config5/vmmon-only/linux/driver.c:71:
/tmp/vmware-config5/vmmon-only/./include/compat_semaphore.h:5:27: error: asm/semaphore.h: No such file or directory
/tmp/vmware-config5/vmmon-only/linux/driver.c:146: error: unknown field ‘nopage’ specified in initializer
/tmp/vmware-config5/vmmon-only/linux/driver.c:147: warning: initialization from incompatible pointer type
/tmp/vmware-config5/vmmon-only/linux/driver.c:150: error: unknown field ‘nopage’ specified in initializer
/tmp/vmware-config5/vmmon-only/linux/driver.c:151: warning: initialization from incompatible pointer type
/tmp/vmware-config5/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config5/vmmon-only/linux/driver.c:1650: error: ‘struct task_struct’ has no member named ‘euid’
/tmp/vmware-config5/vmmon-only/linux/driver.c:1650: error: ‘struct task_struct’ has no member named ‘uid’
/tmp/vmware-config5/vmmon-only/linux/driver.c:1651: error: ‘struct task_struct’ has no member named ‘fsuid’
/tmp/vmware-config5/vmmon-only/linux/driver.c:1651: error: ‘struct task_struct’ has no member named ‘uid’
/tmp/vmware-config5/vmmon-only/linux/driver.c:1652: error: ‘struct task_struct’ has no member named ‘egid’
/tmp/vmware-config5/vmmon-only/linux/driver.c:1652: error: ‘struct task_struct’ has no member named ‘gid’
/tmp/vmware-config5/vmmon-only/linux/driver.c:1653: error: ‘struct task_struct’ has no member named ‘fsgid’
/tmp/vmware-config5/vmmon-only/linux/driver.c:1653: error: ‘struct task_struct’ has no member named ‘gid’
/tmp/vmware-config5/vmmon-only/linux/driver.c:1670: error: too many arguments to function ‘smp_call_function’
make[2]: *** [/tmp/vmware-config5/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config5/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-30-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config5/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted

Please help me

---

### Post by mynameisnotbob on 2011-04-24
*whistle* Not quite an absolute beginner question...

Do you have FreeBSD installed?

---

