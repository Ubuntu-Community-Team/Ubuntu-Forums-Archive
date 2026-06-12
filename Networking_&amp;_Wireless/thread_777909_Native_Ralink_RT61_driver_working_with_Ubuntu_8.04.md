---
title: "Native Ralink RT61 driver working with Ubuntu 8.04 Hardy 2.6.24-16 kernel"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by deRooij on 2008-05-01
For all of you who still use the native Ralink drivers, and who do have serious problems in getting their rt61 PCI card to work after upgrading to 8.04 LTS the following:

Download the 2007_1210_RT61_Linux_STA_v1.1.2.0 driver from the Ralink web-site.
Note that this driver does not support the 2.6.24-16 kernel, so yes this does not work out of the box.

Edit the rt_config.h, and add just before the last line (#endif  // __RT_CONFIG_H__):

#if (LINUX_VERSION_CODE >= KERNEL_VERSION(2,6,24))
#define SET_MODULE_OWNER(some_struct) do { } while (0)
#define dev_get_by_name(slot_name) dev_get_by_name(&init_net, slot_name)
#define first_net_device() first_net_device(&init_net)
#endif
#if (LINUX_VERSION_CODE < KERNEL_VERSION(2,6,18))
#define IRQFLAGS SA_SHIRQ
#else
#define IRQFLAGS IRQF_SHARED
#endif

Next edit the rtmp_main.c and replace the word SA_SHIRQ with IRQFLAGS - this should be on one line only:
status = request_irq(pAd->pPci_Dev->irq, &RTMPIsr, IRQFLAGS, net_dev->name, net_dev);

Now you can follow the compilation and installation exercise from Ralink's README file using the Makefile.6, but add an extra parameter on the commandline:
# make KBUILD_NOPEDANTIC=1

You should have no errors left, just a bunch of warnings at compilation time.

When using the driver, I had problems as follows:

# ifconfig ra0 up
SIOCSIFFLAGS: Invalid argument

You can work around that by adding the following to your /etc/network/interfaces:

iface ra0 inet dhcp
pre-up ifconfig ra0 hw ether XX:XX:XX:XX:XX:XX
auto ra0

Replace the  XX:XX:XX:XX:XX:XX with your MAC address of your card.

Now you should be up and running again on native Ralink, a good performing and stable driver and when you use rt61sta.dat you will not be bothered by keyrings either!

Good-luck,

Ton

---

### Post by Silent Ninja on 2008-05-02
> **deRooij said:**
> #if (LINUX_VERSION_CODE < KERNEL_VERSION(2,6,18))

This tutorial is great and actually works, the only thing is that the cool emoticon shouldn't be there, heh..

It should end with: ( 2, 6, 18 )) 
All unspaced, like the previous line.

---

### Post by zigomir on 2008-05-30
> **deRooij said:**
> 
Now you can follow the compilation and installation exercise from Ralink's README file using the Makefile.6, but add an extra parameter on the commandline:
# make KBUILD_NOPEDANTIC=1

You should have no errors left, just a bunch of warnings at compilation time.

Hi!

Tnx for helping us out, but I still get an error when making KBUILD_NOPEDANTIC=1 and even later on I can't build with make all.

At make KBUILD_NOPEDANTIC=1 I get:

> make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/home/zigomir/Desktop/2008_0506_RT61_Linux_STA_v1.1.2.1/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /home/zigomir/Desktop/2008_0506_RT61_Linux_STA_v1.1.2.1/Module/rtmp_main.o
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'


---

