---
title: "Arg!!! ZD1211B Troubles"
date: 2007-05-09
forum: Networking &amp; Wireless
---

### Post by Unisyst on 2007-05-09
It's 7:30 AM and I'm tired. I want this to work! Anyway.

Ok, I'm using Xubuntu 7.04, and I have a Zydas1211B (0ace:1215 ZyDAS) USB Stick.

I've installed build-essential,  I've tried compiling any driver I could find, all give me errors. =/

First when trying to install the Linux drivers off of the CD (my CD in the wireless card package, ZD1211LnxDrv_2_2_0_0) I get the following errors/warnings:

```
root@unisyst-desktop:~/Desktop/ZD1211LnxDrv_2_2_0_0# make clean && make && make install
rm -rf .tmp_versions .*.cmd *.ko *.mod.c *.mod.o *.o src/*.o  src/.*.o.cmd menudbg apdbg
make both
make[1]: Entering directory `/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0'
make clean
make[2]: Entering directory `/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0'
rm -rf .tmp_versions .*.cmd *.ko *.mod.c *.mod.o *.o src/*.o  src/.*.o.cmd menudbg apdbg
make[2]: Leaving directory `/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0'
make ZD1211REV_B=0
make[2]: Entering directory `/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0'
/lib/modules/2.6.20-15-generic/build
/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0
-I/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/include -fomit-frame-pointer -O2 -Wall -Wstrict-prototypes -pipe -DHOST_IF_USB -DAMAC -DGCCK -DOFDM -DHOSTAPD_SUPPORT -DUSE_EP4_SET_REG -DDOWNLOADFIRMWARE -DfTX_GAIN_OFDM=0 -DfNEW_CODE_MAP=1 -DfWRITE_WORD_REG=1 -DfREAD_MUL_REG=1 -DENHANCE_RX=1 -DZDCONF_MENUDBG -DZDCONF_APDBG -DZD1211
src/zd1205.o src/zdasocsvc.o src/zdauthreq.o src/zdauthrsp.o src/zdmmrx.o src/zdshared.o src/zdhci.o src/zdglobal.o src/zdencrypt.o src/zdpmfilter.o src/zdpsmon.o src/zdsynch.o src/zdbuf.o src/zd1205_proc.o src/zdhw.o src/zddebug.o src/zdtkipseed.o src/zdmic.o src/zddebug2.o src/zdusb.o src/zd1211.o
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0 modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.o
/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:34:26: error: linux/config.h: No such file or directory
In file included from /home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:42:
/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.h:663: warning: ‘__packed__’ attribute ignored
/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:244: warning: function declaration isn’t a prototype
/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:245: warning: function declaration isn’t a prototype
/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:312: warning: useless storage class specifier in empty declaration
/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:439: error: expected declaration specifiers or ‘...’ before ‘write’
/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:439: error: expected declaration specifiers or ‘...’ before ‘fd’
/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:439: error: expected declaration specifiers or ‘...’ before ‘buf’
/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:439: error: expected declaration specifiers or ‘...’ before ‘count’
/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:440: warning: type defaults to ‘int’ in declaration of ‘_syscall3’
/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:440: error: expected ‘,’ or ‘;’ before ‘_syscall3’
/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:445: error: ‘dot11A_Channel’ undeclared here (not in a function)
/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function ‘zd1205_house_keeping’:
/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:1441: warning: unused variable ‘tmpvalue’
/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function ‘zd1205_config’:
/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:2313: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘U32’
/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function ‘zd1205_validate_frame’:
/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:2688: warning: unused variable ‘len1’
/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function ‘zd1205_close’:
/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:4608: warning: implicit declaration of function ‘re_initFdescBuf’
/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function ‘zd1205_xmit_frame’:
/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:4701: warning: suggest parentheses around && within ||
/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function ‘zd1205_watchdog’:
/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:5335: warning: unused variable ‘ssidLenToDump’
/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:5334: warning: unused variable ‘cbTemp’
/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function ‘zd1205_ioctl_setiwencode’:
/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:5724: warning: unused variable ‘bReconnect’
/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function ‘zd1205wext_siwscan’:
/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:6595: warning: implicit declaration of function ‘zd_CmdProbeReq’
/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:6539: warning: unused variable ‘ul_mac_ps_state’
/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:6538: warning: unused variable ‘oldMacMode’
/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:6537: warning: unused variable ‘i’
/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function ‘zd1205_translate_scan’:
/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:6715: warning: unknown conversion type character ‘,’ in format
/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:6715: warning: spurious trailing ‘%’ in format
/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function ‘zd1205_list_bss’:
/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:6891: warning: spurious trailing ‘%’ in format
/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function ‘zd1205_ioctl’:
/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:7163: warning: implicit declaration of function ‘verify_area’
/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:7572: warning: ISO C90 forbids mixed declarations and code
/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function ‘zd1205_load_card_setting’:
/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:7940: warning: implicit declaration of function ‘open’
/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:7957: warning: implicit declaration of function ‘read’
/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:7961: warning: implicit declaration of function ‘close’
/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:7967: warning: suggest parentheses around assignment used as truth value
/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function ‘zd1205_save_card_setting’:
/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:8113: warning: implicit declaration of function ‘write’
/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function ‘zdcb_AssocRequest’:
/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:9153: warning: implicit declaration of function ‘HashSearch’
/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:9153: warning: assignment makes pointer from integer without a cast
/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function ‘zd1205_set_zd_cbs’:
/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:9209: warning: assignment from incompatible pointer type
/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function ‘CalculateQuality’:
/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:9423: warning: ISO C90 forbids mixed declarations and code
/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:9425: warning: unused variable ‘rxOffset’
make[4]: *** [/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.o] Error 1
make[3]: *** [_module_/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0'
make[1]: *** [both] Error 2
make[1]: Leaving directory `/home/unisyst/Desktop/ZD1211LnxDrv_2_2_0_0'
make: *** [all] Error 2

