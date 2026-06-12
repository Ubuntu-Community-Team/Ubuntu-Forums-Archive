---
title: "AWUS036H Driver in Ubuntu 16.10???"
date: 2016-10-26
forum: Networking &amp; Wireless
---

### Post by ocp2k on 2016-10-26
Hi!

I downloaded the last AWUS036H Driver from Alfa Network web, a tar file.
Extracted, and made a make in a terminal and this is the result:

> 
ocp2k@ocp2k-MS-7978:~/Descargas/Drivers Wifi/AWUS036H$ make
make[1]: se entra en el directorio '/usr/src/linux-headers-4.8.0-22-generic'
arch/x86/Makefile:140: CONFIG_X86_X32 enabled but no binutils support
make[1]: *** No hay ninguna regla para construir el objetivo 'Wifi/AWUS036H/rtl8187'.  Alto.
make[1]: se sale del directorio '/usr/src/linux-headers-4.8.0-22-generic'
Makefile:15: fallo en las instrucciones para el objetivo 'all'
make: *** [all] Error 2
ocp2k@ocp2k-MS-7978:~/Descargas/Drivers Wifi/AWUS036H$ 


Can you helpme?

Thx!

---

### Post by chili555 on 2016-10-26
Please see my comment to your question at askubuntu.> ocp2k@ocp2k-MS-7978:~/Descargas/Drivers Wifi/AWUS036H

