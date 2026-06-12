---
title: "Avermedia DVB-T drivers on Ubuntu 14.04"
date: 2014-04-25
forum: Networking &amp; Wireless
---

### Post by SrP3L4 on 2014-04-25
Hi, I just upgrade to ubuntu 14.04 (kernel 3.13.0-24-generic) from 12.04 and now I can't compile Avermedia DVB-T drivers.

This is what lsusb shows:

```
luismi@luismi--Ubuntu:~$ lsusb
Bus 002 Device 003: ID 046d:c077 Logitech, Inc. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 07ca:0337 AVerMedia Technologies, Inc. A867 DVB-T dongle
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 5986:02ac Acer, Inc 
Bus 001 Device 003: ID 138a:0018 Validity Sensors, Inc. Fingerprint scanner
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

When I was in ubuntu 12.04 I followed this steps (see this thread: [http://ubuntuforums.org/showthread.php?t=1576024](http://ubuntuforums.org/showthread.php?t=1576024) ) and it works nice:

Download propietary drivers from avermedia webpage [http://avertv.avermedia.com/Support/DownloadCount.aspx?FDFId=5653](http://avertv.avermedia.com/Support/DownloadCount.aspx?FDFId=5653)

```
tar -jxf a867_drv_v1.0.29.tar.bz2
cd a867_drv_v1.0.29
patch < a867_ubuntu_12_04.patch.txt
make
make install
```

But now I get this:

```
luismi@luismi--Ubuntu:~/TDT/a867_drv_v1.0.29$ make
make -C /lib/modules/3.13.0-24-generic/source O=/lib/modules/3.13.0-24-generic/build SUBDIRS=`pwd` modules
make[1]: se ingresa al directorio «/usr/src/linux-source-3.13.0»
  CC [M]  /home/luismi/TDT/a867_drv_v1.0.29/af903x-core.o
  CC [M]  /home/luismi/TDT/a867_drv_v1.0.29/af903x-devices.o
  CC [M]  /home/luismi/TDT/a867_drv_v1.0.29/af903x-drv.o
  CC [M]  /home/luismi/TDT/a867_drv_v1.0.29/af903x-fe.o
/home/luismi/TDT/a867_drv_v1.0.29/af903x-fe.c:25:2: error: unknown type name ‘fe_bandwidth_t’
  fe_bandwidth_t current_bandwidth;
  ^
/home/luismi/TDT/a867_drv_v1.0.29/af903x-fe.c:309:12: warning: ‘struct dvb_frontend_parameters’ declared inside parameter list [enabled by default]
     struct dvb_frontend_parameters *fep)
            ^
/home/luismi/TDT/a867_drv_v1.0.29/af903x-fe.c:309:12: warning: its scope is only this definition or declaration, which is probably not what you want [enabled by default]
/home/luismi/TDT/a867_drv_v1.0.29/af903x-fe.c: In function ‘af903x_get_frontend’:
/home/luismi/TDT/a867_drv_v1.0.29/af903x-fe.c:314:24: error: dereferencing pointer to incomplete type
  memset(fep, 0, sizeof(*fep));
                        ^
/home/luismi/TDT/a867_drv_v1.0.29/af903x-fe.c:315:5: error: dereferencing pointer to incomplete type
  fep->frequency = state->current_frequency;
     ^
/home/luismi/TDT/a867_drv_v1.0.29/af903x-fe.c:316:5: error: dereferencing pointer to incomplete type
  fep->inversion = INVERSION_AUTO;
     ^
/home/luismi/TDT/a867_drv_v1.0.29/af903x-fe.c:317:5: error: dereferencing pointer to incomplete type
  fep->u.ofdm.bandwidth = state->current_bandwidth;
     ^
/home/luismi/TDT/a867_drv_v1.0.29/af903x-fe.c: At top level:
/home/luismi/TDT/a867_drv_v1.0.29/af903x-fe.c:322:12: warning: ‘struct dvb_frontend_parameters’ declared inside parameter list [enabled by default]
     struct dvb_frontend_parameters *fep)
            ^
