---
title: "ndiswrapper / make problems"
date: 2008-11-29
forum: Networking &amp; Wireless
---

### Post by HibernoS on 2008-11-29
I am trying to sort out issues with wireless connection on a new Ubuntu 8.10 install. My HP laptop is using the following:

Ethernet controller: Broadcom Corp BCM4401/B0
Network controller: Broadcom Corp BCM4311 802.11b/g

After reviewing the extensive amount of information available, I believe that the information contained in:

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper))

is the most comprehensive. Unfortunately, along the way (whilst experimenting with the numerous solutions out there), I seem to have disabled my cable-based connection to the internet as well.

Anyway, on step 3 (Prepare the Linux build environment), I come up against a build warnings (since the URLs cannot be reached). More critically, on step 5 when trying to

> make distclean

I get an error: No rule to make target 'distclean' which is listed as Error 2.

With other attempted solutions, I am coming up against Lock errors (also when I sudo as root) and overall, I am getting into a bit of a tangle. I am new to Linux, but have limited Unix knowledge from a long time ago.

---

### Post by night_fox on 2008-11-29
My dell laptop has exactly the same wireless card. It wouldn't work for me on the live-cd, but as soon as I installed it, I connected via a LAN cable and it updated the kernel and downloaded the driver for the wireless card.

Did this happen and not work? If not, find out how to get the wired internet back, then use it to download the update/driver.

Did you blacklist some stuff or remove modules? How did you stop your ethernet from working?

When you install stuff on modern Ubuntu, use Applications, then Add/Remove programs, failing thatm, Synaptic, failing that, download the .deb packages and their dependancies to a memory stick, failing that you have to install stuff from source. Building from source is unnecessarily hard.

---

### Post by Phlogiston on 2008-11-29
I can't do make:
```
~/ndiswrapper-1.53# make                                      
make -C driver                                                               
make[1]: Entering directory `/root/ndiswrapper-1.53/driver'                  
make -C /usr/src/linux-headers-2.6.27-9-generic M=/root/ndiswrapper-1.53/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'          
  CC [M]  /root/ndiswrapper-1.53/driver/iw_ndis.o                              
