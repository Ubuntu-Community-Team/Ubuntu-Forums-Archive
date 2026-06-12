---
title: "Safecom SWMULZ-5400 USB2.0 wireless plug-in adapter"
date: 2008-03-22
forum: Networking &amp; Wireless
---

### Post by TimGS on 2008-03-22
The above card when plugged into my Desktop (Ubuntu 7.10, USB2.0 ports) is fine with wifi-radar. I haven't got any networks yet to link to so I can't be certain, but no error messages are thrown in the terminal that I started wifi-radar from. Also System->Administration->Network recognises its presence.

On my Thinkpad T23 (Fluxbuntu 7.10, USB1.1 ports) I get the following:

> root@zebedee:/home/tim# wifi-radar
dhclient3 --version 2>&1
eth1      Interface doesn't support scanning : No such device

eth1      Interface doesn't support scanning : No such device

eth1      Interface doesn't support scanning : No such device

eth1      Interface doesn't support scanning : No such device

root@zebedee:/home/tim# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth1      IEEE 802.11b/g  ESSID: off/any  Nickname:"zd1211"
          Mode:Managed  Access Point: Invalid   
          Encryption key: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

root@zebedee:/home/tim# 

I'm not sure if the problem is that the T23 has USB1.1 ports (theoretically I understand that this shouldn't matter, and Windows XP on the same (dual-booted) laptop is fine with it and installed the windows drivers automatically without complaint), or whether there is something missing from Fluxbuntu that Ubuntu has and I need.

