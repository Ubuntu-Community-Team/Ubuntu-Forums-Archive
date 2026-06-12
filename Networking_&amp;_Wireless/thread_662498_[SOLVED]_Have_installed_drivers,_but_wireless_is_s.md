---
title: "[SOLVED] Have installed drivers, but wireless is still not working"
date: 2008-01-09
forum: Networking &amp; Wireless
---

### Post by mahasmb on 2008-01-09
I managed to install my wireless drivers after a lot of work, but I still can't get the internet to work.

```
$ sudo ndiswrapper -l
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_CA:en",
        LC_ALL = (unset),
        LANG = "en_CA.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
sis163u : driver installed
        device (0457:0163) present

```

I'm using a TEW-424UB (trendnet usb wireless adapter) on a desktop. It's connected to the computer but I get the following with a "iwlist scanning"

```

$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

```

I'm using WICD, and it can only connect to my wired network.

If you could just give me a push in the right way, I'd really appreciate it.

Edit: I am on Dapper Drake 6.06

---

### Post by amingv on 2008-01-09
Hi,
did you remember to reload the ndiswrapper module? Try this:

```
sudo modprobe ndiswrapper
```

Assuming the install was correct, that should do the rest.

---

### Post by mahasmb on 2008-01-09
I get the following

```
$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-29-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

```

---

### Post by amingv on 2008-01-09
What ndiswrapper version are you running? Maybe try downloading the [last stable version]("http://sourceforge.net/project/showfiles.php?group_id=93482") and compile it (first uninstall your old version). I find the one in the repos a little cheesy...

