---
title: "ndiswrapper won't install at all"
date: 2008-11-26
forum: Networking &amp; Wireless
---

### Post by Nikmaster0 on 2008-11-26
I am new to Linux and I can't get past the part to install Ndiswrapper. I also have the problem that all the additional programs added by the package manager, starts, then immediately quits.
Here is the code, that I use to unpack ndiswrapper and install it.
```
tar zxvf ndiswrapper-1.53.tar.gz

``` 
After that, I cd the directory to ndiswrapper-1.53 and it switches. This is what I use to install it.(I am logged in under root using sudo -s.)
```
make uninstall
```
Results:
```
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.

```
```
make
```
Results:
```
make -C driver
make[1]: Entering directory `/home/nikmaster0/ndiswrapper-1.53/driver'
make -C /usr/src/linux-headers-2.6.27-7-generic M=/home/nikmaster0/ndiswrapper-1.53/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  LD      /home/nikmaster0/ndiswrapper-1.53/driver/built-in.o
  MKEXPORT /home/nikmaster0/ndiswrapper-1.53/driver/crt_exports.h
  MKEXPORT /home/nikmaster0/ndiswrapper-1.53/driver/hal_exports.h
  MKEXPORT /home/nikmaster0/ndiswrapper-1.53/driver/ndis_exports.h
  MKEXPORT /home/nikmaster0/ndiswrapper-1.53/driver/ntoskernel_exports.h
  MKEXPORT /home/nikmaster0/ndiswrapper-1.53/driver/ntoskernel_io_exports.h
  MKEXPORT /home/nikmaster0/ndiswrapper-1.53/driver/rtl_exports.h
  MKEXPORT /home/nikmaster0/ndiswrapper-1.53/driver/usb_exports.h
  CC [M]  /home/nikmaster0/ndiswrapper-1.53/driver/crt.o
  CC [M]  /home/nikmaster0/ndiswrapper-1.53/driver/hal.o
  CC [M]  /home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.o
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c: In function ‘ndis_translate_scan’:
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1037: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1037: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1037: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1037: error: too few arguments to function ‘iwe_stream_add_event’
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1047: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1047: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1047: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1047: error: too few arguments to function ‘iwe_stream_add_point’
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1053: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1053: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1053: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1053: error: too few arguments to function ‘iwe_stream_add_event’
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1064: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1064: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1064: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1064: error: too few arguments to function ‘iwe_stream_add_event’
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1079: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1079: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1079: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1079: error: too few arguments to function ‘iwe_stream_add_event’
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1093: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1093: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1093: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1093: error: too few arguments to function ‘iwe_stream_add_event’
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1104: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1104: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1104: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1104: error: too few arguments to function ‘iwe_stream_add_point’
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1120: warning: passing argument 1 of ‘iwe_stream_add_value’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1120: warning: passing argument 4 of ‘iwe_stream_add_value’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1120: warning: passing argument 5 of ‘iwe_stream_add_value’ makes pointer from integer without a cast
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1120: error: too few arguments to function ‘iwe_stream_add_value’
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1131: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1131: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1131: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1131: error: too few arguments to function ‘iwe_stream_add_point’
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1137: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1137: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1137: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1137: error: too few arguments to function ‘iwe_stream_add_point’
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1159: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1159: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1159: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1159: error: too few arguments to function ‘iwe_stream_add_point’
make[3]: *** [/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.o] Error 1
make[2]: *** [_module_/home/nikmaster0/ndiswrapper-1.53/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/nikmaster0/ndiswrapper-1.53/driver'
make: *** [all] Error 2

```
```
make install
```
Results:
```
make -C driver install
make[1]: Entering directory `/home/nikmaster0/ndiswrapper-1.53/driver'
make -C /usr/src/linux-headers-2.6.27-7-generic M=/home/nikmaster0/ndiswrapper-1.53/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.o
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c: In function ‘ndis_translate_scan’:
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1037: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1037: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1037: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1037: error: too few arguments to function ‘iwe_stream_add_event’
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1047: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1047: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1047: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1047: error: too few arguments to function ‘iwe_stream_add_point’
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1053: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1053: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1053: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1053: error: too few arguments to function ‘iwe_stream_add_event’
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1064: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1064: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1064: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1064: error: too few arguments to function ‘iwe_stream_add_event’
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1079: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1079: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1079: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1079: error: too few arguments to function ‘iwe_stream_add_event’
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1093: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1093: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1093: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1093: error: too few arguments to function ‘iwe_stream_add_event’
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1104: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1104: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1104: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1104: error: too few arguments to function ‘iwe_stream_add_point’
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1120: warning: passing argument 1 of ‘iwe_stream_add_value’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1120: warning: passing argument 4 of ‘iwe_stream_add_value’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1120: warning: passing argument 5 of ‘iwe_stream_add_value’ makes pointer from integer without a cast
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1120: error: too few arguments to function ‘iwe_stream_add_value’
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1131: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1131: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1131: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1131: error: too few arguments to function ‘iwe_stream_add_point’
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1137: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1137: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1137: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1137: error: too few arguments to function ‘iwe_stream_add_point’
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1159: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1159: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1159: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1159: error: too few arguments to function ‘iwe_stream_add_point’
make[3]: *** [/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.o] Error 1
make[2]: *** [_module_/home/nikmaster0/ndiswrapper-1.53/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/nikmaster0/ndiswrapper-1.53/driver'
make: *** [install] Error 2

```
But when I type ndiswrapper, I get:
```
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found

```
What am I doing wrong?

---

### Post by Ayuthia on 2008-11-26
> **Nikmaster0 said:**
> I am new to Linux and I can't get past the part to install Ndiswrapper. I also have the problem that all the additional programs added by the package manager, starts, then immediately quits.
Here is the code, that I use to unpack ndiswrapper and install it.
```
tar zxvf ndiswrapper-1.53.tar.gz

``` 
After that, I cd the directory to ndiswrapper-1.53 and it switches. This is what I use to install it.(I am logged in under root using sudo -s.)
```
make uninstall
```
Results:
```
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.

```
```
make
```
Results:
```
make -C driver
make[1]: Entering directory `/home/nikmaster0/ndiswrapper-1.53/driver'
make -C /usr/src/linux-headers-2.6.27-7-generic M=/home/nikmaster0/ndiswrapper-1.53/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  LD      /home/nikmaster0/ndiswrapper-1.53/driver/built-in.o
  MKEXPORT /home/nikmaster0/ndiswrapper-1.53/driver/crt_exports.h
  MKEXPORT /home/nikmaster0/ndiswrapper-1.53/driver/hal_exports.h
  MKEXPORT /home/nikmaster0/ndiswrapper-1.53/driver/ndis_exports.h
  MKEXPORT /home/nikmaster0/ndiswrapper-1.53/driver/ntoskernel_exports.h
  MKEXPORT /home/nikmaster0/ndiswrapper-1.53/driver/ntoskernel_io_exports.h
  MKEXPORT /home/nikmaster0/ndiswrapper-1.53/driver/rtl_exports.h
  MKEXPORT /home/nikmaster0/ndiswrapper-1.53/driver/usb_exports.h
  CC [M]  /home/nikmaster0/ndiswrapper-1.53/driver/crt.o
  CC [M]  /home/nikmaster0/ndiswrapper-1.53/driver/hal.o
  CC [M]  /home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.o
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c: In function ‘ndis_translate_scan’:
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1037: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1037: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1037: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1037: error: too few arguments to function ‘iwe_stream_add_event’
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1047: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1047: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1047: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1047: error: too few arguments to function ‘iwe_stream_add_point’
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1053: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1053: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1053: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1053: error: too few arguments to function ‘iwe_stream_add_event’
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1064: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1064: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1064: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1064: error: too few arguments to function ‘iwe_stream_add_event’
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1079: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1079: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1079: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1079: error: too few arguments to function ‘iwe_stream_add_event’
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1093: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1093: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1093: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1093: error: too few arguments to function ‘iwe_stream_add_event’
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1104: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1104: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1104: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1104: error: too few arguments to function ‘iwe_stream_add_point’
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1120: warning: passing argument 1 of ‘iwe_stream_add_value’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1120: warning: passing argument 4 of ‘iwe_stream_add_value’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1120: warning: passing argument 5 of ‘iwe_stream_add_value’ makes pointer from integer without a cast
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1120: error: too few arguments to function ‘iwe_stream_add_value’
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1131: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1131: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1131: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1131: error: too few arguments to function ‘iwe_stream_add_point’
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1137: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1137: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1137: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1137: error: too few arguments to function ‘iwe_stream_add_point’
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1159: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1159: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1159: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1159: error: too few arguments to function ‘iwe_stream_add_point’
make[3]: *** [/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.o] Error 1
make[2]: *** [_module_/home/nikmaster0/ndiswrapper-1.53/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/nikmaster0/ndiswrapper-1.53/driver'
make: *** [all] Error 2

```
```
make install
```
Results:
```
make -C driver install
make[1]: Entering directory `/home/nikmaster0/ndiswrapper-1.53/driver'
make -C /usr/src/linux-headers-2.6.27-7-generic M=/home/nikmaster0/ndiswrapper-1.53/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.o
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c: In function ‘ndis_translate_scan’:
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1037: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1037: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1037: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1037: error: too few arguments to function ‘iwe_stream_add_event’
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1047: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1047: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1047: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1047: error: too few arguments to function ‘iwe_stream_add_point’
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1053: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1053: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1053: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1053: error: too few arguments to function ‘iwe_stream_add_event’
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1064: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1064: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1064: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1064: error: too few arguments to function ‘iwe_stream_add_event’
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1079: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1079: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1079: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1079: error: too few arguments to function ‘iwe_stream_add_event’
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1093: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1093: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1093: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1093: error: too few arguments to function ‘iwe_stream_add_event’
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1104: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1104: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1104: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1104: error: too few arguments to function ‘iwe_stream_add_point’
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1120: warning: passing argument 1 of ‘iwe_stream_add_value’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1120: warning: passing argument 4 of ‘iwe_stream_add_value’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1120: warning: passing argument 5 of ‘iwe_stream_add_value’ makes pointer from integer without a cast
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1120: error: too few arguments to function ‘iwe_stream_add_value’
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1131: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1131: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1131: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1131: error: too few arguments to function ‘iwe_stream_add_point’
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1137: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1137: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1137: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1137: error: too few arguments to function ‘iwe_stream_add_point’
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1159: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1159: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1159: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c:1159: error: too few arguments to function ‘iwe_stream_add_point’
make[3]: *** [/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.o] Error 1
make[2]: *** [_module_/home/nikmaster0/ndiswrapper-1.53/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/nikmaster0/ndiswrapper-1.53/driver'
make: *** [install] Error 2

```
But when I type ndiswrapper, I get:
```
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found

```
What am I doing wrong?

There is a [patch]("http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=6115739&postcount=3") that needs to be applied to the code to allow it to compile in 2.6.27.  If you have the install CD, ndiswrapper is on there.  Just add the cd to the list of repositories:
```
sudo apt-cdrom add
```It will ask you for the CD.  Once that is done:
```
sudo apt-get update
sudo apt-get install ndiswrapper-utils-1.9
```

---

### Post by Nikmaster0 on 2008-11-26
do i just install as usual after that or where is ndiswrapper on the cd?
EDIT: I don't know what to do....can you explain it to me....what exactly need to do, sorry, I'm new to linux.

---

### Post by Ayuthia on 2008-11-26
You should be able to find it in /media/cdrom/pool/main/n/ndiswrapper (the /media/cdrom portion may be different for you.  I am currently in Arch.  The /pool/main/n/ndiswrapper portion is the same).  However, if you do the commands in my earlier post, it will install ndiswrapper so you won't need to compile.  You can proceed with getting your Windows driver and doing the ndiswrapper -i commands.

---

### Post by Nikmaster0 on 2008-11-26
i installed the utils....and it still says that the ndiswrapper is not installed....do I need a different ndiswrapper command to run it.

---

### Post by Skripka on 2008-11-26
> **Nikmaster0 said:**
> i installed the utils....and it still says that the ndiswrapper is not installed....do I need a different ndiswrapper command to run it.

Ndiswrapper should be on the CD, throw it in the CD drive, fire up Synaptic, add the CD to Synaptic---search for it and BAM, as they say.


OR-

If you are on Intrepid Ibex and have a wired internet connection, you can get Ndiswrapper right off the repos through synaptic.

---

### Post by Ayuthia on 2008-11-26
> **Nikmaster0 said:**
> i installed the utils....and it still says that the ndiswrapper is not installed....do I need a different ndiswrapper command to run it.

You might check and see if ndiswrapper-common is installed.  If it is not, it needs to be.  I was thinking that if you did apt-get install ndiswrapper-utils-1.9 would install ndiswrapper-common automatically.

If you like a graphical version, you can also include ndisgtk.

---

### Post by Nikmaster0 on 2008-11-26
ok...I tried the graphical version, that's when it starts, then quits. I said something about that....lol.I'll try to install common. I get ```
E: Couldn't find package ndiswrapper-common.
```. What do I do now?

---

### Post by Ayuthia on 2008-11-26
> **Nikmaster0 said:**
> ok...I tried the graphical version, that's when it starts, then quits. I said something about that....lol.I'll try to install common. I get ```
E: Couldn't find package ndiswrapper-common.
```. What do I do now?

How are you installing ndiswrapper?  Are you just clicking on the icon on the cd or did you add the cd to the repository?

Are you able to find it on the cd?  If so, it might just be easier to just click on the ndiswrapper-common icon there so that it will install it.  ndiswrapper-common is in the same location as ndiswrapper-utils-1.9.

---

### Post by Nikmaster0 on 2008-11-26
where would that be? and I am using the Terminal, I can't find the icon in the Package Manager to install Ndiswrapper at all. I did add the cd to repos.

---

### Post by Nikmaster0 on 2008-11-26
I found all three, graphical, and the common and utils in the package manager. I was looking in the wrong place. but when I tried to use the graphical, I get ```
Module could not be loaded. Error was: WARNING: /etc/modprobe.d/blacklist line 50: ignoring bad line starting with "ndiswrapper" FATAL: Module ndiswrapper not found. Is the ndiswrapper module installed?
```

---

### Post by Ayuthia on 2008-11-26
> **Nikmaster0 said:**
> where would that be? and I am using the Terminal, I can't find the icon in the Package Manager to install Ndiswrapper at all. I did add the cd to repos.

Did you run:
```
sudo apt-get update
```
If you did, can you enter this in the Terminal:
```
aptitude search ndiswrapper
```check and see what packages are there.

Otherwise, you can find the package at:
```
/media/cdrom/pool/main/n/ndiswrapper
```You should be able to install it manually in the Terminal by doing:
```
sudo dpkg -i /media/cdrom/pool/main/n/ndiswrapper/ndiswrapper-common_1.52-1-ubuntu1_all.deb
```

---

### Post by Ayuthia on 2008-11-26
> **Nikmaster0 said:**
> I found all three, graphical, and the common and utils in the package manager. I was looking in the wrong place. but when I tried to use the graphical, I get ```
Module could not be loaded. Error was: WARNING: /etc/modprobe.d/blacklist line 50: ignoring bad line starting with "ndiswrapper" FATAL: Module ndiswrapper not found. Is the ndiswrapper module installed?
```

Can you attach /etc/modprobe.d/blacklist?  If not, you might just edit /etc/modprobe.d/blacklist:
```
gksu gedit /etc/modprobe.d/blacklist
```and go to line 50 and place a # in front of line 50.  Apparently line 50 has some incorrect information.  Generally the blacklist file lines start with blacklist and then have one driver after it (example: blacklist pcspkr).  Adding the # at the beginning of the line will comment out the line so that the system will not read it.

---

### Post by Nikmaster0 on 2008-11-26
when i do sudo apt-get update, I get:
```
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid/main Translation-en_US
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid/restricted Translation-en_US
Hit http://archive.ubuntu.com intrepid Release.gpg                             
Ign http://archive.ubuntu.com intrepid/main Translation-en_US                  
Hit http://archive.canonical.com intrepid Release.gpg
Ign http://archive.canonical.com intrepid/partner Translation-en_US
Ign http://archive.ubuntu.com intrepid/restricted Translation-en_US
Ign http://archive.ubuntu.com intrepid/universe Translation-en_US
Ign http://archive.ubuntu.com intrepid/multiverse Translation-en_US
Hit http://archive.ubuntu.com intrepid-updates Release.gpg
Ign http://archive.ubuntu.com intrepid-updates/main Translation-en_US
Ign http://archive.ubuntu.com intrepid-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com intrepid-updates/universe Translation-en_US
Ign http://archive.ubuntu.com intrepid-updates/multiverse Translation-en_US
Hit http://archive.ubuntu.com intrepid-security Release.gpg
Hit http://archive.canonical.com intrepid Release
Ign http://archive.ubuntu.com intrepid-security/main Translation-en_US
Ign http://archive.ubuntu.com intrepid-security/restricted Translation-en_US
Hit http://archive.canonical.com intrepid/partner Packages
Ign http://archive.ubuntu.com intrepid-security/universe Translation-en_US
Ign http://archive.ubuntu.com intrepid-security/multiverse Translation-en_US
Hit http://archive.ubuntu.com intrepid Release
Hit http://archive.ubuntu.com intrepid-updates Release
Hit http://archive.canonical.com intrepid/partner Sources
Hit http://archive.ubuntu.com intrepid-security Release
Hit http://archive.ubuntu.com intrepid/main Packages
Hit http://archive.ubuntu.com intrepid/restricted Packages
Hit http://archive.ubuntu.com intrepid/restricted Sources
Hit http://archive.ubuntu.com intrepid/main Sources
Hit http://archive.ubuntu.com intrepid/multiverse Sources
Hit http://archive.ubuntu.com intrepid/universe Sources
Hit http://archive.ubuntu.com intrepid/universe Packages
Hit http://archive.ubuntu.com intrepid/multiverse Packages
Hit http://archive.ubuntu.com intrepid-updates/main Packages
Hit http://archive.ubuntu.com intrepid-updates/restricted Packages
Hit http://archive.ubuntu.com intrepid-updates/restricted Sources
Hit http://archive.ubuntu.com intrepid-updates/main Sources
Hit http://archive.ubuntu.com intrepid-updates/multiverse Sources
Hit http://archive.ubuntu.com intrepid-updates/universe Sources
Hit http://archive.ubuntu.com intrepid-updates/universe Packages
Hit http://archive.ubuntu.com intrepid-updates/multiverse Packages
Hit http://archive.ubuntu.com intrepid-security/main Packages
Hit http://archive.ubuntu.com intrepid-security/restricted Packages
Hit http://archive.ubuntu.com intrepid-security/restricted Sources
Hit http://archive.ubuntu.com intrepid-security/main Sources
Hit http://archive.ubuntu.com intrepid-security/multiverse Sources
Hit http://archive.ubuntu.com intrepid-security/universe Sources
Hit http://archive.ubuntu.com intrepid-security/universe Packages
Hit http://archive.ubuntu.com intrepid-security/multiverse Packages
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```
What do I do?
Ayuthia: I edited the blacklist and at line 50, it said ndiswrapper. Tried the graphical again, said ndiswrapper wasn't installed but no blacklist error.

---

### Post by Ayuthia on 2008-11-26
> **Nikmaster0 said:**
> when i do sudo apt-get update, I get:
```
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid/main Translation-en_US
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid/restricted Translation-en_US
Hit http://archive.ubuntu.com intrepid Release.gpg                             
Ign http://archive.ubuntu.com intrepid/main Translation-en_US                  
Hit http://archive.canonical.com intrepid Release.gpg
Ign http://archive.canonical.com intrepid/partner Translation-en_US
Ign http://archive.ubuntu.com intrepid/restricted Translation-en_US
Ign http://archive.ubuntu.com intrepid/universe Translation-en_US
Ign http://archive.ubuntu.com intrepid/multiverse Translation-en_US
Hit http://archive.ubuntu.com intrepid-updates Release.gpg
Ign http://archive.ubuntu.com intrepid-updates/main Translation-en_US
Ign http://archive.ubuntu.com intrepid-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com intrepid-updates/universe Translation-en_US
Ign http://archive.ubuntu.com intrepid-updates/multiverse Translation-en_US
Hit http://archive.ubuntu.com intrepid-security Release.gpg
Hit http://archive.canonical.com intrepid Release
Ign http://archive.ubuntu.com intrepid-security/main Translation-en_US
Ign http://archive.ubuntu.com intrepid-security/restricted Translation-en_US
Hit http://archive.canonical.com intrepid/partner Packages
Ign http://archive.ubuntu.com intrepid-security/universe Translation-en_US
Ign http://archive.ubuntu.com intrepid-security/multiverse Translation-en_US
Hit http://archive.ubuntu.com intrepid Release
Hit http://archive.ubuntu.com intrepid-updates Release
Hit http://archive.canonical.com intrepid/partner Sources
Hit http://archive.ubuntu.com intrepid-security Release
Hit http://archive.ubuntu.com intrepid/main Packages
Hit http://archive.ubuntu.com intrepid/restricted Packages
Hit http://archive.ubuntu.com intrepid/restricted Sources
Hit http://archive.ubuntu.com intrepid/main Sources
Hit http://archive.ubuntu.com intrepid/multiverse Sources
Hit http://archive.ubuntu.com intrepid/universe Sources
Hit http://archive.ubuntu.com intrepid/universe Packages
Hit http://archive.ubuntu.com intrepid/multiverse Packages
Hit http://archive.ubuntu.com intrepid-updates/main Packages
Hit http://archive.ubuntu.com intrepid-updates/restricted Packages
Hit http://archive.ubuntu.com intrepid-updates/restricted Sources
Hit http://archive.ubuntu.com intrepid-updates/main Sources
Hit http://archive.ubuntu.com intrepid-updates/multiverse Sources
Hit http://archive.ubuntu.com intrepid-updates/universe Sources
Hit http://archive.ubuntu.com intrepid-updates/universe Packages
Hit http://archive.ubuntu.com intrepid-updates/multiverse Packages
Hit http://archive.ubuntu.com intrepid-security/main Packages
Hit http://archive.ubuntu.com intrepid-security/restricted Packages
Hit http://archive.ubuntu.com intrepid-security/restricted Sources
Hit http://archive.ubuntu.com intrepid-security/main Sources
Hit http://archive.ubuntu.com intrepid-security/multiverse Sources
Hit http://archive.ubuntu.com intrepid-security/universe Sources
Hit http://archive.ubuntu.com intrepid-security/universe Packages
Hit http://archive.ubuntu.com intrepid-security/multiverse Packages
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```
What do I do?

Sorry.  I am about one post behind you.  This message is popping up because you are most likely in Synaptic.  Since you already have the packages installed, you don't need to do this step.

---

### Post by Nikmaster0 on 2008-11-26
What do I do now?
EDIT: Ah....I see, I'll just go to the next step. I'll post if I have more problems.

---

### Post by Nikmaster0 on 2008-11-26
did the package search in terminal, got this:
```
i   ndiswrapper-common              - Common scripts required to use the utiliti
v   ndiswrapper-modules-1.9         -                                           
i   ndiswrapper-utils-1.9           - Userspace utilities for the ndiswrapper Li
```
did the manual install, got this:
```
dpkg: error processing media/cdrom/pool/main/n/ndiswrapper/ndiswrapper-common_1.52-1-ubuntu1_all.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 media/cdrom/pool/main/n/ndiswrapper/ndiswrapper-common_1.52-1-ubuntu1_all.deb

```

---

### Post by Ayuthia on 2008-11-26
> **Nikmaster0 said:**
> What do I do now?

If you have already commented out line 50 in /etc/modprobe.d/blacklist based on post #14, you should be able to add the driver and then try to see if you can connect.  If it does not work, please check:
```
ndiswrapper -l
```and see if the device is present.  If you are using Windows Wireless Drivers, the driver should be listed and it should show that the hardware is present.

---

### Post by Nikmaster0 on 2008-11-26
Ayuthia: it says ndiswrapper not installed
EDIT: actually, if I type ndiswrapper now, it doesn't say it's not installed anymore.....I'll try the Windows Driver Install.

---

### Post by Nikmaster0 on 2008-11-26
using graphical, it still says that ndiswrapper is not installed. I'll try to install using terminal.

---

### Post by Ayuthia on 2008-11-26
> **Nikmaster0 said:**
> Ayuthia: it says ndiswrapper not installed
EDIT: actually, if I type ndiswrapper now, it doesn't say it's not installed anymore.....I'll try the Windows Driver Install.
Can you check and see if the following shows the location of ndiswrapper:
```
which ndiswrapper
```It should return /usr/sbin/ndiswrapper.  If it does, then all is ok.  You might want to make sure that you are not in a directory that has ndiswrapper files.  Sometimes it causes conflicts.

---

### Post by Nikmaster0 on 2008-11-26
it does, now we have another problem. when i go into the network thing, it has no wireless anything. on the app that you can install "Network", it says Wireless Disabled. How do I fix it?

---

### Post by Ayuthia on 2008-11-26
> **Nikmaster0 said:**
> it does, now we have another problem. when i go into the network thing, it has no wireless anything. on the app that you can install "Network", it says Wireless Disabled. How do I fix it?

You might want to go to the Terminal and check lshw -C network.  See if it shows your wireless card.  If it does, check under the Configuration and see if the driver listed is ndiswrapper.  If you can, please post the results.  Hopefully this will give us some clues on what is happening.

---

### Post by Nikmaster0 on 2008-11-26
terminal network command:
```
PCI (sysfs)  
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:c3:f4:e3
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.1.7 latency=32 module=ssb multicast=yes
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 9e:8c:7d:6b:33:e4
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```
which config are you talking about?

---

### Post by Ayuthia on 2008-11-26
> **Nikmaster0 said:**
> terminal network command:
```

  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb

```
which config are you talking about?

The one above.  You will see that the configuration shows that the driver is b43-pci-bridge.  This is what the system is trying to use for your wireless.  This also means that ndiswrapper does not have access to your card.

You have a special situation because you also have a Broadcom 44xx wired card.  This means that the ssb driver is needed.  To test out ndiswrapper:
```
sudo modprobe -r b43 b44 ssb ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe b44
sudo /etc/init.d/networking restart
sudo iwlist scan
```
This will only work for this session.  The commands will remove all the wired and wireless drivers for your system, load ndiswrapper, then load the b44 driver (your wired card).  It will then reset the network and then scan for wireless sites.  The commands will temporarily disconnect your wired connection.

By the way, did you try the b43 driver before using ndiswrapper?

---

### Post by Nikmaster0 on 2008-11-26
no. no b43 driver before ndiswrapper. and I will try the code, will post. Would it be a good idea to not blacklist ssb.

---

### Post by Nikmaster0 on 2008-11-26
here's the result....it's intresting, how it thinks ndiswrapper isin't installed, when I run ndiswrapper and install drivers, it works.
```
nikmaster0@sheldon2:~$ sudo modprobe -r b43 b44 ssb ndiswrapper
[sudo] password for nikmaster0: 
FATAL: Module ndiswrapper not found.
nikmaster0@sheldon2:~$ sudo modprobe -r b43 b44 ssb ndiswrapper
FATAL: Module ndiswrapper not found.
nikmaster0@sheldon2:~$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.
nikmaster0@sheldon2:~$ sudo modprobe b44
nikmaster0@sheldon2:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ] 
nikmaster0@sheldon2:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

```

---

### Post by Ayuthia on 2008-11-26
> **Nikmaster0 said:**
> no. no b43 driver before ndiswrapper. and I will try the code, will post. Would it be a good idea to not blacklist ssb.

I would not blacklist ssb because your wired card will either quit working (because the b44 driver needs it) or else ndiswrapper will not work (because b44 needed it, it will load the ssb module and prevent ndiswrapper from accessing your wireless card).  If this works, you will need to use the following:
```
echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/ndiswrapper 
```
This comes from the no-fluff guide:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Version%200.3](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Version%200.3)

This will add additional instructions for when the ndiswrapper module is loaded.  It will tell the system to remove the conflicting drivers, load ndiswrapper, then load the b44 driver.

---

### Post by Nikmaster0 on 2008-11-26
it didn't appear to do anything, it just spit out what I just pasted into it. Still no wireless, what do I do now?

---

### Post by Ayuthia on 2008-11-26
> **Nikmaster0 said:**
> here's the result....it's intresting, how it thinks ndiswrapper isin't installed, when I run ndiswrapper and install drivers, it works.
```
nikmaster0@sheldon2:~$ sudo modprobe -r b43 b44 ssb ndiswrapper
[sudo] password for nikmaster0: 
FATAL: Module ndiswrapper not found.
nikmaster0@sheldon2:~$ sudo modprobe -r b43 b44 ssb ndiswrapper
FATAL: Module ndiswrapper not found.
nikmaster0@sheldon2:~$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.
nikmaster0@sheldon2:~$ sudo modprobe b44
nikmaster0@sheldon2:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ] 
nikmaster0@sheldon2:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

```

Interesting.  Can you check and see if the ndiswrapper.ko file exists:
```
ls /lib/modules/`uname -r`/kernel/ubuntu/ndiswrapper
```If it does not, please try the following:
```
sudo aptitude reinstall linux-image-`uname-r`
ls /lib/modules/`uname -r`/kernel/ubuntu/ndiswrapper
```

By the way, the ` is a back-quote and not a single-quote '.  To test this, type:
```
echo `uname -r`
```and it should return the kernel version.  if it returns uname -r, then you used the single-quote.

---

### Post by Nikmaster0 on 2008-11-26
results:
```
nikmaster0@sheldon2:~$ ls /lib/modules/`uname -r`/kernel/ubuntu/ndiswrapper
nikmaster0@sheldon2:~$ sudo aptitude reinstall linux-image-`uname-r`

bash: uname-r: command not found
[sudo] password for nikmaster0: 
Sorry, try again.
[sudo] password for nikmaster0: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

nikmaster0@sheldon2:~$ echo `uname -r`
2.6.27-7-generic

```

---

### Post by Ayuthia on 2008-11-26
> **Nikmaster0 said:**
> results:
```
nikmaster0@sheldon2:~$ ls /lib/modules/`uname -r`/kernel/ubuntu/ndiswrapper
nikmaster0@sheldon2:~$ sudo aptitude reinstall linux-image-`uname-r`

bash: uname-r: command not found
[sudo] password for nikmaster0: 
Sorry, try again.
[sudo] password for nikmaster0: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

nikmaster0@sheldon2:~$ echo `uname -r`
2.6.27-7-generic

```

Oops.  I meant:
```
sudo aptitude reinstall linux-image-`uname -r`
```forgot the space.  If that does not work, please try:
```
sudo dpkg-reconfigure linux-image-`uname -r`
ls /lib/modules/`uname -r`/kernel/ubuntu/ndiswrapper
```linux-image-`uname -r` is the package that contains the ndiswrapper.ko file (along with other kernel modules).  Since ndiswrapper.ko is missing, hopefully this will bring it back.

---

### Post by Nikmaster0 on 2008-11-26
did both.....what now?

---

### Post by Ayuthia on 2008-11-26
> **Nikmaster0 said:**
> did both.....what now?

Does ndiswrapper.ko show up when you do:
```
ls /lib/modules/`uname -r`/kernel/ubuntu/ndiswrapper
```
If so, try this again:
```
sudo modprobe -r b43 b44 ssb ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe b44
sudo /etc/init.d/networking restart
sudo iwlist scan
```

---

### Post by kevdog on 2008-11-26
sudo updatedb
locate ndiswrapper


Does it come up with anything?

---

### Post by Nikmaster0 on 2008-11-26
Kevdog:```
nikmaster0@sheldon2:~$ locate ndiswrapper
/etc/ndiswrapper
/etc/modprobe.d/ndiswrapper
/etc/modprobe.d/ndiswrapper~
/etc/ndiswrapper/bcmwl5
/etc/ndiswrapper/bcmwl5/14E4:4301.5.conf
/etc/ndiswrapper/bcmwl5/14E4:4301:12F3:103C.5.conf
/etc/ndiswrapper/bcmwl5/14E4:4318.5.conf
/etc/ndiswrapper/bcmwl5/14E4:4318:1355:103C.5.conf
/etc/ndiswrapper/bcmwl5/14E4:4318:1356:103C.5.conf
/etc/ndiswrapper/bcmwl5/14E4:4318:1357:103C.5.conf
/etc/ndiswrapper/bcmwl5/14E4:4319.5.conf
/etc/ndiswrapper/bcmwl5/14E4:4319:1358:103C.5.conf
/etc/ndiswrapper/bcmwl5/14E4:4319:1359:103C.5.conf
/etc/ndiswrapper/bcmwl5/14E4:4319:135A:103C.5.conf
/etc/ndiswrapper/bcmwl5/14E4:4320.5.conf
/etc/ndiswrapper/bcmwl5/14E4:4320:00E7:0E11.5.conf
/etc/ndiswrapper/bcmwl5/14E4:4320:12F4:103C.5.conf
/etc/ndiswrapper/bcmwl5/14E4:4320:12F8:103C.5.conf
/etc/ndiswrapper/bcmwl5/14E4:4320:12FA:103C.5.conf
/etc/ndiswrapper/bcmwl5/14E4:4320:12FB:103C.5.conf
/etc/ndiswrapper/bcmwl5/14E4:4324.5.conf
/etc/ndiswrapper/bcmwl5/14E4:4324:12F9:103C.5.conf
/etc/ndiswrapper/bcmwl5/14E4:4324:12FC:103C.5.conf
/etc/ndiswrapper/bcmwl5/14E4:4324:12FD:103C.5.conf
/etc/ndiswrapper/bcmwl5/bcmwl5.inf
/etc/ndiswrapper/bcmwl5/bcmwl5.sys
/home/nikmaster0/ndiswrapper
/home/nikmaster0/ndiswrapper-1.53
/home/nikmaster0/ndiswrapper-1.53.tar.gz
/home/nikmaster0/.fr-jldX1Z/ndiswrapper-1.53
/home/nikmaster0/.fr-jldX1Z/ndiswrapper-1.53/INSTALL
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/AUTHORS
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/ChangeLog
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/INSTALL
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/Makefile
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/README
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/driver
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/loadndisdriver.8
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/ndiswrapper.8
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/ndiswrapper.spec
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/utils
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/driver/.built-in.o.cmd
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/driver/.crt.o.cmd
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/driver/.crt_exports.h.cmd
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/driver/.hal.o.cmd
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/driver/.hal_exports.h.cmd
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/driver/.iw_ndis.o.d
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/driver/.ndis_exports.h.cmd
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/driver/.ntoskernel_exports.h.cmd
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/driver/.ntoskernel_io_exports.h.cmd
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/driver/.rtl_exports.h.cmd
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/driver/.tmp_versions
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/driver/.usb_exports.h.cmd
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/driver/Makefile
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/driver/built-in.o
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/driver/crt.c
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/driver/crt.o
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/driver/crt_exports.h
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/driver/divdi3.c
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/driver/hal.c
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/driver/hal.o
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/driver/hal_exports.h
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/driver/iw_ndis.c
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/driver/iw_ndis.h
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/driver/lin2win.h
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/driver/loader.c
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/driver/loader.h
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/driver/longlong.h
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/driver/mkexport.sh
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/driver/mkstubs.sh
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/driver/ndis.c
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/driver/ndis.h
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/driver/ndis_exports.h
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/driver/ndiswrapper.h
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/driver/ntoskernel.c
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/driver/ntoskernel.h
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/driver/ntoskernel_exports.h
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/driver/ntoskernel_io.c
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/driver/ntoskernel_io_exports.h
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/driver/pe_linker.c
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/driver/pe_linker.h
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/driver/pnp.c
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/driver/pnp.h
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/driver/proc.c
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/driver/rtl.c
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/driver/rtl_exports.h
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/driver/usb.c
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/driver/usb.h
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/driver/usb_exports.h
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/driver/win2lin_stubs.S
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/driver/winnt_types.h
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/driver/workqueue.c
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/driver/wrapmem.c
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/driver/wrapmem.h
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/driver/wrapndis.c
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/driver/wrapndis.h
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/driver/wrapper.c
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/driver/wrapper.h
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/utils/Makefile
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/utils/loadndisdriver.c
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/utils/ndiswrapper
/home/nikmaster0/.local/share/Trash/files/ndiswrapper-1.53/utils/ndiswrapper-buginfo
/home/nikmaster0/.local/share/Trash/info/ndiswrapper-1.48.tar.gz.trashinfo
/home/nikmaster0/.local/share/Trash/info/ndiswrapper-1.48.trashinfo
/home/nikmaster0/.local/share/Trash/info/ndiswrapper-1.53.trashinfo
/home/nikmaster0/.local/share/Trash/info/ndiswrapper.trashinfo
/home/nikmaster0/.nautilus/metafiles/file:%2F%2F%2Fhome%2Fnikmaster0%2Fndiswrapper-1.53.xml
/home/nikmaster0/Desktop/ndiswrapper-1.53.tar.gz
/home/nikmaster0/ndiswrapper/ndiswrapper-1.48
/home/nikmaster0/ndiswrapper/ndiswrapper-1.48.tar.gz
/home/nikmaster0/ndiswrapper/ndiswrapper-1.48/AUTHORS
/home/nikmaster0/ndiswrapper/ndiswrapper-1.48/ChangeLog
/home/nikmaster0/ndiswrapper/ndiswrapper-1.48/INSTALL
/home/nikmaster0/ndiswrapper/ndiswrapper-1.48/Makefile
/home/nikmaster0/ndiswrapper/ndiswrapper-1.48/README
/home/nikmaster0/ndiswrapper/ndiswrapper-1.48/driver
/home/nikmaster0/ndiswrapper/ndiswrapper-1.48/loadndisdriver.8
/home/nikmaster0/ndiswrapper/ndiswrapper-1.48/ndiswrapper.8
/home/nikmaster0/ndiswrapper/ndiswrapper-1.48/ndiswrapper.spec
/home/nikmaster0/ndiswrapper/ndiswrapper-1.48/utils
/home/nikmaster0/ndiswrapper/ndiswrapper-1.48/driver/.tmp_versions
/home/nikmaster0/ndiswrapper/ndiswrapper-1.48/driver/Makefile
/home/nikmaster0/ndiswrapper/ndiswrapper-1.48/driver/compat.h
/home/nikmaster0/ndiswrapper/ndiswrapper-1.48/driver/crt.c
/home/nikmaster0/ndiswrapper/ndiswrapper-1.48/driver/crt_exports.h
/home/nikmaster0/ndiswrapper/ndiswrapper-1.48/driver/divdi3.c
/home/nikmaster0/ndiswrapper/ndiswrapper-1.48/driver/hal.c
/home/nikmaster0/ndiswrapper/ndiswrapper-1.48/driver/hal_exports.h
/home/nikmaster0/ndiswrapper/ndiswrapper-1.48/driver/iw_ndis.c
/home/nikmaster0/ndiswrapper/ndiswrapper-1.48/driver/iw_ndis.h
/home/nikmaster0/ndiswrapper/ndiswrapper-1.48/driver/lin2win.h
/home/nikmaster0/ndiswrapper/ndiswrapper-1.48/driver/loader.c
/home/nikmaster0/ndiswrapper/ndiswrapper-1.48/driver/loader.h
/home/nikmaster0/ndiswrapper/ndiswrapper-1.48/driver/longlong.h
/home/nikmaster0/ndiswrapper/ndiswrapper-1.48/driver/ndis.c
/home/nikmaster0/ndiswrapper/ndiswrapper-1.48/driver/ndis.h
/home/nikmaster0/ndiswrapper/ndiswrapper-1.48/driver/ndis_exports.h
/home/nikmaster0/ndiswrapper/ndiswrapper-1.48/driver/ndiswrapper.h
/home/nikmaster0/ndiswrapper/ndiswrapper-1.48/driver/ntoskernel.c
/home/nikmaster0/ndiswrapper/ndiswrapper-1.48/driver/ntoskernel.h
/home/nikmaster0/ndiswrapper/ndiswrapper-1.48/driver/ntoskernel_exports.h
/home/nikmaster0/ndiswrapper/ndiswrapper-1.48/driver/ntoskernel_io.c
/home/nikmaster0/ndiswrapper/ndiswrapper-1.48/driver/ntoskernel_io_exports.h
/home/nikmaster0/ndiswrapper/ndiswrapper-1.48/driver/pe_linker.c
/home/nikmaster0/ndiswrapper/ndiswrapper-1.48/driver/pe_linker.h
/home/nikmaster0/ndiswrapper/ndiswrapper-1.48/driver/pnp.c
/home/nikmaster0/ndiswrapper/ndiswrapper-1.48/driver/pnp.h
/home/nikmaster0/ndiswrapper/ndiswrapper-1.48/driver/proc.c
/home/nikmaster0/ndiswrapper/ndiswrapper-1.48/driver/rtl.c
/home/nikmaster0/ndiswrapper/ndiswrapper-1.48/driver/rtl_exports.h
/home/nikmaster0/ndiswrapper/ndiswrapper-1.48/driver/usb.c
/home/nikmaster0/ndiswrapper/ndiswrapper-1.48/driver/usb.h
/home/nikmaster0/ndiswrapper/ndiswrapper-1.48/driver/usb_exports.h
/home/nikmaster0/ndiswrapper/ndiswrapper-1.48/driver/win2lin_stubs.S
/home/nikmaster0/ndiswrapper/ndiswrapper-1.48/driver/winnt_types.h
/home/nikmaster0/ndiswrapper/ndiswrapper-1.48/driver/workqueue.c
/home/nikmaster0/ndiswrapper/ndiswrapper-1.48/driver/wrapmem.c
/home/nikmaster0/ndiswrapper/ndiswrapper-1.48/driver/wrapmem.h
/home/nikmaster0/ndiswrapper/ndiswrapper-1.48/driver/wrapndis.c
/home/nikmaster0/ndiswrapper/ndiswrapper-1.48/driver/wrapndis.h
/home/nikmaster0/ndiswrapper/ndiswrapper-1.48/driver/wrapper.c
/home/nikmaster0/ndiswrapper/ndiswrapper-1.48/utils/Makefile
/home/nikmaster0/ndiswrapper/ndiswrapper-1.48/utils/loadndisdriver.c
/home/nikmaster0/ndiswrapper/ndiswrapper-1.48/utils/ndiswrapper
/home/nikmaster0/ndiswrapper/ndiswrapper-1.48/utils/ndiswrapper-buginfo
/home/nikmaster0/ndiswrapper-1.53/AUTHORS
/home/nikmaster0/ndiswrapper-1.53/ChangeLog
/home/nikmaster0/ndiswrapper-1.53/INSTALL
/home/nikmaster0/ndiswrapper-1.53/Makefile
/home/nikmaster0/ndiswrapper-1.53/README
/home/nikmaster0/ndiswrapper-1.53/driver
/home/nikmaster0/ndiswrapper-1.53/loadndisdriver.8
/home/nikmaster0/ndiswrapper-1.53/ndis.patch
/home/nikmaster0/ndiswrapper-1.53/ndiswrapper.8
/home/nikmaster0/ndiswrapper-1.53/ndiswrapper.spec
/home/nikmaster0/ndiswrapper-1.53/utils
/home/nikmaster0/ndiswrapper-1.53/driver/.built-in.o.cmd
/home/nikmaster0/ndiswrapper-1.53/driver/.crt.o.cmd
/home/nikmaster0/ndiswrapper-1.53/driver/.crt_exports.h.cmd
/home/nikmaster0/ndiswrapper-1.53/driver/.hal.o.cmd
/home/nikmaster0/ndiswrapper-1.53/driver/.hal_exports.h.cmd
/home/nikmaster0/ndiswrapper-1.53/driver/.iw_ndis.o.d
/home/nikmaster0/ndiswrapper-1.53/driver/.ndis_exports.h.cmd
/home/nikmaster0/ndiswrapper-1.53/driver/.ntoskernel_exports.h.cmd
/home/nikmaster0/ndiswrapper-1.53/driver/.ntoskernel_io_exports.h.cmd
/home/nikmaster0/ndiswrapper-1.53/driver/.rtl_exports.h.cmd
/home/nikmaster0/ndiswrapper-1.53/driver/.tmp_versions
/home/nikmaster0/ndiswrapper-1.53/driver/.usb_exports.h.cmd
/home/nikmaster0/ndiswrapper-1.53/driver/Makefile
/home/nikmaster0/ndiswrapper-1.53/driver/built-in.o
/home/nikmaster0/ndiswrapper-1.53/driver/crt.c
/home/nikmaster0/ndiswrapper-1.53/driver/crt.o
/home/nikmaster0/ndiswrapper-1.53/driver/crt_exports.h
/home/nikmaster0/ndiswrapper-1.53/driver/divdi3.c
/home/nikmaster0/ndiswrapper-1.53/driver/hal.c
/home/nikmaster0/ndiswrapper-1.53/driver/hal.o
/home/nikmaster0/ndiswrapper-1.53/driver/hal_exports.h
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.c
/home/nikmaster0/ndiswrapper-1.53/driver/iw_ndis.h
/home/nikmaster0/ndiswrapper-1.53/driver/lin2win.h
/home/nikmaster0/ndiswrapper-1.53/driver/loader.c
/home/nikmaster0/ndiswrapper-1.53/driver/loader.h
/home/nikmaster0/ndiswrapper-1.53/driver/longlong.h
/home/nikmaster0/ndiswrapper-1.53/driver/mkexport.sh
/home/nikmaster0/ndiswrapper-1.53/driver/mkstubs.sh
/home/nikmaster0/ndiswrapper-1.53/driver/ndis.c
/home/nikmaster0/ndiswrapper-1.53/driver/ndis.h
/home/nikmaster0/ndiswrapper-1.53/driver/ndis_exports.h
/home/nikmaster0/ndiswrapper-1.53/driver/ndiswrapper.h
/home/nikmaster0/ndiswrapper-1.53/driver/ntoskernel.c
/home/nikmaster0/ndiswrapper-1.53/driver/ntoskernel.h
/home/nikmaster0/ndiswrapper-1.53/driver/ntoskernel_exports.h
/home/nikmaster0/ndiswrapper-1.53/driver/ntoskernel_io.c
/home/nikmaster0/ndiswrapper-1.53/driver/ntoskernel_io_exports.h
/home/nikmaster0/ndiswrapper-1.53/driver/pe_linker.c
/home/nikmaster0/ndiswrapper-1.53/driver/pe_linker.h
/home/nikmaster0/ndiswrapper-1.53/driver/pnp.c
/home/nikmaster0/ndiswrapper-1.53/driver/pnp.h
/home/nikmaster0/ndiswrapper-1.53/driver/proc.c
/home/nikmaster0/ndiswrapper-1.53/driver/rtl.c
/home/nikmaster0/ndiswrapper-1.53/driver/rtl_exports.h
/home/nikmaster0/ndiswrapper-1.53/driver/usb.c
/home/nikmaster0/ndiswrapper-1.53/driver/usb.h
/home/nikmaster0/ndiswrapper-1.53/driver/usb_exports.h
/home/nikmaster0/ndiswrapper-1.53/driver/win2lin_stubs.S
/home/nikmaster0/ndiswrapper-1.53/driver/winnt_types.h
/home/nikmaster0/ndiswrapper-1.53/driver/workqueue.c
/home/nikmaster0/ndiswrapper-1.53/driver/wrapmem.c
/home/nikmaster0/ndiswrapper-1.53/driver/wrapmem.h
/home/nikmaster0/ndiswrapper-1.53/driver/wrapndis.c
/home/nikmaster0/ndiswrapper-1.53/driver/wrapndis.h
/home/nikmaster0/ndiswrapper-1.53/driver/wrapper.c
/home/nikmaster0/ndiswrapper-1.53/driver/wrapper.h
/home/nikmaster0/ndiswrapper-1.53/utils/Makefile
/home/nikmaster0/ndiswrapper-1.53/utils/loadndisdriver.c
/home/nikmaster0/ndiswrapper-1.53/utils/ndiswrapper
/home/nikmaster0/ndiswrapper-1.53/utils/ndiswrapper-buginfo
/lib/modules/2.6.27-7-generic/kernel/ubuntu/ndiswrapper
/lib/modules/2.6.27-7-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
/usr/sbin/ndiswrapper
/usr/sbin/ndiswrapper-1.9
/usr/share/doc/ndiswrapper-common
/usr/share/doc/ndiswrapper-utils-1.9
/usr/share/doc/ndiswrapper-common/NEWS.Debian.gz
/usr/share/doc/ndiswrapper-common/README.Debian
/usr/share/doc/ndiswrapper-common/changelog.Debian.gz
/usr/share/doc/ndiswrapper-common/changelog.gz
/usr/share/doc/ndiswrapper-common/copyright
/usr/share/doc/ndiswrapper-utils-1.9/NEWS.Debian.gz
/usr/share/doc/ndiswrapper-utils-1.9/changelog.Debian.gz
/usr/share/doc/ndiswrapper-utils-1.9/changelog.gz
/usr/share/doc/ndiswrapper-utils-1.9/copyright
/usr/share/man/man8/ndiswrapper-1.9.8.gz
/usr/share/man/man8/ndiswrapper.8.gz
/usr/src/linux-headers-2.6.27-7/ubuntu/ndiswrapper
/usr/src/linux-headers-2.6.27-7/ubuntu/ndiswrapper/Kconfig
/usr/src/linux-headers-2.6.27-7/ubuntu/ndiswrapper/Makefile
/usr/src/linux-headers-2.6.27-7/ubuntu/ndiswrapper/mkexport.sh
/usr/src/linux-headers-2.6.27-7/ubuntu/ndiswrapper/mkstubs.sh
/usr/src/linux-headers-2.6.27-7-generic/include/config/ndiswrapper.h
/var/cache/apt/archives/ndiswrapper-common_1.52-1ubuntu1_all.deb
/var/cache/apt/archives/ndiswrapper-utils-1.9_1.52-1ubuntu1_i386.deb
/var/lib/dpkg/info/ndiswrapper-common.list
/var/lib/dpkg/info/ndiswrapper-common.md5sums
/var/lib/dpkg/info/ndiswrapper-utils-1.9.list
/var/lib/dpkg/info/ndiswrapper-utils-1.9.md5sums

```
When I do those codes I get:
```
nikmaster0@sheldon2:~$ ls /lib/modules/`uname -r`/kernel/ubuntu/ndiswrapper
ndiswrapper.ko
nikmaster0@sheldon2:~$ sudo modprobe -r b43 b44 ssb ndiswrapper
nikmaster0@sheldon2:~$ sudo modprobe ndiswrapper
nikmaster0@sheldon2:~$ sudo modprobe b44
nikmaster0@sheldon2:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ] 
nikmaster0@sheldon2:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

