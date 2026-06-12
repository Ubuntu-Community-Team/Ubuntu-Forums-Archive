---
title: "How can I use the Adlink RTV-24 video card with the latest [2.6.24 and higher] Linux"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by rtv on 2009-04-29
I am using Adlink RTV-24 video card ([http://www.adlinktech.com/PD/web/PD_detail.php?cKind=FN&pid=247&seq=&id=&sid=](http://www.adlinktech.com/PD/web/PD_detail.php?cKind=FN&pid=247&seq=&id=&sid=)). I have currently installed Kubuntu 8.04 kernel 2.6.24-23-generic. I downloaded the driver RTV-kernel-2.6.22 from the [www.adlinktech.com](www.adlinktech.com) website. When I compile the driver on 2.6.24-23 kernel, I got the following warning and error messages.



I am able to compile the driver and use the video card with the 2.6.23 kernel. But my requirement is to run the driver in a 2.6.24 or higher version kernel. How can I use the Adlink RTV-24 video card with the latest [2.6.24 and higher] Linux kernels?

```
***WARNING:*** You do not have the full kernel sources installed.
This does not prevent you from building the v4l-dvb tree if you have the
kernel headers, but the full kernel source may be required in order to use
make menuconfig / xconfig / qconfig.

If you are experiencing problems building the v4l-dvb tree, please try
building against a vanilla kernel before reporting a bug.

Vanilla kernels are available at http://kernel.org.
On most distros, this will compile a newly downloaded kernel:

cp /boot/config-`uname -r` <your kernel dir>/.config
cd <your kernel dir>
make all modules_install install

Please see your distro's web site for instructions to build a new kernel.

VIDEO_PLANB: Requires at least kernel 2.6.99
Created default (all yes) .config file
./scripts/make_myconfig.pl
```

```
Error
...
from /home/user/Desktop/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l/flexcop-pci.c:10:
/home/user/Desktop/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l/dvb_frontend.h:165: error: field 'tuner_ops' has incomplete type
make[3]: *** [/home/user/Desktop/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l/flexcop-pci.o] Error 1
make[2]: *** [_module_/home/user/Desktop/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-2.6.29.2'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/user/Desktop/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l'
make: *** [all] Error 2
```


Then I downloaded a patch (v4l-dvb-kernel-Makefile-2.6.24.obj ) for the makefile located at:
[http://mcentral.de/pipermail/em28xx/...ile-2.6.24.obj](http://mcentral.de/pipermail/em28xx/...ile-2.6.24.obj)
(from the em28xx mail list message: [http://mcentral.de/pipermail/em28xx/...il/001481.html](http://mcentral.de/pipermail/em28xx/...il/001481.html))
into the v4l-dvb-experimental directory, and in the terminal, in the same directory, executed:
    patch -p0 < v4l-dvb-kernel-Makefile-2.6.24.obj 

which solves the previous error but now I get the following errors while make:

```
...
from /home/user/Desktop/Test/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l/bttv-driver.c:32:
include/linux/kernel.h:419:1: warning: this is the location of the previous definition
/home/user/Desktop/Test/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l/bttv-driver.c:170: warning: 'struct class_device' declared inside parameter list
/home/user/Desktop/Test/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l/bttv-driver.c:170: warning: its scope is only this definition or declaration, which is probably not what you want
/home/user/Desktop/Test/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l/bttv-driver.c: In function 'show_card':
/home/user/Desktop/Test/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l/bttv-driver.c:172: warning: initialization from incompatible pointer type
/home/user/Desktop/Test/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l/bttv-driver.c:173: error: incompatible type for argument 1 of 'dev_get_drvdata'
/home/user/Desktop/Test/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l/bttv-driver.c: At top level:
/home/user/Desktop/Test/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l/bttv-driver.c:176: error: expected ')' before '(' token
/home/user/Desktop/Test/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l/bttv-driver.c: In function 'bttv_common_ioctls':
/home/user/Desktop/Test/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l/bttv-driver.c:1952: error: 'BT878_SET_GPIO_OUT_ENABLE' undeclared (first use in this function)
/home/user/Desktop/Test/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l/bttv-driver.c:1952: error: (Each undeclared identifier is reported only once
/home/user/Desktop/Test/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l/bttv-driver.c:1952: error: for each function it appears in.)
/home/user/Desktop/Test/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l/bttv-driver.c:1953: error: 'BT878_S_GPIO_OUT_ENABLE' undeclared (first use in this function)
/home/user/Desktop/Test/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l/bttv-driver.c:1963: error: 'BT878_SET_GPIO_VALUE' undeclared (first use in this function)
/home/user/Desktop/Test/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l/bttv-driver.c:1964: error: 'BT878_S_GPIO_VALUE' undeclared (first use in this function)
/home/user/Desktop/Test/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l/bttv-driver.c:1971: error: 'BT878_GET_GPIO_VALUE' undeclared (first use in this function)
/home/user/Desktop/Test/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l/bttv-driver.c:1972: error: 'BT878_G_GPIO_VALUE' undeclared (first use in this function)
/home/user/Desktop/Test/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l/bttv-driver.c:2133: error: implicit declaration of function 'v4l2_video_std_construct'
/home/user/Desktop/Test/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l/bttv-driver.c: In function 'bttv_do_ioctl':
/home/user/Desktop/Test/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l/bttv-driver.c:2851: error: implicit declaration of function 'v4l_print_ioctl'
/home/user/Desktop/Test/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l/bttv-driver.c:3207: error: implicit declaration of function 'v4l_compat_translate_ioctl'
/home/user/Desktop/Test/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l/bttv-driver.c:3221: error: 'BT878_SET_GPIO_OUT_ENABLE' undeclared (first use in this function)
/home/user/Desktop/Test/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l/bttv-driver.c:3222: error: 'BT878_SET_GPIO_VALUE' undeclared (first use in this function)
/home/user/Desktop/Test/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l/bttv-driver.c:3223: error: 'BT878_GET_GPIO_VALUE' undeclared (first use in this function)
/home/user/Desktop/Test/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l/bttv-driver.c:3640: error: 'BT878_S_GPIO_OUT_ENABLE' undeclared (first use in this function)
/home/user/Desktop/Test/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l/bttv-driver.c:3641: error: 'BT878_S_GPIO_VALUE' undeclared (first use in this function)
/home/user/Desktop/Test/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l/bttv-driver.c:3642: error: 'BT878_G_GPIO_VALUE' undeclared (first use in this function)
/home/user/Desktop/Test/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l/bttv-driver.c: In function 'bttv_ioctl':
/home/user/Desktop/Test/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l/bttv-driver.c:3689: error: implicit declaration of function 'video_usercopy'
/home/user/Desktop/Test/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l/bttv-driver.c: In function 'bttv_read':
/home/user/Desktop/Test/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l/bttv-driver.c:3702: error: 'v4l2_type_names' undeclared (first use in this function)
/home/user/Desktop/Test/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l/bttv-driver.c: In function 'bttv_open':
/home/user/Desktop/Test/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l/bttv-driver.c:3808: error: 'v4l2_type_names' undeclared (first use in this function)
/home/user/Desktop/Test/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l/bttv-driver.c: In function 'bttv_mmap':
/home/user/Desktop/Test/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l/bttv-driver.c:3905: error: 'v4l2_type_names' undeclared (first use in this function)
/home/user/Desktop/Test/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l/bttv-driver.c: At top level:
/home/user/Desktop/Test/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l/bttv-driver.c:3917: error: 'v4l_compat_ioctl32' undeclared here (not in a function)
/home/user/Desktop/Test/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l/bttv-driver.c:3928: error: unknown field 'type' specified in initializer
/home/user/Desktop/Test/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l/bttv-driver.c:3930: error: unknown field 'hardware' specified in initializer
/home/user/Desktop/Test/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l/bttv-driver.c:3930: error: 'VID_HARDWARE_BT848' undeclared here (not in a function)
/home/user/Desktop/Test/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l/bttv-driver.c:3931: warning: initialization from incompatible pointer type
/home/user/Desktop/Test/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l/bttv-driver.c:3938: error: unknown field 'type' specified in initializer
/home/user/Desktop/Test/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l/bttv-driver.c:3939: error: unknown field 'hardware' specified in initializer
/home/user/Desktop/Test/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l/bttv-driver.c:3940: warning: initialization from incompatible pointer type
/home/user/Desktop/Test/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l/bttv-driver.c:4084: error: unknown field 'type' specified in initializer
/home/user/Desktop/Test/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l/bttv-driver.c:4085: error: unknown field 'hardware' specified in initializer
/home/user/Desktop/Test/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l/bttv-driver.c:4086: warning: initialization from incompatible pointer type
/home/user/Desktop/Test/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l/bttv-driver.c: In function 'vdev_init':
/home/user/Desktop/Test/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l/bttv-driver.c:4628: error: incompatible types in assignment
/home/user/Desktop/Test/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l/bttv-driver.c: In function 'bttv_register_video':
/home/user/Desktop/Test/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l/bttv-driver.c:4666: error: 'struct video_device' has no member named 'type'
/home/user/Desktop/Test/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l/bttv-driver.c:4679: error: implicit declaration of function 'class_device_create_file'
/home/user/Desktop/Test/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l/bttv-driver.c:4679: error: 'struct video_device' has no member named 'class_dev'
/home/user/Desktop/Test/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l/bttv-driver.c:4680: error: 'class_device_attr_card' undeclared (first use in this function)
make[3]: *** [/home/user/Desktop/Test/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l/bttv-driver.o] Error 1
make[2]: *** [_module_/home/user/Desktop/Test/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-2.6.29.2'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/user/Desktop/Test/RTV-kernel-2.6.22/v4l-dvb-20070609/v4l'
make: *** [all] Error 2
```

Thanks in advance.

---

