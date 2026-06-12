---
title: "Ubuntu 12.04, Kernel 3.13.0-71-generic. Problem with drivers for MOXA UPort 1150"
date: 2015-12-31
forum: Networking &amp; Wireless
---

### Post by frostyland on 2015-12-31
Hi there!
Can not install drivers for USB/Serial Moxa UPort 1150.

[FONT=courier]make install[/FONT] generates errors

```
/home/valerius/Moxa/driver/mxu11x0.c:292:13: error: ‘usb_serial_probe’ undeclared here (not in a function)
/home/valerius/Moxa/driver/mxu11x0.c:293:17: error: ‘usb_serial_disconnect’ undeclared here (not in a function)
```

The fact is Makefile has no information about kernels above 2.6, just


```
    @echo "  *******************************************************************"
    @echo "  # MOXA UPort 1110/1130/1150/1150I USB to Serial Hub Driver v$(DRV_VER) #"
    @echo "  #                for Linux Kernel 2.6.x                           #"
    @echo "  #                                                                 #"
    @echo "  #               release date : $(REL_DATE)                         #"
    @echo "  *******************************************************************"
```

Driver pack has downloaded from official site and is correct.
Does anyone has solutions?

Best regards, Valery

---

### Post by chili555 on 2015-12-31
I believe that in later Ubuntu versions, those including kernel version 3.16 and later, that your device is covered by the module *mxuport*. I suggest you upgrade to 14.04.3 LTS. You can try the live session USB or DVD to make sure.

---

