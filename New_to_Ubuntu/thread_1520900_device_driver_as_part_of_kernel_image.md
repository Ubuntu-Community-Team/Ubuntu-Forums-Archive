---
title: "device driver as part of kernel image"
date: 2010-06-30
forum: New to Ubuntu
---

### Post by sneghu on 2010-06-30
Hi,
 
    I am using the iMX25 PDK  to which linux-2.6.31 is ported.I have developed parport_arm using GPIO pins.If I build the kernel with lp,parport and parport_arm as modules.
 
In the pdk, i will give
insmod parport.ko
insmod parport_arm.ko
insmod lp.ko
 
cat somefile > /dev/lp0 - It is working fine.
 
If I try to configure parport,parport_arm and lp as part of kernel, I can see /dev/lp0.But when I try I to print ,Its not printing.I think some dependencies are missing for these device drivers.
 
please suggest me where i am going wrong.
Regards,
sneha.

---

### Post by iponeverything on 2010-06-30
is the device being detected during boot. Check dmesg.

---

### Post by sneghu on 2010-07-01
Hi ,

  I did the dmesg.My driver was detected.I am trying to use my parallel port driver as executable image.As a module its working fine.

I tried by copying lp.c inside parport driver file and made the changes in makefile as

obj-$(CONFIG_PARPORT)            += parport.o
obj-$(CONFIG_PARPORT_ARM)    += parport_arm.o
obj-$(CONFIG_PRINTER)              += lp.o

But the priblem is still there.

Regards,
sneha

---

### Post by sneghu on 2010-07-01
Hi ,

  I did the dmesg.My driver was detected.I am trying to use my parallel port driver as executable image.As a module its working fine.

I tried by copying lp.c inside parport driver file and made the changes in makefile as

obj-$(CONFIG_PARPORT)            += parport.o
obj-$(CONFIG_PARPORT_ARM)    += parport_arm.o
obj-$(CONFIG_PRINTER)              += lp.o

But the problem is still there.

Regards,
sneha

---

