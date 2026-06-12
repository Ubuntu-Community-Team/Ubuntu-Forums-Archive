---
title: "Lenovo z40, Realtek RTL r8168"
date: 2015-02-09
forum: Networking &amp; Wireless
---

### Post by Haven_McClure on 2015-02-09
Hi, I have a Lenovo z40 laptop and the wireless doesn't work at all with Ubuntu Studio 14.10.  In reading mulitple forums, it seems that I need to download the driver for Realtek RTL r8168 and blacklist r8169.  I have downloaded r8168 but run into error messages after trying to build the kernel:

```

haven@haven-Lenovo-Z40-70:~/Downloads$ sudo dpkg -i *.deb
[sudo] password for haven: 
(Reading database ... 283768 files and directories currently installed.)
Preparing to unpack dkms_2.2.0.3-1.1ubuntu5_all.deb ...
Unpacking dkms (2.2.0.3-1.1ubuntu5) over (2.2.0.3-1.1ubuntu5) ...
Setting up dkms (2.2.0.3-1.1ubuntu5) ...
Processing triggers for man-db (2.7.0.2-2) ...
haven@haven-Lenovo-Z40-70:~/Downloads$ sudo tar xvf 3005217-r8168-dkms-8.038.00.tar.gz -C /usr/src
r8168-dkms-8.038.00/src/Makefile
r8168-dkms-8.038.00/src/Makefile_linux24x
r8168-dkms-8.038.00/src/r8168.h
r8168-dkms-8.038.00/src/r8168_asf.c
r8168-dkms-8.038.00/src/r8168_asf.h
r8168-dkms-8.038.00/src/r8168_dash.h
r8168-dkms-8.038.00/src/r8168_n.c
r8168-dkms-8.038.00/src/rtltool.c
r8168-dkms-8.038.00/src/rtltool.h
r8168-dkms-8.038.00/src/rtl_eeprom.c
r8168-dkms-8.038.00/src/rtl_eeprom.h
r8168-dkms-8.038.00/dkms.conf
r8168-dkms-8.038.00/autorun.sh
r8168-dkms-8.038.00/Makefile
r8168-dkms-8.038.00/README
r8168-dkms-8.038.00/src/
r8168-dkms-8.038.00/
haven@haven-Lenovo-Z40-70:~/Downloads$ sudo dkms add -m r8168-dkms -v 8.038.00
Error! DKMS tree already contains: r8168-dkms-8.038.00
You cannot add the same module/version combo more than once.

haven@haven-Lenovo-Z40-70:~/Downloads$ sudo dkms build -m r8168-dkms -v 8.038.00 
Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
'make' -C src/ all............(bad exit status: 2)
ERROR (dkms apport): binary package for r8168-dkms: 8.038.00 not found
Error! Bad return status for module build on kernel: 3.16.0-30-lowlatency (x86_64)
Consult /var/lib/dkms/r8168-dkms/8.038.00/build/make.log for more information.

```

So I consulted that file and this is what it told me:

```
 
Mon Feb  9 12:38:05 CST 2015
make: Entering directory '/var/lib/dkms/r8168-dkms/8.038.00/build/src'
make -C /lib/modules/3.16.0-30-lowlatency/build SUBDIRS=/var/lib/dkms/r8168-dkms/8.038.00/build/src clean
make[1]: Entering directory '/usr/src/linux-headers-3.16.0-30-lowlatency'
make[1]: Leaving directory '/usr/src/linux-headers-3.16.0-30-lowlatency'
make -C /lib/modules/3.16.0-30-lowlatency/build SUBDIRS=/var/lib/dkms/r8168-dkms/8.038.00/build/src modules
make[1]: Entering directory '/usr/src/linux-headers-3.16.0-30-lowlatency'
  CC [M]  /var/lib/dkms/r8168-dkms/8.038.00/build/src/r8168_n.o
/var/lib/dkms/r8168-dkms/8.038.00/build/src/r8168_n.c: In function &#8216;rtl8168_init_one&#8217;:
/var/lib/dkms/r8168-dkms/8.038.00/build/src/r8168_n.c:17545:5: error: implicit declaration of function &#8216;SET_ETHTOOL_OPS&#8217; [-Werror=implicit-function-declaration]
     SET_ETHTOOL_OPS(dev, &rtl8168_ethtool_ops);
     ^
/var/lib/dkms/r8168-dkms/8.038.00/build/src/r8168_n.c: In function &#8216;rtl8168_schedule_work&#8217;:
/var/lib/dkms/r8168-dkms/8.038.00/build/src/r8168_n.c:19122:5: error: implicit declaration of function &#8216;PREPARE_DELAYED_WORK&#8217; [-Werror=implicit-function-declaration]
     PREPARE_DELAYED_WORK(&tp->task, task);
     ^
cc1: some warnings being treated as errors
scripts/Makefile.build:257: recipe for target '/var/lib/dkms/r8168-dkms/8.038.00/build/src/r8168_n.o' failed
make[2]: *** [/var/lib/dkms/r8168-dkms/8.038.00/build/src/r8168_n.o] Error 1
Makefile:1345: recipe for target '_module_/var/lib/dkms/r8168-dkms/8.038.00/build/src' failed
make[1]: *** [_module_/var/lib/dkms/r8168-dkms/8.038.00/build/src] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-3.16.0-30-lowlatency'
Makefile:70: recipe for target 'modules' failed
make: *** [modules] Error 2
make: Leaving directory '/var/lib/dkms/r8168-dkms/8.038.00/build/src'

```

So I get stuck when trying to rebuild the kernel.  I've been consulting the following threads:

[http://ubuntuforums.org/showthread.php?t=2238805](http://ubuntuforums.org/showthread.php?t=2238805)
[http://ubuntuforums.org/showthread.php?t=2261277](http://ubuntuforums.org/showthread.php?t=2261277)
[http://ubuntuforums.org/showthread.php?t=2238805](http://ubuntuforums.org/showthread.php?t=2238805)

Any ideas as to where i can go from here?

---

### Post by Haven_McClure on 2015-02-12
cancel

---

### Post by Haven_McClure on 2015-02-12
Okay, now I'm embarrassed.  Turns out I had a Broadcom, with the Realtek being the Ethernet port.  Now I feel completely stupid.  Problem is now solved.

---

### Post by sabman83 on 2015-09-07
So if it Broadcom, how did you resolve your original issue of the ethernet not connecting?

---

### Post by jeremy31 on 2015-09-07
> **sabman83 said:**
> So if it Broadcom, how did you resolve your original issue of the ethernet not connecting?

Reread the original post, it was a wireless issue.  If you have a ethernet issue, please feel free to start your own topic

---

### Post by PaulW2U on 2015-09-07
Closing old "solved" thread.

sabman83, please start a new thread for whatever problems you are experiencing.

---

