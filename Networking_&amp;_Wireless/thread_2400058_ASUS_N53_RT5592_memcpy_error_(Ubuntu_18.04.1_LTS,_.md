---
title: "ASUS N53 RT5592 memcpy error (Ubuntu 18.04.1 LTS, Linux 4.15.0-29-generic)"
date: 2018-09-01
forum: Networking &amp; Wireless
---

### Post by mmiguel on 2018-09-01
I am trying to get my ASUS N53 PCI-E wireless adaptor working with bionic.
There are a few github repos that seem to have solved this for previous versions of Ubuntu, but I run into what seems to be a new problem when I try them.
 
[https://github.com/mareksuscak/asus-pce-n53-linux](https://github.com/mareksuscak/asus-pce-n53-linux)
[https://github.com/kuttor/Asus-N53-PCU-RT5592STA-Driver-for-Linux-Kernel-4.6-Ubuntu-16.10](https://github.com/kuttor/Asus-N53-PCU-RT5592STA-Driver-for-Linux-Kernel-4.6-Ubuntu-16.10)

When running make on either of these, I get the following error:[INDENT]In function &#8216;memcpy&#8217;,
    inlined from &#8216;rt_ioctl_iwaplist&#8217; at /opt/asus-n53/os/linux/../../os/linux/sta_ioctl.c:697:2:
./include/linux/string.h:340:4: error: call to &#8216;__read_overflow2&#8217; declared with attribute error: detected read beyond size of object passed as 2nd parameter
    __read_overflow2();
    ^~~~~~~~~~~~~~~~~~
scripts/Makefile.build:332: recipe for target '/opt/asus-n53/os/linux/../../os/linux/sta_ioctl.o' failed
make[2]: *** [/opt/asus-n53/os/linux/../../os/linux/sta_ioctl.o] Error 1
Makefile:1552: recipe for target '_module_/opt/asus-n53/os/linux' failed
make[1]: *** [_module_/opt/asus-n53/os/linux] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.15.0-29-generic'
Makefile:384: recipe for target 'LINUX' failed
make: *** [LINUX] Error 2


[/INDENT]
I am not sure how to proceed.
Any thoughts would be appreciated.

---