/home/luismi/TDT/a867_drv_v1.0.29/af903x-fe.c: In function ‘af903x_set_frontend’:
/home/luismi/TDT/a867_drv_v1.0.29/af903x-fe.c:332:9: error: dereferencing pointer to incomplete type
  if( fep->frequency < A333_FREQ_MIN || fep->frequency > A333_FREQ_MAX ) {
         ^
/home/luismi/TDT/a867_drv_v1.0.29/af903x-fe.c:332:43: error: dereferencing pointer to incomplete type
  if( fep->frequency < A333_FREQ_MIN || fep->frequency > A333_FREQ_MAX ) {
                                           ^
/home/luismi/TDT/a867_drv_v1.0.29/af903x-fe.c:341:12: error: dereferencing pointer to incomplete type
  switch(fep->u.ofdm.bandwidth) {
            ^
/home/luismi/TDT/a867_drv_v1.0.29/af903x-fe.c:342:7: error: ‘BANDWIDTH_8_MHZ’ undeclared (first use in this function)
  case BANDWIDTH_8_MHZ: bw=8; break;
       ^
/home/luismi/TDT/a867_drv_v1.0.29/af903x-fe.c:342:7: note: each undeclared identifier is reported only once for each function it appears in
/home/luismi/TDT/a867_drv_v1.0.29/af903x-fe.c:343:7: error: ‘BANDWIDTH_7_MHZ’ undeclared (first use in this function)
  case BANDWIDTH_7_MHZ: bw=7; break;
       ^
/home/luismi/TDT/a867_drv_v1.0.29/af903x-fe.c:344:7: error: ‘BANDWIDTH_6_MHZ’ undeclared (first use in this function)
  case BANDWIDTH_6_MHZ: bw=6; break;
       ^
/home/luismi/TDT/a867_drv_v1.0.29/af903x-fe.c:349:11: error: dereferencing pointer to incomplete type
   bw = fep->u.ofdm.bandwidth;
           ^
/home/luismi/TDT/a867_drv_v1.0.29/af903x-fe.c:359:27: error: dereferencing pointer to incomplete type
  ch.RF_kHz           = fep->frequency / 1000;
                           ^
/home/luismi/TDT/a867_drv_v1.0.29/af903x-fe.c:363:32: error: dereferencing pointer to incomplete type
  state->current_bandwidth = fep->u.ofdm.bandwidth;
                                ^
/home/luismi/TDT/a867_drv_v1.0.29/af903x-fe.c:364:32: error: dereferencing pointer to incomplete type
  state->current_frequency = fep->frequency;
                                ^
/home/luismi/TDT/a867_drv_v1.0.29/af903x-fe.c: At top level:
/home/luismi/TDT/a867_drv_v1.0.29/af903x-fe.c:563:2: warning: initialization from incompatible pointer type [enabled by default]
  .set_frontend         = af903x_set_frontend,
  ^
/home/luismi/TDT/a867_drv_v1.0.29/af903x-fe.c:563:2: warning: (near initialization for ‘af903x_ops.set_frontend’) [enabled by default]
/home/luismi/TDT/a867_drv_v1.0.29/af903x-fe.c:564:2: warning: initialization from incompatible pointer type [enabled by default]
  .get_frontend         = af903x_get_frontend,
  ^
/home/luismi/TDT/a867_drv_v1.0.29/af903x-fe.c:564:2: warning: (near initialization for ‘af903x_ops.get_frontend’) [enabled by default]
/home/luismi/TDT/a867_drv_v1.0.29/af903x-fe.c: In function ‘af903x_monitor_thread_func’:
/home/luismi/TDT/a867_drv_v1.0.29/af903x-fe.c:691:2: error: implicit declaration of function ‘daemonize’ [-Werror=implicit-function-declaration]
  daemonize("%s", thread_name);
  ^
/home/luismi/TDT/a867_drv_v1.0.29/af903x-fe.c: At top level:
/home/luismi/TDT/a867_drv_v1.0.29/af903x-fe.c:222:12: warning: ‘af903x_set_bandwidth’ defined but not used [-Wunused-function]
 static int af903x_set_bandwidth(struct dvb_frontend *demod, u8 bw_idx)
            ^
cc1: some warnings being treated as errors
make[3]: *** [/home/luismi/TDT/a867_drv_v1.0.29/af903x-fe.o] Error 1
make[2]: *** [_module_/home/luismi/TDT/a867_drv_v1.0.29] Error 2
make[1]: *** [sub-make] Error 2
make[1]: se sale del directorio «/usr/src/linux-source-3.13.0»
make: *** [default] Error 2
```

I think maybe I need a new patch file for ubuntu 14.04 but I don't know where I can find it.

I also tried install linuxtv.org drivers but it didn't work.

Could anyone help me?

---

### Post by Yellow Pasque on 2014-04-25
You shouldn't have to compile it. The dvb-usb-af9035.ko module is supposed to support it in newer kernels.

[https://github.com/torvalds/linux/blob/master/drivers/media/usb/dvb-usb-v2/af9035.c#L1491](https://github.com/torvalds/linux/blob/master/drivers/media/usb/dvb-usb-v2/af9035.c#L1491)

---

### Post by SrP3L4 on 2014-04-28
I loaded the dvb-usb-af9035 module and I added it to /etc/modules but it doesn't work.

I remembered, when I was in 12.04, that the module name was something like 867 so I searched and I got this:
```
luismi@luismi--Ubuntu:~$ find /lib/modules/`uname -r` -type f -name "*867*.ko"
/lib/modules/3.13.0-24-generic/kernel/drivers/media/dvb/a867/a867.ko
```

then I tried this but...
```
luismi@luismi--Ubuntu:~$ sudo modprobe a867
modprobe: ERROR: could not insert 'a867': Exec format error
```

---

### Post by SrP3L4 on 2014-04-29
Thanks to this [forum]("http://translate.google.es/translate?sl=auto&tl=en&js=y&prev=_t&hl=es&ie=UTF-8&u=http%3A%2F%2Fforum.ubuntu.cz%2Findex.php%3Ftopic%3D69173.msg497156%23msg497156&edit-text=") I realize that my device ID (Bus 003 Device 003: ID 07ca:**0337** AVerMedia Technologies, Inc. A867 DVB-T dongle) is not listed in the dvb-usb-af9035.ko file. 

```
luismi@luismi--Ubuntu:~$ modinfo /lib/modules/3.13.0-24-generic/kernel/drivers/media/usb/dvb-usb-v2/dvb-usb-af9035.ko 
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/media/usb/dvb-usb-v2/dvb-usb-af9035.ko
firmware:       dvb-usb-it9135-02.fw
firmware:       dvb-usb-it9135-01.fw
firmware:       dvb-usb-af9035-02.fw
license:        GPL
description:    Afatech AF9035 driver
author:         Antti Palosaari <crope@iki.fi>
srcversion:     A07821C21D756D83EF98880
alias:          usb:v2040pF900d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0413p6A05d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CCDp0099d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B80pE410d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B80pE411d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B80pE409d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07CAp0335d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07CAp4835d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07CAp3835d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07CAp2835d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07CAp1835d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v048Dp9006d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v048Dp9005d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v048Dp9135d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CCDp00AAd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1779d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07CAp0825d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07CApA867d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07CAp1867d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07CApB835d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07CApA835d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CCDp0093d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v15A4p1003d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v15A4p1002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v15A4p1001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v15A4p1000d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v15A4p9035d*dc*dsc*dp*ic*isc*ip*in*
depends:        dvb_usb_v2,rc-core
vermagic:       3.13.0-24-generic SMP mod_unload modversions 
parm:           adapter_nr:DVB adapter numbers (array of short)

luismi@luismi--Ubuntu:~$ modinfo /lib/modules/3.13.0-24-generic/kernel/drivers/media/usb/dvb-usb-v2/dvb-usb-af9035.ko| grep 0337
```


How can I add my device id to the dvb-usb-af9035.ko file?

---

