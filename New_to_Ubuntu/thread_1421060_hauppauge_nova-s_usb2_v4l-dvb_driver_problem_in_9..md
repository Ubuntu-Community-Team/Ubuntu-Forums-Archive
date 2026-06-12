---
title: "hauppauge nova-s usb2 v4l-dvb driver problem in 9.10"
date: 2010-03-03
forum: New to Ubuntu
---

### Post by Trinity33 on 2010-03-03
hi i have little problem wanted to install driver from linux-org v4l-dvb so i downloaded it hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)  then went to directory and typed make after 20 sec error #

/home/trinity/v4l-dvb/v4l/firedtv-1394.c: In function 'fdtv_1394_init':
/home/trinity/v4l-dvb/v4l/firedtv-1394.c:286: error: implicit declaration of function 'hpsb_register_highlevel'
/home/trinity/v4l-dvb/v4l/firedtv-1394.c:287: error: implicit declaration of function 'hpsb_register_protocol'
/home/trinity/v4l-dvb/v4l/firedtv-1394.c:290: error: implicit declaration of function 'hpsb_unregister_highlevel'
/home/trinity/v4l-dvb/v4l/firedtv-1394.c: In function 'fdtv_1394_exit':
/home/trinity/v4l-dvb/v4l/firedtv-1394.c:297: error: implicit declaration of function 'hpsb_unregister_protocol'
make[3]: *** [/home/trinity/v4l-dvb/v4l/firedtv-1394.o] Error 1
make[2]: *** [_module_/home/trinity/v4l-dvb/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/trinity/v4l-dvb/v4l'
make: *** [all] Error 2

so i found that there is a bug or something and i need to go to vl4 directory open .config file and change existing CONFIG_DVB_FIREDTV=m to CONFIG_DVB_FIREDTV=n in vl4 there is no file called .config there is many of them like config.compat.h or Kconfig etc etc . so i checked all of them my files are not hiden and found in config-compat.h line  CONFIG_DVB_FIREDTV without =m or =n so i dont know what to do now. cannt make this driver or install it. thanks for your help.

use ubuntu 9.10 x32 kernel 2.6.31.14generic  and hauppauge wintv nova-s usb2

---