The command *make* doesn't like spaces in the name. Please try renaming the folder to:```
Drivers_Wifi
```Or something with no spaces. Then try the make, sudo make install sequence again.

As well, the driver rtl8187 already exists in Ubuntu 16.04. Installing a different, probably older, driver will not solve any problem.

---

### Post by ocp2k on 2016-10-29
> **chili555 said:**
> Please see my comment to your question at askubuntu.

The command *make* doesn't like spaces in the name. Please try renaming the folder to:```
Drivers_Wifi
```Or something with no spaces. Then try the make, sudo make install sequence again.

As well, the driver rtl8187 already exists in Ubuntu 16.04. Installing a different, probably older, driver will not solve any problem.

Hi, thanks for your answer and your time.

I copied the folder to the desktop and this is the answer after a make.

> ocp2k@ocp2k-MS-7978:~/Escritorio/AWUS036H$ make
make[1]: se entra en el directorio '/usr/src/linux-headers-4.8.0-26-generic'
  CC [M]  /home/ocp2k/Escritorio/AWUS036H/rtl8187/r8187_core.o
/home/ocp2k/Escritorio/AWUS036H/rtl8187/r8187_core.c:149:22: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘rtl8187_usb_probe’
 static int __devinit rtl8187_usb_probe(struct usb_interface *intf,
                      ^~~~~~~~~~~~~~~~~
/home/ocp2k/Escritorio/AWUS036H/rtl8187/r8187_core.c:151:23: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘rtl8187_usb_disconnect’
 static void __devexit rtl8187_usb_disconnect(struct usb_interface *intf);
                       ^~~~~~~~~~~~~~~~~~~~~~
/home/ocp2k/Escritorio/AWUS036H/rtl8187/r8187_core.c:164:12: error: ‘rtl8187_usb_probe’ undeclared here (not in a function)
  .probe  = rtl8187_usb_probe,
            ^~~~~~~~~~~~~~~~~
/home/ocp2k/Escritorio/AWUS036H/rtl8187/r8187_core.c:165:16: error: ‘rtl8187_usb_disconnect’ undeclared here (not in a function)
  .disconnect = rtl8187_usb_disconnect,
                ^~~~~~~~~~~~~~~~~~~~~~
/home/ocp2k/Escritorio/AWUS036H/rtl8187/r8187_core.c: In function ‘rtl8180_proc_module_init’:
/home/ocp2k/Escritorio/AWUS036H/rtl8187/r8187_core.c:423:15: error: implicit declaration of function ‘create_proc_entry’ [-Werror=implicit-function-declaration]
  rtl8180_proc=create_proc_entry(RTL8187_MODULE_NAME, S_IFDIR, init_net.proc_net);
               ^~~~~~~~~~~~~~~~~
/home/ocp2k/Escritorio/AWUS036H/rtl8187/r8187_core.c:423:14: warning: assignment makes pointer from integer without a cast [-Wint-conversion]
  rtl8180_proc=create_proc_entry(RTL8187_MODULE_NAME, S_IFDIR, init_net.proc_net);
              ^
/home/ocp2k/Escritorio/AWUS036H/rtl8187/r8187_core.c: In function ‘rtl8180_proc_init_one’:
/home/ocp2k/Escritorio/AWUS036H/rtl8187/r8187_core.c:457:16: warning: assignment makes pointer from integer without a cast [-Wint-conversion]
  priv->dir_dev = create_proc_entry(dev->name, 
                ^
/home/ocp2k/Escritorio/AWUS036H/rtl8187/r8187_core.c:475:6: error: implicit declaration of function ‘create_proc_read_entry’ [-Werror=implicit-function-declaration]
  e = create_proc_read_entry("stats-rx", S_IFREG | S_IRUGO,
      ^~~~~~~~~~~~~~~~~~~~~~
/home/ocp2k/Escritorio/AWUS036H/rtl8187/r8187_core.c:475:4: warning: assignment makes pointer from integer without a cast [-Wint-conversion]
  e = create_proc_read_entry("stats-rx", S_IFREG | S_IRUGO,
    ^
/home/ocp2k/Escritorio/AWUS036H/rtl8187/r8187_core.c:485:4: warning: assignment makes pointer from integer without a cast [-Wint-conversion]
  e = create_proc_read_entry("stats-tx", S_IFREG | S_IRUGO,
    ^
/home/ocp2k/Escritorio/AWUS036H/rtl8187/r8187_core.c:514:4: warning: assignment makes pointer from integer without a cast [-Wint-conversion]
  e = create_proc_read_entry("registers", S_IFREG | S_IRUGO,
    ^
/home/ocp2k/Escritorio/AWUS036H/rtl8187/r8187_core.c: In function ‘rtl8180_tx’:
/home/ocp2k/Escritorio/AWUS036H/rtl8187/r8187_core.c:1378:12: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
  u8 seg = ((u32)txbuf % 4);
            ^
/home/ocp2k/Escritorio/AWUS036H/rtl8187/r8187_core.c: In function ‘rtl8187_usb_initendpoints’:
/home/ocp2k/Escritorio/AWUS036H/rtl8187/r8187_core.c:1584:14: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
   seg_size = (u32)ptrcontext->transfer_buffer % 4;
              ^
/home/ocp2k/Escritorio/AWUS036H/rtl8187/r8187_core.c: At top level:
/home/ocp2k/Escritorio/AWUS036H/rtl8187/r8187_core.c:3755:22: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘rtl8187_usb_probe’
 static int __devinit rtl8187_usb_probe(struct usb_interface *intf,
                      ^~~~~~~~~~~~~~~~~
/home/ocp2k/Escritorio/AWUS036H/rtl8187/r8187_core.c:3855:23: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘rtl8187_usb_disconnect’
 static void __devexit rtl8187_usb_disconnect(struct usb_interface *intf)
                       ^~~~~~~~~~~~~~~~~~~~~~
/home/ocp2k/Escritorio/AWUS036H/rtl8187/r8187_core.c:3357:13: warning: ‘r8180_set_multicast’ defined but not used [-Wunused-function]
 static void r8180_set_multicast(struct net_device *dev)
             ^~~~~~~~~~~~~~~~~~~
/home/ocp2k/Escritorio/AWUS036H/rtl8187/r8187_core.c:3151:33: warning: ‘rtl8180_stats’ defined but not used [-Wunused-function]
 static struct net_device_stats *rtl8180_stats(struct net_device *dev)
                                 ^~~~~~~~~~~~~
cc1: some warnings being treated as errors
scripts/Makefile.build:289: fallo en las instrucciones para el objetivo '/home/ocp2k/Escritorio/AWUS036H/rtl8187/r8187_core.o'
make[2]: *** [/home/ocp2k/Escritorio/AWUS036H/rtl8187/r8187_core.o] Error 1
Makefile:1489: fallo en las instrucciones para el objetivo '_module_/home/ocp2k/Escritorio/AWUS036H/rtl8187'
make[1]: *** [_module_/home/ocp2k/Escritorio/AWUS036H/rtl8187] Error 2
make[1]: se sale del directorio '/usr/src/linux-headers-4.8.0-26-generic'
Makefile:15: fallo en las instrucciones para el objetivo 'all'
make: *** [all] Error 2
ocp2k@ocp2k-MS-7978:~/Escritorio/AWUS036H$ 


About the driver, i suppose, that the driver is newest than the ubuntu 16.10, i downloaded the driver from the Alfa webpage.

In Windows 7, the signal with this new drivers, the signal it's about 20% stronger.

---

### Post by chili555 on 2016-10-29
> About the driver, i suppose, that the driver is newest than the ubuntu 16.10I don't think so; this is from the Release Notes in the file you downloaded:> 
-------------------------------------
Wireless LAN Linux driver for RTL8187
-------------------------------------
Release date = [COLOR="#FF0000"]2010-08-20[/COLOR]
Operating system release = REDHAT 9/OPENSUSE 11/ubuntu9.04/ubuntu9.10/ubuntu10.04
Kernel version = 2.4.20-8smp/2.4.31/2.6.25.5-1/2.6.28/2.6.31/2.6.35-1
Release driver version = 1040.0820.2010
Change history = 1. fix the wep challenge text overflow.
		 2. Update to [COLOR="#FF0000"]kernel 2.6.35-1[/COLOR]


That is not just old; it's very, very old.

So, is your concern just the signal strength?

---

