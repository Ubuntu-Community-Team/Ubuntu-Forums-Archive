---
title: "Linksys USB6300"
date: 2014-01-19
forum: Networking &amp; Wireless
---

### Post by Toaster on 2014-01-19
Hi all, I use to be running windows for plex(media server), and I thought I would give ubuntu a try for a change I have everything setup great, but I can't get the wireless drivers to install for a wireless USB dongle. I did a 'lsusb' and found the device in the list:

'Bus 002 Device 006: ID 13b1:003f Linksys'

But I don't have any drivers to install for it. Checked linksys website and they don't have any on there. I also did a google search but I came up empty handed. Does anyone have this device working with ubuntu, or have any suggestions?

Thanks,
-Toaster

---

### Post by praseodym on 2014-01-19
Hi,

this is a brand new device which needs a seperate driver. Install it via LAN connection:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential
wget media.cdn.ubuntu-de.org/forum/attachments/29/51/6222752-rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100.tar.gz
tar xvf 6222752-rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100.tar.gz 
cd rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100
make
sudo make install 
```(You better copy/paste these line ;) )

Load the driver and check:
```
modinfo 8812au | egrep -i 'versi|filen|003f'
sudo modprobe -v 8812au
iwconfig
iwlist chan
```
Do not remove the driver folder. After a kernel update you need to compile again:
 ```
cd rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100
make clean
make
sudo make install 
```
For those interested, here in the grey boxes the supported IDs are mentioned (or use "modinfo 8812au")
[http://forum.ubuntuusers.de/topic/problem-mit-netgear-wlan-mini-adapter-wps-a610/?highlight=13b1%3A003f#post-6222752](http://forum.ubuntuusers.de/topic/problem-mit-netgear-wlan-mini-adapter-wps-a610/?highlight=13b1%3A003f#post-6222752)
Some IDs were added, too (2nd grey box)

---

### Post by Toaster on 2014-01-19
Getting some errors on the make with the first block of code. I think it might have something to do with my ubuntu version..

Which is:
Distributor ID:	Ubuntu
Description:	Ubuntu 13.10
Release:	13.10
Codename:	saucy


The error is here:

> make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.11.0-15-generic/build M=/home/toaster/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100  modules
make[1]: Entering directory `/usr/src/linux-headers-3.11.0-15-generic'
  CC [M]  /home/toaster/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100/os_dep/linux/os_intfs.o
/home/toaster/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100/os_dep/linux/os_intfs.c: In function ‘rtw_proc_init_one’:
/home/toaster/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100/os_dep/linux/os_intfs.c:352:3: error: implicit declaration of function ‘create_proc_entry’ [-Werror=implicit-function-declaration]
   rtw_proc=create_proc_entry(rtw_proc_name, S_IFDIR, init_net.proc_net);
   ^
/home/toaster/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100/os_dep/linux/os_intfs.c:352:11: warning: assignment makes pointer from integer without a cast [enabled by default]
   rtw_proc=create_proc_entry(rtw_proc_name, S_IFDIR, init_net.proc_net);
           ^
/home/toaster/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100/os_dep/linux/os_intfs.c:359:3: error: implicit declaration of function ‘create_proc_read_entry’ [-Werror=implicit-function-declaration]
   entry = create_proc_read_entry("ver_info", S_IFREG | S_IRUGO, rtw_proc, proc_get_drv_version, dev);
   ^
/home/toaster/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100/os_dep/linux/os_intfs.c:359:9: warning: assignment makes pointer from integer without a cast [enabled by default]
   entry = create_proc_read_entry("ver_info", S_IFREG | S_IRUGO, rtw_proc, proc_get_drv_version, dev);
         ^
