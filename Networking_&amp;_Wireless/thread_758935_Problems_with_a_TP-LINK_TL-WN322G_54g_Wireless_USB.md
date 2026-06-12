---
title: "Problems with a TP-LINK TL-WN322G 54g Wireless USB Adapter (ZyDAS zd1211b Chipset )"
date: 2008-04-18
forum: Networking &amp; Wireless
---

### Post by robinbutler on 2008-04-18
Hello,

I am having serious driver issues with a cheap USB 802.11g wireless adapter, that will teach me! The device is a TP-LINK TL-WN322G Wireless USB Adapter with a ZyDAS zd1211b chipset, I believe.
I am currently running Ubuntu 7.10 Gutsy Gibbon with a 2.6.22-14-generic kernel.

I have attempted 3 different approaches to resolving this issue with various success. The closest I have come to resolving this issue is with ndiswrapper see 'Attempt 2/3'. I have searched many sites such as the ubuntu forums, [http://zd1211.wiki.sourceforge.net/](http://zd1211.wiki.sourceforge.net/) and [http://www.linuxwireless.org/en/users/Drivers/zd1211rw/devices](http://www.linuxwireless.org/en/users/Drivers/zd1211rw/devices) to name but a few. Any help will be greatly appreciated.


Attempt 1/3: I attempted to use the default zd1211rw driver, part of the 2.6.22 linux kernel, as follows . According to a number of forums there are problems with this driver and chipset?

# lsusb
Bus 005 Device 002: ID 0ace:1215 ZyDAS

# modprobe -v zd1211rw
insmod /lib/modules/2.6.22-14-generic/kernel/net/ieee80211/ieee80211_crypt.ko
insmod /lib/modules/2.6.22-14-generic/kernel/net/ieee80211/ieee80211.ko
insmod /lib/modules/2.6.22-14-generic/kernel/net/ieee80211/softmac/ieee80211softmac.ko
insmod /lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/zd1211rw/zd1211rw.ko

# lsmod | grep zd
zd1211rw               53508  0
ieee80211softmac       31360  1 zd1211rw
ieee80211              35656  2 zd1211rw,ieee80211softmac
usbcore               138632  6 zd1211rw,xpad,usbhid,ehci_hcd,uhci_hcd

/var/log/messages
Apr 15 22:03:44 living-room kernel: [ 6822.588279] ieee80211: 802.11 data/management/control stack, git-1.1.13
Apr 15 22:03:44 living-room kernel: [ 6822.588284] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Apr 15 22:03:44 living-room kernel: [ 6822.704446] usb 5-2: reset high speed USB device using ehci_hcd and address 2
Apr 15 22:03:44 living-room kernel: [ 6822.999931] usb 5-2: reset high speed USB device using ehci_hcd and address 2
Apr 15 22:03:44 living-room kernel: [ 6823.132499] usbcore: registered new interface driver zd1211rw

iwconfig  reveals no wireless device, ifconfig obviously reveals the same.
I have also attempted to copy various incantations of the firmware into /lib/firmware/zd1211 and /lib/firmware and also /lib/firmware/2.6.22-14-generic/zd1211


******

Attempt 2/3: Using ndiswrapper with windows XP device driver, and blacklisting the zd1211rw driver in /etc/modprobe.d/blacklist, or simplymodprobe -r zd1211rw gives the following status

# ndiswrapper -l
zd1211bu : driver installed
        device (0ACE:1215) present (alternate driver: zd1211rw)

# modprobe -v ndiswrapper
insmod /lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko

# lsmod | grep ndis
ndiswrapper           185240  0
usbcore               138632  6 ndiswrapper,xpad,usbhid,ehci_hcd,uhci_hcd

# lshw
*-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1d:0f:af:4b:fe
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+zd1211bu driverversion=1.45+TP-LINK,06/25/2007,6.22.0.0 link=no multicast=yes wireless=IEEE 802.11g


/var/log/messages
Apr 15 22:09:54 living-room kernel: [ 7191.914904] ndiswrapper version 1.45 loaded (smp=yes)
Apr 15 22:09:54 living-room kernel: [ 7192.042022] usb 5-2: reset high speed USB device using ehci_hcd and address 2
Apr 15 22:09:54 living-room kernel: [ 7192.192679] ndiswrapper: driver zd1211bu (TP-LINK,06/25/2007,6.22.0.0) loaded
Apr 15 22:09:55 living-room kernel: [ 7193.294012] wlan0: ethernet device 00:1d:0f:af:4b:fe using NDIS driver: zd1211bu, version: 0x6160000, NDIS version: 0x501, vendor: '802.11 b+g Wireless LAN', 0ACE:1215.F.conf
Apr 15 22:09:55 living-room kernel: [ 7193.329278] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Apr 15 22:09:55 living-room kernel: [ 7193.329329] usbcore: registered new interface driver ndiswrapper
Apr 15 22:09:55 living-room kernel: [ 7193.334306] ADDRCONF(NETDEV_UP): wlan0: link is not ready

Restart networking to populate wireless settings. /etc/init.d/networking restart

# iwconfig
wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.452 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:33 dBm   Sensitivity=0/3
          RTS thr:off   Fragment thr:off
          Encryption key:1234-D5A0-DDA3-4575-A431-81BE-98   Security mode:restricted
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

# ifconfig 
wlan0     Link encap:Ethernet  HWaddr 00:1D:0F:AF:4B:FE
          inet addr:192.168.100.2  Bcast:192.168.100.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

The wirless USB donggle light flashes on and off and the computer freeze in time with the flashes. The device is not sending or recieving packets. However, iwlist wlan0 scan shows available Wireless Access Points.


*******
Attempt 3/3: Compiling the latest zd1211 driver from [http://zd1211.wiki.sourceforge.net/VendorBasedDriver](http://zd1211.wiki.sourceforge.net/VendorBasedDriver)

I have attempted to compile zd1211-driver-r85 source code, also tried the latest SVN entry from source forge. I have all the required packages, linux source packages, linux header packages that various forums have recommended. I get the follows errors while attempting to compile the source code. I have modified the Makefile.C configuration to point to /usr/src/linux for the kernel source code, I've created the relevent symbolic link. I have also set the relevent flag to 1 for the zd1211b device driver. 

# make
/lib/modules/2.6.22-14-generic/build
/home/home/zd1211-driver-r85
-I/home/home/zd1211-driver-r85/src/include -fomit-frame-pointer -O2 -Wall -Wstrict-prototypes -pipe -DZDCONF_WE_STAT_SUPPORT=1 -DHOST_IF_USB -DAMAC -DGCCK -DOFDM -DHOSTAPD_SUPPORT -DUSE_EP4_SET_REG -DDOWNLOADFIRMWARE -DfTX_GAIN_OFDM=0 -DfNEW_CODE_MAP=1 -DfWRITE_WORD_REG=1 -DfREAD_MUL_REG=1 -DENHANCE_RX=1 -DZD1211B
src/zd1205.o src/zdasocsvc.o src/zdauthreq.o src/zdauthrsp.o src/zdmmrx.o src/zdshared.o src/zdhci.o src/zdglobal.o src/zdencrypt.o src/zdpmfilter.o src/zdpsmon.o src/zdsynch.o src/zdbuf.o src/zd1205_proc.o src/zdhw.o src/zddebug.o src/zdtkipseed.o src/zdmic.o src/zdusb.o src/zd1211.o
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/home/zd1211-driver-r85 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/home/zd1211-driver-r85/src/zd1205.o
/home/home/zd1211-driver-r85/src/zd1205.c: In function âzd1205_rx_isrâ:
/home/home/zd1211-driver-r85/src/zd1205.c:4162: error: âstruct sk_buffâ has no member named âmacâ
/home/home/zd1211-driver-r85/src/zd1205.c: In function âzd1205wext_iw_get_statsâ:
/home/home/zd1211-driver-r85/src/zd1205.c:4783: error: âstruct driver_statsâ has no member named âiw_statsâ
make[2]: *** [/home/home/zd1211-driver-r85/src/zd1205.o] Error 1
make[1]: *** [_module_/home/home/zd1211-driver-r85] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [all] Error 2


P.S. This is my first time with ubuntu after 10 years of Redhat and I have got to say I am impressed!

---

### Post by ale3andro on 2008-07-09
I bougth the same wifi usb adapter and had the same problem. I solved it using the guide in the Greek Ubuntu users forum ([http://ubuntu.opengr.net/viewtopic.php?f=9&t=408](http://ubuntu.opengr.net/viewtopic.php?f=9&t=408)).
If you need any help with the translation let me know. Good luck :)

---

### Post by PeruDM on 2008-07-23
it would better in english :-?, thanks for your reference

---

