---
title: "cisco vpn and 8.04..."
date: 2008-09-22
forum: Networking &amp; Wireless
---

### Post by adramalech on 2008-09-22
okay so i have downloaded the newest version of cisco vpn client for linux from my school website i then went to install but got the cflag error so i switched the Makefile from cflag += to extra_cflag +=  but still have the problem this time about all the variables that are in the patches that i need to patch the installation with to make it work...

so i get the 2 patch files downloaded for the 64bit....and i then go and patch them the .diff file gives me 2 out of 7 hunks failed....i then go to the file where it said it copied the parts too but i don't know how to cut and paste into the patch file correctly!!!!

here is where i am at:

```

adramalech@adramalech:~$ cd Desktop/vpnclient
adramalech@adramalech:~/Desktop/vpnclient$ ls
cisco_cert_mgr   IPSecDrvOSFunctions.h  linuxcniapi.h     vpnapi.h
Cniapi.h         IPSecDrvOS_linux.c     linuxkernelapi.c  vpnclient
config.h         IPSecDrvOS_linux.h     linux_os.h        vpnclient.ini
cvpnd            ipseclog               Makefile          vpnclient_init
driver_build.sh  libdriver.so           Makefile~         vpn_install
frag.c           libvpnapi.so           mtu.h             vpn_ioctl_linux.h
frag.h           license.rtf            sample.pcf        vpn_uninstall
GenDefs.h        license.txt            unixcniapi.h
interceptor.c    linuxcniapi.c          unixkernelapi.h
adramalech@adramalech:~/Desktop/vpnclient$ sudo ./vpn_install
[sudo] password for adramalech: 
Cisco Systems VPN Client Version 4.8.00 (0490) Linux Installer
Copyright (C) 1998-2005 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms. 


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.24-19-generic/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.24-19-generic/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.24-19-generic/build" will be used to build the module.

Is the above correct [y]

Making module
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/adramalech/Desktop/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/adramalech/Desktop/vpnclient/linuxcniapi.o
/home/adramalech/Desktop/vpnclient/linuxcniapi.c:12:26: error: linux/config.h: No such file or directory
In file included from /home/adramalech/Desktop/vpnclient/Cniapi.h:15,
                 from /home/adramalech/Desktop/vpnclient/linuxcniapi.c:27:
/home/adramalech/Desktop/vpnclient/GenDefs.h:110:2: warning: #warning 64 bit
In file included from /home/adramalech/Desktop/vpnclient/Cniapi.h:15,
                 from /home/adramalech/Desktop/vpnclient/linuxcniapi.c:27:
/home/adramalech/Desktop/vpnclient/GenDefs.h:111: error: conflicting types for ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
/home/adramalech/Desktop/vpnclient/linuxcniapi.c: In function ‘CniInjectReceive’:
/home/adramalech/Desktop/vpnclient/linuxcniapi.c:297: error: implicit declaration of function ‘skb_set_timestamp’
/home/adramalech/Desktop/vpnclient/linuxcniapi.c:331: error: ‘struct sk_buff’ has no member named ‘nh’
/home/adramalech/Desktop/vpnclient/linuxcniapi.c:332: error: ‘struct sk_buff’ has no member named ‘mac’
/home/adramalech/Desktop/vpnclient/linuxcniapi.c: In function ‘CniInjectSend’:
/home/adramalech/Desktop/vpnclient/linuxcniapi.c:454: error: ‘struct sk_buff’ has no member named ‘mac’
/home/adramalech/Desktop/vpnclient/linuxcniapi.c:455: error: ‘struct sk_buff’ has no member named ‘nh’
/home/adramalech/Desktop/vpnclient/linuxcniapi.c:458: error: ‘struct sk_buff’ has no member named ‘h’
/home/adramalech/Desktop/vpnclient/linuxcniapi.c:458: error: ‘struct sk_buff’ has no member named ‘nh’
make[2]: *** [/home/adramalech/Desktop/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/adramalech/Desktop/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".
adramalech@adramalech:~/Desktop/vpnclient$ 

```

then this is where i downloaded the patches and then tried to patch the files...

```

adramalech@adramalech:~/Desktop/vpnclient$ wget lamnk.com/vpnclient-linux-2.6.24-final.diff
--18:59:14--  http://lamnk.com/vpnclient-linux-2.6.24-final.diff
           => `vpnclient-linux-2.6.24-final.diff'
Resolving lamnk.com... 69.73.155.56
Connecting to lamnk.com|69.73.155.56|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3,989 (3.9K) [application/octet-stream]