```

---

### Post by Ayuthia on 2008-11-26
It looks like ndiswrapper.ko has been recreated but your wireless is not turning on.  Can you post the results of:
```
dmesg|grep ndis
```Also are you using the 32-bit or 64-bit version of Ubuntu?

---

### Post by Nikmaster0 on 2008-11-26
32 bit
```
nikmaster0@sheldon2:~$ dmesg|grep ndis
[   16.273951] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   16.709413] ndiswrapper: driver bcmwl5 (Broadcom,02/11/2005, 3.100.64.0) loaded
[   16.709837] ndiswrapper 0000:02:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[   16.717333] ndiswrapper (NdisWriteErrorLogEntry:190): log: C000138D, count: 1, return_address: f8b43d7b
[   16.717341] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x10e
[   16.717435] ndiswrapper (mp_init:219): couldn't initialize device: C0000001
[   16.717445] ndiswrapper (pnp_start_device:435): Windows driver couldn't initialize the device (C0000001)
[   16.717472] ndiswrapper (mp_halt:262): device f7a3e480 is not initialized - not halting
[   16.717477] ndiswrapper: device eth%d removed
[   16.717566] ndiswrapper 0000:02:03.0: PCI INT A disabled
[   16.717594] ndiswrapper: probe of 0000:02:03.0 failed with error -22
[   16.717763] usbcore: registered new interface driver ndiswrapper
```

---

### Post by Nikmaster0 on 2008-11-27
I solved the problem and my wireless card now works. I owe a thorough thank you to all of the users of the Ubuntu community that helped me and now I know alot more about the terminal than I think I wanted to know. lol. Thank you and I will put thanks under the first post of each users contribution in this solution. Thanks again,
Nikmaster0

---

### Post by Ayuthia on 2008-11-27
It looks like ndiswrapper did not like the driver.  Did you try using the driver suggested in:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
The guide recommends the driver in 2a:
```
sudo apt-get install cabextract
wget ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe
cabextract sp34152.exe
```

The other option is to try the b43 driver:
```
sudo aptitude install b43-fwcutter
```
It looks like you have a working connection in Ubuntu so you can have the system fetch the firmware for you.  Once that is done, please do the following:
```
sudo modprobe -r b43 b44 ssb ndiswrapper
sudo modprobe b43
sudo modprobe b44
sudo /etc/init.d/networking restart
sudo iwlist scan
```

---

### Post by Ayuthia on 2008-11-27
> **Nikmaster0 said:**
> I solved the problem and my wireless card now works. I owe a thorough thank you to all of the users of the Ubuntu community that helped me and now I know alot more about the terminal than I think I wanted to know. lol. Thank you and I will put thanks under the first post of each users contribution in this solution. Thanks again,
Nikmaster0

Can you let us know what you did?  I am very curious.

---

### Post by Nikmaster0 on 2008-11-27
well....I just did what you said, and plugged in my Linksys WPC54G (which wouldn't work), and it just connected. And that (plugging in my (used to not working) wireless card in) worked in Kubuntu and Sabayon Linux too....Just never thought it would work here. Thanks.

---

### Post by kevdog on 2008-11-27
I'll take a bet you are using the b43 module?!!  

lshw -C network will reveal the answer.  Please post.

---

### Post by Nikmaster0 on 2008-11-27
here you go. It doesn't even recognise my Linksys WPC54G, even though when I unplug it, it won't work.
```
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:c3:f4:e3
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=32 module=ssb multicast=yes
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan1
       version: 02
       serial: 00:14:bf:d8:cb:8f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.53+Broadcom,02/11/2005, 3.100. ip=192.168.1.2 latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: e2:7b:30:f0:8e:24
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

---

### Post by kevdog on 2008-11-27
Hmm interesting

Wasn't what I expected

How about post
sudo iwlist scan

Thanks

---

