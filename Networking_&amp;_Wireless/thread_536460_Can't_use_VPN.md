---
title: "Can't use VPN"
date: 2007-08-27
forum: Networking &amp; Wireless
---

### Post by angryfirelord on 2007-08-27
My campus has wifi all over the place, but I can't seem to to build VPN. I have installed the patch and changed all config.h headers to autoconf.h, yet I still can't build it. Here's the output:

```
master@ubuntu:~/vpnclient$ sudo ./vpn_install
Cisco Systems VPN Client Version 4.8.00 (0490) Linux Installer
Copyright (C) 1998-2005 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms. 


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.20-16-generic/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.20-16-generic/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.20-16-generic/build" will be used to build the module.

Is the above correct [y]

Making module
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/home/master/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /home/master/vpnclient/interceptor.o
/home/master/vpnclient/interceptor.c: In function ‘handle_vpnup’:
/home/master/vpnclient/interceptor.c:310: warning: assignment from incompatible pointer type
/home/master/vpnclient/interceptor.c:334: warning: assignment from incompatible pointer type
/home/master/vpnclient/interceptor.c:335: warning: assignment from incompatible pointer type
/home/master/vpnclient/interceptor.c: In function ‘do_cleanup’:
/home/master/vpnclient/interceptor.c:378: warning: assignment from incompatible pointer type
/home/master/vpnclient/interceptor.c: In function ‘recv_ip_packet_handler’:
/home/master/vpnclient/interceptor.c:557: error: too many arguments to function ‘skb_checksum_help’
/home/master/vpnclient/interceptor.c: In function ‘do_cni_send’:
/home/master/vpnclient/interceptor.c:683: error: too many arguments to function ‘skb_checksum_help’
make[2]: *** [/home/master/vpnclient/interceptor.o] Error 1
make[1]: *** [_module_/home/master/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".
```

Any ideas?

---

### Post by plumpy on 2007-08-27
Which patch are you using?

Try [this one]("http://www.longren.org/files/vpnclient-linux-2.6.22.diff")?  Apply it to a clean vpnclient directory and you shouldn't need to make any other additional changes.

---

### Post by linuxfreakus on 2007-09-19
Awesome, I was just going through that code myself trying to figure out the errors, luckily, I decided to check google before spending too much effort.  The patch worked great for me.

---