100%[====================================>] 3,989         --.--K/s             

18:59:14 (134.81 MB/s) - `vpnclient-linux-2.6.24-final.diff' saved [3989/3989]

adramalech@adramalech:~/Desktop/vpnclient$ wget lamnk.com/cisco_skbuff_offset.patch
--18:59:29--  http://lamnk.com/cisco_skbuff_offset.patch
           => `cisco_skbuff_offset.patch'
Resolving lamnk.com... 69.73.155.56
Connecting to lamnk.com|69.73.155.56|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4,586 (4.5K) [application/octet-stream]

100%[====================================>] 4,586         --.--K/s             

18:59:30 (56.16 KB/s) - `cisco_skbuff_offset.patch' saved [4586/4586]

adramalech@adramalech:~/Desktop/vpnclient$ patch < ./vpnclient-linux-2.6.24-final.diff
patching file GenDefs.h
patching file interceptor.c
Hunk #1 succeeded at 24 (offset -4 lines).
Hunk #2 succeeded at 48 (offset -4 lines).
Hunk #3 FAILED at 107.
Hunk #4 succeeded at 123 (offset -23 lines).
Hunk #5 FAILED at 350.
Hunk #6 succeeded at 849 (offset -86 lines).
Hunk #7 succeeded at 891 (offset -86 lines).
2 out of 7 hunks FAILED -- saving rejects to file interceptor.c.rej
adramalech@adramalech:~/Desktop/vpnclient$ patch < ./cisco_skbuff_offset.patch
(Stripping trailing CRs from patch.)
patching file frag.c
Hunk #1 FAILED at 22.
1 out of 1 hunk FAILED -- saving rejects to file frag.c.rej
(Stripping trailing CRs from patch.)
patching file interceptor.c
Hunk #1 FAILED at 630.
Hunk #2 FAILED at 669.
Hunk #3 FAILED at 791.
3 out of 3 hunks FAILED -- saving rejects to file interceptor.c.rej
(Stripping trailing CRs from patch.)
patching file linuxcniapi.c
Hunk #1 FAILED at 338.
Hunk #2 FAILED at 483.
Hunk #3 FAILED at 497.
3 out of 3 hunks FAILED -- saving rejects to file linuxcniapi.c.rej
(Stripping trailing CRs from patch.)
patching file linuxkernelapi.c
adramalech@adramalech:~/Desktop/vpnclient$ 

```

and then i tried to run the install again...and got the same error as before with the install...i don't know what vpn client version i am using because the school's site that i downloaded it from i have these files...
```

adramalech@adramalech:~/Desktop/vpnclient$ ls
cisco_cert_mgr             frag.c         interceptor.c.orig     libdriver.so        linuxcniapi.c.rej  mtu.h            vpnclient.ini
cisco_skbuff_offset.patch  frag.c.orig    interceptor.c.rej      libvpnapi.so        linuxcniapi.h      sample.pcf       vpnclient_init
Cniapi.h                   frag.c.rej     IPSecDrvOSFunctions.h  license.rtf         linuxkernelapi.c   unixcniapi.h     vpnclient-linux-2.6.24-final.diff
config.h                   frag.h         IPSecDrvOS_linux.c     license.txt         linux_os.h         unixkernelapi.h  vpn_install
cvpnd                      GenDefs.h      IPSecDrvOS_linux.h     linuxcniapi.c       Makefile           vpnapi.h         vpn_ioctl_linux.h
driver_build.sh            interceptor.c  ipseclog               linuxcniapi.c.orig  Makefile~          vpnclient        vpn_uninstall
adramalech@adramalech:~/Desktop/vpnclient$ 


```

ciscovpn_4.8_linux..tar.gz  this is the file i downloaded and extracted is this the right one???:confused:

so pretty much what i am asking is there any way i can get someone to help me out...

---

### Post by casevh on 2008-09-23
I think your issue is a version mis-match between the Cisco client and the patches. The latest version is actually "vpnclient-linux-x86_64-4.8.02.0030-k9.tar" and I think that is what the patches assume.

HTH,

casevh

---

### Post by adramalech on 2008-09-24
thanks i will see if that will work...:lolflag:

---

### Post by adramalech on 2008-09-26
okay so i got it to patch and install correctly...now how do i get it to work??? like configure and start etc...

i don't know why but i have a script setup to black list everything except for ndiswrapper on my bcm4318 and the script should work everytime i log in...but yet i still see the ssb in the module name...like bcmwl5.inf and ssb are conflicting so that could be causing me issues with using vpn client until i can get my interent working...

---

