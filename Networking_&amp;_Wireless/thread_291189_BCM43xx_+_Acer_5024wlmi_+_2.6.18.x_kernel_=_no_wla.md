---
title: "BCM43xx + Acer 5024wlmi + 2.6.18.x kernel = no wlan :("
date: 2006-11-02
forum: Networking &amp; Wireless
---

### Post by Xemanth on 2006-11-02
Hmm  do you guys know how to enable 5024wlmi's broadcom's integrated wlan chip without acer_acpi  because it doesn't compile with kernel 2.6.18?

edit: Without acer_acpi its impossible to enable bcm chip on acer laptop :(

---

### Post by wieman01 on 2006-11-02
Try this ("ndiswrapper"):
[http://www.ubuntuforums.org/showthread.php?t=285809]("http://www.ubuntuforums.org/showthread.php?t=285809")

---

### Post by finite9 on 2006-11-02
What errors do you get when trying to compile acer_acpi?

---

### Post by Xemanth on 2006-11-02
> **finite9 said:**
> What errors do you get when trying to compile acer_acpi?


```

root@5024wlmi:/usr/src/acer_acpi-0.3# make
gcc -I/lib/modules/`uname -r`/build/include -c -Wall -Wstrict-prototypes -Wno-trigraphs -O2 -fomit-frame-pointer -fno-strict-aliasing -fno-common -pipe -DMODVERSIONS -DMODULE -D__KERNEL__ -o acer_acpi.o acer_acpi.c
In file included from /lib/modules/2.6.18.1-ver2-5024wlmi/build/include/asm/thread_info.h:16,
                 from /lib/modules/2.6.18.1-ver2-5024wlmi/build/include/linux/thread_info.h:21,
                 from /lib/modules/2.6.18.1-ver2-5024wlmi/build/include/linux/preempt.h:9,
                 from /lib/modules/2.6.18.1-ver2-5024wlmi/build/include/linux/spinlock.h:49,
                 from /lib/modules/2.6.18.1-ver2-5024wlmi/build/include/linux/capability.h:45,
                 from /lib/modules/2.6.18.1-ver2-5024wlmi/build/include/linux/sched.h:44,
                 from /lib/modules/2.6.18.1-ver2-5024wlmi/build/include/linux/module.h:9,
                 from acer_acpi.c:41:
/lib/modules/2.6.18.1-ver2-5024wlmi/build/include/asm/processor.h:80: error: ‘CONFIG_X86_L1_CACHE_SHIFT’ undeclared here (not in a function)
/lib/modules/2.6.18.1-ver2-5024wlmi/build/include/asm/processor.h:80: error: requested alignment is not a constant
In file included from /lib/modules/2.6.18.1-ver2-5024wlmi/build/include/linux/rwsem.h:24,
                 from /lib/modules/2.6.18.1-ver2-5024wlmi/build/include/asm/semaphore.h:42,
                 from /lib/modules/2.6.18.1-ver2-5024wlmi/build/include/linux/sched.h:57,
                 from /lib/modules/2.6.18.1-ver2-5024wlmi/build/include/linux/module.h:9,
                 from acer_acpi.c:41:
/lib/modules/2.6.18.1-ver2-5024wlmi/build/include/asm/rwsem.h: In function ‘__down_read’:
/lib/modules/2.6.18.1-ver2-5024wlmi/build/include/asm/rwsem.h:104: error: expected ‘:’ or ‘)’ before ‘KBUILD_BASENAME’
/lib/modules/2.6.18.1-ver2-5024wlmi/build/include/asm/rwsem.h: In function ‘__down_write_nested’:
/lib/modules/2.6.18.1-ver2-5024wlmi/build/include/asm/rwsem.h:156: error: expected ‘:’ or ‘)’ before ‘KBUILD_BASENAME’
/lib/modules/2.6.18.1-ver2-5024wlmi/build/include/asm/rwsem.h: In function ‘__up_read’:
/lib/modules/2.6.18.1-ver2-5024wlmi/build/include/asm/rwsem.h:198: error: expected ‘:’ or ‘)’ before ‘KBUILD_BASENAME’
/lib/modules/2.6.18.1-ver2-5024wlmi/build/include/asm/rwsem.h:192: warning: unused variable ‘tmp’
/lib/modules/2.6.18.1-ver2-5024wlmi/build/include/asm/rwsem.h: In function ‘__up_write’:
/lib/modules/2.6.18.1-ver2-5024wlmi/build/include/asm/rwsem.h:224: error: expected ‘:’ or ‘)’ before ‘KBUILD_BASENAME’
/lib/modules/2.6.18.1-ver2-5024wlmi/build/include/asm/rwsem.h: In function ‘__downgrade_write’:
/lib/modules/2.6.18.1-ver2-5024wlmi/build/include/asm/rwsem.h:249: error: expected ‘:’ or ‘)’ before ‘KBUILD_BASENAME’
In file included from /lib/modules/2.6.18.1-ver2-5024wlmi/build/include/linux/sched.h:57,
                 from /lib/modules/2.6.18.1-ver2-5024wlmi/build/include/linux/module.h:9,
                 from acer_acpi.c:41:
/lib/modules/2.6.18.1-ver2-5024wlmi/build/include/asm/semaphore.h: In function ‘down’:
/lib/modules/2.6.18.1-ver2-5024wlmi/build/include/asm/semaphore.h:105: error: expected ‘:’ or ‘)’ before ‘KBUILD_BASENAME’
/lib/modules/2.6.18.1-ver2-5024wlmi/build/include/asm/semaphore.h: In function ‘down_interruptible’:
/lib/modules/2.6.18.1-ver2-5024wlmi/build/include/asm/semaphore.h:130: error: expected ‘:’ or ‘)’ before ‘KBUILD_BASENAME’
/lib/modules/2.6.18.1-ver2-5024wlmi/build/include/asm/semaphore.h: In function ‘down_trylock’:
/lib/modules/2.6.18.1-ver2-5024wlmi/build/include/asm/semaphore.h:155: error: expected ‘:’ or ‘)’ before ‘KBUILD_BASENAME’
/lib/modules/2.6.18.1-ver2-5024wlmi/build/include/asm/semaphore.h: In function ‘up’:
/lib/modules/2.6.18.1-ver2-5024wlmi/build/include/asm/semaphore.h:179: error: expected ‘:’ or ‘)’ before ‘KBUILD_BASENAME’
In file included from /lib/modules/2.6.18.1-ver2-5024wlmi/build/include/linux/module.h:9,
                 from acer_acpi.c:41:
/lib/modules/2.6.18.1-ver2-5024wlmi/build/include/linux/sched.h: In function ‘dequeue_signal_lock’:
/lib/modules/2.6.18.1-ver2-5024wlmi/build/include/linux/sched.h:1209: warning: implicit declaration of function ‘local_irq_save’
/lib/modules/2.6.18.1-ver2-5024wlmi/build/include/linux/sched.h:1211: warning: implicit declaration of function ‘local_irq_restore’
In file included from /lib/modules/2.6.18.1-ver2-5024wlmi/build/include/linux/kernel_stat.h:4,
                 from /lib/modules/2.6.18.1-ver2-5024wlmi/build/include/asm/i387.h:16,
                 from /lib/modules/2.6.18.1-ver2-5024wlmi/build/include/asm/suspend.h:7,
                 from /lib/modules/2.6.18.1-ver2-5024wlmi/build/include/linux/suspend.h:5,
                 from acer_acpi.c:46:
/lib/modules/2.6.18.1-ver2-5024wlmi/build/include/asm/irq.h:15:25: error: irq_vectors.h: No such file or directory
In file included from /lib/modules/2.6.18.1-ver2-5024wlmi/build/include/asm/i387.h:16,
                 from /lib/modules/2.6.18.1-ver2-5024wlmi/build/include/asm/suspend.h:7,
                 from /lib/modules/2.6.18.1-ver2-5024wlmi/build/include/linux/suspend.h:5,
                 from acer_acpi.c:46:
/lib/modules/2.6.18.1-ver2-5024wlmi/build/include/linux/kernel_stat.h: At top level:
/lib/modules/2.6.18.1-ver2-5024wlmi/build/include/linux/kernel_stat.h:30: error: ‘NR_IRQS’ undeclared here (not in a function)
In file included from /lib/modules/2.6.18.1-ver2-5024wlmi/build/include/acpi/platform/acenv.h:140,
                 from /lib/modules/2.6.18.1-ver2-5024wlmi/build/include/acpi/acpi.h:54,
                 from /lib/modules/2.6.18.1-ver2-5024wlmi/build/include/linux/acpi.h:37,
                 from /lib/modules/2.6.18.1-ver2-5024wlmi/build/include/acpi/acpi_drivers.h:29,
                 from acer_acpi.c:49:
/lib/modules/2.6.18.1-ver2-5024wlmi/build/include/acpi/platform/aclinux.h: In function ‘acpi_os_allocate’:
/lib/modules/2.6.18.1-ver2-5024wlmi/build/include/acpi/platform/aclinux.h:116: warning: implicit declaration of function ‘irqs_disabled’
make: *** [acer_acpi.o] Error 1
root@5024wlmi:/usr/src/acer_acpi-0.3#

```

---

### Post by Xemanth on 2006-11-02
> **wieman01 said:**
> Try this ("ndiswrapper"):
[http://www.ubuntuforums.org/showthread.php?t=285809]("http://www.ubuntuforums.org/showthread.php?t=285809")

You didn't understand the issue.
Without acer_acpi its impossible to enable bcm chip.
I have used ndiswrapper but it doesn't work either in this case... and I like to keep my stuff open source.

---

### Post by wieman01 on 2006-11-02
> **Xemanth said:**
> You didn't understand the issue.
Without acer_acpi its impossible to enable bcm chip.
I have used ndiswrapper but it doesn't work either in this case... and I like to keep my stuff open source.
Perhaps you have not been explicit enough... Good luck.

---

### Post by finite9 on 2006-11-02
Have you been able to compile acer_acpi before on Dapper?  Have you upgraded to Edgy, or have you installed a custom kernel?  If you have upgraded, done a new install or installed a custom kernel, then you'll need updated kernel headers--maybe you haven't installed them?  Try this and then do make again and see if it helps:

```
sudo apt-get install build-essential linux-kernel-headers linux-headers-`uname -r`
```

P.S.  Make sure you remove any previous make attempts with 'make clean' or by removing the directory and unzipping acer_acpi from the zip file again.

---

### Post by Xemanth on 2006-11-03
> **finite9 said:**
> Have you been able to compile acer_acpi before on Dapper?  Have you upgraded to Edgy, or have you installed a custom kernel?  If you have upgraded, done a new install or installed a custom kernel, then you'll need updated kernel headers--maybe you haven't installed them?  Try this and then do make again and see if it helps:

```
sudo apt-get install build-essential linux-kernel-headers linux-headers-`uname -r`
```

P.S.  Make sure you remove any previous make attempts with 'make clean' or by removing the directory and unzipping acer_acpi from the zip file again.

That 2.6.18.1 is my self compiled kernel. Kernel source downloaded from kernel.org.

With 2.6.17 I can compile acer_acpi but suspend doesn't work properly with 2.6.18 it works much better.
Yeah I have tried to remove acer_acpi folder and unzip fresh source v0.3 but still no go. Same errors come.

This is a very bad problem because if I want to use 2.6.18 or newer kernel I can't use acer_acpi -> WLAN is crippled completely.

Somebody should integrate acer_acpi to official kernel tree
[http://www.archernar.co.uk/acer_acpi/acer_acpi_main.html](http://www.archernar.co.uk/acer_acpi/acer_acpi_main.html)

---

### Post by Xemanth on 2006-11-03
Woohoo acer_acpi works again!
[img]http://www.thescuderia.net/forums/images/smilies/nana2.gif[/img]

I just followed this:
[http://lists.debian.org/debian-amd64/2006/10/msg00022.html](http://lists.debian.org/debian-amd64/2006/10/msg00022.html)

"do compile acer_acpi not only with "make" but with "make acer_acpi.ko", 
as make does not recognize the kernel correctly. After this copy the *.ko 
to /lib/modules/<kernelversion>/kernel/driver/char/ and make a depmod -a."

And then just hit modprobe acer_acpi and kazaboom it works woohoo I'm so happy :lol:

Working combo is ndiswrapper-1.8 + ndiswrapper + kernel 2.6.18.1 + acer_acpi

---

### Post by finite9 on 2006-11-06
I think there is a note about this in the acer_acpi INSTALL file.

---

