---
title: "rt2500 driver on a patched kernel"
date: 2005-08-02
forum: Networking &amp; Wireless
---

### Post by traaf on 2005-08-02
hi everyone
newb on linux, i installed ubuntu 5.04 hoary on my pc
i have a 802.11g card i installed easily following this tutorial
[https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/](https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/)

but unfortunately, my motherboard is a asus p5gd1, with a it8212 ide/raid controller, unsupported by ubuntu

to activate it, i needed to apply a patch, alan cox -ac patch
as you can see on [www.kernel.org](www.kernel.org) home page, it is available with 2.6.11 kernel
and is not valid for ubuntu kernels

so i had to get 2.6.11 generic kernel and patch it with 2.6.11ac7 patch

i tried to reinstall the driver with the same method, but there's no linux-headers-2.6.11ac7
i tried ubuntu linux-headers 2.6.11-1 and 2.6.11-1-386
but creating module fails

is there any way to fix this issue?

now i have to boot with old 2.6.10-5-386 kernel if i want web acces
and with 2.6.11ac7 kernel if i want to use cd and dvd drives, that are on it8212 controller

my only ide standard controller is busy with 2 HD

thx for your help

traaf

---

### Post by traaf on 2005-08-22
up

??no none??


in fact, the module is created, i find the rt2500.ko file but

ocalhost modprobe: FATAL: Error inserting rt2500 (/lib/modules/2.6.11ac7/kernel/drivers/net/wireless/rt2500.ko): Invalid module format

any idea?

---

### Post by traaf on 2005-08-22
i did it again
it gives
```

regis@ubuntu:~$ tar -xzf rt2500-cvs-daily.tar.gz
regis@ubuntu:~$ cd ./rt2500-cvs-20050609/Module
regis@ubuntu:~/rt2500-cvs-20050609/Module$ make
make[1]: entrant dans le répertoire « /usr/src/linux-2.6.11ac7 »
  CC [M]  /home/regis/rt2500-cvs-20050609/Module/rtmp_main.o
  CC [M]  /home/regis/rt2500-cvs-20050609/Module/mlme.o
  CC [M]  /home/regis/rt2500-cvs-20050609/Module/connect.o
  CC [M]  /home/regis/rt2500-cvs-20050609/Module/sync.o
  CC [M]  /home/regis/rt2500-cvs-20050609/Module/assoc.o
  CC [M]  /home/regis/rt2500-cvs-20050609/Module/auth.o
  CC [M]  /home/regis/rt2500-cvs-20050609/Module/auth_rsp.o
  CC [M]  /home/regis/rt2500-cvs-20050609/Module/rtmp_data.o
  CC [M]  /home/regis/rt2500-cvs-20050609/Module/rtmp_init.o
  CC [M]  /home/regis/rt2500-cvs-20050609/Module/sanity.o
  CC [M]  /home/regis/rt2500-cvs-20050609/Module/rtmp_wep.o
  CC [M]  /home/regis/rt2500-cvs-20050609/Module/wpa.o
  CC [M]  /home/regis/rt2500-cvs-20050609/Module/md5.o
  CC [M]  /home/regis/rt2500-cvs-20050609/Module/rtmp_tkip.o
  CC [M]  /home/regis/rt2500-cvs-20050609/Module/rtmp_info.o
  CC [M]  /home/regis/rt2500-cvs-20050609/Module/eeprom.o
  LD [M]  /home/regis/rt2500-cvs-20050609/Module/rt2500.o
  Building modules, stage 2.
  MODPOST
  CC      /home/regis/rt2500-cvs-20050609/Module/rt2500.mod.o
  LD [M]  /home/regis/rt2500-cvs-20050609/Module/rt2500.ko
make[1]: quittant le répertoire « /usr/src/linux-2.6.11ac7 »
regis@ubuntu:~/rt2500-cvs-20050609/Module$ sudo insmod rt2500.ko
regis@ubuntu:~/rt2500-cvs-20050609/Module$ sudo modinfo ./rt2500.ko
filename:       ./rt2500.ko
parm:           debug:Enable level: accepted values: 1 to switch debug on, 0 to switch debug off.
parm:           ifname:Network device name (default ra%d)
author:         http://rt2x00.serialmonkey.com
description:    Ralink RT2500 802.11g WLAN driver 1.1.0 BETA2 2005/02/21
license:        GPL
vermagic:       2.6.11ac7 SMP preempt PENTIUM4 4KSTACKS gcc-3.3
depends:
alias:          pci:v00001814d00000201sv*sd*bc*sc*i*
regis@ubuntu:~/rt2500-cvs-20050609/Module$sudo modprobe rt2500.ko
FATAL: Module rt2500.ko not found.
regis@ubuntu:~/rt2500-cvs-20050609/Module$

```
thx

---