/home/toaster/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100/os_dep/linux/os_intfs.c:370:21: warning: assignment makes pointer from integer without a cast [enabled by default]
   padapter->dir_dev = create_proc_entry(dev->name,
                     ^
/home/toaster/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100/os_dep/linux/os_intfs.c:401:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("write_reg", S_IFREG | S_IRUGO,
        ^
/home/toaster/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100/os_dep/linux/os_intfs.c:407:7: error: dereferencing pointer to incomplete type
  entry->write_proc = proc_set_write_reg;
       ^
/home/toaster/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100/os_dep/linux/os_intfs.c:409:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("read_reg", S_IFREG | S_IRUGO,
        ^
/home/toaster/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100/os_dep/linux/os_intfs.c:415:7: error: dereferencing pointer to incomplete type
  entry->write_proc = proc_set_read_reg;
       ^
/home/toaster/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100/os_dep/linux/os_intfs.c:418:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("fwstate", S_IFREG | S_IRUGO,
        ^
/home/toaster/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100/os_dep/linux/os_intfs.c:426:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("sec_info", S_IFREG | S_IRUGO,
        ^
/home/toaster/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100/os_dep/linux/os_intfs.c:434:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("mlmext_state", S_IFREG | S_IRUGO,
        ^
/home/toaster/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100/os_dep/linux/os_intfs.c:442:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("qos_option", S_IFREG | S_IRUGO,
        ^
/home/toaster/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100/os_dep/linux/os_intfs.c:449:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("ht_option", S_IFREG | S_IRUGO,
        ^
/home/toaster/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100/os_dep/linux/os_intfs.c:456:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("rf_info", S_IFREG | S_IRUGO,
        ^
/home/toaster/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100/os_dep/linux/os_intfs.c:463:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("ap_info", S_IFREG | S_IRUGO,
        ^
/home/toaster/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100/os_dep/linux/os_intfs.c:470:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("adapter_state", S_IFREG | S_IRUGO,
        ^
/home/toaster/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100/os_dep/linux/os_intfs.c:477:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("trx_info", S_IFREG | S_IRUGO,
        ^
/home/toaster/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100/os_dep/linux/os_intfs.c:484:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("mac_reg_dump1", S_IFREG | S_IRUGO,
        ^
/home/toaster/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100/os_dep/linux/os_intfs.c:491:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("mac_reg_dump2", S_IFREG | S_IRUGO,
        ^
/home/toaster/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100/os_dep/linux/os_intfs.c:498:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("mac_reg_dump3", S_IFREG | S_IRUGO,
        ^
/home/toaster/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100/os_dep/linux/os_intfs.c:505:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("bb_reg_dump1", S_IFREG | S_IRUGO,
        ^
/home/toaster/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100/os_dep/linux/os_intfs.c:512:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("bb_reg_dump2", S_IFREG | S_IRUGO,
        ^
/home/toaster/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100/os_dep/linux/os_intfs.c:519:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("bb_reg_dump3", S_IFREG | S_IRUGO,
        ^
/home/toaster/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100/os_dep/linux/os_intfs.c:526:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("rf_reg_dump1", S_IFREG | S_IRUGO,
        ^
/home/toaster/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100/os_dep/linux/os_intfs.c:533:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("rf_reg_dump2", S_IFREG | S_IRUGO,
        ^
/home/toaster/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100/os_dep/linux/os_intfs.c:542:9: warning: assignment makes pointer from integer without a cast [enabled by default]
   entry = create_proc_read_entry("rf_reg_dump3", S_IFREG | S_IRUGO,
         ^
/home/toaster/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100/os_dep/linux/os_intfs.c:549:9: warning: assignment makes pointer from integer without a cast [enabled by default]
   entry = create_proc_read_entry("rf_reg_dump4", S_IFREG | S_IRUGO,
         ^
/home/toaster/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100/os_dep/linux/os_intfs.c:559:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("all_sta_info", S_IFREG | S_IRUGO,
        ^
/home/toaster/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100/os_dep/linux/os_intfs.c:577:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("best_channel", S_IFREG | S_IRUGO,
        ^
/home/toaster/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100/os_dep/linux/os_intfs.c:585:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("rx_signal", S_IFREG | S_IRUGO,
        ^
/home/toaster/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100/os_dep/linux/os_intfs.c:591:7: error: dereferencing pointer to incomplete type
  entry->write_proc = proc_set_rx_signal;
       ^
/home/toaster/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100/os_dep/linux/os_intfs.c:593:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("ht_enable", S_IFREG | S_IRUGO,
        ^
/home/toaster/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100/os_dep/linux/os_intfs.c:599:7: error: dereferencing pointer to incomplete type
  entry->write_proc = proc_set_ht_enable;
       ^
/home/toaster/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100/os_dep/linux/os_intfs.c:601:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("bw_mode", S_IFREG | S_IRUGO,
        ^
/home/toaster/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100/os_dep/linux/os_intfs.c:607:7: error: dereferencing pointer to incomplete type
  entry->write_proc = proc_set_bw_mode;
       ^
/home/toaster/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100/os_dep/linux/os_intfs.c:609:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("ampdu_enable", S_IFREG | S_IRUGO,
        ^
/home/toaster/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100/os_dep/linux/os_intfs.c:615:7: error: dereferencing pointer to incomplete type
  entry->write_proc = proc_set_ampdu_enable;
       ^
/home/toaster/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100/os_dep/linux/os_intfs.c:617:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("rx_stbc", S_IFREG | S_IRUGO,
        ^
/home/toaster/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100/os_dep/linux/os_intfs.c:623:7: error: dereferencing pointer to incomplete type
  entry->write_proc = proc_set_rx_stbc;
       ^
/home/toaster/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100/os_dep/linux/os_intfs.c:626:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("path_rssi", S_IFREG | S_IRUGO,
        ^
/home/toaster/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100/os_dep/linux/os_intfs.c:629:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("rssi_disp", S_IFREG | S_IRUGO,
        ^
/home/toaster/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100/os_dep/linux/os_intfs.c:635:7: error: dereferencing pointer to incomplete type
  entry->write_proc = proc_set_rssi_disp;
       ^
/home/toaster/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100/os_dep/linux/os_intfs.c:647:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("sreset", S_IFREG | S_IRUGO,
        ^
/home/toaster/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100/os_dep/linux/os_intfs.c:653:7: error: dereferencing pointer to incomplete type
  entry->write_proc = proc_set_sreset;
       ^
cc1: some warnings being treated as errors
make[2]: *** [/home/toaster/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100/os_dep/linux/os_intfs.o] Error 1
make[1]: *** [_module_/home/toaster/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.11.0-15-generic'
make: *** [modules] Error 2

---

### Post by chili555 on 2014-01-19
@praseodym--

This package makes with a couple of warnings but no errors on my 13.10: [https://github.com/abperiasamy/rtl8812AU_8821AU_linux](https://github.com/abperiasamy/rtl8812AU_8821AU_linux)  It needs your dkms magic!

---

### Post by praseodym on 2014-01-20
Normally my colleague flash63 is the dkms-guru, especially for new drivers ;)

Try:
```

sudo apt-get install git
git clone https://github.com/abperiasamy/rtl8812AU_8821AU_linux
cd rtl8812AU_8821AU_linux
make
sudo make install
```
Reinstallation after a kernel upgrade via
```
cd rtl8812AU_8821AU_linux
make clean
make
sudo make install
```

---

### Post by Toaster on 2014-01-20
Wow thanks a ton! It works like a charm now! I'm seriously starting to love ubuntu way more then windows. The only thing that is/was holding me to windows is for gaming, but I've been using ubuntu for everything else!

I do have one more question. If I restart my PC the driver should still work correct? I'll only need to recompile/install on kernal uprades?

---

### Post by chili555 on 2014-01-20
> I do have one more question. If I restart my PC the driver should still work correct? I'll only need to recompile/install on kernal uprades?Correct on both counts.

Glad it's working.

---

### Post by oblivion2k on 2014-04-15
My Apologies for bumping an old topic, I didn't notice that the post under toasters error was a fix for the same error he was having. Ran the new source and it compiled and installed wonderfully. Thank you for your help!

---

### Post by Cinderboot on 2015-01-29
> 
sudo apt-get install git
git clone [https://github.com/abperiasamy/rtl8812AU_8821AU_linux](https://github.com/abperiasamy/rtl8812AU_8821AU_linux)
cd rtl8812AU_8821AU_linux
make
sudo make install


This post was awesome.
Works like a charm.

I'm running Kubuntu 14.04.

---

### Post by zilvador2 on 2015-07-23
Thanks praseodym!

T[**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=1411497")he instructions worked very well! Only thing to add is that one WiFi network didn't work for me, but after changes from WPA Personal security to WEP, it worked again (and a few other changes...but I'm fairly sure this was the one that made the difference).

Best regards,
Daniel

---

### Post by bug4 on 2015-08-26
> **zilvador2 said:**
> Thanks praseodym!

The instructions worked very well! Only thing to add is that one WiFi network didn't work for me, but after changes from WPA Personal security to WEP, it worked again (and a few other changes...but I'm fairly sure this was the one that made the difference).

Best regards,
Daniel

I STRONGLY suggest you do not use WEP !! Its bubblewrap security and very easily cracked .. or so I hear , I use wired internet mostly :-)

---

### Post by QIII on 2015-08-26
WEP is pretty much an open invitation for the neighbor's pimply-faced teenager to log in to your wireless in 10 seconds or less.

---

