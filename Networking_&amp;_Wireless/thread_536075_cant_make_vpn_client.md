---
title: "cant make vpn client?"
date: 2007-08-27
forum: Networking &amp; Wireless
---

### Post by sdowney717 on 2007-08-27
gives me some error about config.h file which seems to be in the directory

scott@scott-desktop:~/vpnclient$ ls
cisco_cert_mgr   GenDefs.h              libdriver.so      linux_os.h       vpnclient
Cniapi.h         interceptor.c          libvpnapi.so      Makefile         vpnclient.ini
config.h         IPSecDrvOSFunctions.h  license.rtf       mtu.h            vpnclient_init
cvpnd            IPSecDrvOS_linux.c     license.txt       sample.pcf       vpn_install
driver_build.sh  IPSecDrvOS_linux.h     linuxcniapi.c     unixcniapi.h     vpn_ioctl_linux.h
frag.c           ipseclog               linuxcniapi.h     unixkernelapi.h  vpn_uninstall
frag.h           libdriver64.so         linuxkernelapi.c  vpnapi.h

scott@scott-desktop:~/vpnclient$ sudo ./vpn_install
Cisco Systems VPN Client Version 4.8.00 (0490) Linux Installer
Copyright (C) 1998-2005 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms. 


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]no

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.20-16-generic/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.20-16-generic/CiscoVPN".
* The VPN service will *NOT* be started automatically at boot time.
* Kernel source from "/lib/modules/2.6.20-16-generic/build" will be used to build the module.

Is the above correct [y]y

Making module
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/home/scott/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /home/scott/vpnclient/linuxcniapi.o
/home/scott/vpnclient/linuxcniapi.c:12:26: error: linux/config.h: No such file or directory
make[2]: *** [/home/scott/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/scott/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".
scott@scott-desktop:~/vpnclient$ sudo aptitude install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
scott@scott-desktop:~/vpnclient$

---

### Post by plumpy on 2007-08-27
Download [this patch]("http://www.longren.org/files/vpnclient-linux-2.6.22.diff") and apply it by typing (in a clean vpnclient directory):

```
patch -p1 < vpnclient-linux-2.6.22.diff
```

Then you should be able to install it like normal.

---

### Post by sdowney717 on 2007-08-28
thanks, it got thru the make.
I got a few warnings, could you glance thru this and see if it is alright?

root@scott-desktop:/home/scott/vpnclient# patch -p1 < vpnclient-linux-2.6.22.diff
patching file frag.c
patching file interceptor.c
patching file IPSecDrvOS_linux.c
patching file linuxcniapi.c
patching file linux_os.h
root@scott-desktop:/home/scott/vpnclient# ./vpn_install
Cisco Systems VPN Client Version 4.8.00 (0490) Linux Installer
Copyright (C) 1998-2005 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms. 


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]no

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.20-16-generic/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.20-16-generic/CiscoVPN".
* The VPN service will *NOT* be started automatically at boot time.
* Kernel source from "/lib/modules/2.6.20-16-generic/build" will be used to build the module.

Is the above correct [y]

Making module
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/home/scott/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /home/scott/vpnclient/linuxcniapi.o
  CC [M]  /home/scott/vpnclient/frag.o
  CC [M]  /home/scott/vpnclient/IPSecDrvOS_linux.o
  CC [M]  /home/scott/vpnclient/interceptor.o
/home/scott/vpnclient/interceptor.c: In function &#8216;handle_vpnup&#8217;:
/home/scott/vpnclient/interceptor.c:313: warning: assignment from incompatible pointer type
/home/scott/vpnclient/interceptor.c:337: warning: assignment from incompatible pointer type
/home/scott/vpnclient/interceptor.c:338: warning: assignment from incompatible pointer type
/home/scott/vpnclient/interceptor.c: In function &#8216;do_cleanup&#8217;:
/home/scott/vpnclient/interceptor.c:386: warning: assignment from incompatible pointer type
  CC [M]  /home/scott/vpnclient/linuxkernelapi.o
  LD [M]  /home/scott/vpnclient/cisco_ipsec.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: /home/scott/vpnclient/cisco_ipsec.o - Section mismatch: reference to .init.text: from .data between 'interceptor_dev' (at offset 0xb4) and 'interceptor_notifier'
WARNING: could not find /home/scott/vpnclient/.libdriver.so.cmd for /home/scott/vpnclient/libdriver.so
  CC      /home/scott/vpnclient/cisco_ipsec.mod.o
  LD [M]  /home/scott/vpnclient/cisco_ipsec.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
Create module directory "/lib/modules/2.6.20-16-generic/CiscoVPN".
Copying module to directory "/lib/modules/2.6.20-16-generic/CiscoVPN".
Already have group 'bin'

Creating start/stop script "/etc/init.d/vpnclient_init".
    /etc/init.d/vpnclient_init
Creating global config /etc/opt/cisco-vpnclient

Installing license.txt (VPN Client license) in "/opt/cisco-vpnclient/":

Installing bundled user profiles in "/etc/opt/cisco-vpnclient/Profiles/":
* New Profiles     : sample 

Copying binaries to directory "/opt/cisco-vpnclient/bin".
Adding symlinks to "/usr/local/bin".
    /opt/cisco-vpnclient/bin/vpnclient
    /opt/cisco-vpnclient/bin/cisco_cert_mgr
    /opt/cisco-vpnclient/bin/ipseclog
Copying setuid binaries to directory "/opt/cisco-vpnclient/bin".
    /opt/cisco-vpnclient/bin/cvpnd
Copying libraries to directory "/opt/cisco-vpnclient/lib".
    /opt/cisco-vpnclient/lib/libvpnapi.so
Copying header files to directory "/opt/cisco-vpnclient/include".
    /opt/cisco-vpnclient/include/vpnapi.h

Setting permissions.
    /opt/cisco-vpnclient/bin/cvpnd (setuid root)
    /opt/cisco-vpnclient (group bin readable)
    /etc/opt/cisco-vpnclient (group bin readable)
    /etc/opt/cisco-vpnclient/Profiles (group bin readable)
    /etc/opt/cisco-vpnclient/Certificates (group bin readable)
* You may wish to change these permissions to restrict access to root.
* You must run "/etc/init.d/vpnclient_init start" before using the client.
* You will need to run this script every time you reboot your computer.
root@scott-desktop:/home/scott/vpnclient#

---

### Post by sdowney717 on 2007-08-28
[http://72.14.253.104/search?q=cache:ef2Q5lIr5rIJ:www.mcmaster.ca/uts/network/vpn/vpnclient_linux.htm+.libdriver.so.cmd&hl=en&ct=clnk&cd=1&gl=us&client=firefox-a](http://72.14.253.104/search?q=cache:ef2Q5lIr5rIJ:www.mcmaster.ca/uts/network/vpn/vpnclient_linux.htm+.libdriver.so.cmd&hl=en&ct=clnk&cd=1&gl=us&client=firefox-a)

I found this page and theirs seems to match mine. So I think it is ok.
Reason I was trying to do this, my daughter is going to JMU and needs cisco VPN for wireless. And IF I dual booted her new vista laptop, I would have to figure out the vpn.

---