```

Next when trying to install the driver from [http://zd1211.ath.cx/](http://zd1211.ath.cx/), I get:

```
root@unisyst-desktop:~/Desktop/zd1211# make clean && make && make install
rm -rf .tmp_versions .*.cmd *.ko *.mod.c *.mod.o *.o src/*.o  src/.*.o.cmd
/lib/modules/2.6.20-15-generic/build
/home/unisyst/Desktop/zd1211
-I/home/unisyst/Desktop/zd1211/src/include -fomit-frame-pointer -O2 -Wall -Wstrict-prototypes -pipe -DZDCONF_WE_STAT_SUPPORT=1 -DHOST_IF_USB -DAMAC -DGCCK -DOFDM -DHOSTAPD_SUPPORT -DUSE_EP4_SET_REG -DDOWNLOADFIRMWARE -DfTX_GAIN_OFDM=0 -DfNEW_CODE_MAP=1 -DfWRITE_WORD_REG=1 -DfREAD_MUL_REG=1 -DENHANCE_RX=1 -DZD1211B
src/zd1205.o src/zdasocsvc.o src/zdauthreq.o src/zdauthrsp.o src/zdmmrx.o src/zdshared.o src/zdhci.o src/zdglobal.o src/zdencrypt.o src/zdpmfilter.o src/zdpsmon.o src/zdsynch.o src/zdbuf.o src/zd1205_proc.o src/zdhw.o src/zddebug.o src/zdtkipseed.o src/zdmic.o src/zdusb.o src/zd1211.o
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/unisyst/Desktop/zd1211 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/unisyst/Desktop/zd1211/src/zd1205.o
/home/unisyst/Desktop/zd1211/src/zd1205.c:34:26: error: linux/config.h: No such file or directory
In file included from /home/unisyst/Desktop/zd1211/src/zd1205.c:42:
/home/unisyst/Desktop/zd1211/src/zd1205.h:1332: warning: type qualifiers ignored on function return type
/home/unisyst/Desktop/zd1211/src/zd1205.h:1279: warning: ‘zd_readl’ declared inline after being called
/home/unisyst/Desktop/zd1211/src/zd1205.h:1279: warning: previous declaration of ‘zd_readl’ was here
/home/unisyst/Desktop/zd1211/src/zd1205.c: In function ‘zd1205_validate_frame’:
/home/unisyst/Desktop/zd1211/src/zd1205.c:2809: warning: unused variable ‘len1’
/home/unisyst/Desktop/zd1211/src/zd1205.c: In function ‘zd1205_translate_scan’:
/home/unisyst/Desktop/zd1211/src/zd1205.c:7183: warning: format ‘%d’ expects type ‘int’, but argument 4 has type ‘U32’
/home/unisyst/Desktop/zd1211/src/zd1205.c:7183: warning: unknown conversion type character ‘,’ in format
/home/unisyst/Desktop/zd1211/src/zd1205.c:7183: warning: spurious trailing ‘%’ in format
/home/unisyst/Desktop/zd1211/src/zd1205.c: In function ‘zd1205_list_bss’:
/home/unisyst/Desktop/zd1211/src/zd1205.c:7388: warning: format ‘%2d’ expects type ‘int’, but argument 2 has type ‘U32’
/home/unisyst/Desktop/zd1211/src/zd1205.c:7388: warning: spurious trailing ‘%’ in format
/home/unisyst/Desktop/zd1211/src/zd1205.c: At top level:
/home/unisyst/Desktop/zd1211/src/zd1205.c:7527: warning: type qualifiers ignored on function return type
/home/unisyst/Desktop/zd1211/src/zd1205.c:7608: warning: type qualifiers ignored on function return type
/home/unisyst/Desktop/zd1211/src/zd1205.c:7697: warning: type qualifiers ignored on function return type
/home/unisyst/Desktop/zd1211/src/zd1205.c:7713: warning: type qualifiers ignored on function return type
/home/unisyst/Desktop/zd1211/src/zd1205.c: In function ‘CalculateQuality’:
/home/unisyst/Desktop/zd1211/src/zd1205.c:10074: warning: unused variable ‘rxOffset’
make[2]: *** [/home/unisyst/Desktop/zd1211/src/zd1205.o] Error 1
make[1]: *** [_module_/home/unisyst/Desktop/zd1211] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [all] Error 2

```

I'm at a loss, I've been searching google with error messages, ideas and alternatives for hours, anyone's help would be greatly appreciated.

Thanks
Uni

---

### Post by chili555 on 2007-05-09
Please plug in your wireless, open a terminal and do:```
sudo tail -f /var/log/messages
```Leave it open so you can watch any kernel meaasges or errors as we do, in another terminal:```
sudo modprobe zd1211rw
```In the messages terminal, did a new interface register or were there errors? If it registered, you can now configure your wireless interface.

Let us know.

---

### Post by Unisyst on 2007-05-09
Ok maybe I'm going about this the wrong way.

Basically what I want to do is set it up as an access point, and I was under the impression that new drivers had to be installed for that.

The device is showing up in ifconfig as eth2, and iwconfig lists it as a valid wireless card.

From here all I want is to set up an access point. I can probably find a tutorial/guide on that, unless there's anything I'm missing.

---

### Post by chili555 on 2007-05-09
Does it accept ```
sudo iwconfig eth2 mode master
```

---

### Post by sectionEight on 2007-05-17
I have an old machine and I was hoping to do the same thing (use it as an access point).

I have a Belkin USB Wireless adaptor but it has the same chipset (using zd1211rw).

At the moment I am at the same place as you Unisyst. (I initially tried to build the driver but ended up using the zd1211rw driver that is in the kernel).

When I tried to set it to master I get an error:

Typed: sudo iwconfig eth1 mode master

Got: Error for wireless request "Set Mode" (8B06)
        SET failed on device eth1 ; Invalid argument.

Which I have a funny feeling means that it can't be set to master!!

Is there any way around this??

Is there another driver around that would allow it to be set to master?

Is there a way to do it without setting it to master?

Or is the whole idea just scuppered!!!

Any help or advice would be greatly appreciated!

---

### Post by Countra on 2008-01-19
I have the same problem and this thread hasent been solved yet so im reviving it (and dont call me a threadomancer lol) 
> arsham@arsham-desktop:~$ sudo modprobe zd1211rw
[sudo] password for arsham:
arsham@arsham-desktop:~$ 
arsham@arsham-desktop:~$ sudo iwconfig eth2 mode master
Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth2 ; No such device.
arsham@arsham-desktop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"zd1211"
          Mode:Managed  Frequency:2.472 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

arsham@arsham-desktop:~$ sudo iwconfig eth1 mode master
Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth1 ; Invalid argument.
arsham@arsham-desktop:~$ 

See? And yeah, the device im using is the WiFi MAX. Why doesent this work? :(

---

### Post by Countra on 2008-01-19
And btw, i downloaded this driver from [www.zd1211.ath.cx](www.zd1211.ath.cx) and i got this when i tried to install it (make it? lol)
> root@arsham-desktop:/home/arsham/Desktop/compat-wireless-2.6# make
./scripts/gen-compat-autoconf.sh config.mk > include/linux/compat_autoconf.h
make -C /lib/modules/2.6.22-14-generic/build M=/home/arsham/Desktop/compat-wireless-2.6 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/misc/eeprom_93cx6.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/ipw2100.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/ipw2200.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/rtl8180_dev.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/rtl8180_rtl8225.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/rtl8180_sa2400.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/rtl8180_max2820.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/rtl8180_grf5101.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/rtl8187_dev.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/rtl8187_rtl8225.o
  LD [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/rtl8180.o
  LD [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/rtl8187.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/adm8211.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/p54common.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/p54usb.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/p54pci.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/ath5k/base.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/ath5k/hw.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/ath5k/regdom.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/ath5k/initvals.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/ath5k/phy.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/ath5k/debug.o
  LD [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/ath5k/ath5k.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/b43/main.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/b43/tables.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/b43/tables_nphy.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/b43/phy.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/b43/nphy.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/b43/sysfs.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/b43/xmit.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/b43/lo.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/b43/wa.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/b43/dma.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/b43/pcmcia.o
  LD [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/b43/b43.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/b43legacy/main.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/b43legacy/ilt.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/b43legacy/phy.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/b43legacy/radio.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/b43legacy/sysfs.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/b43legacy/xmit.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/b43legacy/dma.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/b43legacy/pio.o
  LD [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/b43legacy/b43legacy.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/iwlwifi/iwl3945-base.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/iwlwifi/iwl-3945.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/iwlwifi/iwl-3945-rs.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/iwlwifi/iwl4965-base.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/iwlwifi/iwl-4965.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/iwlwifi/iwl-4965-rs.o
  LD [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/iwlwifi/iwl3945.o
  LD [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/iwlwifi/iwl4965.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/libertas/main.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/libertas/wext.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/libertas/rx.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/libertas/tx.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/libertas/cmd.o
/home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/libertas/cmd.c: In function &#8216;lbs_set_channel&#8217;:
/home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/libertas/cmd.c:802: warning: unused variable &#8216;old_channel&#8217;
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/libertas/cmdresp.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/libertas/scan.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/libertas/join.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/libertas/11d.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/libertas/debugfs.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/libertas/ethtool.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/libertas/assoc.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/libertas/if_cs.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/libertas/if_usb.o
  LD [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/libertas/libertas.o
  LD [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/libertas/usb8xxx.o
  LD [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/libertas/libertas_cs.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/rt2x00/rt2x00dev.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/rt2x00/rt2x00mac.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/rt2x00/rt2x00config.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/rt2x00/rt2x00firmware.o
  LD [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/rt2x00/rt2x00lib.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/rt2x00/rt2x00pci.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/rt2x00/rt2x00usb.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/rt2x00/rt2400pci.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/rt2x00/rt2500pci.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/rt2x00/rt61pci.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/rt2x00/rt2500usb.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/rt2x00/rt73usb.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/zd1211rw/zd_chip.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/zd1211rw/zd_ieee80211.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/zd1211rw/zd_mac.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/zd1211rw/zd_rf_al2230.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/zd1211rw/zd_rf_rf2959.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/zd1211rw/zd_rf_al7230b.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/zd1211rw/zd_rf_uw2453.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/zd1211rw/zd_rf.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/zd1211rw/zd_usb.o
  LD [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/zd1211rw/zd1211rw.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/ssb/main.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/ssb/scan.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/ssb/pci.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/ssb/pcihost_wrapper.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/ssb/pcmcia.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/ssb/driver_chipcommon.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/ssb/driver_pcicore.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/ssb/b43_pci_bridge.o
  LD [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/ssb/ssb.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/net/ieee80211/ieee80211_module.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/net/ieee80211/ieee80211_tx.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/net/ieee80211/ieee80211_rx.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/net/ieee80211/ieee80211_wx.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/net/ieee80211/ieee80211_geo.o
  LD [M]  /home/arsham/Desktop/compat-wireless-2.6/net/ieee80211/ieee80211.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/net/ieee80211/ieee80211_crypt.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/net/ieee80211/ieee80211_crypt_wep.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/net/ieee80211/ieee80211_crypt_ccmp.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/net/ieee80211/ieee80211_crypt_tkip.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/net/mac80211/ieee80211.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/net/mac80211/ieee80211_ioctl.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/net/mac80211/sta_info.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/net/mac80211/wep.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/net/mac80211/wpa.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/net/mac80211/ieee80211_sta.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/net/mac80211/ieee80211_iface.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/net/mac80211/ieee80211_rate.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/net/mac80211/michael.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/net/mac80211/regdomain.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/net/mac80211/tkip.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/net/mac80211/aes_ccm.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/net/mac80211/cfg.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/net/mac80211/rx.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/net/mac80211/tx.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/net/mac80211/key.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/net/mac80211/util.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/net/mac80211/compat.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/net/mac80211/event.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/net/mac80211/wme.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/net/mac80211/debugfs.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/net/mac80211/debugfs_sta.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/net/mac80211/debugfs_netdev.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/net/mac80211/debugfs_key.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/net/mac80211/rc80211_simple.o
  LD [M]  /home/arsham/Desktop/compat-wireless-2.6/net/mac80211/mac80211.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/net/wireless/core.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/net/wireless/sysfs.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/net/wireless/radiotap.o
  CC [M]  /home/arsham/Desktop/compat-wireless-2.6/net/wireless/nl80211.o
  LD [M]  /home/arsham/Desktop/compat-wireless-2.6/net/wireless/cfg80211.o
  Building modules, stage 2.
  MODPOST 34 modules
  CC      /home/arsham/Desktop/compat-wireless-2.6/drivers/misc/eeprom_93cx6.mod.o
  LD [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/misc/eeprom_93cx6.ko
  CC      /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/adm8211.mod.o
  LD [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/adm8211.ko
  CC      /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/ath5k/ath5k.mod.o
  LD [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/ath5k/ath5k.ko
  CC      /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/b43/b43.mod.o
  LD [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/b43/b43.ko
  CC      /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/b43legacy/b43legacy.mod.o
  LD [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/b43legacy/b43legacy.ko
  CC      /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/ipw2100.mod.o
  LD [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/ipw2100.ko
  CC      /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/ipw2200.mod.o
  LD [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/ipw2200.ko
  CC      /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/iwlwifi/iwl3945.mod.o
  LD [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/iwlwifi/iwl3945.ko
  CC      /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/iwlwifi/iwl4965.mod.o
  LD [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/iwlwifi/iwl4965.ko
  CC      /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/libertas/libertas.mod.o
  LD [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/libertas/libertas.ko
  CC      /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/libertas/libertas_cs.mod.o
  LD [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/libertas/libertas_cs.ko
  CC      /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/libertas/usb8xxx.mod.o
  LD [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/libertas/usb8xxx.ko
  CC      /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/p54common.mod.o
  LD [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/p54common.ko
  CC      /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/p54pci.mod.o
  LD [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/p54pci.ko
  CC      /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/p54usb.mod.o
  LD [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/p54usb.ko
  CC      /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/rt2x00/rt2400pci.mod.o
  LD [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/rt2x00/rt2400pci.ko
  CC      /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/rt2x00/rt2500pci.mod.o
  LD [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/rt2x00/rt2500pci.ko
  CC      /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/rt2x00/rt2500usb.mod.o
  LD [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/rt2x00/rt2500usb.ko
  CC      /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/rt2x00/rt2x00lib.mod.o
  LD [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/rt2x00/rt2x00lib.ko
  CC      /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/rt2x00/rt2x00pci.mod.o
  LD [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/rt2x00/rt2x00pci.ko
  CC      /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/rt2x00/rt2x00usb.mod.o
  LD [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/rt2x00/rt2x00usb.ko
  CC      /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/rt2x00/rt61pci.mod.o
  LD [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/rt2x00/rt61pci.ko
  CC      /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/rt2x00/rt73usb.mod.o
  LD [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/rt2x00/rt73usb.ko
  CC      /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/rtl8180.mod.o
  LD [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/rtl8180.ko
  CC      /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/rtl8187.mod.o
  LD [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/rtl8187.ko
  CC      /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/zd1211rw/zd1211rw.mod.o
  LD [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/net/wireless/zd1211rw/zd1211rw.ko
  CC      /home/arsham/Desktop/compat-wireless-2.6/drivers/ssb/ssb.mod.o
  LD [M]  /home/arsham/Desktop/compat-wireless-2.6/drivers/ssb/ssb.ko
  CC      /home/arsham/Desktop/compat-wireless-2.6/net/ieee80211/ieee80211.mod.o
  LD [M]  /home/arsham/Desktop/compat-wireless-2.6/net/ieee80211/ieee80211.ko
  CC      /home/arsham/Desktop/compat-wireless-2.6/net/ieee80211/ieee80211_crypt.mod.o
  LD [M]  /home/arsham/Desktop/compat-wireless-2.6/net/ieee80211/ieee80211_crypt.ko
  CC      /home/arsham/Desktop/compat-wireless-2.6/net/ieee80211/ieee80211_crypt_ccmp.mod.o
  LD [M]  /home/arsham/Desktop/compat-wireless-2.6/net/ieee80211/ieee80211_crypt_ccmp.ko
  CC      /home/arsham/Desktop/compat-wireless-2.6/net/ieee80211/ieee80211_crypt_tkip.mod.o
  LD [M]  /home/arsham/Desktop/compat-wireless-2.6/net/ieee80211/ieee80211_crypt_tkip.ko
  CC      /home/arsham/Desktop/compat-wireless-2.6/net/ieee80211/ieee80211_crypt_wep.mod.o
  LD [M]  /home/arsham/Desktop/compat-wireless-2.6/net/ieee80211/ieee80211_crypt_wep.ko
  CC      /home/arsham/Desktop/compat-wireless-2.6/net/mac80211/mac80211.mod.o
  LD [M]  /home/arsham/Desktop/compat-wireless-2.6/net/mac80211/mac80211.ko
  CC      /home/arsham/Desktop/compat-wireless-2.6/net/wireless/cfg80211.mod.o
  LD [M]  /home/arsham/Desktop/compat-wireless-2.6/net/wireless/cfg80211.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
root@arsham-desktop:/home/arsham/Desktop/compat-wireless-2.6#
is it working? I dont know but look:
> root@arsham-desktop:~# iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"zd1211"
          Mode:Managed  Frequency:2.472 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

So yeah, its still invalid >.< ... Is there any way around this? HELP!

---

### Post by chili555 on 2008-01-19
Why are you trying to set the mode as 'Master'? Are you wanting to set up your computer as a router? Or, are you simply trying to wirelessly connect to your router or access point and surf the web? If you just want to connect, then 'Managed' is the correct mode. That means, roughly, I will be managed by the router; the router will tell me what bit-rate, channel, etc. I will use.

It looks to me as if your zd1211 is working fine! I suggest doing:```
sudo iwlist eth1 scan
```This will tell you the exact ESSID of the router. Then do:```
sudo iwconfig eth1 essid <essid_you_found_in_scan>
sudo ifup eth1
```If you have no encryption in place, you should connect.

---

### Post by Countra on 2008-01-19
Well this is what i got:
> arsham@arsham-desktop:~$ sudo iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:01:38:92:97:22
                    ESSID:"B2_private_CB"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=100/100  
                    Extra: Last beacon: 156ms ago

arsham@arsham-desktop:~$ sudo ifup eth1
Ignoring unknown interface eth1=eth1.
arsham@arsham-desktop:~$ sudo ifup eth1 "B2_private_CB"
Ignoring unknown interface eth1=eth1.
Ignoring unknown interface B2_private_CB=B2_private_CB.

> Why are you trying to set the mode as 'Master'? Are you wanting to set up your computer as a router?
Not really, im trying to use the WiFi MAX(a wifi dongle) to connect my Wii(and ds) to internet.
And.. Well it didnt really work, am i doing something wrong? How can i turn off the encryption? Thanks for answering =)

---

### Post by Countra on 2008-01-19
> arsham@arsham-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"B2_private_CB"  Nickname:"zd1211"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:01:38:92:97:22   
          Bit Rate=24 Mb/s   
          Link Quality=94/100  Signal level=32/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

arsham@arsham-desktop:~$ 

From a look from here i would get the impression that it should be working by now so why is it not? Hmph, stuff never works out-of-the-box for me! ;(

EDIT: Better yet, how do i set or change my encryption key? I havent set it yet but it says that i have. Thats weird.

---

### Post by Countra on 2008-01-19
Btw, i have  a feeling that i am totally now offtrack since you shouldnt be able to connect to your wifi dongle(there is a option in the "wired connections settings" now to connect to a  about four diffrent connections). Might it be that these are my neighbors wireless routers and have nothing to do with the wifi dongle? Btw, yes it is a usb wifi dongle that is connected to the computer and its job is to provide the house with wireless internet but it doesent seem to work right now, im doing something wrong lol

EDIT: yes, that router was my neighbors router i presume.. Hmm. However, what i want to do is to set up my wifi usb dongle as an access point for other devices around the house

---

### Post by chili555 on 2008-01-19
> However, what i want to do is to set up my wifi usb dongle as an access point for other devices around the house Then you will need a wireless device that can be placed into 'Master' mode, which your ZD1211 is not. Not every device has every capability.

The only way you can connect to 'B2_private_CB' is if you know the encryption key. How do you get internet connectivity otherwise? Through a DSL or cable modem? And now you want to share that with other computers in the house?

It sounds to me as if your ZD1211 has limited capabilities and will not act as 'Master' to the other computers in the house. Have you considered buying a wireless router such as the Linksys WRT54G or others? I believe it would save you a whole lot of pain.

---

### Post by Countra on 2008-01-19
No, the dongle im using is made for what i want to use it for. Its the WiFi MAX and i want to use it to provide wireless internet to my Nintendo DS and Wii(using it as an accept point for them, that is); here is more info on the device [http://gear.ign.com/articles/704/704528p1.html](http://gear.ign.com/articles/704/704528p1.html)
But doing it with linux is hard. And, well.. frankly, im a bit of a noob when it comes to linux, especially in kernell.

---

### Post by Countra on 2008-01-19
Btw, i cant install the  drivers that came in the cd with the device itself, look what i get when i try to run the command "make" in the directory:
> arsham@arsham-desktop:~$ cd '/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0' 
arsham@arsham-desktop:~/Desktop/ZD1211LnxDrv_2_2_0_0$ make
/lib/modules/2.6.22-14-generic/build
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0
-I/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/include -fomit-frame-pointer -O2 -Wall -Wstrict-prototypes -pipe -DHOST_IF_USB -DAMAC -DGCCK -DOFDM -DHOSTAPD_SUPPORT -DUSE_EP4_SET_REG -DDOWNLOADFIRMWARE -DfTX_GAIN_OFDM=0 -DfNEW_CODE_MAP=1 -DfWRITE_WORD_REG=1 -DfREAD_MUL_REG=1 -DENHANCE_RX=1 -DZDCONF_MENUDBG -DZDCONF_APDBG -DZD1211B
src/zd1205.o src/zdasocsvc.o src/zdauthreq.o src/zdauthrsp.o src/zdmmrx.o src/zdshared.o src/zdhci.o src/zdglobal.o src/zdencrypt.o src/zdpmfilter.o src/zdpsmon.o src/zdsynch.o src/zdbuf.o src/zd1205_proc.o src/zdhw.o src/zddebug.o src/zdtkipseed.o src/zdmic.o src/zddebug2.o src/zdusb.o src/zd1211.o
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.o
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:34:26: error: linux/config.h: No such file or directory
In file included from /home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:42:
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.h:663: warning: &#8216;__packed__&#8217; attribute ignored
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:244: warning: function declaration isn&#8217;t a prototype
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:245: warning: function declaration isn&#8217;t a prototype
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:312: warning: useless storage class specifier in empty declaration
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:439: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;write&#8217;
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:439: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;fd&#8217;
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:439: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;buf&#8217;
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:439: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;count&#8217;
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:440: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;_syscall3&#8217;
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:440: error: expected &#8216;,&#8217; or &#8216;;&#8217; before &#8216;_syscall3&#8217;
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:445: error: &#8216;dot11A_Channel&#8217; undeclared here (not in a function)
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function &#8216;zd1205_house_keeping&#8217;:
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:1441: warning: unused variable &#8216;tmpvalue&#8217;
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function &#8216;zd1205_config&#8217;:
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:2313: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 2 has type &#8216;U32&#8217;
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function &#8216;zd1205_validate_frame&#8217;:
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:2688: warning: unused variable &#8216;len1&#8217;
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function &#8216;zd1205_rx_isr&#8217;:
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:3927: error: &#8216;struct sk_buff&#8217; has no member named &#8216;mac&#8217;
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function &#8216;zd1205_close&#8217;:
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:4608: warning: implicit declaration of function &#8216;re_initFdescBuf&#8217;
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function &#8216;zd1205_xmit_frame&#8217;:
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:4701: warning: suggest parentheses around && within ||
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function &#8216;zd1205_watchdog&#8217;:
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:5335: warning: unused variable &#8216;ssidLenToDump&#8217;
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:5334: warning: unused variable &#8216;cbTemp&#8217;
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function &#8216;zd1205_ioctl_setiwencode&#8217;:
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:5724: warning: unused variable &#8216;bReconnect&#8217;
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function &#8216;zd1205wext_siwscan&#8217;:
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:6595: warning: implicit declaration of function &#8216;zd_CmdProbeReq&#8217;
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:6539: warning: unused variable &#8216;ul_mac_ps_state&#8217;
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:6538: warning: unused variable &#8216;oldMacMode&#8217;
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:6537: warning: unused variable &#8216;i&#8217;
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function &#8216;zd1205_translate_scan&#8217;:
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:6715: warning: unknown conversion type character &#8216;,&#8217; in format
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:6715: warning: spurious trailing &#8216;%&#8217; in format
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function &#8216;zd1205_list_bss&#8217;:
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:6891: warning: spurious trailing &#8216;%&#8217; in format
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function &#8216;zd1205_ioctl&#8217;:
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:7163: warning: implicit declaration of function &#8216;verify_area&#8217;
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:7572: warning: ISO C90 forbids mixed declarations and code
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function &#8216;zd1205_load_card_setting&#8217;:
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:7940: warning: implicit declaration of function &#8216;open&#8217;
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:7957: warning: implicit declaration of function &#8216;read&#8217;
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:7961: warning: implicit declaration of function &#8216;close&#8217;
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:7967: warning: suggest parentheses around assignment used as truth value
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function &#8216;zd1205_save_card_setting&#8217;:
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:8113: warning: implicit declaration of function &#8216;write&#8217;
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function &#8216;zdcb_AssocRequest&#8217;:
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:9153: warning: implicit declaration of function &#8216;HashSearch&#8217;
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:9153: warning: assignment makes pointer from integer without a cast
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function &#8216;zd1205_set_zd_cbs&#8217;:
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:9209: warning: assignment from incompatible pointer type
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function &#8216;CalculateQuality&#8217;:
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:9423: warning: ISO C90 forbids mixed declarations and code
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:9425: warning: unused variable &#8216;rxOffset&#8217;
make[2]: *** [/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.o] Error 1
make[1]: *** [_module_/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [all] Error 2
arsham@arsham-desktop:~/Desktop/ZD1211LnxDrv_2_2_0_0$ 


---

### Post by Countra on 2008-01-20
bump

---

### Post by chili555 on 2008-01-22
I got this to work: [http://dsd.object4.net/zd1211-vendor/releases/ZD1211LnxDrv_2_22_0_0.tar.gz](http://dsd.object4.net/zd1211-vendor/releases/ZD1211LnxDrv_2_22_0_0.tar.gz)

I changed the Makefile so that the KERNEL_SOURCE lines read like this:```
ifeq ($(KERN_VER), 2.6) 

    KERN_26=y

    KERNEL_SOURCE=/usr/src/linux
```In other words, it looks at /usr/src/linux rather than /usr/src/linux-2.6.blah.

Also, I ran the make command as sudo:```
sudo make
```I got a few warnings, but no errors. You will probably then want to run:```
sudo make install
```

Try it and let me know if this driver allows you to set 'Master' mode.

---

