---
title: "Ralink RT3070 &quot;sudo make&quot; error"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by gannggstaz on 2009-10-30
I have an engenius EUB9706 300 mbps wireless adapter which, after calling tech support had a driver made by ralink, the ralink RT3070 driver available from ralinktech.com 
I followed the instructions and once I got to the step telling me to run ```
james@james-desktop:~/2009_0525_RT3070_Linux_STA_v2.1.1.0$ make
```it gives me the output of:
```
make -C tools
make[1]: Entering directory `/home/james/2009_0525_RT3070_Linux_STA_v2.1.1.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/james/2009_0525_RT3070_Linux_STA_v2.1.1.0/tools'
/home/james/2009_0525_RT3070_Linux_STA_v2.1.1.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/james/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/Makefile
make  -C  /lib/modules/2.6.31-14-generic/build SUBDIRS=/home/james/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/james/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/crypt_md5.o
In file included from /home/james/2009_0525_RT3070_Linux_STA_v2.1.1.0/include/rt_config.h:56,
                 from /home/james/2009_0525_RT3070_Linux_STA_v2.1.1.0/include/crypt_md5.h:35,
                 from /home/james/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/crypt_md5.c:27:
/home/james/2009_0525_RT3070_Linux_STA_v2.1.1.0/include/rtmp.h:654: error: ‘TX_RING_SIZE’ undeclared here (not in a function)
/home/james/2009_0525_RT3070_Linux_STA_v2.1.1.0/include/rtmp.h:662: error: ‘RX_RING_SIZE’ undeclared here (not in a function)
/home/james/2009_0525_RT3070_Linux_STA_v2.1.1.0/include/rtmp.h:670: error: ‘MGMT_RING_SIZE’ undeclared here (not in a function)
/home/james/2009_0525_RT3070_Linux_STA_v2.1.1.0/include/rtmp.h:728: error: ‘NUM_OF_TX_RING’ undeclared here (not in a function)
/home/james/2009_0525_RT3070_Linux_STA_v2.1.1.0/include/rtmp.h:2175: error: expected specifier-qualifier-list before ‘RTMP_INF_TYPE’
/home/james/2009_0525_RT3070_Linux_STA_v2.1.1.0/include/rtmp.h:2296: error: expected specifier-qualifier-list before ‘RTMP_INF_TYPE’
/home/james/2009_0525_RT3070_Linux_STA_v2.1.1.0/include/rtmp.h:2738: error: expected specifier-qualifier-list before ‘RT28XX_RXD_STRUC’
/home/james/2009_0525_RT3070_Linux_STA_v2.1.1.0/include/rtmp.h:3521: error: expected declaration specifiers or ‘...’ before ‘INT_SOURCE_CSR_STRUC’
/home/james/2009_0525_RT3070_Linux_STA_v2.1.1.0/include/rtmp.h:3612: error: expected declaration specifiers or ‘...’ before ‘PTXWI_STRUC’
/home/james/2009_0525_RT3070_Linux_STA_v2.1.1.0/include/rtmp.h:3632: error: expected declaration specifiers or ‘...’ before ‘PTXWI_STRUC’
/home/james/2009_0525_RT3070_Linux_STA_v2.1.1.0/include/rtmp.h:3638: error: expected declaration specifiers or ‘...’ before ‘PTXWI_STRUC’
/home/james/2009_0525_RT3070_Linux_STA_v2.1.1.0/include/rtmp.h:3677: error: expected declaration specifiers or ‘...’ before ‘PRT28XX_RXD_STRUC’
/home/james/2009_0525_RT3070_Linux_STA_v2.1.1.0/include/rtmp.h:5395: error: expected declaration specifiers or ‘...’ before ‘PRXWI_STRUC’
In file included from /home/james/2009_0525_RT3070_Linux_STA_v2.1.1.0/include/rt_config.h:56,
                 from /home/james/2009_0525_RT3070_Linux_STA_v2.1.1.0/include/crypt_md5.h:35,
                 from /home/james/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/crypt_md5.c:27:
/home/james/2009_0525_RT3070_Linux_STA_v2.1.1.0/include/rtmp.h:6322: error: expected declaration specifiers or ‘...’ before ‘PRXWI_STRUC’
/home/james/2009_0525_RT3070_Linux_STA_v2.1.1.0/include/rtmp.h:6326: error: expected declaration specifiers or ‘...’ before ‘PRT28XX_RXD_STRUC’
/home/james/2009_0525_RT3070_Linux_STA_v2.1.1.0/include/rtmp.h:6534: error: expected declaration specifiers or ‘...’ before ‘RTMP_INF_TYPE’
In file included from /home/james/2009_0525_RT3070_Linux_STA_v2.1.1.0/include/rt_config.h:57,
                 from /home/james/2009_0525_RT3070_Linux_STA_v2.1.1.0/include/crypt_md5.h:35,
                 from /home/james/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/crypt_md5.c:27:
/home/james/2009_0525_RT3070_Linux_STA_v2.1.1.0/include/ap.h:82: error: expected declaration specifiers or ‘...’ before ‘PRT28XX_RXD_STRUC’
/home/james/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/crypt_md5.c:348: fatal error: opening dependency file /home/james/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/.crypt_md5.o.d: Permission denied
compilation terminated.
make[2]: *** [/home/james/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/crypt_md5.o] Error 1
make[1]: *** [_module_/home/james/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [LINUX] Error 2
```How can i fix it?

---