I also tried installing the linux drivers from the Safecom website manually but got the same problems as [http://ubuntuforums.org/showthread.php?t=281057](http://ubuntuforums.org/showthread.php?t=281057). 
> tim@zebedee:~/Linux-Driver$ uname -r
2.6.22-14-generic
tim@zebedee:~/Linux-Driver$ more Makefile
#
# .zd1211 - USB2.0 802.11b/g driver for Zydas ZD1211 chipsets
#
#
#

CC=gcc
CPP=g++
LD=ld
rM=rm -f -r

# if the kernel is 2.6.x, trun on this
KERN_26=y
KERNEL_SOURCE=/usr/src/linux-headers-2.6.22-14-generic

# if the kernel is 2.4.x, trun on this
#KERN_24=y
#KERNEL_SOURCE=/usr/src/linux-2.4.26

SRC_DIR=src
DEFINES=-D__KERNEL__ -DMODULE=1


tim@zebedee:~/Linux-Driver$  

As you can see I have edited my makefile as instructed in the above link, but I still get the same problems as Tobywuk. Any ideas?

My Thinkpad is happy talking to the world via a wired connection to my desktop, so installing stuff at home from the net is not a problem.

-- Tim.

---

### Post by TimGS on 2008-04-02
bump!

---

### Post by dstew on 2008-04-02
Did you install the linux-headers package for your kernel? After sudo make and sudo make install, what are the error messages you get? Please post them.

---

### Post by TimGS on 2008-04-03
Hi dstew,
Linux headers is now installed and up to date.
Output as below.
thanks,
-- Tim.

> tim@zebedee:~/WLAN files/Linux-Driver$ sudo apt-get install linux-headers-2.6.22-14-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.22-14-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 99 not upgraded.
tim@zebedee:~/WLAN files/Linux-Driver$ sudo make
make both
make[1]: Entering directory `/home/tim/WLAN files/Linux-Driver'
make clean
make[2]: Entering directory `/home/tim/WLAN files/Linux-Driver'
rm -rf .tmp_versions .*.cmd *.ko *.mod.c *.mod.o *.o src/*.o  src/.*.o.cmd menudbg apdbg
make[2]: Leaving directory `/home/tim/WLAN files/Linux-Driver'
make ZD1211REV_B=0
make[2]: Entering directory `/home/tim/WLAN files/Linux-Driver'
/lib/modules/2.6.22-14-generic/build
/home/tim/WLAN files/Linux-Driver
-I/home/tim/WLAN files/Linux-Driver/src/include -fomit-frame-pointer -O2 -Wall -Wstrict-prototypes -pipe -DHOST_IF_USB -DAMAC -DGCCK -DOFDM -DHOSTAPD_SUPPORT -DUSE_EP4_SET_REG -DDOWNLOADFIRMWARE -DfTX_GAIN_OFDM=0 -DfNEW_CODE_MAP=1 -DfWRITE_WORD_REG=1 -DfREAD_MUL_REG=1 -DENHANCE_RX=1 -DZDCONF_MENUDBG -DZDCONF_APDBG -DZD1211
src/zd1205.o src/zdasocsvc.o src/zdauthreq.o src/zdauthrsp.o src/zdmmrx.o src/zdshared.o src/zdhci.o src/zdglobal.o src/zdencrypt.o src/zdpmfilter.o src/zdpsmon.o src/zdsynch.o src/zdbuf.o src/zd1205_proc.o src/zdhw.o src/zddebug.o src/zdtkipseed.o src/zdmic.o src/zddebug2.o src/zdusb.o src/zd1211.o
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/tim/WLAN files/Linux-Driver modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
make[3]: *** No rule to make target `files/Linux-Driver'.  Stop.
make[3]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/tim/WLAN files/Linux-Driver'
make[1]: *** [both] Error 2
make[1]: Leaving directory `/home/tim/WLAN files/Linux-Driver'
make: *** [all] Error 2
tim@zebedee:~/WLAN files/Linux-Driver$ sudo make install
make both
make[1]: Entering directory `/home/tim/WLAN files/Linux-Driver'
make clean
make[2]: Entering directory `/home/tim/WLAN files/Linux-Driver'
rm -rf .tmp_versions .*.cmd *.ko *.mod.c *.mod.o *.o src/*.o  src/.*.o.cmd menudbg apdbg
make[2]: Leaving directory `/home/tim/WLAN files/Linux-Driver'
make ZD1211REV_B=0
make[2]: Entering directory `/home/tim/WLAN files/Linux-Driver'
/lib/modules/2.6.22-14-generic/build
/home/tim/WLAN files/Linux-Driver
-I/home/tim/WLAN files/Linux-Driver/src/include -fomit-frame-pointer -O2 -Wall -Wstrict-prototypes -pipe -DHOST_IF_USB -DAMAC -DGCCK -DOFDM -DHOSTAPD_SUPPORT -DUSE_EP4_SET_REG -DDOWNLOADFIRMWARE -DfTX_GAIN_OFDM=0 -DfNEW_CODE_MAP=1 -DfWRITE_WORD_REG=1 -DfREAD_MUL_REG=1 -DENHANCE_RX=1 -DZDCONF_MENUDBG -DZDCONF_APDBG -DZD1211
src/zd1205.o src/zdasocsvc.o src/zdauthreq.o src/zdauthrsp.o src/zdmmrx.o src/zdshared.o src/zdhci.o src/zdglobal.o src/zdencrypt.o src/zdpmfilter.o src/zdpsmon.o src/zdsynch.o src/zdbuf.o src/zd1205_proc.o src/zdhw.o src/zddebug.o src/zdtkipseed.o src/zdmic.o src/zddebug2.o src/zdusb.o src/zd1211.o
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/tim/WLAN files/Linux-Driver modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
make[3]: *** No rule to make target `files/Linux-Driver'.  Stop.
make[3]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/tim/WLAN files/Linux-Driver'
make[1]: *** [both] Error 2
make[1]: Leaving directory `/home/tim/WLAN files/Linux-Driver'
make: *** [all] Error 2
tim@zebedee:~/WLAN files/Linux-Driver$ 

---

### Post by dstew on 2008-04-03
> SUBDIRS=/home/tim/WLAN files/Linux-Driver modules
.
make[3]: *** No rule to make target `files/Linux-Driver'. Stop.You might need to put quotes around this path name. Make seems to be confused by the space between WLAN and files, and between Linux-Driver and modules.

---

### Post by TimGS on 2008-04-04
I got rid of the space in my directory name:

> tim@zebedee:~$ cd WLANfiles/Linux-Driver
tim@zebedee:~/WLANfiles/Linux-Driver$ sudo make
[sudo] password for tim:
make both
make[1]: Entering directory `/home/tim/WLANfiles/Linux-Driver'
make clean
make[2]: Entering directory `/home/tim/WLANfiles/Linux-Driver'
rm -rf .tmp_versions .*.cmd *.ko *.mod.c *.mod.o *.o src/*.o  src/.*.o.cmd menudbg apdbg
make[2]: Leaving directory `/home/tim/WLANfiles/Linux-Driver'
make ZD1211REV_B=0
make[2]: Entering directory `/home/tim/WLANfiles/Linux-Driver'
/lib/modules/2.6.22-14-generic/build
/home/tim/WLANfiles/Linux-Driver
-I/home/tim/WLANfiles/Linux-Driver/src/include -fomit-frame-pointer -O2 -Wall -Wstrict-prototypes -pipe -DHOST_IF_USB -DAMAC -DGCCK -DOFDM -DHOSTAPD_SUPPORT -DUSE_EP4_SET_REG -DDOWNLOADFIRMWARE -DfTX_GAIN_OFDM=0 -DfNEW_CODE_MAP=1 -DfWRITE_WORD_REG=1 -DfREAD_MUL_REG=1 -DENHANCE_RX=1 -DZDCONF_MENUDBG -DZDCONF_APDBG -DZD1211
src/zd1205.o src/zdasocsvc.o src/zdauthreq.o src/zdauthrsp.o src/zdmmrx.o src/zdshared.o src/zdhci.o src/zdglobal.o src/zdencrypt.o src/zdpmfilter.o src/zdpsmon.o src/zdsynch.o src/zdbuf.o src/zd1205_proc.o src/zdhw.o src/zddebug.o src/zdtkipseed.o src/zdmic.o src/zddebug2.o src/zdusb.o src/zd1211.o
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/tim/WLANfiles/Linux-Driver modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/tim/WLANfiles/Linux-Driver/src/zd1205.o
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:34:26: error: linux/config.h: No such file or directory
In file included from /home/tim/WLANfiles/Linux-Driver/src/zd1205.c:42:
/home/tim/WLANfiles/Linux-Driver/src/zd1205.h:663: warning: '__packed__' attribute ignored
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:244: warning: function declaration isn't a prototype
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:245: warning: function declaration isn't a prototype
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:312: warning: useless storage class specifier in empty declaration
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:439: error: expected declaration specifiers or '...' before 'write'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:439: error: expected declaration specifiers or '...' before 'fd'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:439: error: expected declaration specifiers or '...' before 'buf'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:439: error: expected declaration specifiers or '...' before 'count'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:440: warning: type defaults to 'int' in declaration of '_syscall3'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:440: error: expected ',' or ';' before '_syscall3'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:445: error: 'dot11A_Channel' undeclared here (not in a function)
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c: In function 'zd1205_house_keeping':
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:1441: warning: unused variable 'tmpvalue'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c: In function 'zd1205_config':
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:2313: warning: format '%d' expects type 'int', but argument 2 has type 'U32'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c: In function 'zd1205_validate_frame':
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:2688: warning: unused variable 'len1'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c: In function 'zd1205_rx_isr':
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:3927: error: 'struct sk_buff' has no member named 'mac'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c: In function 'zd1205_close':
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:4608: warning: implicit declaration of function 're_initFdescBuf'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c: In function 'zd1205_xmit_frame':
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:4701: warning: suggest parentheses around && within ||
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c: In function 'zd1205_watchdog':
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:5335: warning: unused variable 'ssidLenToDump'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:5334: warning: unused variable 'cbTemp'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c: In function 'zd1205_ioctl_setiwencode':
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:5724: warning: unused variable 'bReconnect'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c: In function 'zd1205wext_siwscan':
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:6595: warning: implicit declaration of function 'zd_CmdProbeReq'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:6539: warning: unused variable 'ul_mac_ps_state'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:6538: warning: unused variable 'oldMacMode'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:6537: warning: unused variable 'i'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c: In function 'zd1205_translate_scan':
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:6715: warning: unknown conversion type character ',' in format
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:6715: warning: spurious trailing '%' in format
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c: In function 'zd1205_list_bss':
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:6891: warning: spurious trailing '%' in format
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c: In function 'zd1205_ioctl':
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:7163: warning: implicit declaration of function 'verify_area'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:7572: warning: ISO C90 forbids mixed declarations and code
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c: In function 'zd1205_load_card_setting':
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:7940: warning: implicit declaration of function 'open'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:7957: warning: implicit declaration of function 'read'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:7961: warning: implicit declaration of function 'close'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:7967: warning: suggest parentheses around assignment used as truth value
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c: In function 'zd1205_save_card_setting':
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:8113: warning: implicit declaration of function 'write'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c: In function 'zdcb_AssocRequest':
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:9153: warning: implicit declaration of function 'HashSearch'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:9153: warning: assignment makes pointer from integer without a cast
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c: In function 'zd1205_set_zd_cbs':
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:9209: warning: assignment from incompatible pointer type
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c: In function 'CalculateQuality':
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:9423: warning: ISO C90 forbids mixed declarations and code
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:9425: warning: unused variable 'rxOffset'
make[4]: *** [/home/tim/WLANfiles/Linux-Driver/src/zd1205.o] Error 1
make[3]: *** [_module_/home/tim/WLANfiles/Linux-Driver] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/tim/WLANfiles/Linux-Driver'
make[1]: *** [both] Error 2
make[1]: Leaving directory `/home/tim/WLANfiles/Linux-Driver'
make: *** [all] Error 2
tim@zebedee:~/WLANfiles/Linux-Driver$ sudo make install
make both
make[1]: Entering directory `/home/tim/WLANfiles/Linux-Driver'
make clean
make[2]: Entering directory `/home/tim/WLANfiles/Linux-Driver'
rm -rf .tmp_versions .*.cmd *.ko *.mod.c *.mod.o *.o src/*.o  src/.*.o.cmd menudbg apdbg
make[2]: Leaving directory `/home/tim/WLANfiles/Linux-Driver'
make ZD1211REV_B=0
make[2]: Entering directory `/home/tim/WLANfiles/Linux-Driver'
/lib/modules/2.6.22-14-generic/build
/home/tim/WLANfiles/Linux-Driver
-I/home/tim/WLANfiles/Linux-Driver/src/include -fomit-frame-pointer -O2 -Wall -Wstrict-prototypes -pipe -DHOST_IF_USB -DAMAC -DGCCK -DOFDM -DHOSTAPD_SUPPORT -DUSE_EP4_SET_REG -DDOWNLOADFIRMWARE -DfTX_GAIN_OFDM=0 -DfNEW_CODE_MAP=1 -DfWRITE_WORD_REG=1 -DfREAD_MUL_REG=1 -DENHANCE_RX=1 -DZDCONF_MENUDBG -DZDCONF_APDBG -DZD1211
src/zd1205.o src/zdasocsvc.o src/zdauthreq.o src/zdauthrsp.o src/zdmmrx.o src/zdshared.o src/zdhci.o src/zdglobal.o src/zdencrypt.o src/zdpmfilter.o src/zdpsmon.o src/zdsynch.o src/zdbuf.o src/zd1205_proc.o src/zdhw.o src/zddebug.o src/zdtkipseed.o src/zdmic.o src/zddebug2.o src/zdusb.o src/zd1211.o
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/tim/WLANfiles/Linux-Driver modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/tim/WLANfiles/Linux-Driver/src/zd1205.o
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:34:26: error: linux/config.h: No such file or directory
In file included from /home/tim/WLANfiles/Linux-Driver/src/zd1205.c:42:
/home/tim/WLANfiles/Linux-Driver/src/zd1205.h:663: warning: '__packed__' attribute ignored
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:244: warning: function declaration isn't a prototype
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:245: warning: function declaration isn't a prototype
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:312: warning: useless storage class specifier in empty declaration
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:439: error: expected declaration specifiers or '...' before 'write'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:439: error: expected declaration specifiers or '...' before 'fd'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:439: error: expected declaration specifiers or '...' before 'buf'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:439: error: expected declaration specifiers or '...' before 'count'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:440: warning: type defaults to 'int' in declaration of '_syscall3'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:440: error: expected ',' or ';' before '_syscall3'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:445: error: 'dot11A_Channel' undeclared here (not in a function)
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c: In function 'zd1205_house_keeping':
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:1441: warning: unused variable 'tmpvalue'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c: In function 'zd1205_config':
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:2313: warning: format '%d' expects type 'int', but argument 2 has type 'U32'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c: In function 'zd1205_validate_frame':
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:2688: warning: unused variable 'len1'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c: In function 'zd1205_rx_isr':
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:3927: error: 'struct sk_buff' has no member named 'mac'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c: In function 'zd1205_close':
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:4608: warning: implicit declaration of function 're_initFdescBuf'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c: In function 'zd1205_xmit_frame':
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:4701: warning: suggest parentheses around && within ||
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c: In function 'zd1205_watchdog':
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:5335: warning: unused variable 'ssidLenToDump'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:5334: warning: unused variable 'cbTemp'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c: In function 'zd1205_ioctl_setiwencode':
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:5724: warning: unused variable 'bReconnect'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c: In function 'zd1205wext_siwscan':
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:6595: warning: implicit declaration of function 'zd_CmdProbeReq'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:6539: warning: unused variable 'ul_mac_ps_state'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:6538: warning: unused variable 'oldMacMode'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:6537: warning: unused variable 'i'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c: In function 'zd1205_translate_scan':
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:6715: warning: unknown conversion type character ',' in format
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:6715: warning: spurious trailing '%' in format
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c: In function 'zd1205_list_bss':
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:6891: warning: spurious trailing '%' in format
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c: In function 'zd1205_ioctl':
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:7163: warning: implicit declaration of function 'verify_area'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:7572: warning: ISO C90 forbids mixed declarations and code
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c: In function 'zd1205_load_card_setting':
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:7940: warning: implicit declaration of function 'open'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:7957: warning: implicit declaration of function 'read'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:7961: warning: implicit declaration of function 'close'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:7967: warning: suggest parentheses around assignment used as truth value
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c: In function 'zd1205_save_card_setting':
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:8113: warning: implicit declaration of function 'write'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c: In function 'zdcb_AssocRequest':
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:9153: warning: implicit declaration of function 'HashSearch'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:9153: warning: assignment makes pointer from integer without a cast
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c: In function 'zd1205_set_zd_cbs':
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:9209: warning: assignment from incompatible pointer type
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c: In function 'CalculateQuality':
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:9423: warning: ISO C90 forbids mixed declarations and code
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:9425: warning: unused variable 'rxOffset'
make[4]: *** [/home/tim/WLANfiles/Linux-Driver/src/zd1205.o] Error 1
make[3]: *** [_module_/home/tim/WLANfiles/Linux-Driver] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/tim/WLANfiles/Linux-Driver'
make[1]: *** [both] Error 2
make[1]: Leaving directory `/home/tim/WLANfiles/Linux-Driver'
make: *** [all] Error 2
tim@zebedee:~/WLANfiles/Linux-Driver$ 


---

### Post by dstew on 2008-04-04
> SUBDIRS=/home/tim/WLANfiles/Linux-Driver modulesThe directory name **Linux-Driver modules** has a space in it. If that is the correct name, put quotes around it. If not, change the SUBDIRS= line.> /home/tim/WLANfiles/Linux-Driver/src/zd1205.c:34:26: error: linux/config.h: No such file or directoryThis implies that the zd1205.c file is looking for a header file named linux/config.h which is a funny name. The path is not complete. Is there in fact a linux directory in the /home/tim/WLANfiles/Linux-Driver/src directory? If not, then look at the zd1205.c file and try to figure out what it is looking for.

---

### Post by TimGS on 2008-04-04
There is no modules directory, so I've just deleted the 'modules' part leaving SUBDIR....Linux-Driver.

There are no other directories within Linux-Driver/src, but zd1205.c also tries to include config.h, tcp.h, udp.h, fs.h and stat.h from such a directory.

-- Tim.

---

### Post by dstew on 2008-04-04
I am not much of an expert on compiling, but I recall that sometimes you have to modify the #include statements in the source code to have the correct path the the headers, unless they are in the local directory. I am out of my depth at this point, maybe post on the [Compiling and Packaging forum]("http://ubuntuforums.org/forumdisplay.php?f=44"). It is not as active, but you might get better help.

EDIT:And, you installed the build-essential package some time in the past, not just the gcc compiler, correct? The build-essential package has lots of standard headers in it.

---

### Post by TimGS on 2008-04-07
I think I do have build essential - will check when I get home.

Thanks for your time!

-- Tim.

Edit:I have build essential.

---

