---
title: "Trouble installing EDIMAX EW-7811UTC"
date: 2014-04-08
forum: Networking &amp; Wireless
---

### Post by greg45 on 2014-04-08
Hello all,

I've been trying for the past 6 hours to install the USB wifi device on a client's PC, with mixed progress.  I'm halfway through installation, but I keep running into errors when using the "sudo make" command, which I shall list here:

```
kathy@kathy-Dimension-2400:~/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517$sudo make[sudo] password for kathy: 
make ARCH=i386 CROSS_COMPILE= -C/lib/modules/3.11.0-19-generic/buildM=/home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517 modules
make[1]: Entering directory`/usr/src/linux-headers-3.11.0-19-generic'
  CC [M] /home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/core/rtw_cmd.o
  CC [M] /home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/core/rtw_security.o
  CC [M] /home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/core/rtw_debug.o
  CC [M] /home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/core/rtw_io.o
  CC [M] /home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/core/rtw_ioctl_query.o
  CC [M] /home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/core/rtw_ioctl_set.o
  CC [M] /home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/core/rtw_ieee80211.o
  CC [M] /home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/core/rtw_mlme.o
  CC [M] /home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/core/rtw_mlme_ext.o
  CC [M] /home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/core/rtw_wlan_util.o
  CC [M] /home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/core/rtw_vht.o
  CC [M] /home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/core/rtw_pwrctrl.o
  CC [M] /home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/core/rtw_rf.o
  CC [M] /home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/core/rtw_recv.o
  CC [M] /home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/core/rtw_sta_mgt.o
  CC [M] /home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/core/rtw_ap.o
  CC [M] /home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/core/rtw_xmit.o
  CC [M] /home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/core/rtw_p2p.o
  CC [M] /home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/core/rtw_tdls.o
  CC [M] /home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/core/rtw_br_ext.o
  CC [M] /home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/core/rtw_iol.o
  CC [M] /home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/core/rtw_sreset.o
  CC [M] /home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/core/efuse/rtw_efuse.o
  CC [M] /home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/os_dep/osdep_service.o
  CC [M] /home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/os_dep/linux/os_intfs.o
/home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/os_dep/linux/os_intfs.c:In function &#8216;rtw_proc_init_one&#8217;:
/home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/os_dep/linux/os_intfs.c:352:3:error: implicit declaration of function &#8216;create_proc_entry&#8217;[-Werror=implicit-function-declaration]
/home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/os_dep/linux/os_intfs.c:352:11:warning: assignment makes pointer from integer without a cast[enabled by default]
/home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/os_dep/linux/os_intfs.c:359:3:error: implicit declaration of function &#8216;create_proc_read_entry&#8217;[-Werror=implicit-function-declaration]
/home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/os_dep/linux/os_intfs.c:359:9:warning: assignment makes pointer from integer without a cast[enabled by default]
/home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/os_dep/linux/os_intfs.c:370:21:warning: assignment makes pointer from integer without a cast[enabled by default]
/home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/os_dep/linux/os_intfs.c:401:8:warning: assignment makes pointer from integer without a cast[enabled by default]
/home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/os_dep/linux/os_intfs.c:407:7:error: dereferencing pointer to incomplete type
/home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/os_dep/linux/os_intfs.c:409:8:warning: assignment makes pointer from integer without a cast[enabled by default]
/home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/os_dep/linux/os_intfs.c:415:7:error: dereferencing pointer to incomplete type
/home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/os_dep/linux/os_intfs.c:418:8:warning: assignment makes pointer from integer without a cast[enabled by default]
/home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/os_dep/linux/os_intfs.c:426:8:warning: assignment makes pointer from integer without a cast[enabled by default]
/home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/os_dep/linux/os_intfs.c:434:8:warning: assignment makes pointer from integer without a cast[enabled by default]
/home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/os_dep/linux/os_intfs.c:442:8:warning: assignment makes pointer from integer without a cast[enabled by default]
/home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/os_dep/linux/os_intfs.c:449:8:warning: assignment makes pointer from integer without a cast[enabled by default]
/home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/os_dep/linux/os_intfs.c:456:8:warning: assignment makes pointer from integer without a cast[enabled by default]
/home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/os_dep/linux/os_intfs.c:463:8:warning: assignment makes pointer from integer without a cast[enabled by default]
/home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/os_dep/linux/os_intfs.c:470:8:warning: assignment makes pointer from integer without a cast[enabled by default]
/home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/os_dep/linux/os_intfs.c:477:8:warning: assignment makes pointer from integer without a cast[enabled by default]
/home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/os_dep/linux/os_intfs.c:484:8:warning: assignment makes pointer from integer without a cast[enabled by default]
/home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/os_dep/linux/os_intfs.c:491:8:warning: assignment makes pointer from integer without a cast[enabled by default]
/home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/os_dep/linux/os_intfs.c:498:8:warning: assignment makes pointer from integer without a cast[enabled by default]
/home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/os_dep/linux/os_intfs.c:505:8:warning: assignment makes pointer from integer without a cast[enabled by default]
/home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/os_dep/linux/os_intfs.c:512:8:warning: assignment makes pointer from integer without a cast[enabled by default]
/home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/os_dep/linux/os_intfs.c:519:8:warning: assignment makes pointer from integer without a cast[enabled by default]
/home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/os_dep/linux/os_intfs.c:526:8:warning: assignment makes pointer from integer without a cast[enabled by default]
/home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/os_dep/linux/os_intfs.c:533:8:warning: assignment makes pointer from integer without a cast[enabled by default]
/home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/os_dep/linux/os_intfs.c:542:9:warning: assignment makes pointer from integer without a cast[enabled by default]
/home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/os_dep/linux/os_intfs.c:549:9:warning: assignment makes pointer from integer without a cast[enabled by default]
/home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/os_dep/linux/os_intfs.c:559:8:warning: assignment makes pointer from integer without a cast[enabled by default]
/home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/os_dep/linux/os_intfs.c:577:8:warning: assignment makes pointer from integer without a cast[enabled by default]
/home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/os_dep/linux/os_intfs.c:585:8:warning: assignment makes pointer from integer without a cast[enabled by default]
/home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/os_dep/linux/os_intfs.c:591:7:error: dereferencing pointer to incomplete type
/home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/os_dep/linux/os_intfs.c:593:8:warning: assignment makes pointer from integer without a cast[enabled by default]
/home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/os_dep/linux/os_intfs.c:599:7:error: dereferencing pointer to incomplete type
/home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/os_dep/linux/os_intfs.c:601:8:warning: assignment makes pointer from integer without a cast[enabled by default]
/home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/os_dep/linux/os_intfs.c:607:7:error: dereferencing pointer to incomplete type
/home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/os_dep/linux/os_intfs.c:609:8:warning: assignment makes pointer from integer without a cast[enabled by default]
/home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/os_dep/linux/os_intfs.c:615:7:error: dereferencing pointer to incomplete type
/home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/os_dep/linux/os_intfs.c:617:8:warning: assignment makes pointer from integer without a cast[enabled by default]
/home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/os_dep/linux/os_intfs.c:623:7:error: dereferencing pointer to incomplete type
/home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/os_dep/linux/os_intfs.c:626:8:warning: assignment makes pointer from integer without a cast[enabled by default]
/home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/os_dep/linux/os_intfs.c:629:8:warning: assignment makes pointer from integer without a cast[enabled by default]
/home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/os_dep/linux/os_intfs.c:635:7:error: dereferencing pointer to incomplete type
/home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/os_dep/linux/os_intfs.c:647:8:warning: assignment makes pointer from integer without a cast[enabled by default]
/home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/os_dep/linux/os_intfs.c:653:7:error: dereferencing pointer to incomplete type
cc1: some warnings being treated aserrors
make[2]: ***[/home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517/os_dep/linux/os_intfs.o]Error 1
make[1]: ***[_module_/home/kathy/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517]Error 2
make[1]: Leaving directory`/usr/src/linux-headers-3.11.0-19-generic'
make: *** [modules] Error 2
kathy@kathy-Dimension-2400:~/Downloads/bob/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517$  
```

