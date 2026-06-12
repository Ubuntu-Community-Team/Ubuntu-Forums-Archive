---
title: "rndis wireless ASUS WL-169gE question"
date: 2008-04-08
forum: Networking &amp; Wireless
---

### Post by crazytrain1978 on 2008-04-08
Hi I am trying to compile usb  kernel modules that support rndis so that i can use ndis to install my asus wl-169ge windows wireless drivers.

there is a thread here [http://ubuntuforums.org/showthread.php?t=540942&highlight=ndiswrapperless&page=1]("http://ubuntuforums.org/showthread.php?t=540942&highlight=ndiswrapperless&page=1")

where the process is described, and i am fine getting all the necessary requirements, for this ([http://www.jooz.net/rndis/]("http://www.jooz.net/rndis/") ) but when i try and make it gives me an error i don't know what to do with.

I have tried this with both the rndis_wlan-snapshot-20071213.tar.gz and rndis_wlan-snapshot-20071220.tar.gz snapshots 

Here is the error output when trying to make.


john@linux-usb:~/Documents/rndis_wlan$ make
make -C /lib/modules/2.6.24-15-generic/build SUBDIRS=/home/john/Documents/rndis_wlan modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-15-generic'
CC [M] /home/john/Documents/rndis_wlan/usbnet.o
/home/john/Documents/rndis_wlan/usbnet.c: In function â&#8364;&#732;usbnet_probeâ&#8364;&#8482;:
/home/john/Documents/rndis_wlan/usbnet.c:1161: error: implicit declaration of function â&#8364;&#732;SET_MODULE_OWNERâ&#8364;&#8482;
make[2]: *** [/home/john/Documents/rndis_wlan/usbnet.o] Error 1
make[1]: *** [_module_/home/john/Documents/rndis_wlan] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-15-generic'
make: *** [default] Error 2
john@linux-usb:~/Documents/rndis_wlan$



does anyone know why? I am a bit lost. I am trying this to get my ASUS wl-169gE working.

if anyone has any suggestions I would be most obliged.

Cheers,
John

PS: i tried asking this question on the original thread and even bumped it a while after no responses and still no joy, so hence the separate post.

---

### Post by evilspy on 2008-04-21
If you know how to, try compile 2.6.25 kernel. It has rndis_wlan included.

---

### Post by crazytrain1978 on 2008-06-02
> **evilspy said:**
> If you know how to, try compile 2.6.25 kernel. It has rndis_wlan included.

Ok I have downloaded and compiled 2.6.25 kernel. What do I have to do next to get linux to see my rndis wl-169gE wireless usb dongle?

do I have to load the windows drivers through some sort of rndis wrapperless? or should linux (ubuntu) be able to see my usb and use it without having the windows driver?

I am not really sure what the next step is.

Cheers,
crazytrain

---

