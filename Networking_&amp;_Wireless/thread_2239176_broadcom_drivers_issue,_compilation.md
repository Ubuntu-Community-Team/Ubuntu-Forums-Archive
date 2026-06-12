---
title: "broadcom drivers issue, compilation"
date: 2014-08-12
forum: Networking &amp; Wireless
---

### Post by Igor_Matveyevskii on 2014-08-12
Hello every one,
I have Ubuntu 12.04 and kernel version is 3.11.0-15-generic
I downloaded linux source via command

```
apt-get source linux-image-3.11.0-15-generic
```

After that I tried to compile broadcom drivers and got following error:

```
root@VirtualBox:~/linux-lts-saucy-3.11.0/drivers/net/ethernet/broadcom# make -C /lib/modules/3.11.0-15-generic/build M=`pwd` modulesmake: Entering directory `/usr/src/linux-headers-3.11.0-15-generic'
  CC [M]  /root/linux-lts-saucy-3.11.0/drivers/net/ethernet/broadcom/b44.o
  CC [M]  /root/linux-lts-saucy-3.11.0/drivers/net/ethernet/broadcom/bnx2.o
  CC [M]  /root/linux-lts-saucy-3.11.0/drivers/net/ethernet/broadcom/cnic.o
/root/linux-lts-saucy-3.11.0/drivers/net/ethernet/broadcom/cnic.c: In function &#8216;cnic_start_bnx2_hw&#8217;:
/root/linux-lts-saucy-3.11.0/drivers/net/ethernet/broadcom/cnic.c:4822:1: warning: the frame size of 1312 bytes is larger than 1024 bytes [-Wframe-larger-than=]
  CC [M]  /root/linux-lts-saucy-3.11.0/drivers/net/ethernet/broadcom/tg3.o
  CC [M]  /root/linux-lts-saucy-3.11.0/drivers/net/ethernet/broadcom/bnx2x/bnx2x_main.o
  CC [M]  /root/linux-lts-saucy-3.11.0/drivers/net/ethernet/broadcom/bnx2x/bnx2x_link.o
  CC [M]  /root/linux-lts-saucy-3.11.0/drivers/net/ethernet/broadcom/bnx2x/bnx2x_cmn.o
  CC [M]  /root/linux-lts-saucy-3.11.0/drivers/net/ethernet/broadcom/bnx2x/bnx2x_ethtool.o
  CC [M]  /root/linux-lts-saucy-3.11.0/drivers/net/ethernet/broadcom/bnx2x/bnx2x_stats.o
  CC [M]  /root/linux-lts-saucy-3.11.0/drivers/net/ethernet/broadcom/bnx2x/bnx2x_dcb.o
  CC [M]  /root/linux-lts-saucy-3.11.0/drivers/net/ethernet/broadcom/bnx2x/bnx2x_sp.o
/root/linux-lts-saucy-3.11.0/drivers/net/ethernet/broadcom/bnx2x/bnx2x_sp.c: In function &#8216;bnx2x_vlan_mac_restore&#8217;:
/root/linux-lts-saucy-3.11.0/drivers/net/ethernet/broadcom/bnx2x/bnx2x_sp.c:1062:3: error: implicit declaration of function &#8216;list_next_entry&#8217; [-Werror=implicit-function-declaration]
/root/linux-lts-saucy-3.11.0/drivers/net/ethernet/broadcom/bnx2x/bnx2x_sp.c:1062:34: error: &#8216;link&#8217; undeclared (first use in this function)
/root/linux-lts-saucy-3.11.0/drivers/net/ethernet/broadcom/bnx2x/bnx2x_sp.c:1062:34: note: each undeclared identifier is reported only once for each function it appears in
cc1: some warnings being treated as errors
make[2]: *** [/root/linux-lts-saucy-3.11.0/drivers/net/ethernet/broadcom/bnx2x/bnx2x_sp.o] Error 1
make[1]: *** [/root/linux-lts-saucy-3.11.0/drivers/net/ethernet/broadcom/bnx2x] Error 2
make: *** [_module_/root/linux-lts-saucy-3.11.0/drivers/net/ethernet/broadcom] Error 2
make: Leaving directory `/usr/src/linux-headers-3.11.0-15-generic'
root@VirtualBox:~/linux-lts-saucy-3.11.0/drivers/net/ethernet/broadcom# 



```

Where is my mistake?

---

### Post by varunendra on 2014-08-12
Welcome to Ubuntu Forums Igor !

Why are you trying to compile broadcom drivers from source? Are the supplied ones not good enough? Or are you experimenting with something?

How much familiar you are with Linux and package compilation?

Answer to these questions and details of what you are trying to achieve may help us help you.

---

### Post by Igor_Matveyevskii on 2014-08-13
I need to add some functionality in this driver. But now I compile virgin code that I downloaded. This is my first time in compilation modules.

---

