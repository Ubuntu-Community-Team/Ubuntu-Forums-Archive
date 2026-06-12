---
title: "orinoco monitor mode 0.13e driver wont compile"
date: 2006-10-15
forum: Networking &amp; Wireless
---

### Post by skynet01 on 2006-10-15
running ubuntu 6.06 (kernel 2.6.15) . With built in orinoco card firmware 8.10 so i can use 0.15 driver. I tried 0.13e-sn12 all the way to the latest one, when i try to make the driver i get this :

root@Laptop:/orinoco/orinoco-0.13e-SN-12# make
make -C /lib/modules/2.6.15-27-686/build SUBDIRS=/orinoco/orinoco-0.13e-SN-12 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-27-686'
  CC [M]  /orinoco/orinoco-0.13e-SN-12/hermes.o
  CC [M]  /orinoco/orinoco-0.13e-SN-12/orinoco.o
  CC [M]  /orinoco/orinoco-0.13e-SN-12/orinoco_cs.o
/orinoco/orinoco-0.13e-SN-12/orinoco_cs.c: In function ‘orinoco_cs_attach’:
/orinoco/orinoco-0.13e-SN-12/orinoco_cs.c:249: warning: assignment from incompatible pointer type
/orinoco/orinoco-0.13e-SN-12/orinoco_cs.c:196: warning: unused variable ‘ret’
/orinoco/orinoco-0.13e-SN-12/orinoco_cs.c: In function ‘orinoco_cs_detach’:
/orinoco/orinoco-0.13e-SN-12/orinoco_cs.c:284: warning: implicit declaration of function ‘dev_to_instance’
/orinoco/orinoco-0.13e-SN-12/orinoco_cs.c:284: warning: initialization makes pointer from integer without a cast
/orinoco/orinoco-0.13e-SN-12/orinoco_cs.c: In function ‘orinoco_cs_event’:
/orinoco/orinoco-0.13e-SN-12/orinoco_cs.c:611: warning: initialization makes pointer from integer without a cast
/orinoco/orinoco-0.13e-SN-12/orinoco_cs.c: At top level:
/orinoco/orinoco-0.13e-SN-12/orinoco_cs.c:768: error: unknown field ‘probe’ specified in initializer
/orinoco/orinoco-0.13e-SN-12/orinoco_cs.c:768: warning: excess elements in struct initializer
/orinoco/orinoco-0.13e-SN-12/orinoco_cs.c:768: warning: (near initialization for ‘orinoco_driver’)
/orinoco/orinoco-0.13e-SN-12/orinoco_cs.c:769: error: unknown field ‘suspend’ specified in initializer
/orinoco/orinoco-0.13e-SN-12/orinoco_cs.c:769: warning: excess elements in struct initializer
/orinoco/orinoco-0.13e-SN-12/orinoco_cs.c:769: warning: (near initialization for ‘orinoco_driver’)
/orinoco/orinoco-0.13e-SN-12/orinoco_cs.c:770: error: unknown field ‘resume’ specified in initializer
/orinoco/orinoco-0.13e-SN-12/orinoco_cs.c:770: warning: excess elements in struct initializer
/orinoco/orinoco-0.13e-SN-12/orinoco_cs.c:770: warning: (near initialization for ‘orinoco_driver’)
/orinoco/orinoco-0.13e-SN-12/orinoco_cs.c:772: error: unknown field ‘remove’ specified in initializer
/orinoco/orinoco-0.13e-SN-12/orinoco_cs.c:772: warning: excess elements in struct initializer
/orinoco/orinoco-0.13e-SN-12/orinoco_cs.c:772: warning: (near initialization for ‘orinoco_driver’)
/orinoco/orinoco-0.13e-SN-12/orinoco_cs.c: In function ‘exit_orinoco_cs’:
/orinoco/orinoco-0.13e-SN-12/orinoco_cs.c:813: warning: passing argument 1 of ‘orinoco_cs_detach’ from incompatible pointer type
make[2]: *** [/orinoco/orinoco-0.13e-SN-12/orinoco_cs.o] Error 1
make[1]: *** [_module_/orinoco/orinoco-0.13e-SN-12] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-27-686'
make: *** [modules] Error 2


Thanks for the help !

---

### Post by skynet01 on 2006-10-15
bumpety bump bump .. ..anyone ?

---

### Post by tturrisi on 2006-10-16
What's the exact wlan device you have?  The orinoco driver works with several different chipsets and firmware, but getting monitor mode to work w/ orinoco requires certain chipsets.  Monitor mode support is broken in the newer orinoco drivers and to get it to work you will need a patched driver, but it is still hit or miss depending on the chipset you have.  You may have to downgrade the 8.10 firmware (flash the card to one of the 7.x versions).
[http://www.kismetwireless.net/HOWTO-orinoco-drivers.txt](http://www.kismetwireless.net/HOWTO-orinoco-drivers.txt)

---

### Post by skynet01 on 2006-10-18
thanks for the reply tturrisi. I have Hermes I chipset. Unfortunatly i cant downgrade the firmware since i dont have windowns on that laptop and it's an internal card. I know my firmware is not supported by the newer 0.15 drivers .. but they are not compiling either ... 

thanks!

---