A few things to note:

This PC is using Ubuntu 12.04

The driver is downloaded from the EDIMAX website

I have limited experience with Ubuntu

The client does not want to spend money on a new PC

The instructions included with the wifi device are poorly written, listing entirely different file names.

If anyone could help, I'd greatly appreciate it.

---

### Post by chili555 on 2014-04-08
I think you will have better luck with:```
sudo apt-get install git
git clone https://github.com/gnab/rtl8812au.git
cd rtl8812au
make
sudo make install
sudo modprobe 8812au
```It 'makes' with quite a few warnings but no error on my 3.11.0-xx system. I haven't the device, so I can test no further.> The instructions included with the wifi device are poorly written, listing entirely different file names.
That's quite often the case; as well, the driver files are often outdated.

---

### Post by kurt18947 on 2014-04-08
I have no clue if this is of any use or not because I don't have that adapter, or an AC adapter for that matter.  If it were from Larry Finger I'd have more confidence in it.

[https://github.com/gnab/rtl8812au](https://github.com/gnab/rtl8812au)

---

### Post by greg45 on 2014-04-08
Awesome!  Thanks for the quick reply.  Will try chili555's suggestion first.

---

### Post by greg45 on 2014-04-08
I am posting this reply over wifi using the suggestion chili555 gave.  Thanks, you're a lifesaver!

---

### Post by chili555 on 2014-04-08
Until the driver is included in the mainline kernel, you will need to recompile whenever Update Manager installs a later kernel, known in Ubuntu World as linux-image. After the requisite reboot:```
cd ~/rtl8812au
make clean
make
sudo make install
sudo modprobe 8812au
```Please retain the file and these instructions for that time.

Please use thread tools at the top to mark Solved. The searchers will appreciate it.

---

### Post by exactt on 2014-07-21
Although it is in German here you get a nice solution using DKMS: [https://www.debinux.de/2014/06/sitecom-wifi-usb-adapter-ac1200-treiber-dkms-einrichtung-unter-ubuntu/](https://www.debinux.de/2014/06/sitecom-wifi-usb-adapter-ac1200-treiber-dkms-einrichtung-unter-ubuntu/)

---