/root/ndiswrapper-1.53/driver/iw_ndis.c: In function 'ndis_translate_scan':    
/root/ndiswrapper-1.53/driver/iw_ndis.c:1037: warning: passing argument 1 of 'iwe_stream_add_event' from incompatible pointer type                              
/root/ndiswrapper-1.53/driver/iw_ndis.c:1037: warning: passing argument 3 of 'iwe_stream_add_event' from incompatible pointer type                              
/root/ndiswrapper-1.53/driver/iw_ndis.c:1037: warning: passing argument 4 of 'iwe_stream_add_event' makes pointer from integer without a cast                   
/root/ndiswrapper-1.53/driver/iw_ndis.c:1037: error: too few arguments to function 'iwe_stream_add_event'                                                       
/root/ndiswrapper-1.53/driver/iw_ndis.c:1047: warning: passing argument 1 of 'iwe_stream_add_point' from incompatible pointer type                              
/root/ndiswrapper-1.53/driver/iw_ndis.c:1047: warning: passing argument 3 of 'iwe_stream_add_point' from incompatible pointer type                              
/root/ndiswrapper-1.53/driver/iw_ndis.c:1047: warning: passing argument 4 of 'iwe_stream_add_point' from incompatible pointer type                              
/root/ndiswrapper-1.53/driver/iw_ndis.c:1047: error: too few arguments to function 'iwe_stream_add_point'                                                       
/root/ndiswrapper-1.53/driver/iw_ndis.c:1053: warning: passing argument 1 of 'iwe_stream_add_event' from incompatible pointer type                              
/root/ndiswrapper-1.53/driver/iw_ndis.c:1053: warning: passing argument 3 of 'iwe_stream_add_event' from incompatible pointer type                              
/root/ndiswrapper-1.53/driver/iw_ndis.c:1053: warning: passing argument 4 of 'iwe_stream_add_event' makes pointer from integer without a cast                   
/root/ndiswrapper-1.53/driver/iw_ndis.c:1053: error: too few arguments to function 'iwe_stream_add_event'                                                       
/root/ndiswrapper-1.53/driver/iw_ndis.c:1064: warning: passing argument 1 of 'iwe_stream_add_event' from incompatible pointer type                              
/root/ndiswrapper-1.53/driver/iw_ndis.c:1064: warning: passing argument 3 of 'iwe_stream_add_event' from incompatible pointer type                              
/root/ndiswrapper-1.53/driver/iw_ndis.c:1064: warning: passing argument 4 of 'iwe_stream_add_event' makes pointer from integer without a cast                   
/root/ndiswrapper-1.53/driver/iw_ndis.c:1064: error: too few arguments to function 'iwe_stream_add_event'                                                       
/root/ndiswrapper-1.53/driver/iw_ndis.c:1079: warning: passing argument 1 of 'iwe_stream_add_event' from incompatible pointer type                              
/root/ndiswrapper-1.53/driver/iw_ndis.c:1079: warning: passing argument 3 of 'iwe_stream_add_event' from incompatible pointer type                              
/root/ndiswrapper-1.53/driver/iw_ndis.c:1079: warning: passing argument 4 of 'iwe_stream_add_event' makes pointer from integer without a cast                   
/root/ndiswrapper-1.53/driver/iw_ndis.c:1079: error: too few arguments to function 'iwe_stream_add_event'                                                       
/root/ndiswrapper-1.53/driver/iw_ndis.c:1093: warning: passing argument 1 of 'iwe_stream_add_event' from incompatible pointer type                              
/root/ndiswrapper-1.53/driver/iw_ndis.c:1093: warning: passing argument 3 of 'iwe_stream_add_event' from incompatible pointer type                              
/root/ndiswrapper-1.53/driver/iw_ndis.c:1093: warning: passing argument 4 of 'iwe_stream_add_event' makes pointer from integer without a cast                   
/root/ndiswrapper-1.53/driver/iw_ndis.c:1093: error: too few arguments to function 'iwe_stream_add_event'                                                       
/root/ndiswrapper-1.53/driver/iw_ndis.c:1104: warning: passing argument 1 of 'iwe_stream_add_point' from incompatible pointer type                              
/root/ndiswrapper-1.53/driver/iw_ndis.c:1104: warning: passing argument 3 of 'iwe_stream_add_point' from incompatible pointer type                              
/root/ndiswrapper-1.53/driver/iw_ndis.c:1104: warning: passing argument 4 of 'iwe_stream_add_point' from incompatible pointer type                              
/root/ndiswrapper-1.53/driver/iw_ndis.c:1104: error: too few arguments to function 'iwe_stream_add_point'                                                       
/root/ndiswrapper-1.53/driver/iw_ndis.c:1120: warning: passing argument 1 of 'iwe_stream_add_value' from incompatible pointer type                              
/root/ndiswrapper-1.53/driver/iw_ndis.c:1120: warning: passing argument 4 of 'iwe_stream_add_value' from incompatible pointer type
/root/ndiswrapper-1.53/driver/iw_ndis.c:1120: warning: passing argument 5 of 'iwe_stream_add_value' makes pointer from integer without a cast
/root/ndiswrapper-1.53/driver/iw_ndis.c:1120: error: too few arguments to function 'iwe_stream_add_value'
/root/ndiswrapper-1.53/driver/iw_ndis.c:1131: warning: passing argument 1 of 'iwe_stream_add_point' from incompatible pointer type
/root/ndiswrapper-1.53/driver/iw_ndis.c:1131: warning: passing argument 3 of 'iwe_stream_add_point' from incompatible pointer type
/root/ndiswrapper-1.53/driver/iw_ndis.c:1131: warning: passing argument 4 of 'iwe_stream_add_point' from incompatible pointer type
/root/ndiswrapper-1.53/driver/iw_ndis.c:1131: error: too few arguments to function 'iwe_stream_add_point'
/root/ndiswrapper-1.53/driver/iw_ndis.c:1137: warning: passing argument 1 of 'iwe_stream_add_point' from incompatible pointer type
/root/ndiswrapper-1.53/driver/iw_ndis.c:1137: warning: passing argument 3 of 'iwe_stream_add_point' from incompatible pointer type
/root/ndiswrapper-1.53/driver/iw_ndis.c:1137: warning: passing argument 4 of 'iwe_stream_add_point' from incompatible pointer type
/root/ndiswrapper-1.53/driver/iw_ndis.c:1137: error: too few arguments to function 'iwe_stream_add_point'
/root/ndiswrapper-1.53/driver/iw_ndis.c:1159: warning: passing argument 1 of 'iwe_stream_add_point' from incompatible pointer type
/root/ndiswrapper-1.53/driver/iw_ndis.c:1159: warning: passing argument 3 of 'iwe_stream_add_point' from incompatible pointer type
/root/ndiswrapper-1.53/driver/iw_ndis.c:1159: warning: passing argument 4 of 'iwe_stream_add_point' from incompatible pointer type
/root/ndiswrapper-1.53/driver/iw_ndis.c:1159: error: too few arguments to function 'iwe_stream_add_point'
make[3]: *** [/root/ndiswrapper-1.53/driver/iw_ndis.o] Error 1
make[2]: *** [_module_/root/ndiswrapper-1.53/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/root/ndiswrapper-1.53/driver'
make: *** [all] Error 2

```

---

### Post by HibernoS on 2008-11-29
It transpired that ndiswrapper itself was not the source of my problems, but rather the actual Broadcom driver itself. Of the many sources of information that I reviewed, I found this one to be the most helpful:

[http://penkin.wordpress.com/2008/03/28/ubuntu-804-broadcom-wireless/](http://penkin.wordpress.com/2008/03/28/ubuntu-804-broadcom-wireless/)

although I appreciate that this won't be a one-size-fits-all solution. Without having access to a second machine with a functionning internet connection, this would have been a non-starter obviously.

Thanks for your responses and good luck to all my fellow Ubuntu newbies trying to wireless up and running! It's not an easy task (unfortunately), but there's plenty of help out there and you'll get there in the end.

---

### Post by Ayuthia on 2008-11-29
The 4311 card also has another option which is to use the Broadcom STA driver (wl).  It could be found under System->Administration->Hardware Drivers.  That one does not require any downloads.

---

