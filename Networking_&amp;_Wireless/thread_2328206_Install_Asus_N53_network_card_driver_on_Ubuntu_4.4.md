---
title: "Install Asus N53 network card driver on Ubuntu 4.4.x"
date: 2016-06-18
forum: Networking &amp; Wireless
---

### Post by azzuri3 on 2016-06-18
I am newbie to Ubuntu and tried to follow the solution posted on old thread [here]("http://ubuntuforums.org/showthread.php?t=2203226") is. But i am getting this-. Please assist

```
root@mane:/home/mohan/Downloads/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326# make
make -C tools
make[1]: Entering directory '/home/mohan/Downloads/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory '/home/mohan/Downloads/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/tools'
/home/mohan/Downloads/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/tools/bin2h
cp -f os/linux/Makefile.6 /home/mohan/Downloads/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/Makefile
make -C /lib/modules/4.4.0-24-generic/build SUBDIRS=/home/mohan/Downloads/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux modules
make[1]: Entering directory '/usr/src/linux-headers-4.4.0-24-generic'
  CC [M]  /home/mohan/Downloads/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../sta/sta_cfg.o
In file included from /home/mohan/Downloads/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_os.h:44:0,
                 from /home/mohan/Downloads/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_comm.h:69,
                 from /home/mohan/Downloads/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rt_config.h:33,
                 from /home/mohan/Downloads/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../sta/sta_cfg.c:28:
/home/mohan/Downloads/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../sta/sta_cfg.c: In function &#8216;RTMPQueryInformation&#8217;:
/home/mohan/Downloads/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../sta/sta_cfg.c:3953:30: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 2 has type &#8216;long unsigned int&#8217; [-Wformat=]
    DBGPRINT(RT_DEBUG_TRACE, ("sizeof UCHAR=%d, channel=%d \n", sizeof(UCHAR), p
                              ^
/home/mohan/Downloads/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/os/rt_linux.h:665:16: note: in definition of macro &#8216;DBGPRINT_RAW&#8217;
         printk Fmt;               \
                ^
/home/mohan/Downloads/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../sta/sta_cfg.c:3953:4: note: in expansion of macro &#8216;DBGPRINT&#8217;
    DBGPRINT(RT_DEBUG_TRACE, ("sizeof UCHAR=%d, channel=%d \n", sizeof(UCHAR), p
    ^
/home/mohan/Downloads/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../sta/sta_cfg.c: In function &#8216;RTMPIoctlShow&#8217;:
/home/mohan/Downloads/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../sta/sta_cfg.c:4896:85: error: macro "__DATE__" might prevent reproducible builds [-Werror=date-time]
 intf(extra, size, "Driver version-%s, %s %s\n", STA_DRIVER_VERSION, __DATE__, _
                                                                     ^
/home/mohan/Downloads/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../sta/sta_cfg.c:4896:95: error: macro "__TIME__" might prevent reproducible builds [-Werror=date-time]
 , size, "Driver version-%s, %s %s\n", STA_DRIVER_VERSION, __DATE__, __TIME__ );
                                                                     ^
cc1: some warnings being treated as errors
scripts/Makefile.build:258: recipe for target '/home/mohan/Downloads/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../sta/sta_cfg.o' failed
make[2]: *** [/home/mohan/Downloads/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../sta/sta_cfg.o] Error 1
Makefile:1402: recipe for target '_module_/home/mohan/Downloads/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux' failed
make[1]: *** [_module_/home/mohan/Downloads/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.4.0-24-generic'
Makefile:381: recipe for target 'LINUX' failed
make: *** [LINUX] Error 2
root@mane:/home/mohan/Downloads/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326# 

if I continue to make install -
root@mane:/home/mohan/Downloads/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326# make install
make -C /home/mohan/Downloads/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux -f Makefile.6 install
make[1]: Entering directory '/home/mohan/Downloads/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux'
mkdir: cannot create directory &#8216;/etc/Wireless&#8217;: File exists
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
cp /home/mohan/Downloads/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/RT2860STA.dat /etc/Wireless/RT2860STA/.
install -d /lib/modules/4.4.0-24-generic/kernel/drivers/net/wireless/
install -m 644 -c rt5592sta.ko /lib/modules/4.4.0-24-generic/kernel/drivers/net/wireless/
install: cannot stat 'rt5592sta.ko': No such file or directory
Makefile.6:294: recipe for target 'install' failed
make[1]: *** [install] Error 1
make[1]: Leaving directory '/home/mohan/Downloads/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux'
Makefile:474: recipe for target 'install' failed
make: *** [install] Error 2
root@mane:/home/mohan/Downloads/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326#
```

---

### Post by chili555 on 2016-06-18
> DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_[COLOR="#FF0000"]2012[/COLOR]0326We really can't bolt wooden wheels on our shiny new 4.4 kernels. The package you downloaded is too old and there are too many structural differences between the 2.6 kernel that I suspect it was written for and the 4.4 kernel you are trying to compile it for.

Let's begin at the beginning. Please run and post:```
lspci -nnk | grep 0280 -A2
```Thanks.

---