Before processing the ini file unload ndiswrapper (in case it's loaded):

```
sudo modprobe -r ndiswrapper
```

Work on the ini as normal and load it back again.

---

### Post by mahasmb on 2008-01-09
*sighs* I get the following...

```
1# make install
make -C driver install
make[1]: Entering directory `/home/maha/Desktop/ndiswrapper-1.51/driver'
Makefile:35: *** Cannot find kernel version in /lib/modules/2.6.15-29-386/build, is it configured?.  Stop.
make[1]: Leaving directory `/home/maha/Desktop/ndiswrapper-1.51/driver'
make: *** [install] Error 2
```

---

### Post by amingv on 2008-01-09
make sure you have 'build-essential' installed:

```
sudo apt-get install build-essential
```

---

### Post by mahasmb on 2008-01-09
This is super weird...

```

# sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: gcc (>= 4:4.1.1) but 4:4.0.3-1 is to be installed
                   Depends: g++ (>= 4:4.1.1) but it is not going to be installed
                   Depends: dpkg-dev (>= 1.13.5) but it is not going to be installed
E: Broken packages


```

---

### Post by amingv on 2008-01-09
Is this a new installation?
OK... my fault then, run:

```
sudo apt-get update
```
and then
```
sudo apt-get install build-essential
```

---

### Post by mahasmb on 2008-01-09
Yes, this is a brand new Dapper Drake installation and I'm still getting the following

```

1# sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: gcc (>= 4:4.1.1) but 4:4.0.3-1 is to be installed
                   Depends: g++ (>= 4:4.1.1) but it is not going to be installed
                   Depends: dpkg-dev (>= 1.13.5) but it is not going to be installed
E: Broken packages



```

---

### Post by mahasmb on 2008-01-09
I've tried the instructions at this site to no avail

[http://hansengel.wordpress.com/2007/07/24/ubuntu-710-wireless-adapter-problems/](http://hansengel.wordpress.com/2007/07/24/ubuntu-710-wireless-adapter-problems/)

---

### Post by mahasmb on 2008-01-10
This is very frustrating...

I've noticed ndisgtk always crashes when I try to use it. And I see the same "locale" errors that I had in my first post. What in the world are these locale errors and how do I fix them? I've tried googling and searching this forum but nothing works! This shouldn't be this hard

```

$ ndisgtk

(ndisgtk:10387): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
Traceback (most recent call last):
  File "/usr/bin/ndisgtk", line 44, in ?
    locale.setlocale(locale.LC_ALL, "")
  File "/usr/lib/python2.4/locale.py", line 381, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting


```

```
$ sudo ndiswrapper -l
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_CA:en",
        LC_ALL = (unset),
        LANG = "en_CA.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
```

I'm on my hands and knees begging for help from anyone.

Edit: The following thread seems to have fixed my "locale" problems, but ndiswrapper is still giving me problems.

---

### Post by mahasmb on 2008-01-10
So...

For the dozenth time I've completely uninstalled ndswrapper again and tried to install it from source (version 1.51)

This is what I get 

```

$ sudo make
make -C driver
make[1]: Entering directory `/home/maha/Desktop/ndiswrapper-1.51/driver'
make -C /usr/src/linux-headers-2.6.15-29-386 SUBDIRS=/home/maha/Desktop/ndiswrapper-1.51/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.15-29-386'
  CC [M]  /home/maha/Desktop/ndiswrapper-1.51/driver/crt.o
In file included from /home/maha/Desktop/ndiswrapper-1.51/driver/crt.c:16:
/home/maha/Desktop/ndiswrapper-1.51/driver/ntoskernel.h:718: [COLOR="#ff0000"]error[/COLOR]: field 'lock' has incomplete type
/home/maha/Desktop/ndiswrapper-1.51/driver/ntoskernel.h: In function 'raise_irql':
/home/maha/Desktop/ndiswrapper-1.51/driver/ntoskernel.h:755: [COLOR="#ff0000"]warning[/COLOR]: implicit declaration of function 'mutex_lock'
/home/maha/Desktop/ndiswrapper-1.51/driver/ntoskernel.h: In function 'lower_irql':
/home/maha/Desktop/ndiswrapper-1.51/driver/ntoskernel.h:777: [COLOR="#ff0000"]warning[/COLOR]: implicit declaration of function 'mutex_unlock'
make[3]: *** [/home/maha/Desktop/ndiswrapper-1.51/driver/crt.o] Error 1
make[2]: *** [_module_/home/maha/Desktop/ndiswrapper-1.51/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.15-29-386'
make[1]: *** [default] [COLOR="Red"]Error 2[/COLOR]
make[1]: Leaving directory `/home/maha/Desktop/ndiswrapper-1.51/driver'
make: *** [all] [COLOR="#ff0000"]Error 2[/COLOR]


```

I get a bunch of errors and warnings which I've written out in red.

Maybe if someone could help me from here?

---

### Post by xeth_delta on 2008-01-10
> **mahasmb said:**
> So...

For the dozenth time I've completely uninstalled ndswrapper again and tried to install it from source (version 1.51)

This is what I get 

```

$ sudo make
make -C driver
make[1]: Entering directory `/home/maha/Desktop/ndiswrapper-1.51/driver'
make -C /usr/src/linux-headers-2.6.15-29-386 SUBDIRS=/home/maha/Desktop/ndiswrapper-1.51/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.15-29-386'
  CC [M]  /home/maha/Desktop/ndiswrapper-1.51/driver/crt.o
In file included from /home/maha/Desktop/ndiswrapper-1.51/driver/crt.c:16:
/home/maha/Desktop/ndiswrapper-1.51/driver/ntoskernel.h:718: [COLOR="#ff0000"]error[/COLOR]: field 'lock' has incomplete type
/home/maha/Desktop/ndiswrapper-1.51/driver/ntoskernel.h: In function 'raise_irql':
/home/maha/Desktop/ndiswrapper-1.51/driver/ntoskernel.h:755: [COLOR="#ff0000"]warning[/COLOR]: implicit declaration of function 'mutex_lock'
/home/maha/Desktop/ndiswrapper-1.51/driver/ntoskernel.h: In function 'lower_irql':
/home/maha/Desktop/ndiswrapper-1.51/driver/ntoskernel.h:777: [COLOR="#ff0000"]warning[/COLOR]: implicit declaration of function 'mutex_unlock'
make[3]: *** [/home/maha/Desktop/ndiswrapper-1.51/driver/crt.o] Error 1
make[2]: *** [_module_/home/maha/Desktop/ndiswrapper-1.51/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.15-29-386'
make[1]: *** [default] [COLOR="Red"]Error 2[/COLOR]
make[1]: Leaving directory `/home/maha/Desktop/ndiswrapper-1.51/driver'
make: *** [all] [COLOR="#ff0000"]Error 2[/COLOR]


```

I get a bunch of errors and warnings which I've written out in red.

Maybe if someone could help me from here?

In the output you've posted the actual error is:
```
/home/maha/Desktop/ndiswrapper-1.51/driver/ntoskernel.h:718: [COLOR="#ff0000"]error[/COLOR]: field 'lock' has incomplete type
```
Warnings would not stop compilation. Can you please post the line 718 of /home/maha/Desktop/ndiswrapper-1.51/driver/ntoskernel.h? Or better, give us a link to the source code.

Xeth

---

### Post by mahasmb on 2008-01-10
I hope copying and pasting it is fine. 

```

/*
 *  Copyright (C) 2003-2005 Pontus Fuchs, Giridhar Pemmasani
 *
 *  This program is free software; you can redistribute it and/or modify
 *  it under the terms of the GNU General Public License as published by
 *  the Free Software Foundation; either version 2 of the License, or
 *  (at your option) any later version.
 *
 *  This program is distributed in the hope that it will be useful,
 *  but WITHOUT ANY WARRANTY; without even the implied warranty of
 *  MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
 *  GNU General Public License for more details.
 *
 */

#ifndef _NTOSKERNEL_H_
#define _NTOSKERNEL_H_

#include <linux/types.h>
#include <linux/timer.h>
#include <linux/time.h>
#include <linux/module.h>
#include <linux/kmod.h>

#include <linux/netdevice.h>
#include <linux/wireless.h>
#include <linux/pci.h>
#include <linux/wait.h>
#include <linux/pm.h>
#include <linux/delay.h>
#include <linux/mm.h>
#include <linux/random.h>
#include <linux/ctype.h>
#include <linux/list.h>
#include <linux/sched.h>
#include <linux/usb.h>
#include <linux/spinlock.h>
#include <asm/mman.h>
#include <linux/version.h>
#include <linux/etherdevice.h>
#include <net/iw_handler.h>
#include <linux/netdevice.h>
#include <linux/ethtool.h>
#include <linux/if_arp.h>
#include <linux/rtnetlink.h>
#include <linux/highmem.h>

#if !defined(CONFIG_X86) && !defined(CONFIG_X86_64)
#error "this module is for x86 or x86_64 architectures only"
#endif

#if LINUX_VERSION_CODE >= KERNEL_VERSION(2,6,7)
#include <linux/kthread.h>
#else
#include <linux/config.h>
#endif
/* Interrupt backwards compatibility stuff */
#include <linux/interrupt.h>
#ifndef IRQ_HANDLED
#define IRQ_HANDLED
#define IRQ_NONE
#define irqreturn_t void
#endif

/* Workqueue / task queue backwards compatibility stuff */
#if LINUX_VERSION_CODE > KERNEL_VERSION(2,5,41)
#include <linux/workqueue.h>
/* pci functions in 2.6 kernels have problems allocating dma buffers,
 * but seem to work fine with dma functions
 */
#include <asm/dma-mapping.h>

#define PCI_DMA_ALLOC_COHERENT(pci_dev,size,dma_handle)			\
	dma_alloc_coherent(&pci_dev->dev,size,dma_handle,		\
			   GFP_KERNEL | __GFP_REPEAT)
#define PCI_DMA_FREE_COHERENT(pci_dev,size,cpu_addr,dma_handle)		\
	dma_free_coherent(&pci_dev->dev,size,cpu_addr,dma_handle)
#define PCI_DMA_MAP_SINGLE(pci_dev,addr,size,direction)		\
	dma_map_single(&pci_dev->dev,addr,size,direction)
#define PCI_DMA_UNMAP_SINGLE(pci_dev,dma_handle,size,direction)		\
	dma_unmap_single(&pci_dev->dev,dma_handle,size,direction)
#define MAP_SG(pci_dev, sglist, nents, direction)		\
	dma_map_sg(&pci_dev->dev, sglist, nents, direction)
#define UNMAP_SG(pci_dev, sglist, nents, direction)		\
	dma_unmap_sg(&pci_dev->dev, sglist, nents, direction)
#define PCI_DMA_MAP_ERROR(dma_addr) dma_mapping_error(dma_addr)

#else // linux version <= 2.5.41

#define PCI_DMA_ALLOC_COHERENT(dev,size,dma_handle)	\
	pci_alloc_consistent(dev,size,dma_handle)
#define PCI_DMA_FREE_COHERENT(dev,size,cpu_addr,dma_handle)	\
	pci_free_consistent(dev,size,cpu_addr,dma_handle)
#define PCI_DMA_MAP_SINGLE(dev,addr,size,direction)	\
	pci_map_single(dev,addr,size,direction)
#define PCI_DMA_UNMAP_SINGLE(dev,dma_handle,size,direction)	\
	pci_unmap_single(dev,dma_handle,size,direction)
#define MAP_SG(dev, sglist, nents, direction)		\
	pci_map_sg(dev, sglist, nents, direction)
#define UNMAP_SG(dev, sglist, nents, direction)		\
	pci_unmap_sg(dev, sglist, nents, direction)
#define PCI_DMA_MAP_ERROR(dma_addr) pci_dma_mapping_error(dma_addr)

#include <linux/smp_lock.h>

/* RedHat kernels define irqs_disabled this way */
#ifndef irqs_disabled
#define irqs_disabled()                \
({                                     \
	unsigned long flags;	       \
       __save_flags(flags);            \
       !(flags & (1<<9));              \
})
#endif

#endif // LINUX_VERSION_CODE

#if defined(CONFIG_NET_RADIO) && !defined(CONFIG_WIRELESS_EXT)
#define CONFIG_WIRELESS_EXT
#endif

#ifndef CONFIG_WIRELESS_EXT
#warning "wirelss devices are not supported by this kernel"
#endif

#define prepare_wait_condition(task, var, value)	\
do {							\
	var = value;					\
	task = current;					\
	barrier();					\
} while (0)

/* Wait in wait_state (e.g., TASK_INTERRUPTIBLE) for condition to
 * become true; timeout is either jiffies (> 0) to wait or 0 to wait
 * forever.
 * When timeout == 0, return value is
 *    > 0 if condition becomes true, or
 *    < 0 if signal is pending on the thread.
 * When timeout > 0, return value is
 *    > 0 if condition becomes true before timeout,
 *    < 0 if signal is pending on the thread before timeout, or
 *    0 if timedout (condition may have become true at the same time)
 */

#define wait_condition(condition, timeout, wait_state)		\
({								\
	long ret = timeout ? timeout : 1;			\
	while (1) {						\
		if (signal_pending(current)) {			\
			ret = -ERESTARTSYS;			\
			break;					\
		}						\
		set_current_state(wait_state);			\
		if (condition) {				\
			__set_current_state(TASK_RUNNING);	\
			break;					\
		}						\
		if (timeout) {					\
			ret = schedule_timeout(ret);		\
			if (!ret)				\
				break;				\
		} else						\
			schedule();				\
	}							\
	ret;							\
})

#ifdef WRAP_WQ

struct workqueue_struct;

struct workqueue_thread {
	spinlock_t lock;
	struct task_struct *task;
	struct completion *completion;
	char name[16];
	int pid;
	/* whether any work_structs pending? <0 implies quit */
	s8 pending;
	/* list of work_structs pending */
	struct list_head work_list;
};

typedef struct workqueue_struct {
	u8 singlethread;
	u8 qon;
	int num_cpus;
	struct workqueue_thread threads[0];
} workqueue_struct_t;

typedef struct {
	struct list_head list;
	void (*func)(void *data);
	void *data;
	/* whether/on which thread scheduled */
	struct workqueue_thread *thread;
} work_struct_t;

#define initialize_work(work, pfunc, pdata)			\
	do {							\
		(work)->func = (pfunc);				\
		(work)->data = (pdata);				\
		(work)->thread = NULL;				\
	} while (0)

#undef create_singlethread_workqueue
#define create_singlethread_workqueue(name) wrap_create_wq(name, 1, 0)
#undef create_workqueue
#if LINUX_VERSION_CODE > KERNEL_VERSION(2,6,0)
#define create_workqueue(name) wrap_create_wq(name, 0, 0)
#else
#define create_workqueue(name) wrap_create_wq(name, 1, 0)
#define for_each_online_cpu(cpu) while ((cpu = 0) || 1)
#define kthread_bind(thread, cpu) do { } while (0)
#endif
#undef destroy_workqueue
#define destroy_workqueue wrap_destroy_wq
#undef queue_work
#define queue_work wrap_queue_work
#undef flush_workqueue
#define flush_workqueue wrap_flush_wq

workqueue_struct_t *wrap_create_wq(const char *name, u8 singlethread, u8 freeze);
void wrap_destroy_wq_on(workqueue_struct_t *workq, int cpu);
void wrap_destroy_wq(workqueue_struct_t *workq);
int wrap_queue_work_on(workqueue_struct_t *workq, work_struct_t *work,
		       int cpu) wfastcall;
int wrap_queue_work(workqueue_struct_t *workq, work_struct_t *work) wfastcall;
void wrap_cancel_work(work_struct_t *work);
void wrap_flush_wq_on(workqueue_struct_t *workq, int cpu);
void wrap_flush_wq(workqueue_struct_t *workq);
typedef void *worker_param_t;
#define worker_param_data(param, type, member) param

#else // WRAP_WQ

typedef struct workqueue_struct workqueue_struct_t;
typedef struct work_struct work_struct_t;

#if defined(INIT_WORK_NAR) || defined(INIT_DELAYED_WORK_DEFERRABLE)
#define initialize_work(work, func, data) INIT_WORK(work, func)
typedef struct work_struct *worker_param_t;
#define worker_param_data(param, type, member)	\
	container_of(param, type, member)
#else
#define initialize_work(work, func, data) INIT_WORK(work, func, data)
typedef void *worker_param_t;
#define worker_param_data(param, type, member) param
#endif // INIT_WORK_NAR

#endif // WRAP_WQ

struct nt_thread *wrap_worker_init(workqueue_struct_t *wq);

#ifdef module_param
#define WRAP_MODULE_PARM_INT(name, perm) module_param(name, int, perm)
#define WRAP_MODULE_PARM_STRING(name, perm) module_param(name, charp, perm)
#else
#define WRAP_MODULE_PARM_INT(name, perm) MODULE_PARM(name, "i")
#define WRAP_MODULE_PARM_STRING(name, perm) MODULE_PARM(name, "s")
#endif

#ifndef LOCK_PREFIX
#ifdef LOCK
#define LOCK_PREFIX LOCK
#else
#ifdef CONFIG_SMP
#define LOCK_PREFIX "lock ; "
#else
#define LOCK_PREFIX ""
#endif
#endif
#endif

#ifndef NETDEV_TX_OK
#define NETDEV_TX_OK 0
#endif

#ifndef NETDEV_TX_BUSY
#define NETDEV_TX_BUSY 1
#endif

#ifndef CHECKSUM_HW
#define CHECKSUM_HW CHECKSUM_PARTIAL
#endif

#if LINUX_VERSION_CODE < KERNEL_VERSION(2,6,0)

#ifndef container_of
#define container_of(ptr, type, member)					\
({									\
	const typeof( ((type *)0)->member ) *__mptr = (ptr);		\
	(type *)( (char *)__mptr - offsetof(type,member) );		\
})
#endif

#ifndef virt_addr_valid
#define virt_addr_valid(addr) VALID_PAGE(virt_to_page(addr))
#endif

#ifndef SET_NETDEV_DEV
#define SET_NETDEV_DEV(net,pdev) do { } while (0)
#endif

#define usb_set_intfdata(intf, data) do { } while (0)

#endif // LINUX_VERSION_CODE < KERNEL_VERSION(2,6,0)

#ifndef offset_in_page
#define offset_in_page(p) ((unsigned long)(p) & ~PAGE_MASK)
#endif

#if LINUX_VERSION_CODE >= KERNEL_VERSION(2,4,23)
#define HAVE_ETHTOOL 1
#endif

#ifndef PMSG_SUSPEND
#ifdef PM_SUSPEND
/* this is not correct - the value of PM_SUSPEND is different from
 * PMSG_SUSPEND, but ndiswrapper doesn't care about the value when
 * suspending */
#define PMSG_SUSPEND PM_SUSPEND
#define PSMG_ON PM_ON
#else
typedef u32 pm_message_t;
#define PMSG_SUSPEND 2
#define PMSG_ON 0
#endif
#endif

#ifndef PCI_D0
#define PCI_D0 0
#endif

#ifndef PCI_D3hot
#define PCI_D3hot 3
#endif

#ifndef PCI_D3cold
#define PCI_D3cold 3
#endif

#ifndef PM_EVENT_SUSPEND
#define PM_EVENT_SUSPEND 2
#endif

#if LINUX_VERSION_CODE < KERNEL_VERSION(2,6,9)
#define pci_choose_state(dev, state) (state)
#endif

#if !defined(HAVE_NETDEV_PRIV)
#define netdev_priv(dev)  ((dev)->priv)
#endif

#if LINUX_VERSION_CODE > KERNEL_VERSION(2,6,18)
#define ISR_PT_REGS_PARAM_DECL
#define ISR_PT_REGS_ARG
#else
#define ISR_PT_REGS_PARAM_DECL , struct pt_regs *regs
#define ISR_PT_REGS_ARG , NULL
#endif

#ifndef flush_icache_range
#define flush_icache_range(start, end) do { } while (0)
#endif

#ifndef CHECKSUM_PARTIAL
#define CHECKSUM_PARTIAL CHECKSUM_HW
#endif

#ifndef IRQF_SHARED
#define IRQF_SHARED SA_SHIRQ
#endif

#define memcpy_skb(skb, from, length)			\
	memcpy(skb_put(skb, length), from, length)

#if LINUX_VERSION_CODE < KERNEL_VERSION(2,6,9)
#define thread_priority(thread) (thread)->nice
#define set_thread_priority(thread, prio) (thread)->nice = (prio)
#else
#define thread_priority(thread) task_nice(thread)
#define set_thread_priority(thread, prio) set_user_nice(thread, prio)
#endif

#ifndef DMA_24BIT_MASK
#define DMA_24BIT_MASK 0x0000000000ffffffULL
#endif

#ifndef DMA_30BIT_MASK
#define DMA_30BIT_MASK 0x000000003fffffffULL
#endif

#ifndef DMA_31BIT_MASK
#define DMA_31BIT_MASK 0x000000007fffffffULL
#endif

#ifndef DMA_32BIT_MASK
#define DMA_32BIT_MASK 0x00000000ffffffffULL
#endif

#ifndef __GFP_DMA32
#define __GFP_DMA32 GFP_DMA
#endif

#if LINUX_VERSION_CODE <= KERNEL_VERSION(2,6,22)
#define wrap_kmem_cache_create(name, size, align, flags)	\
	kmem_cache_create(name, size, align, flags, NULL, NULL)
#else
#define wrap_kmem_cache_create(name, size, align, flags)	\
	kmem_cache_create(name, size, align, flags, NULL)
#endif

#include "winnt_types.h"
#include "ndiswrapper.h"
#include "pe_linker.h"
#include "wrapmem.h"
#include "lin2win.h"
#include "loader.h"

#include "compat.h"

#if !defined(CONFIG_USB) && defined(CONFIG_USB_MODULE)
#define CONFIG_USB 1
#endif

#if defined(DISABLE_USB)
#undef CONFIG_USB
#undef CONFIG_USB_MODULE
#endif

/* TICK is 100ns */
#define TICKSPERSEC		10000000
#define TICKSPERMSEC		10000
#define SECSPERDAY		86400
#define TICKSPERJIFFY		((TICKSPERSEC + HZ - 1) / HZ)

#define int_div_round(x, y) (((x) + (y - 1)) / (y))

/* 1601 to 1970 is 369 years plus 89 leap days */
#define SECS_1601_TO_1970	((369 * 365 + 89) * (u64)SECSPERDAY)
#define TICKS_1601_TO_1970	(SECS_1601_TO_1970 * TICKSPERSEC)

/* 100ns units to HZ; if sys_time is negative, relative to current
 * clock, otherwise from year 1601 */
#define SYSTEM_TIME_TO_HZ(sys_time)					\
	(((sys_time) <= 0) ? \
	 int_div_round(((u64)HZ * (-(sys_time))), TICKSPERSEC) :	\
	 int_div_round(((s64)HZ * ((sys_time) - ticks_1601())), TICKSPERSEC))

#define MSEC_TO_HZ(ms) int_div_round((ms * HZ), 1000)
#define USEC_TO_HZ(us) int_div_round((us * HZ), 1000000)

extern u64 wrap_ticks_to_boot;

static inline u64 ticks_1601(void)
{
	return wrap_ticks_to_boot + (u64)jiffies * TICKSPERJIFFY;
}

typedef void (*generic_func)(void);

struct wrap_export {
	const char *name;
	generic_func func;
};

#ifdef CONFIG_X86_64

#define WIN_SYMBOL(name, argc)					\
	{#name, (generic_func) win2lin_ ## name ## _ ## argc}
#define WIN_WIN_SYMBOL(name, argc)					\
	{#name, (generic_func) win2lin__win_ ## name ## _ ## argc}
#define WIN_FUNC_DECL(name, argc)			\
	typeof(name) win2lin_ ## name ## _ ## argc;
#define WIN_FUNC_PTR(name, argc) win2lin_ ## name ## _ ## argc

#else

#define WIN_SYMBOL(name, argc) {#name, (generic_func)name}
#define WIN_WIN_SYMBOL(name, argc) {#name, (generic_func)_win_ ## name}
#define WIN_FUNC_DECL(name, argc)
#define WIN_FUNC_PTR(name, argc) name

#endif

#define WIN_FUNC(name, argc) name
/* map name s to f - if f is different from s */
#define WIN_SYMBOL_MAP(s, f)

#define POOL_TAG(A, B, C, D)					\
	((ULONG)((A) + ((B) << 8) + ((C) << 16) + ((D) << 24)))

struct pe_image {
	char name[MAX_DRIVER_NAME_LEN];
	UINT (*entry)(struct driver_object *, struct unicode_string *) wstdcall;
	void *image;
	int size;
	int type;

	IMAGE_NT_HEADERS *nt_hdr;
	IMAGE_OPTIONAL_HEADER *opt_hdr;
};

struct ndis_mp_block;

struct wrap_timer {
	struct nt_slist slist;
	struct timer_list timer;
	struct nt_timer *nt_timer;
	long repeat;
#ifdef TIMER_DEBUG
	unsigned long wrap_timer_magic;
#endif
};

struct ntos_work_item {
	struct nt_list list;
	void *arg1;
	void *arg2;
	NTOS_WORK_FUNC func;
};

struct wrap_device_setting {
	struct nt_list list;
	char name[MAX_SETTING_NAME_LEN];
	char value[MAX_SETTING_VALUE_LEN];
	void *encoded;
};

struct wrap_bin_file {
	char name[MAX_DRIVER_NAME_LEN];
	size_t size;
	void *data;
};

#define WRAP_DRIVER_CLIENT_ID 1

struct wrap_driver {
	struct nt_list list;
	struct driver_object *drv_obj;
	char name[MAX_DRIVER_NAME_LEN];
	char version[MAX_SETTING_VALUE_LEN];
	unsigned short num_pe_images;
	struct pe_image pe_images[MAX_DRIVER_PE_IMAGES];
	unsigned short num_bin_files;
	struct wrap_bin_file *bin_files;
	struct nt_list wrap_devices;
	struct nt_list settings;
	int dev_type;
	struct wrap_ndis_driver *ndis_driver;
};

enum hw_status {
	HW_INITIALIZED = 1, HW_SUSPENDED, HW_HALTED, HW_PRESENT,
};

struct wrap_device {
	/* first part is (de)initialized once by loader */
	struct nt_list list;
	int dev_bus;
	int vendor;
	int device;
	int subvendor;
	int subdevice;
	char conf_file_name[MAX_DRIVER_NAME_LEN];
	char driver_name[MAX_DRIVER_NAME_LEN];
	struct wrap_driver *driver;
	struct nt_list settings;

	/* rest should be (de)initialized when a device is
	 * (un)plugged */
	struct cm_resource_list *resource_list;
	unsigned long hw_status;
	struct device_object *pdo;
	union {
		struct {
			struct pci_dev *pdev;
			enum device_power_state wake_state;
#if LINUX_VERSION_CODE <= KERNEL_VERSION(2,6,9)
			u32 pci_state[16];
#endif
		} pci;
		struct {
			struct usb_device *udev;
			struct usb_interface *intf;
			int num_alloc_urbs;
			struct nt_list wrap_urb_list;
		} usb;
	};
	union {
		struct wrap_ndis_device *wnd;
	};
};

#define wrap_is_pci_bus(dev_bus)			\
	(WRAP_BUS(dev_bus) == WRAP_PCI_BUS ||		\
	 WRAP_BUS(dev_bus) == WRAP_PCMCIA_BUS)
#ifdef CONFIG_USB
/* earlier versions of ndiswrapper used 0 as USB_BUS */
#define wrap_is_usb_bus(dev_bus)			\
	(WRAP_BUS(dev_bus) == WRAP_USB_BUS ||		\
	 WRAP_BUS(dev_bus) == WRAP_INTERNAL_BUS)
#else
#define wrap_is_usb_bus(dev_bus) 0
#endif
#define wrap_is_bluetooth_device(dev_bus)			\
	(WRAP_DEVICE(dev_bus) == WRAP_BLUETOOTH_DEVICE1 ||	\
	 WRAP_DEVICE(dev_bus) == WRAP_BLUETOOTH_DEVICE2)

#ifdef WRAP_WQ
#define NTOS_WQ 1
#endif

#ifndef NTOS_WQ
#define NTOS_WQ 1
#endif

#ifdef NTOS_WQ
extern workqueue_struct_t *ntos_wq;
#define schedule_ntos_work(work_struct) queue_work(ntos_wq, work_struct)
#define schedule_work(work_struct) queue_work(ntos_wq, work_struct)
#else
#define schedule_ntos_work(work_struct) schedule_work(work_struct)
#endif

extern workqueue_struct_t *ndis_wq;
#define schedule_ndis_work(work_struct) queue_work(ndis_wq, work_struct)

extern workqueue_struct_t *wrapndis_wq;
#define schedule_wrapndis_work(work_struct) queue_work(wrapndis_wq, work_struct)

#define atomic_unary_op(var, size, oper)				\
do {									\
	if (size == 1)							\
		__asm__ __volatile__(					\
			LOCK_PREFIX oper "b %b0\n\t" : "+m" (var));	\
	else if (size == 2)						\
		__asm__ __volatile__(					\
			LOCK_PREFIX oper "w %w0\n\t" : "+m" (var));	\
	else if (size == 4)						\
		__asm__ __volatile__(					\
			LOCK_PREFIX oper "l %0\n\t" : "+m" (var));	\
	else if (size == 8)						\
		__asm__ __volatile__(					\
			LOCK_PREFIX oper "q %q0\n\t" : "+m" (var));	\
	else {								\
		extern void _invalid_op_size_(void);			\
		_invalid_op_size_();					\
	}								\
} while (0)

#define atomic_inc_var_size(var, size) atomic_unary_op(var, size, "inc")

#define atomic_inc_var(var) atomic_inc_var_size(var, sizeof(var))

#define atomic_dec_var_size(var, size) atomic_unary_op(var, size, "dec")

#define atomic_dec_var(var) atomic_dec_var_size(var, sizeof(var))

#define pre_atomic_add(var, i)					\
({								\
	typeof(var) pre;					\
	__asm__ __volatile__(					\
		LOCK_PREFIX "xadd %0, %1\n\t"			\
		: "=r"(pre), "+m"(var)				\
		: "0"(i));					\
	pre;							\
})

#define post_atomic_add(var, i) (pre_atomic_add(var, i) + i)

#ifndef in_atomic
#define in_atomic() in_interrupt()
#endif

#ifndef preempt_enable_no_resched
#define preempt_enable_no_resched() preempt_enable()
#endif

//#define DEBUG_IRQL 1

#ifdef DEBUG_IRQL
#define assert_irql(cond)						\
do {									\
	KIRQL _irql_ = current_irql();					\
	if (!(cond)) {							\
		WARNING("assertion '%s' failed: %d", #cond, _irql_);	\
		DBG_BLOCK(4) {						\
			dump_stack();					\
		}							\
	}								\
} while (0)
#else
#define assert_irql(cond) do { } while (0)
#endif

/* When preempt is enabled, we should preempt_disable to raise IRQL to
 * DISPATCH_LEVEL, to be consistent with the semantics. However, using
 * a mutex instead, so that only ndiswrapper threads run one at a time
 * on a processor when at DISPATCH_LEVEL seems to be enough. So that
 * is what we will use until we learn otherwise. If
 * preempt_(en|dis)able is required for some reason, comment out
 * following #define. */

#define WRAP_PREEMPT 1

#if !defined(CONFIG_PREEMPT) || defined(CONFIG_PREEMPT_RT)
#ifndef WRAP_PREEMPT
#define WRAP_PREEMPT 1
#endif
#endif

#ifdef WRAP_PREEMPT

typedef struct {
	int count;
	struct mutex lock;
#ifdef CONFIG_SMP
	typeof(current->cpus_allowed) cpus_allowed;
#endif
	struct task_struct *task;
} irql_info_t;

DECLARE_PER_CPU(irql_info_t, irql_info);

static inline KIRQL raise_irql(KIRQL newirql)
{
	irql_info_t *info;

	assert(newirql == DISPATCH_LEVEL);
	info = &get_cpu_var(irql_info);
	if (info->task == current) {
		assert(info->count > 0);
		assert(mutex_is_locked(&info->lock));
#if defined(CONFIG_SMP) && defined(DEBUG)
		do {
			cpumask_t cpumask;
			cpumask = cpumask_of_cpu(smp_processor_id());
			cpus_xor(cpumask, cpumask, current->cpus_allowed);
			assert(cpus_empty(cpumask));
		} while (0);
#endif
		info->count++;
		put_cpu_var(irql_info);
		return DISPATCH_LEVEL;
	}
	/* TODO: is this enough to pin down to current cpu? */
#ifdef CONFIG_SMP
	assert(task_cpu(current) == smp_processor_id());
	info->cpus_allowed = current->cpus_allowed;
	current->cpus_allowed = cpumask_of_cpu(smp_processor_id());
#endif
	put_cpu_var(irql_info);
	mutex_lock(&info->lock);
	assert(info->count == 0);
	assert(info->task == NULL);
	info->count = 1;
	info->task = current;
	return PASSIVE_LEVEL;
}

static inline void lower_irql(KIRQL oldirql)
{									
	irql_info_t *info;

	assert(oldirql <= DISPATCH_LEVEL);
	info = &get_cpu_var(irql_info);
	assert(info->task == current);
	assert(mutex_is_locked(&info->lock));
	assert(info->count > 0);
	if (--info->count == 0) {
		info->task = NULL;
#ifdef CONFIG_SMP
		current->cpus_allowed = info->cpus_allowed;
#endif
		mutex_unlock(&info->lock);
	}
	put_cpu_var(irql_info);
}

static inline KIRQL current_irql(void)
{
	int count;
	if (in_irq() || irqs_disabled())
		EXIT4(return DIRQL);
	if (in_atomic() || in_interrupt())
		EXIT4(return SOFT_IRQL);
	count = get_cpu_var(irql_info).count;
	put_cpu_var(irql_info);
	if (count)
		EXIT6(return DISPATCH_LEVEL);
	else
		EXIT6(return PASSIVE_LEVEL);
}

#else

static inline KIRQL current_irql(void)
{
	if (in_irq() || irqs_disabled())
		EXIT4(return DIRQL);
	if (in_interrupt())
		EXIT4(return SOFT_IRQL);
	if (in_atomic())
		EXIT6(return DISPATCH_LEVEL);
	else
		EXIT6(return PASSIVE_LEVEL);
}

static inline KIRQL raise_irql(KIRQL newirql)
{
	KIRQL ret = in_atomic() ? DISPATCH_LEVEL : PASSIVE_LEVEL;
	assert(newirql == DISPATCH_LEVEL);
	assert(current_irql() <= DISPATCH_LEVEL);
	preempt_disable();
	return ret;
}

static inline void lower_irql(KIRQL oldirql)
{
	assert(current_irql() == DISPATCH_LEVEL);
	preempt_enable();
}

#endif

#define irql_gfp() (in_atomic() ? GFP_ATOMIC : GFP_KERNEL)

/* Windows spinlocks are of type ULONG_PTR which is not big enough to
 * store Linux spinlocks; so we implement Windows spinlocks using
 * ULONG_PTR space with our own functions/macros */

/* Windows seems to use 0 for unlocked state of spinlock - if Linux
 * convention of 1 for unlocked state is used, at least prism54 driver
 * crashes */

#define NT_SPIN_LOCK_UNLOCKED 0
#define NT_SPIN_LOCK_LOCKED 1

static inline void  nt_spin_lock_init(NT_SPIN_LOCK *lock)
{
	*lock = NT_SPIN_LOCK_UNLOCKED;
}

#ifdef CONFIG_SMP

static inline void nt_spin_lock(NT_SPIN_LOCK *lock)
{
	__asm__ __volatile__(
		"1:\t"
		"  xchgl %1, %0\n\t"
		"  testl %1, %1\n\t"
		"  jz 3f\n"
		"2:\t"
		"  rep; nop\n\t"
		"  cmpl %2, %0\n\t"
		"  je 1b\n\t"
		"  jmp 2b\n"
		"3:\n\t"
		: "+m" (*lock)
		: "r" (NT_SPIN_LOCK_LOCKED), "i" (NT_SPIN_LOCK_UNLOCKED));
}

static inline void nt_spin_unlock(NT_SPIN_LOCK *lock)
{
	*lock = NT_SPIN_LOCK_UNLOCKED;
}

#else // CONFIG_SMP

#define nt_spin_lock(lock) do { } while (0)

#define nt_spin_unlock(lock)  do { } while (0)

#endif // CONFIG_SMP

/* When kernel would've disabled preempt (e.g., in interrupt
 * handlers), we need to fake preempt so driver thinks it is running
 * at right IRQL */

/* raise IRQL to given (higher) IRQL if necessary before locking */
static inline KIRQL nt_spin_lock_irql(NT_SPIN_LOCK *lock, KIRQL newirql)
{
	KIRQL oldirql = raise_irql(newirql);
	nt_spin_lock(lock);
	return oldirql;
}

/* lower IRQL to given (lower) IRQL if necessary after unlocking */
static inline void nt_spin_unlock_irql(NT_SPIN_LOCK *lock, KIRQL oldirql)
{
	nt_spin_unlock(lock);
	lower_irql(oldirql);
}

#define nt_spin_lock_irqsave(lock, flags)				\
do {									\
	preempt_disable();						\
	local_irq_save(flags);						\
	nt_spin_lock(lock);						\
} while (0)

#define nt_spin_unlock_irqrestore(lock, flags)				\
do {									\
	nt_spin_unlock(lock);						\
	local_irq_restore(flags);					\
	preempt_enable();						\
} while (0)

static inline ULONG SPAN_PAGES(void *ptr, SIZE_T length)
{
	return PAGE_ALIGN(((unsigned long)ptr & (PAGE_SIZE - 1)) + length)
		>> PAGE_SHIFT;
}

#ifdef CONFIG_X86_64

/* TODO: can these be implemented without using spinlock? */

static inline struct nt_slist *PushEntrySList(nt_slist_header *head,
					      struct nt_slist *entry,
					      NT_SPIN_LOCK *lock)
{
	KIRQL irql = nt_spin_lock_irql(lock, DISPATCH_LEVEL);
	entry->next = head->next;
	head->next = entry;
	head->depth++;
	nt_spin_unlock_irql(lock, irql);
	TRACE4("%p, %p, %p", head, entry, entry->next);
	return entry->next;
}

static inline struct nt_slist *PopEntrySList(nt_slist_header *head,
					     NT_SPIN_LOCK *lock)
{
	struct nt_slist *entry;
	KIRQL irql = nt_spin_lock_irql(lock, DISPATCH_LEVEL);
	entry = head->next;
	if (entry) {
		head->next = entry->next;
		head->depth--;
	}
	nt_spin_unlock_irql(lock, irql);
	TRACE4("%p, %p", head, entry);
	return entry;
}

#else

#define u64_low_32(x) ((u32)x)
#define u64_high_32(x) ((u32)(x >> 32))

static inline u64 cmpxchg8b(volatile u64 *ptr, u64 old, u64 new)
{
	u64 prev;

	__asm__ __volatile__(
		"\n"
		LOCK_PREFIX "cmpxchg8b %0\n"
		: "+m" (*ptr), "=A" (prev)
		: "A" (old), "b" (u64_low_32(new)), "c" (u64_high_32(new)));
	return prev;
}

/* slist routines below update slist atomically - no need for
 * spinlocks */

static inline struct nt_slist *PushEntrySList(nt_slist_header *head,
					      struct nt_slist *entry,
					      NT_SPIN_LOCK *lock)
{
	nt_slist_header old, new;
	do {
		old.align = head->align;
		entry->next = old.next;
		new.next = entry;
		new.depth = old.depth + 1;
	} while (cmpxchg8b(&head->align, old.align, new.align) != old.align);
	TRACE4("%p, %p, %p", head, entry, old.next);
	return old.next;
}

static inline struct nt_slist *PopEntrySList(nt_slist_header *head,
					     NT_SPIN_LOCK *lock)
{
	struct nt_slist *entry;
	nt_slist_header old, new;
	do {
		old.align = head->align;
		entry = old.next;
		if (!entry)
			break;
		new.next = entry->next;
		new.depth = old.depth - 1;
	} while (cmpxchg8b(&head->align, old.align, new.align) != old.align);
	TRACE4("%p, %p", head, entry);
	return entry;
}

#endif

#define sleep_hz(n)					\
do {							\
	set_current_state(TASK_INTERRUPTIBLE);		\
	schedule_timeout(n);				\
} while (0)

int ntoskernel_init(void);
void ntoskernel_exit(void);
int ntoskernel_init_device(struct wrap_device *wd);
void ntoskernel_exit_device(struct wrap_device *wd);
void *allocate_object(ULONG size, enum common_object_type type,
		      struct unicode_string *name);
void free_object(void *object);

int usb_init(void);
void usb_exit(void);
int usb_init_device(struct wrap_device *wd);
void usb_exit_device(struct wrap_device *wd);
void usb_cancel_pending_urbs(void);

int crt_init(void);
void crt_exit(void);
int rtl_init(void);
void rtl_exit(void);
int wrap_procfs_init(void);
void wrap_procfs_remove(void);

int link_pe_images(struct pe_image *pe_image, unsigned short n);

int stricmp(const char *s1, const char *s2);
void dump_bytes(const char *name, const u8 *from, int len);
struct mdl *allocate_init_mdl(void *virt, ULONG length);
void free_mdl(struct mdl *mdl);
struct driver_object *find_bus_driver(const char *name);
void free_custom_extensions(struct driver_extension *drv_obj_ext);
struct nt_thread *get_current_nt_thread(void);
u64 ticks_1601(void);
int schedule_ntos_work_item(NTOS_WORK_FUNC func, void *arg1, void *arg2);
void wrap_init_timer(struct nt_timer *nt_timer, enum timer_type type,
		     struct ndis_mp_block *nmb);
BOOLEAN wrap_set_timer(struct nt_timer *nt_timer, unsigned long expires_hz,
		       unsigned long repeat_hz, struct kdpc *kdpc);

LONG InterlockedDecrement(LONG volatile *val) wfastcall;
LONG InterlockedIncrement(LONG volatile *val) wfastcall;
struct nt_list *ExInterlockedInsertHeadList
	(struct nt_list *head, struct nt_list *entry,
	 NT_SPIN_LOCK *lock) wfastcall;
struct nt_list *ExInterlockedInsertTailList
	(struct nt_list *head, struct nt_list *entry,
	 NT_SPIN_LOCK *lock) wfastcall;
struct nt_list *ExInterlockedRemoveHeadList
	(struct nt_list *head, NT_SPIN_LOCK *lock) wfastcall;
NTSTATUS IofCallDriver(struct device_object *dev_obj, struct irp *irp) wfastcall;
KIRQL KfRaiseIrql(KIRQL newirql) wfastcall;
void KfLowerIrql(KIRQL oldirql) wfastcall;
KIRQL KfAcquireSpinLock(NT_SPIN_LOCK *lock) wfastcall;
void KfReleaseSpinLock(NT_SPIN_LOCK *lock, KIRQL oldirql) wfastcall;
void IofCompleteRequest(struct irp *irp, CHAR prio_boost) wfastcall;
void KefReleaseSpinLockFromDpcLevel(NT_SPIN_LOCK *lock) wfastcall;

LONG ObfReferenceObject(void *object) wfastcall;
void ObfDereferenceObject(void *object) wfastcall;

#define ObReferenceObject(object) ObfReferenceObject(object)
#define ObDereferenceObject(object) ObfDereferenceObject(object)

void WRITE_PORT_UCHAR(ULONG_PTR port, UCHAR value) wstdcall;
UCHAR READ_PORT_UCHAR(ULONG_PTR port) wstdcall;

#undef ExAllocatePoolWithTag
void *ExAllocatePoolWithTag(enum pool_type pool_type, SIZE_T size,
			    ULONG tag) wstdcall;
#if defined(ALLOC_DEBUG) && ALLOC_DEBUG > 1
#define ExAllocatePoolWithTag(pool_type, size, tag)			\
	wrap_ExAllocatePoolWithTag(pool_type, size, tag, __FILE__, __LINE__)
#endif

void ExFreePool(void *p) wstdcall;
ULONG MmSizeOfMdl(void *base, ULONG length) wstdcall;
void *MmMapIoSpace(PHYSICAL_ADDRESS phys_addr, SIZE_T size,
		   enum memory_caching_type cache) wstdcall;
void MmUnmapIoSpace(void *addr, SIZE_T size) wstdcall;
void MmProbeAndLockPages(struct mdl *mdl, KPROCESSOR_MODE access_mode,
			 enum lock_operation operation) wstdcall;
void MmUnlockPages(struct mdl *mdl) wstdcall;
void KeInitializeEvent(struct nt_event *nt_event,
		       enum event_type type, BOOLEAN state) wstdcall;
LONG KeSetEvent(struct nt_event *nt_event, KPRIORITY incr,
		BOOLEAN wait) wstdcall;
LONG KeResetEvent(struct nt_event *nt_event) wstdcall;
void KeClearEvent(struct nt_event *nt_event) wstdcall;
void KeInitializeDpc(struct kdpc *kdpc, void *func, void *ctx) wstdcall;
BOOLEAN queue_kdpc(struct kdpc *kdpc);
BOOLEAN dequeue_kdpc(struct kdpc *kdpc);

void KeFlushQueuedDpcs(void) wstdcall;
NTSTATUS IoConnectInterrupt(struct kinterrupt **kinterrupt,
			    PKSERVICE_ROUTINE service_routine,
			    void *service_context, NT_SPIN_LOCK *lock,
			    ULONG vector, KIRQL irql, KIRQL synch_irql,
			    enum kinterrupt_mode interrupt_mode,
			    BOOLEAN shareable, KAFFINITY processor_enable_mask,
			    BOOLEAN floating_save) wstdcall;
void IoDisconnectInterrupt(struct kinterrupt *interrupt) wstdcall;
BOOLEAN KeSynchronizeExecution(struct kinterrupt *interrupt,
			       PKSYNCHRONIZE_ROUTINE synch_routine,
			       void *ctx) wstdcall;

NTSTATUS KeWaitForSingleObject(void *object, KWAIT_REASON reason,
			       KPROCESSOR_MODE waitmode, BOOLEAN alertable,
			       LARGE_INTEGER *timeout) wstdcall;
struct mdl *IoAllocateMdl(void *virt, ULONG length, BOOLEAN second_buf,
			  BOOLEAN charge_quota, struct irp *irp) wstdcall;
void MmBuildMdlForNonPagedPool(struct mdl *mdl) wstdcall;
void IoFreeMdl(struct mdl *mdl) wstdcall;
NTSTATUS IoCreateDevice(struct driver_object *driver, ULONG dev_ext_length,
			struct unicode_string *dev_name, DEVICE_TYPE dev_type,
			ULONG dev_chars, BOOLEAN exclusive,
			struct device_object **dev_obj) wstdcall;
NTSTATUS IoCreateSymbolicLink(struct unicode_string *link,
			      struct unicode_string *dev_name) wstdcall;
void IoDeleteDevice(struct device_object *dev) wstdcall;
void IoDetachDevice(struct device_object *topdev) wstdcall;
struct device_object *IoGetAttachedDevice(struct device_object *dev) wstdcall;
struct device_object *IoGetAttachedDeviceReference
	(struct device_object *dev) wstdcall;
NTSTATUS IoAllocateDriverObjectExtension
	(struct driver_object *drv_obj, void *client_id, ULONG extlen,
	 void **ext) wstdcall;
void *IoGetDriverObjectExtension(struct driver_object *drv,
				 void *client_id) wstdcall;
struct device_object *IoAttachDeviceToDeviceStack
	(struct device_object *src, struct device_object *dst) wstdcall;
void KeInitializeEvent(struct nt_event *nt_event, enum event_type type,
		       BOOLEAN state) wstdcall;
struct irp *IoAllocateIrp(char stack_count, BOOLEAN charge_quota) wstdcall;
void IoFreeIrp(struct irp *irp) wstdcall;
BOOLEAN IoCancelIrp(struct irp *irp) wstdcall;
struct irp *IoBuildSynchronousFsdRequest
	(ULONG major_func, struct device_object *dev_obj, void *buf,
	 ULONG length, LARGE_INTEGER *offset, struct nt_event *event,
	 struct io_status_block *status) wstdcall;
struct irp *IoBuildAsynchronousFsdRequest
	(ULONG major_func, struct device_object *dev_obj, void *buf,
	 ULONG length, LARGE_INTEGER *offset,
	 struct io_status_block *status) wstdcall;
NTSTATUS PoCallDriver(struct device_object *dev_obj, struct irp *irp) wstdcall;

NTSTATUS IoPassIrpDown(struct device_object *dev_obj, struct irp *irp) wstdcall;
WIN_FUNC_DECL(IoPassIrpDown,2);
NTSTATUS IoSyncForwardIrp(struct device_object *dev_obj,
			  struct irp *irp) wstdcall;
NTSTATUS IoAsyncForwardIrp(struct device_object *dev_obj,
			   struct irp *irp) wstdcall;
NTSTATUS IoInvalidDeviceRequest(struct device_object *dev_obj,
				struct irp *irp) wstdcall;

KIRQL KeGetCurrentIrql(void) wstdcall;
void KeInitializeSpinLock(NT_SPIN_LOCK *lock) wstdcall;
void KeAcquireSpinLock(NT_SPIN_LOCK *lock, KIRQL *irql) wstdcall;
void KeReleaseSpinLock(NT_SPIN_LOCK *lock, KIRQL oldirql) wstdcall;
KIRQL KeAcquireSpinLockRaiseToDpc(NT_SPIN_LOCK *lock) wstdcall;

void IoAcquireCancelSpinLock(KIRQL *irql) wstdcall;
void IoReleaseCancelSpinLock(KIRQL irql) wstdcall;

void RtlCopyMemory(void *dst, const void *src, SIZE_T length) wstdcall;
NTSTATUS RtlUnicodeStringToAnsiString
	(struct ansi_string *dst, const struct unicode_string *src,
	 BOOLEAN dup) wstdcall;
NTSTATUS RtlAnsiStringToUnicodeString
	(struct unicode_string *dst, const struct ansi_string *src,
	 BOOLEAN dup) wstdcall;
void RtlInitAnsiString(struct ansi_string *dst, const char *src) wstdcall;
void RtlInitString(struct ansi_string *dst, const char *src) wstdcall;
void RtlInitUnicodeString(struct unicode_string *dest,
			  const wchar_t *src) wstdcall;
void RtlFreeUnicodeString(struct unicode_string *string) wstdcall;
void RtlFreeAnsiString(struct ansi_string *string) wstdcall;
LONG RtlCompareUnicodeString(const struct unicode_string *s1,
			     const struct unicode_string *s2,
			     BOOLEAN case_insensitive) wstdcall;
void RtlCopyUnicodeString(struct unicode_string *dst,
			  struct unicode_string *src) wstdcall;
NTSTATUS RtlUpcaseUnicodeString(struct unicode_string *dst,
				struct unicode_string *src,
				BOOLEAN alloc) wstdcall;
void KeInitializeTimer(struct nt_timer *nt_timer) wstdcall;
void KeInitializeTimerEx(struct nt_timer *nt_timer,
			 enum timer_type type) wstdcall;
BOOLEAN KeSetTimerEx(struct nt_timer *nt_timer, LARGE_INTEGER duetime_ticks,
		     LONG period_ms, struct kdpc *kdpc) wstdcall;
BOOLEAN KeSetTimer(struct nt_timer *nt_timer, LARGE_INTEGER duetime_ticks,
		   struct kdpc *kdpc) wstdcall;
BOOLEAN KeCancelTimer(struct nt_timer *nt_timer) wstdcall;
void KeInitializeDpc(struct kdpc *kdpc, void *func, void *ctx) wstdcall;
struct nt_thread *KeGetCurrentThread(void) wstdcall;
NTSTATUS ObReferenceObjectByHandle(void *handle, ACCESS_MASK desired_access,
				   void *obj_type, KPROCESSOR_MODE access_mode,
				   void **object, void *handle_info) wstdcall;

void adjust_user_shared_data_addr(char *driver, unsigned long length);

#define IoCompleteRequest(irp, prio) IofCompleteRequest(irp, prio)
#define IoCallDriver(dev, irp) IofCallDriver(dev, irp)

#if defined(IO_DEBUG)
#define DUMP_IRP(irp)							\
do {									\
	struct io_stack_location *irp_sl;				\
	irp_sl = IoGetCurrentIrpStackLocation(irp);			\
	IOTRACE("irp: %p, stack size: %d, cl: %d, sl: %p, dev_obj: %p, " \
		"mj_fn: %d, minor_fn: %d, nt_urb: %p, event: %p",	\
		irp, irp->stack_count, (irp)->current_location,		\
		irp_sl, irp_sl->dev_obj, irp_sl->major_fn,		\
		irp_sl->minor_fn, IRP_URB(irp),				\
		(irp)->user_event);					\
} while (0)
#else
#define DUMP_IRP(irp) do { } while (0)
#endif

#endif // _NTOSKERNEL_H_


```

Line 716 to line 718 are below:

```

typedef struct {
	int count;
	struct mutex lock;

```

Thank you very much for your help.

---

### Post by xeth_delta on 2008-01-10
Can you please do the following:

```
cd /usr/src/linux-headers-2.6.15-29-386
find * | grep -i mutex.h
```

and post the output.

It seems that a defined structure called "struct mutex" can not be found.

---

### Post by mahasmb on 2008-01-10
$ find * | grep -i mutex.h

gave me no output

---

### Post by xeth_delta on 2008-01-10
> **mahasmb said:**
> $ find * | grep -i mutex.h

gave me no output

I wonder if your kernel is too old for that version of ndiswrapper. Would it be feasable to try an ndiswrapper version older than 1.51, but newer than the one installed in dapper?

---

### Post by mahasmb on 2008-01-10
for NDISwrapper version 1.47

```

$ sudo make
make -C driver
make[1]: Entering directory `/home/maha/Desktop/ndiswrapper-1.47/driver'
make -C /lib/modules/2.6.15-29-386/build SUBDIRS=/home/maha/Desktop/ndiswrapper-1.47/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.15-29-386'
  LD      /home/maha/Desktop/ndiswrapper-1.47/driver/built-in.o
  CC [M]  /home/maha/Desktop/ndiswrapper-1.47/driver/crt.o
  CC [M]  /home/maha/Desktop/ndiswrapper-1.47/driver/hal.o
  CC [M]  /home/maha/Desktop/ndiswrapper-1.47/driver/iw_ndis.o
  CC [M]  /home/maha/Desktop/ndiswrapper-1.47/driver/loader.o
  CC [M]  /home/maha/Desktop/ndiswrapper-1.47/driver/ndis.o
  CC [M]  /home/maha/Desktop/ndiswrapper-1.47/driver/ntoskernel.o
  CC [M]  /home/maha/Desktop/ndiswrapper-1.47/driver/ntoskernel_io.o
  CC [M]  /home/maha/Desktop/ndiswrapper-1.47/driver/pe_linker.o
  CC [M]  /home/maha/Desktop/ndiswrapper-1.47/driver/pnp.o
  CC [M]  /home/maha/Desktop/ndiswrapper-1.47/driver/proc.o
  CC [M]  /home/maha/Desktop/ndiswrapper-1.47/driver/rtl.o
  CC [M]  /home/maha/Desktop/ndiswrapper-1.47/driver/wrapmem.o
  CC [M]  /home/maha/Desktop/ndiswrapper-1.47/driver/wrapndis.o
  CC [M]  /home/maha/Desktop/ndiswrapper-1.47/driver/wrapper.o
  CC [M]  /home/maha/Desktop/ndiswrapper-1.47/driver/usb.o
  CC [M]  /home/maha/Desktop/ndiswrapper-1.47/driver/divdi3.o
  LD [M]  /home/maha/Desktop/ndiswrapper-1.47/driver/ndiswrapper.o
  Building modules, stage 2.
  MODPOST
  CC      /home/maha/Desktop/ndiswrapper-1.47/driver/ndiswrapper.mod.o
  LD [M]  /home/maha/Desktop/ndiswrapper-1.47/driver/ndiswrapper.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.15-29-386'
make[1]: Leaving directory `/home/maha/Desktop/ndiswrapper-1.47/driver'
make -C utils
make[1]: Entering directory `/home/maha/Desktop/ndiswrapper-1.47/utils'
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c
loadndisdriver.c:15:20: error: stdlib.h: No such file or directory
loadndisdriver.c:16:19: error: stdio.h: No such file or directory
loadndisdriver.c:17:19: error: errno.h: No such file or directory
loadndisdriver.c:18:20: error: string.h: No such file or directory
loadndisdriver.c:19:20: error: libgen.h: No such file or directory
loadndisdriver.c:21:22: error: sys/mman.h: No such file or directory
loadndisdriver.c:23:23: error: sys/types.h: No such file or directory
loadndisdriver.c:24:23: error: sys/ioctl.h: No such file or directory
loadndisdriver.c:25:22: error: sys/stat.h: No such file or directory
loadndisdriver.c:26:20: error: unistd.h: No such file or directory
loadndisdriver.c:27:19: error: fcntl.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.0.3/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.0.3/include/limits.h:11,
                 from loadndisdriver.c:28:
/usr/lib/gcc/i486-linux-gnu/4.0.3/include/limits.h:122:61: error: limits.h: No such file or directory
loadndisdriver.c:29:19: error: ctype.h: No such file or directory
loadndisdriver.c:30:20: error: dirent.h: No such file or directory
loadndisdriver.c:31:20: error: syslog.h: No such file or directory
loadndisdriver.c:34:25: error: linux/major.h: No such file or directory
loadndisdriver.c:35:25: error: linux/ioctl.h: No such file or directory
In file included from loadndisdriver.c:37:
../driver/loader.h:24: error: syntax error before 'size_t'
../driver/loader.h:24: warning: no semicolon at end of struct or union
../driver/loader.h:26: error: syntax error before '}' token
../driver/loader.h:52: error: array type has incomplete element type
../driver/loader.h:56: error: array type has incomplete element type
loadndisdriver.c: In function 'load_file':
loadndisdriver.c:67: error: 'size_t' undeclared (first use in this function)
loadndisdriver.c:67: error: (Each undeclared identifier is reported only once
loadndisdriver.c:67: error: for each function it appears in.)
loadndisdriver.c:67: error: syntax error before 'size'
loadndisdriver.c:68: error: 'NULL' undeclared (first use in this function)
loadndisdriver.c:69: error: storage size of 'statbuf' isn't known
loadndisdriver.c:71: warning: implicit declaration of function 'basename'
loadndisdriver.c:71: warning: initialization makes pointer from integer without a cast
loadndisdriver.c:73: warning: implicit declaration of function 'open'
loadndisdriver.c:73: error: 'O_RDONLY' undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function 'syslog'
loadndisdriver.c:75: error: 'LOG_KERN' undeclared (first use in this function)
loadndisdriver.c:75: error: 'LOG_INFO' undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function 'strerror'
loadndisdriver.c:75: error: 'errno' undeclared (first use in this function)
loadndisdriver.c:76: error: 'EINVAL' undeclared (first use in this function)
loadndisdriver.c:79: warning: implicit declaration of function 'fstat'
loadndisdriver.c:81: warning: implicit declaration of function 'close'
loadndisdriver.c:84: error: 'size' undeclared (first use in this function)
loadndisdriver.c:86: warning: implicit declaration of function 'mmap'
loadndisdriver.c:86: error: 'PROT_READ' undeclared (first use in this function)
loadndisdriver.c:86: error: 'MAP_PRIVATE' undeclared (first use in this function)
loadndisdriver.c:86: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:87: error: 'MAP_FAILED' undeclared (first use in this function)loadndisdriver.c:93: warning: implicit declaration of function 'strncpy'
loadndisdriver.c:93: warning: incompatible implicit declaration of built-in function 'strncpy'
loadndisdriver.c:93: error: dereferencing pointer to incomplete type
loadndisdriver.c:93: error: dereferencing pointer to incomplete type
loadndisdriver.c:94: error: dereferencing pointer to incomplete type
loadndisdriver.c:94: error: dereferencing pointer to incomplete type
loadndisdriver.c:95: error: dereferencing pointer to incomplete type
loadndisdriver.c:96: error: dereferencing pointer to incomplete type
loadndisdriver.c:69: warning: unused variable 'statbuf'
loadndisdriver.c: In function 'parse_setting_line':
loadndisdriver.c:109: warning: implicit declaration of function 'isspace'
loadndisdriver.c:115: warning: implicit declaration of function 'strchr'
loadndisdriver.c:115: warning: incompatible implicit declaration of built-in function 'strchr'
loadndisdriver.c:115: error: 'NULL' undeclared (first use in this function)
loadndisdriver.c:117: error: 'LOG_KERN' undeclared (first use in this function)
loadndisdriver.c:117: error: 'LOG_INFO' undeclared (first use in this function)
loadndisdriver.c:118: error: 'EINVAL' undeclared (first use in this function)
loadndisdriver.c:138: warning: implicit declaration of function 'strlen'
loadndisdriver.c:138: warning: incompatible implicit declaration of built-in function 'strlen'
loadndisdriver.c: In function 'read_conf_file':
loadndisdriver.c:150: error: storage size of 'statbuf' isn't known
loadndisdriver.c:151: error: 'FILE' undeclared (first use in this function)
loadndisdriver.c:151: error: 'config' undeclared (first use in this function)
loadndisdriver.c:157: warning: implicit declaration of function 'lstat'
loadndisdriver.c:158: error: 'LOG_KERN' undeclared (first use in this function)
loadndisdriver.c:158: error: 'LOG_INFO' undeclared (first use in this function)
loadndisdriver.c:158: error: 'errno' undeclared (first use in this function)
loadndisdriver.c:160: error: 'EINVAL' undeclared (first use in this function)
loadndisdriver.c:163: warning: implicit declaration of function 'sscanf'
loadndisdriver.c:163: warning: incompatible implicit declaration of built-in function 'sscanf'
loadndisdriver.c:178: warning: implicit declaration of function 'fopen'
loadndisdriver.c:178: error: 'NULL' undeclared (first use in this function)
loadndisdriver.c:182: warning: implicit declaration of function 'fgets'
loadndisdriver.c:194: warning: incompatible implicit declaration of built-in function 'strncpy'
loadndisdriver.c:205: warning: implicit declaration of function 'fclose'
loadndisdriver.c:150: warning: unused variable 'statbuf'
loadndisdriver.c: In function 'load_bin_file':
loadndisdriver.c:213: error: storage size of 'driver_file' isn't known
loadndisdriver.c:217: error: 'LOG_KERN' undeclared (first use in this function)
loadndisdriver.c:217: error: 'LOG_INFO' undeclared (first use in this function)
loadndisdriver.c:219: warning: implicit declaration of function 'tolower'
loadndisdriver.c:221: warning: implicit declaration of function 'chdir'
loadndisdriver.c:222: error: 'errno' undeclared (first use in this function)
loadndisdriver.c:224: error: 'EINVAL' undeclared (first use in this function)
loadndisdriver.c:230: warning: incompatible implicit declaration of built-in function 'strncpy'
loadndisdriver.c:232: warning: implicit declaration of function 'ioctl'
loadndisdriver.c:232: warning: implicit declaration of function '_IOW'
loadndisdriver.c:232: error: syntax error before 'struct'
loadndisdriver.c:213: warning: unused variable 'driver_file'
loadndisdriver.c:235: warning: control reaches end of non-void function
loadndisdriver.c: At top level:
loadndisdriver.c:236: error: syntax error before 'return'
loadndisdriver.c: In function 'load_driver':
loadndisdriver.c:249: error: 'DIR' undeclared (first use in this function)
loadndisdriver.c:249: error: 'driver_dir' undeclared (first use in this function)
loadndisdriver.c:251: error: 'NULL' undeclared (first use in this function)
loadndisdriver.c:255: error: 'LOG_KERN' undeclared (first use in this function)
loadndisdriver.c:255: error: 'LOG_INFO' undeclared (first use in this function)
loadndisdriver.c:257: error: 'errno' undeclared (first use in this function)
loadndisdriver.c:259: error: 'EINVAL' undeclared (first use in this function)
loadndisdriver.c:261: warning: implicit declaration of function 'opendir'
loadndisdriver.c:267: warning: implicit declaration of function 'malloc'
loadndisdriver.c:267: warning: incompatible implicit declaration of built-in function 'malloc'
loadndisdriver.c:271: warning: implicit declaration of function 'memset'
loadndisdriver.c:271: warning: incompatible implicit declaration of built-in function 'memset'
loadndisdriver.c:272: warning: incompatible implicit declaration of built-in function 'strncpy'
loadndisdriver.c:280: warning: implicit declaration of function 'readdir'
loadndisdriver.c:280: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:282: error: storage size of 'statbuf' isn't known
loadndisdriver.c:284: error: dereferencing pointer to incomplete type
loadndisdriver.c:287: warning: implicit declaration of function 'stat'
loadndisdriver.c:287: error: dereferencing pointer to incomplete type
loadndisdriver.c:288: warning: implicit declaration of function 'S_ISREG'
loadndisdriver.c:289: error: dereferencing pointer to incomplete type
loadndisdriver.c:294: warning: incompatible implicit declaration of built-in function 'strlen'
loadndisdriver.c:294: error: dereferencing pointer to incomplete type
loadndisdriver.c:296: warning: implicit declaration of function 'strcasecmp'
loadndisdriver.c:296: error: dereferencing pointer to incomplete type
loadndisdriver.c:299: error: dereferencing pointer to incomplete type
loadndisdriver.c:302: error: dereferencing pointer to incomplete type
loadndisdriver.c:303: error: dereferencing pointer to incomplete type
loadndisdriver.c:305: error: dereferencing pointer to incomplete type
loadndisdriver.c:311: error: dereferencing pointer to incomplete type
loadndisdriver.c:312: error: dereferencing pointer to incomplete type
loadndisdriver.c:313: warning: implicit declaration of function 'strcpy'
loadndisdriver.c:313: warning: incompatible implicit declaration of built-in function 'strcpy'
loadndisdriver.c:314: error: dereferencing pointer to incomplete type
loadndisdriver.c:321: error: dereferencing pointer to incomplete type
loadndisdriver.c:282: warning: unused variable 'statbuf'
loadndisdriver.c:344: error: syntax error before 'struct'
loadndisdriver.c:346: warning: implicit declaration of function 'closedir'
loadndisdriver.c:348: warning: implicit declaration of function 'free'
loadndisdriver.c:355: warning: implicit declaration of function 'munmap'
loadndisdriver.c:361: warning: control reaches end of non-void function
loadndisdriver.c: In function 'get_device':
loadndisdriver.c:367: error: storage size of 'statbuf' isn't known
loadndisdriver.c:370: error: 'LOG_KERN' undeclared (first use in this function)
loadndisdriver.c:370: error: 'LOG_INFO' undeclared (first use in this function)
loadndisdriver.c:373: error: 'errno' undeclared (first use in this function)
loadndisdriver.c:374: error: 'EINVAL' undeclared (first use in this function)
loadndisdriver.c:376: warning: implicit declaration of function 'snprintf'
loadndisdriver.c:376: warning: incompatible implicit declaration of built-in function 'snprintf'
loadndisdriver.c:407: warning: incompatible implicit declaration of built-in function 'strncpy'
loadndisdriver.c:367: warning: unused variable 'statbuf'
loadndisdriver.c: In function 'load_device':
loadndisdriver.c:419: error: 'DIR' undeclared (first use in this function)
loadndisdriver.c:419: error: 'dir' undeclared (first use in this function)
loadndisdriver.c:423: error: 'LOG_KERN' undeclared (first use in this function)
loadndisdriver.c:423: error: 'LOG_INFO' undeclared (first use in this function)
loadndisdriver.c:424: warning: incompatible implicit declaration of built-in function 'memset'
loadndisdriver.c:426: error: 'errno' undeclared (first use in this function)
loadndisdriver.c:427: error: 'EINVAL' undeclared (first use in this function)
loadndisdriver.c:429: error: 'NULL' undeclared (first use in this function)
loadndisdriver.c:434: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:435: error: dereferencing pointer to incomplete type
loadndisdriver.c:436: error: dereferencing pointer to incomplete type
loadndisdriver.c:439: error: dereferencing pointer to incomplete type
loadndisdriver.c:447: error: syntax error before 'struct'
loadndisdriver.c: In function 'get_ioctl_device':
loadndisdriver.c:464: error: 'FILE' undeclared (first use in this function)
loadndisdriver.c:464: error: 'proc_misc' undeclared (first use in this function)loadndisdriver.c:472: warning: implicit declaration of function 'strstr'
loadndisdriver.c:472: warning: incompatible implicit declaration of built-in function 'strstr'
loadndisdriver.c:473: warning: implicit declaration of function 'strtol'
loadndisdriver.c:473: error: 'NULL' undeclared (first use in this function)
loadndisdriver.c:483: error: 'LOG_KERN' undeclared (first use in this function)
loadndisdriver.c:483: error: 'LOG_INFO' undeclared (first use in this function)
loadndisdriver.c:488: warning: implicit declaration of function 'unlink'
loadndisdriver.c:489: warning: implicit declaration of function 'mknod'
loadndisdriver.c:489: error: 'S_IFCHR' undeclared (first use in this function)
loadndisdriver.c:489: error: 'MISC_MAJOR' undeclared (first use in this function)
loadndisdriver.c:490: error: 'errno' undeclared (first use in this function)
loadndisdriver.c:495: error: 'O_RDONLY' undeclared (first use in this function)
loadndisdriver.c: In function 'main':
loadndisdriver.c:511: warning: implicit declaration of function 'openlog'
loadndisdriver.c:511: error: 'LOG_PERROR' undeclared (first use in this function)
loadndisdriver.c:511: error: 'LOG_CONS' undeclared (first use in this function)
loadndisdriver.c:511: error: 'LOG_KERN' undeclared (first use in this function)
loadndisdriver.c:511: error: 'LOG_DEBUG' undeclared (first use in this function)loadndisdriver.c:513: error: 'LOG_INFO' undeclared (first use in this function)
loadndisdriver.c:515: warning: implicit declaration of function 'strncmp'
loadndisdriver.c:517: warning: implicit declaration of function 'printf'
loadndisdriver.c:517: warning: incompatible implicit declaration of built-in function 'printf'
loadndisdriver.c:527: warning: implicit declaration of function 'atoi'
loadndisdriver.c:542: warning: implicit declaration of function 'atof'
loadndisdriver.c:549: warning: implicit declaration of function 'strcmp'
loadndisdriver.c:556: warning: incompatible implicit declaration of built-in function 'sscanf'
loadndisdriver.c:590: warning: implicit declaration of function 'closelog'
make[1]: *** [loadndisdriver] Error 1
make[1]: Leaving directory `/home/maha/Desktop/ndiswrapper-1.47/utils'
make: *** [all] Error 2


```

for NDISwrapper version 1.23

```

$ sudo make uninstall
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
removing /lib/modules/2.6.15-29-386/kernel/drivers/net/ndiswrapper
/bin/rm: cannot remove `/lib/modules/2.6.15-29-386/kernel/drivers/net/ndiswrapper': Is a directory
make: *** [uninstall] Error 1


```

I always do " sudo make uninstall" and then "sudo make" until I got an error.

I've tried versions 1.23, 1.40, 1.44,1.47, 1.48,1.49,1.51

---

### Post by xeth_delta on 2008-01-11
> **mahasmb said:**
> for NDISwrapper version 1.47
```

$ sudo make uninstall
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
removing /lib/modules/2.6.15-29-386/kernel/drivers/net/ndiswrapper
/bin/rm: cannot remove `/lib/modules/2.6.15-29-386/kernel/drivers/net/ndiswrapper': Is a directory
make: *** [uninstall] Error 1

```

I always do " sudo make uninstall" and then "sudo make" until I got an error.


Try the following:
```
sudo rm -r /lib/modules/2.6.15-29-386/kernel/drivers/net/ndiswrapper
sudo make uninstall
```
then please remove the ndiswrapper source code directory from where you were trying to compile. Unpack the package you downloaded for ndiswrapper, enter the newly created directory and do:
```
./configure
make
sudo make install
```

---

### Post by mahasmb on 2008-01-11
None of the packages have "configure" files.

---

### Post by mahasmb on 2008-01-12
Okay, I've reinstalled Dapper Drake


The following finally worked
```

$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  binutils cpp cpp-4.0 dpkg-dev g++ g++-4.0 gcc gcc-4.0 libc6-dev
  libstdc++6-4.0-dev linux-kernel-headers
Suggested packages:
  binutils-doc cpp-doc gcc-4.0-locales debian-keyring gcc-4.0-doc lib64stdc++6
  manpages-dev autoconf automake1.9 libtool flex bison gcc-doc libc6-dev-amd64
  lib64gcc1 glibc-doc libstdc++6-4.0-doc stl-manual
Recommended packages:
  libmudflap0-dev
The following NEW packages will be installed:
  binutils build-essential cpp cpp-4.0 dpkg-dev g++ g++-4.0 gcc gcc-4.0
  libc6-dev libstdc++6-4.0-dev linux-kernel-headers
0 upgraded, 12 newly installed, 0 to remove and 0 not upgraded.
Need to get 2985kB/11.7MB of archives.
After unpacking, 45.8MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ca.archive.ubuntu.com dapper-updates/main libc6-dev 2.3.6-0ubuntu20.5 [2822kB]
Get:2 http://ca.archive.ubuntu.com dapper-updates/main dpkg-dev 1.13.11ubuntu7 [163kB]
Fetched 2985kB in 16s (179kB/s)
Selecting previously deselected package binutils.
(Reading database ... 73044 files and directories currently installed.)
Unpacking binutils (from .../binutils_2.16.1cvs20060117-1ubuntu2.1_i386.deb) ...Selecting previously deselected package linux-kernel-headers.
Unpacking linux-kernel-headers (from .../linux-kernel-headers_2.6.11.2-0ubuntu18_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.3.6-0ubuntu20.5_i386.deb) ...
Selecting previously deselected package cpp-4.0.
Unpacking cpp-4.0 (from .../cpp-4.0_4.0.3-1ubuntu5_i386.deb) ...
Selecting previously deselected package cpp.
Unpacking cpp (from .../cpp_4.0.3-1_i386.deb) ...
Selecting previously deselected package gcc-4.0.
Unpacking gcc-4.0 (from .../gcc-4.0_4.0.3-1ubuntu5_i386.deb) ...
Selecting previously deselected package gcc.
Unpacking gcc (from .../gcc_4.0.3-1_i386.deb) ...
Selecting previously deselected package libstdc++6-4.0-dev.
Unpacking libstdc++6-4.0-dev (from .../libstdc++6-4.0-dev_4.0.3-1ubuntu5_i386.deb) ...
Selecting previously deselected package g++-4.0.
Unpacking g++-4.0 (from .../g++-4.0_4.0.3-1ubuntu5_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4.0.3-1_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.13.11ubuntu7_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.1_i386.deb) ...
Setting up binutils (2.16.1cvs20060117-1ubuntu2.1) ...

Setting up linux-kernel-headers (2.6.11.2-0ubuntu18) ...
Setting up libc6-dev (2.3.6-0ubuntu20.5) ...
Setting up cpp-4.0 (4.0.3-1ubuntu5) ...
Setting up cpp (4.0.3-1) ...

Setting up gcc-4.0 (4.0.3-1ubuntu5) ...
Setting up gcc (4.0.3-1) ...

Setting up dpkg-dev (1.13.11ubuntu7) ...
Setting up g++-4.0 (4.0.3-1ubuntu5) ...
Setting up libstdc++6-4.0-dev (4.0.3-1ubuntu5) ...

Setting up g++ (4.0.3-1) ...

Setting up build-essential (11.1) ...


```

```

$ sudo ndiswrapper -l
Installed ndis drivers:
sis163u         driver present, hardware present
```

The following are still giving me problems


```
$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

```

```

$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.

```


As for the "make" problems... I decided to use .deb packages instead of .tar packages to install ndiswrapper.

---

### Post by mahasmb on 2008-01-12
I went to the site below and read the following:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
> 
Note: There is a known bug in the Debian package, detailed  in this thread. If you install from these packages, the kernel module may not get installed, so you may get the error FATAL: Module ndiswrapper not found when you run modprobe ndiswrapper. To avoid this problem, it's best to compile from the source available at  [http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/). This is fairly simple but requires the build-essentials package to be installed. You can install this offline using apt-cdrom from the command line or the synaptic package manager with the ubuntu install CD.


Well... I guess I didn't do anything different. Just after re-installing there were lessed messed up problems. After installing the "build-essential" and it actually working this time, I went back and uninstalled ndiswrapper, then re-installed version 1.18, which I found it came out shortly after Dapper did, thus that version was definitely compatible.

So "make" commands actually worked.

I was able to install and run "sudo ndiswrapper -l" with no FATAL errors. And now I can FINALLY see wireless networks.

I just had a long string of bad luck it seems... a fresh new install gave me problems so I had to do another fresh install.

Finally over... I never want to go through something like that again. Unfortunately this wasn't the first time... so here's hoping it's the last.

---

