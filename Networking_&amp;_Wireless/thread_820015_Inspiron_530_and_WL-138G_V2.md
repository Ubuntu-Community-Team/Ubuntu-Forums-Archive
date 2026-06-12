---
title: "Inspiron 530 and WL-138G_V2"
date: 2008-06-05
forum: Networking &amp; Wireless
---

### Post by shadoweva00 on 2008-06-05
Now I'm trying to set up an inspiron with a multiboot with windows and linux, but getting the wireless to work is a problem. Asus does provide a linux driver for the WL-138G_V2 that came with the computer, but I can't get it to compile on ubuntu. I'm sure it is because the tools that come with ubuntu are out of date and without internet I can't update them. Also I'm not getting a 50' ethernet cable for one time use. Any advice since I can't compile it? anyone else like to? (amd64). (most other distros wont even boot, except fedora which seems to lack the make utility.)

(special note: yes ubuntu says "restricted drivers available" and tries to download the broadcom firmware. At least with phone modems developers seemed to recognize that the drivers had to be on the disk for the ability to connect.)

---

### Post by chili555 on 2008-06-05
> I'm sure it is because the tools that come with ubuntu are out of dateIt's actually because the tools needed to compile from source are not installed by default. You need *build-essential* and *linux-headers-generic.* You might put the install CD in the tray and open System -> Admin -> Synaptic, then go to Settings -> Repositories and enable the CDROM and see if you can get these compiling tools. Then try your compile again.

Are you sure the Broadcom firmware is for the phone modem? Could it be for your wireless?

---

### Post by shadoweva00 on 2008-06-06
With build-essential and linux-headers-generic:


ubuntu@ubuntu:~$ cd src/linuxsta/src/wl/linux
ubuntu@ubuntu:~/src/linuxsta/src/wl/linux$ make clean
rm -f *.ko *.o *.c .*.o.cmd .*.ko.cmd
ubuntu@ubuntu:~/src/linuxsta/src/wl/linux$ make
Linux Directory is /lib/modules/2.6.24-16-generic/build
Linux Kernel Versions is 2.6.24-16-generic
make -C /lib/modules/2.6.24-16-generic/build CROSS_COMPILE= M=/home/ubuntu/src/linuxsta/src/wl/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /home/ubuntu/src/linuxsta/src/wl/linux/wlc_led.o
In file included from /home/ubuntu/src/linuxsta/src/wl/linux/wlc_led.c:17:
/home/ubuntu/src/linuxsta/src/wl/linux/../../include/typedefs.h:166: error: conflicting types for â&#8364;&#732;boolâ&#8364;&#8482;
include/linux/types.h:33: error: previous declaration of â&#8364;&#732;boolâ&#8364;&#8482; was here
In file included from /home/ubuntu/src/linuxsta/src/wl/linux/../../include/linux_osl.h:21,
                 from /home/ubuntu/src/linuxsta/src/wl/linux/../../include/osl.h:24,
                 from /home/ubuntu/src/linuxsta/src/wl/linux/wlc_led.c:19:
/home/ubuntu/src/linuxsta/src/wl/linux/../../include/linuxver.h:19:26: error: linux/config.h: No such file or directory
make[2]: *** [/home/ubuntu/src/linuxsta/src/wl/linux/wlc_led.o] Error 1
make[1]: *** [_module_/home/ubuntu/src/linuxsta/src/wl/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [default] Error 2
ubuntu@ubuntu:~/src/linuxsta/src/wl/linux$ make clean
rm -f *.ko *.o *.c .*.o.cmd .*.ko.cmd
ubuntu@ubuntu:~/src/linuxsta/src/wl/linux$ make
Linux Directory is /lib/modules/2.6.24-16-generic/build
Linux Kernel Versions is 2.6.24-16-generic
make -C /lib/modules/2.6.24-16-generic/build CROSS_COMPILE= M=/home/ubuntu/src/linuxsta/src/wl/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /home/ubuntu/src/linuxsta/src/wl/linux/wlc_led.o
In file included from /home/ubuntu/src/linuxsta/src/wl/linux/wlc_led.c:17:
/home/ubuntu/src/linuxsta/src/wl/linux/../../include/typedefs.h:166: error: conflicting types for â&#8364;&#732;boolâ&#8364;&#8482;
include/linux/types.h:33: error: previous declaration of â&#8364;&#732;boolâ&#8364;&#8482; was here
In file included from /home/ubuntu/src/linuxsta/src/wl/linux/../../include/linux_osl.h:21,
                 from /home/ubuntu/src/linuxsta/src/wl/linux/../../include/osl.h:24,
                 from /home/ubuntu/src/linuxsta/src/wl/linux/wlc_led.c:19:
/home/ubuntu/src/linuxsta/src/wl/linux/../../include/linuxver.h:19:26: error: linux/config.h: No such file or directory
make[2]: *** [/home/ubuntu/src/linuxsta/src/wl/linux/wlc_led.o] Error 1
make[1]: *** [_module_/home/ubuntu/src/linuxsta/src/wl/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [default] Error 2
ubuntu@ubuntu:~/src/linuxsta/src/wl/linux$ clear

ubuntu@ubuntu:~/src/linuxsta/src/wl/linux$ make clean
rm -f *.ko *.o *.c .*.o.cmd .*.ko.cmd
ubuntu@ubuntu:~/src/linuxsta/src/wl/linux$ make
Linux Directory is /lib/modules/2.6.24-16-generic/build
Linux Kernel Versions is 2.6.24-16-generic
make -C /lib/modules/2.6.24-16-generic/build CROSS_COMPILE= M=/home/ubuntu/src/linuxsta/src/wl/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /home/ubuntu/src/linuxsta/src/wl/linux/wlc_led.o
In file included from /home/ubuntu/src/linuxsta/src/wl/linux/wlc_led.c:17:
/home/ubuntu/src/linuxsta/src/wl/linux/../../include/typedefs.h:166: error: conflicting types for â&#8364;&#732;boolâ&#8364;&#8482;
include/linux/types.h:33: error: previous declaration of â&#8364;&#732;boolâ&#8364;&#8482; was here
In file included from /home/ubuntu/src/linuxsta/src/wl/linux/../../include/linux_osl.h:21,
                 from /home/ubuntu/src/linuxsta/src/wl/linux/../../include/osl.h:24,
                 from /home/ubuntu/src/linuxsta/src/wl/linux/wlc_led.c:19:
/home/ubuntu/src/linuxsta/src/wl/linux/../../include/linuxver.h:19:26: error: linux/config.h: No such file or directory
make[2]: *** [/home/ubuntu/src/linuxsta/src/wl/linux/wlc_led.o] Error 1
make[1]: *** [_module_/home/ubuntu/src/linuxsta/src/wl/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [default] Error 2
ubuntu@ubuntu:~/src/linuxsta/src/wl/linux$


and the instructions are: (the driver comes in a zip file so I didn't use tar, and I changed gcc version to the 4.x.x version they say it can use and also tried the correct value, which seemed to give the same error)


			Broadcom Corporation

Introduction:
------------
	This Package contains the the 802.11b and 802.11g Linux Device driver to support Broadcom WLAN chipsets on X86 platforms, for 2.6 linux kernels. This WLAN driver supports Wireless extensions upto rev 19.

Package details:
---------------
	This package is provided as a compressed tar file. The tar file contains all the sources needed, the binary versions of the regulatory domain files and the necessary makefile to build the BROADCOM WLAN driver for specific revisions of the kernel.

	The package contains:

		src/include and src/include/proto : All the header files.
		src/shared, src/wl/sys		  : All the source files
		src/wl/linux			  : Makefile
		src/wl/linux/obj-3.4.2, 
		src/wl/linux/obj-4.0.2		  : pre compiled regulatory binaries
	
	Two sets of precompiled regulatory binaries are avaialble, one for each of the compiler versions gcc 3.4.2 (Redhat FC3 and 2.6.14.3 kernel), and gcc 4.0.2 (Suse 10 distribution)

Distributions and Kernels Tested:
--------------------------------
1. Fedora FC3 with the stock 2.6.9-1.667 kernel (supports WEP only and no support for WPA)
2. Fedora FC3 with 2.6.14.3 kernel. (supports WPA/WPA2 and TKIP/AES/WEP cryptos)
3. Suse 10.0 with 2.6.13-15 kernel. (supports WPA/WPA2 and AES/WEP cryptos)

Chipset Support:
---------------
BCM4318, BCM4311, BCM4309C0

Building the Driver from Package:
--------------------------------

1. Extract the tar package.
		tar -xzvf src-<ver>.tar.gz

2. Build the Driver
	cd src/linuxsta/src/wl/linux
	in the makefile make sure to set the variables 
	CROSS_COMPILE=<xxx>, if the the gcc is not already in the $PATH or if a different compiler needs to be used, and 
	GCC-REV=<xxx>  dictates the path of the prebuild regulatory binaries, to use while building the driver.(values it takes now are 3.4.2 or 4.0.2), 
	if the kernel version is 2.6.14.3 the driver expects that iee80211_crypto.ko module be loaded, prior to loading this driver.

	make clean
	make

3. Test the Driver by loading it
	insmod wl.ko

Supported WLAN feature set:
--------------------------
	1. Supports WLAN STA functionality.
	2. Supports Wireless extensions (rev <= 19). So utilies like iwconfig and iwlist compiled with proper header versions(wireless.h) would be able to interface with the driver through the wireless extensions interface.
	3. Supports using the external TKIP crypto module if the module is available. To support this, the driver assumes that iee80211_crypto.ko is already loaded and available (support of the ieee802111_crypto modules were added to the kernel rev 2.6.14.3)
	4. Supports Only one set of channels for all countries.
	5. Supports Hardware cryptos for AES and WEP and with the proper versions of an external supplicant (such as wpa_supplicant with wireless extensions rev >= 18), one could set up different Authentication Key Managements like WPA/WPA-PSK/WPA2/WPA2-PSK/
	6. Uses only the standard IOCTLs defined in wireless extensions interface, doesn't have any custom IOCTLS defined.

Limitations:
-----------
	Current version of the driver has undergone a limited amount of testing with 2.6.14.3 kernel, Redhat FC3 and Suse 10 Linux distribuitons for i386 platforms. The included makefile only supports compiles for only 2.6 kernel versions.

---

### Post by chili555 on 2008-06-06
> limited amount of testing with 2.6.14.3 kernelWell, we are up to 2.6.24-xx, so this, in the world of Linux, it getting old. I tried compiling it myself and could fix a few errors, but got nowhere with others.

I see this is a Broadcom device. I'd certainly try the firmware you were offered before I'd try to cram a square peg in a round hole.

Post back if you get stuck.

---

### Post by shadoweva00 on 2008-06-07
I can pretty much say there is no possible way of getting it to work (including broadcom drivers), I found out an old dynex usb adapter works perfectly without any setup though...

---

