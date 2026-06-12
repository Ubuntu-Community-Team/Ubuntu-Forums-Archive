---
title: "netbook EEE PC 901 cant use integrated wifi"
date: 2015-12-20
forum: Networking &amp; Wireless
---

### Post by domsztof on 2015-12-20
hello, i have some issues with EEE PC 901.
The integrated wif is Ralink RT2860.
I am using Lubuntu 14.04
Lot of pepole says, i can find drivers here [http://www.ralinktech.com/](http://www.ralinktech.com/) but this site doesnt work.

I tried this [https://github.com/qualiabyte/install-rt2860](https://github.com/qualiabyte/install-rt2860) but it wrote
```
my@my-901:~$ git clone https://github.com/qualiabyte/install-rt2860 \
> 
Cloning into 'install-rt2860'...
remote: Counting objects: 35, done.
remote: Compressing objects: 100% (22/22), done.
remote: Total 35 (delta 13), reused 35 (delta 13), pack-reused 0
Unpacking objects: 100% (35/35), done.
Checking connectivity... done.
my@my-901:~$ cd install-rt2860 \
> sudo ./install-rt2860.sh
my@my-901:~/install-rt2860$ sudo ./install-rt2860.sh
[sudo] password for my: 
--2015-12-20 13:42:40--  https://github.com/downloads/qualiabyte/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0.tar.gz
P&#345;ekládám github.com (github.com)&#8230; 192.30.252.130
Navazuje se spojení s github.com (github.com)|192.30.252.130|:443&#8230; spojeno.
HTTP po&#382;adavek odeslán, program &#269;eká na odpov&#283;&#271;&#8230; 302 Found
P&#345;esm&#283;rováno na: https://cloud.github.com/downloads/qualiabyte/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0.tar.gz [následuji]
--2015-12-20 13:42:41--  https://cloud.github.com/downloads/qualiabyte/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0.tar.gz
P&#345;ekládám cloud.github.com (cloud.github.com)&#8230; 54.230.12.76, 54.230.12.118, 54.230.12.93, ...
Navazuje se spojení s cloud.github.com (cloud.github.com)|54.230.12.76|:443&#8230; spojeno.
HTTP po&#382;adavek odeslán, program &#269;eká na odpov&#283;&#271;&#8230; 200 OK
Délka: 772686 (755K) [application/gzip]
Ukládám do: &#8222;2010_07_16_RT2860_Linux_STA_v2.4.0.0.tar.gz&#8220;

100%[======================================>] 772 686      336KB/s   za 2,2s   

2015-12-20 13:42:44 (336 KB/s) &#8211; &#8222;2010_07_16_RT2860_Linux_STA_v2.4.0.0.tar.gz&#8220; ulo&#382;eno [772686/772686]

patching file common/cmm_wpa.c
patching file os/linux/config.mk
cp -f os/linux/Makefile.6 os/linux/Makefile
make -C os/linux clean
make[1]: Entering directory `/home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux'
rm -f ../../common/*.o
rm -f ../../common/.*.{cmd,flags,d}
rm -f ../../os/linux/*.{o,ko,mod.{o,c}}
rm -f ../../os/linux/.*.{cmd,flags,d}
rm -fr ../../os/linux/.tmp_versions
rm -f ../../os/linux/Module.symvers
rm -f ../../os/linux/Module.markers
rm -f ../../os/linux/modules.order
rm -f ../../chips/*.o
rm -f ../../chips/.*.{cmd,flags,d}
rm -f ../../sta/*.o
rm -f ../../sta/.*.{cmd,flags,d}
make[1]: Leaving directory `/home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux'
rm -rf os/linux/Makefile
make -C tools
make[1]: Entering directory `/home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/tools'
/home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/Makefile
make -C /lib/modules/3.19.0-37-generic/build SUBDIRS=/home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-3.19.0-37-generic'
  CC [M]  /home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/crypt_md5.o
In file included from ./arch/x86/include/asm/string.h:2:0,
                 from include/linux/string.h:17,
                 from ./arch/x86/include/asm/page_32.h:34,
                 from ./arch/x86/include/asm/page.h:13,
                 from ./arch/x86/include/asm/thread_info.h:11,
                 from include/linux/thread_info.h:54,
                 from ./arch/x86/include/asm/preempt.h:6,
                 from include/linux/preempt.h:18,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:35,
                 from include/linux/time.h:5,
                 from include/linux/stat.h:18,
                 from include/linux/module.h:10,
                 from /home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/include/os/rt_linux.h:40,
                 from /home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/include/rtmp_os.h:42,
                 from /home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/include/rt_config.h:72,
                 from /home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/crypt_md5.c:28:
/home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/crypt_md5.c: In function &#8216;MD5Final&#8217;:
/home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/crypt_md5.c:322:32: warning: argument to &#8216;sizeof&#8217; in &#8216;__builtin_memset&#8217; call is the same expression as the destination; did you mean to dereference it? [-Wsizeof-pointer-memaccess]
     NdisZeroMemory(pCtx, sizeof(pCtx)); // memory free 
                                ^
./arch/x86/include/asm/string_32.h:325:52: note: in definition of macro &#8216;memset&#8217;
 #define memset(s, c, count) __builtin_memset(s, c, count)
                                                    ^
/home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/crypt_md5.c:322:5: note: in expansion of macro &#8216;NdisZeroMemory&#8217;
     NdisZeroMemory(pCtx, sizeof(pCtx)); // memory free 
     ^
/home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/crypt_md5.c: In function &#8216;SHAFinal&#8217;:
/home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/crypt_md5.c:621:32: warning: argument to &#8216;sizeof&#8217; in &#8216;__builtin_memset&#8217; call is the same expression as the destination; did you mean to dereference it? [-Wsizeof-pointer-memaccess]
     NdisZeroMemory(pCtx, sizeof(pCtx)); // memory free 
                                ^
./arch/x86/include/asm/string_32.h:325:52: note: in definition of macro &#8216;memset&#8217;
 #define memset(s, c, count) __builtin_memset(s, c, count)
                                                    ^
/home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/crypt_md5.c:621:5: note: in expansion of macro &#8216;NdisZeroMemory&#8217;
     NdisZeroMemory(pCtx, sizeof(pCtx)); // memory free 
     ^
  CC [M]  /home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/crypt_aes.o
/home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/crypt_aes.c: In function &#8216;WscEncryptData&#8217;:
/home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/crypt_aes.c:1522:1: warning: the frame size of 1368 bytes is larger than 1024 bytes [-Wframe-larger-than=]
 }
 ^
/home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/crypt_aes.c: In function &#8216;WscDecryptData&#8217;:
/home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/crypt_aes.c:1592:1: warning: the frame size of 1368 bytes is larger than 1024 bytes [-Wframe-larger-than=]
 }
 ^
/home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/crypt_aes.c: In function &#8216;AES_GTK_KEY_WRAP&#8217;:
/home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/crypt_aes.c:2265:1: warning: the frame size of 1100 bytes is larger than 1024 bytes [-Wframe-larger-than=]
 }
 ^
  CC [M]  /home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/mlme.o
/home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/mlme.c: In function &#8216;BssTableSetEntry&#8217;:
/home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/mlme.c:5547:39: warning: operation on &#8216;Tab->BssOverlapNr&#8217; may be undefined [-Wsequence-point]
                     Tab->BssOverlapNr = (Tab->BssOverlapNr++) % MAX_LEN_OF_BSS_TABLE;
                                       ^
  CC [M]  /home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_wep.o
  CC [M]  /home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/action.o
  CC [M]  /home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_data.o
  CC [M]  /home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/rtmp_init.o
  CC [M]  /home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_aes.o
  CC [M]  /home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_sync.o
  CC [M]  /home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/eeprom.o
  CC [M]  /home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_info.o
  CC [M]  /home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/dfs.o
  CC [M]  /home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/spectrum.o
  CC [M]  /home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/rt_channel.o
  CC [M]  /home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_profile.o
  CC [M]  /home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_asic.o
  CC [M]  /home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../sta/assoc.o
  CC [M]  /home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../sta/auth.o
  CC [M]  /home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../sta/sync.o
  CC [M]  /home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../sta/sanity.o
  CC [M]  /home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../sta/connect.o
  CC [M]  /home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../sta/wpa.o
  CC [M]  /home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../sta/sta_cfg.o
  CC [M]  /home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../os/linux/rt_profile.o
  CC [M]  /home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../os/linux/sta_ioctl.o
/home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../os/linux/sta_ioctl.c: In function &#8216;rt_ioctl_siwencode&#8217;:
/home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../os/linux/sta_ioctl.c:1473:6: warning: suggest parentheses around operand of &#8216;!&#8217; or change &#8216;&&#8217; to &#8216;&&&#8217; or &#8216;!&#8217; to &#8216;~&#8217; [-Wparentheses]
   if(!erq->flags & IW_ENCODE_MODE) 
      ^
/home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../os/linux/sta_ioctl.c: In function &#8216;rt_ioctl_iwaplist&#8217;:
/home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../os/linux/sta_ioctl.c:603:1: warning: the frame size of 1296 bytes is larger than 1024 bytes [-Wframe-larger-than=]
 }
 ^
/home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../os/linux/sta_ioctl.c: In function &#8216;RTMPIoctlMAC&#8217;:
/home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../os/linux/sta_ioctl.c:5839:1: warning: the frame size of 1340 bytes is larger than 1024 bytes [-Wframe-larger-than=]
 }
 ^
/home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../os/linux/sta_ioctl.c: In function &#8216;RTMPIoctlE2PROM&#8217;:
/home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../os/linux/sta_ioctl.c:6038:1: warning: the frame size of 1344 bytes is larger than 1024 bytes [-Wframe-larger-than=]
 }
 ^
  CC [M]  /home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../os/linux/rt_linux.o
/home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../os/linux/rt_linux.c: In function &#8216;RtmpOSFSInfoChange&#8217;:
/home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../os/linux/rt_linux.c:1232:20: error: incompatible types when assigning to type &#8216;int&#8217; from type &#8216;kuid_t&#8217;
   pOSFSInfo->fsuid = current_fsuid();
                    ^
/home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../os/linux/rt_linux.c:1233:20: error: incompatible types when assigning to type &#8216;int&#8217; from type &#8216;kgid_t&#8217;
   pOSFSInfo->fsgid = current_fsgid();  
                    ^
/home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../os/linux/rt_linux.c: In function &#8216;RtmpOSNetDevDetach&#8217;:
/home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../os/linux/rt_linux.c:1698:38: warning: initialization discards &#8216;const&#8217; qualifier from pointer target type [enabled by default]
  struct net_device_ops *pNetDevOps = pNetDev->netdev_ops;
                                      ^
/home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../os/linux/rt_linux.c: In function &#8216;RtmpOSNetDevAttach&#8217;:
/home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../os/linux/rt_linux.c:1735:38: warning: initialization discards &#8216;const&#8217; qualifier from pointer target type [enabled by default]
  struct net_device_ops *pNetDevOps = pNetDev->netdev_ops;
                                      ^
make[2]: *** [/home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../os/linux/rt_linux.o] Error 1
make[1]: *** [_module_/home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.19.0-37-generic'
make: *** [LINUX] Error 2
make -C /home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux -f Makefile.6 install
mkdir: adresá&#345; &#8222;/etc/Wireless&#8220; nelze vytvo&#345;it: Soubor ji&#382; existuje
make[1]: Entering directory `/home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux'
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
cp /home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/RT2860STA.dat /etc/Wireless/RT2860STA/.
install -d /lib/modules/3.19.0-37-generic/kernel/drivers/net/wireless/
install -m 644 -c rt2860sta.ko /lib/modules/3.19.0-37-generic/kernel/drivers/net/wireless/
install: nelze získat informace o &#8222;rt2860sta.ko&#8220;: Adresá&#345; nebo soubor neexistuje
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/my/install-rt2860/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux'
make: *** [install] Error 2
wlan0     Link encap:Ethernet  HWadr 16:b5:c5:4b:8f:25  
rmmod: ERROR: Module rt2860sta is not currently loaded
modprobe: FATAL: Module rt2860sta not found.
ra0: Chyba p&#345;i zji&#353;&#357;ování p&#345;íznak&#367; rozhraní: Takové za&#345;ízení neexistuje
cp: nelze získat informace o &#8222;os/linux/rt2860sta.ko&#8220;: Adresá&#345; nebo soubor neexistuje
rt2860sta
my@my-901:~/install-rt2860$ 


```

any ideas?

---

### Post by howefield on 2015-12-20
Thread moved to the "*Networking & Wireless*" forum as requested.

You might read the [sticky]("http://ubuntuforums.org/showthread.php?t=370108") in this forum and run the wireless script as described.

---

### Post by domsztof on 2015-12-21
OK i tried it, it wont help.
but o paste here the wireless info if you can find the problem.

```

########## wireless info START ##########

Report from: 21 Dec 2015 15:34 CET +0100

Booted last: 21 Dec 2015 15:29 CET +0100

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.19.0-42-generic #48~14.04.1-Ubuntu SMP Fri Dec 18 10:25:23 UTC 2015 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Lubuntu

##### lspci #############################

01:00.0 Network controller [0280]: Ralink corp. RT2800 802.11n PCI [1814:0601]
    Subsystem: Ralink corp. Device [1814:2860]
    Kernel driver in use: rt2800pci

04:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8121/AR8113/AR8114 Gigabit or Fast Ethernet [1969:1026] (rev b0)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8324]
    Kernel driver in use: ATL1E

##### lsusb #############################

Bus 001 Device 002: ID 04f2:b071 Chicony Electronics Co., Ltd 2.0M UVC Webcam / CNF7129
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: eeepc-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: eeepc-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no

##### lsmod #############################

rt2800pci              16384  0 
rt2800mmio             16384  1 rt2800pci
rt2800lib              86016  2 rt2800pci,rt2800mmio
rt2x00pci              16384  1 rt2800pci
rt2x00mmio             16384  2 rt2800pci,rt2800mmio
rt2x00lib              49152  5 rt2x00pci,rt2800lib,rt2800pci,rt2800mmio,rt2x00mmio
mac80211              618496  3 rt2x00lib,rt2x00pci,rt2800lib
cfg80211              450560  2 mac80211,rt2x00lib
eeprom_93cx6           16384  1 rt2800pci
crc_ccitt              16384  1 rt2800lib

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:10.0.0.38  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          inet6 addr: 2a00:1028:8390:28ce:<IP6 'eth0' [IF]>/64 Scope:Global
          inet6 addr: 2a00:1028:8390:28ce:c48a:665e:a3dc:b4af/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:836 errors:0 dropped:0 overruns:0 frame:0
          TX packets:824 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:398006 (398.0 KB)  TX bytes:91551 (91.5 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.138      0.0.0.0         UG    0      0        0 eth0
10.0.0.0        0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       670     1  0 15:29 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

- Device: eth0  [Drátové p&#345;ipojení 1] --------------------------------------
  Type:              Wired
  Driver:            ATL1E
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         10.0.0.38
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.138

    DNS:             10.0.0.138

  IPv6 Settings:
    Address:         2a00:1028:8390:28ce:c48a:665e:a3dc:b4af
    Prefix:          64
    Gateway:         fe80::1

    Address:         2a00:1028:8390:28ce:<IP6 'eth0' [IF]>
    Prefix:          64
    Gateway:         fe80::1

    Address:         fe80::<IP6 'eth0' [IF]>
    Prefix:          64
    Gateway:         fe80::1

    DNS:             fe80::1

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/wifi_dd_1]] (600 root)
[connection] id=wifi_dd_1 | type=802-11-wireless
[802-11-wireless] ssid=wifi_dd_1
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/help]] (600 root)
[connection] id=help | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=help
[ipv6] method=auto
[ipv4] method=shared

##### iw reg get ########################

'iw' is not installed (package "iw").

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

wlan0     29 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 149 : 5.745 GHz
          Channel 151 : 5.755 GHz
          Channel 153 : 5.765 GHz
          Channel 155 : 5.775 GHz
          Channel 157 : 5.785 GHz
          Channel 159 : 5.795 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

##### module infos ######################

[rt2800pci]
filename:       /lib/modules/3.19.0-42-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     5C7768FC9D600016BB9062C
depends:        rt2x00lib,rt2800lib,rt2800mmio,rt2x00mmio,rt2x00pci,eeprom_93cx6
intree:         Y
vermagic:       3.19.0-42-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        D8:CC:8C:1D:9B:A9:63:CC:2C:D3:9E:24:02:1F:3A:AC:39:A4:C5:A3
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2800mmio]
filename:       /lib/modules/3.19.0-42-generic/kernel/drivers/net/wireless/rt2x00/rt2800mmio.ko
license:        GPL
description:    rt2800 MMIO library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     EA7A45E50305BDF0A76BD50
depends:        rt2800lib,rt2x00lib,rt2x00mmio
intree:         Y
vermagic:       3.19.0-42-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        D8:CC:8C:1D:9B:A9:63:CC:2C:D3:9E:24:02:1F:3A:AC:39:A4:C5:A3
sig_hashalgo:   sha512

[rt2800lib]
filename:       /lib/modules/3.19.0-42-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     491D0D9622C1740D95E8041
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       3.19.0-42-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        D8:CC:8C:1D:9B:A9:63:CC:2C:D3:9E:24:02:1F:3A:AC:39:A4:C5:A3
sig_hashalgo:   sha512

[rt2x00pci]
filename:       /lib/modules/3.19.0-42-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     F2A3F87D3DBCA573A6F6E05
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.19.0-42-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        D8:CC:8C:1D:9B:A9:63:CC:2C:D3:9E:24:02:1F:3A:AC:39:A4:C5:A3
sig_hashalgo:   sha512

[rt2x00mmio]
filename:       /lib/modules/3.19.0-42-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     879F1B5CBAAA72A33F68B51
depends:        rt2x00lib
intree:         Y
vermagic:       3.19.0-42-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        D8:CC:8C:1D:9B:A9:63:CC:2C:D3:9E:24:02:1F:3A:AC:39:A4:C5:A3
sig_hashalgo:   sha512

[rt2x00lib]
filename:       /lib/modules/3.19.0-42-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     7C3B03973B59C2A2A136B6C
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.19.0-42-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        D8:CC:8C:1D:9B:A9:63:CC:2C:D3:9E:24:02:1F:3A:AC:39:A4:C5:A3
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.19.0-42-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     47672A7084D52DFBE51E2D2
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-42-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        D8:CC:8C:1D:9B:A9:63:CC:2C:D3:9E:24:02:1F:3A:AC:39:A4:C5:A3
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.19.0-42-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F28307769349A31F4B24FC2
depends:        
intree:         Y
vermagic:       3.19.0-42-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        D8:CC:8C:1D:9B:A9:63:CC:2C:D3:9E:24:02:1F:3A:AC:39:A4:C5:A3
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rt2800pci]
nohwcrypt: N

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rt2860sta

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x1969:0x1026 (ATL1E)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

[    8.021436]  [<f8451017>] rt2800pci_driver_init+0x17/0x1000 [rt2800pci]
[   11.735572] ATL1E 0000:04:00.0 eth0: NIC Link is Up <100 Mbps Full Duplex>
[   11.782803] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2860.bin'
[   11.790217] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.34
[   11.830661] rt2x00mmio_regbusy_read() Indirect register access failed: offset=0x00007010, value=0x01ffffff
[   11.885164] ieee80211 phy0: rt2800pci_mcu_status: Error - MCU request failed, no response from hardware (repeated 3 times)
[   12.052702] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.264163] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush (repeated 25 times)

########## wireless info END ############


########## wireless info START ##########

Report from: 21 Dec 2015 15:34 CET +0100

Booted last: 21 Dec 2015 15:29 CET +0100

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.19.0-42-generic #48~14.04.1-Ubuntu SMP Fri Dec 18 10:25:23 UTC 2015 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Lubuntu

##### lspci #############################

01:00.0 Network controller [0280]: Ralink corp. RT2800 802.11n PCI [1814:0601]
    Subsystem: Ralink corp. Device [1814:2860]
    Kernel driver in use: rt2800pci

04:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8121/AR8113/AR8114 Gigabit or Fast Ethernet [1969:1026] (rev b0)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8324]
    Kernel driver in use: ATL1E

##### lsusb #############################

Bus 001 Device 002: ID 04f2:b071 Chicony Electronics Co., Ltd 2.0M UVC Webcam / CNF7129
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: eeepc-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: eeepc-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no

##### lsmod #############################

rt2800pci              16384  0 
rt2800mmio             16384  1 rt2800pci
rt2800lib              86016  2 rt2800pci,rt2800mmio
rt2x00pci              16384  1 rt2800pci
rt2x00mmio             16384  2 rt2800pci,rt2800mmio
rt2x00lib              49152  5 rt2x00pci,rt2800lib,rt2800pci,rt2800mmio,rt2x00mmio
mac80211              618496  3 rt2x00lib,rt2x00pci,rt2800lib
cfg80211              450560  2 mac80211,rt2x00lib
eeprom_93cx6           16384  1 rt2800pci
crc_ccitt              16384  1 rt2800lib

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:10.0.0.38  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          inet6 addr: 2a00:1028:8390:28ce:<IP6 'eth0' [IF]>/64 Scope:Global
          inet6 addr: 2a00:1028:8390:28ce:c48a:665e:a3dc:b4af/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:836 errors:0 dropped:0 overruns:0 frame:0
          TX packets:824 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:398006 (398.0 KB)  TX bytes:91551 (91.5 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.138      0.0.0.0         UG    0      0        0 eth0
10.0.0.0        0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       670     1  0 15:29 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

- Device: eth0  [Drátové p&#345;ipojení 1] --------------------------------------
  Type:              Wired
  Driver:            ATL1E
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         10.0.0.38
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.138

    DNS:             10.0.0.138

  IPv6 Settings:
    Address:         2a00:1028:8390:28ce:c48a:665e:a3dc:b4af
    Prefix:          64
    Gateway:         fe80::1

    Address:         2a00:1028:8390:28ce:<IP6 'eth0' [IF]>
    Prefix:          64
    Gateway:         fe80::1

    Address:         fe80::<IP6 'eth0' [IF]>
    Prefix:          64
    Gateway:         fe80::1

    DNS:             fe80::1

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/wifi_dd_1]] (600 root)
[connection] id=wifi_dd_1 | type=802-11-wireless
[802-11-wireless] ssid=wifi_dd_1
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/help]] (600 root)
[connection] id=help | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=help
[ipv6] method=auto
[ipv4] method=shared

##### iw reg get ########################

'iw' is not installed (package "iw").

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

wlan0     29 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 149 : 5.745 GHz
          Channel 151 : 5.755 GHz
          Channel 153 : 5.765 GHz
          Channel 155 : 5.775 GHz
          Channel 157 : 5.785 GHz
          Channel 159 : 5.795 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

##### module infos ######################

[rt2800pci]
filename:       /lib/modules/3.19.0-42-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     5C7768FC9D600016BB9062C
depends:        rt2x00lib,rt2800lib,rt2800mmio,rt2x00mmio,rt2x00pci,eeprom_93cx6
intree:         Y
vermagic:       3.19.0-42-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        D8:CC:8C:1D:9B:A9:63:CC:2C:D3:9E:24:02:1F:3A:AC:39:A4:C5:A3
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2800mmio]
filename:       /lib/modules/3.19.0-42-generic/kernel/drivers/net/wireless/rt2x00/rt2800mmio.ko
license:        GPL
description:    rt2800 MMIO library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     EA7A45E50305BDF0A76BD50
depends:        rt2800lib,rt2x00lib,rt2x00mmio
intree:         Y
vermagic:       3.19.0-42-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        D8:CC:8C:1D:9B:A9:63:CC:2C:D3:9E:24:02:1F:3A:AC:39:A4:C5:A3
sig_hashalgo:   sha512

[rt2800lib]
filename:       /lib/modules/3.19.0-42-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     491D0D9622C1740D95E8041
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       3.19.0-42-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        D8:CC:8C:1D:9B:A9:63:CC:2C:D3:9E:24:02:1F:3A:AC:39:A4:C5:A3
sig_hashalgo:   sha512

[rt2x00pci]
filename:       /lib/modules/3.19.0-42-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     F2A3F87D3DBCA573A6F6E05
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.19.0-42-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        D8:CC:8C:1D:9B:A9:63:CC:2C:D3:9E:24:02:1F:3A:AC:39:A4:C5:A3
sig_hashalgo:   sha512

[rt2x00mmio]
filename:       /lib/modules/3.19.0-42-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     879F1B5CBAAA72A33F68B51
depends:        rt2x00lib
intree:         Y
vermagic:       3.19.0-42-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        D8:CC:8C:1D:9B:A9:63:CC:2C:D3:9E:24:02:1F:3A:AC:39:A4:C5:A3
sig_hashalgo:   sha512

[rt2x00lib]
filename:       /lib/modules/3.19.0-42-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     7C3B03973B59C2A2A136B6C
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.19.0-42-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        D8:CC:8C:1D:9B:A9:63:CC:2C:D3:9E:24:02:1F:3A:AC:39:A4:C5:A3
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.19.0-42-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     47672A7084D52DFBE51E2D2
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-42-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        D8:CC:8C:1D:9B:A9:63:CC:2C:D3:9E:24:02:1F:3A:AC:39:A4:C5:A3
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.19.0-42-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F28307769349A31F4B24FC2
depends:        
intree:         Y
vermagic:       3.19.0-42-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        D8:CC:8C:1D:9B:A9:63:CC:2C:D3:9E:24:02:1F:3A:AC:39:A4:C5:A3
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rt2800pci]
nohwcrypt: N

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rt2860sta

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x1969:0x1026 (ATL1E)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

[    8.021436]  [<f8451017>] rt2800pci_driver_init+0x17/0x1000 [rt2800pci]
[   11.735572] ATL1E 0000:04:00.0 eth0: NIC Link is Up <100 Mbps Full Duplex>
[   11.782803] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2860.bin'
[   11.790217] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.34
[   11.830661] rt2x00mmio_regbusy_read() Indirect register access failed: offset=0x00007010, value=0x01ffffff
[   11.885164] ieee80211 phy0: rt2800pci_mcu_status: Error - MCU request failed, no response from hardware (repeated 3 times)
[   12.052702] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.264163] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush (repeated 25 times)

########## wireless info END ############


```

---

### Post by praseodym on 2015-12-21
```
[   11.885164] ieee80211 phy0: rt2800pci_mcu_status: Error - MCU request failed, no response from hardware (repeated 3 times)
```

Please try resetting your BIOS to default settings.

---

### Post by Hadaka on 2015-12-21
Hi, please do..
```
sudo apt-get install iw
sudo sed -i '/^rt2860sta/ d' /etc/modules
sudo modprobe rt2800pci
```
Your driver is already in the kernel
```
 modinfo rt2800pci
```
```
alias: pci:v0000[COLOR=#ff0000]**1814**[/COLOR]d0000[COLOR=#ff0000]**0601**[/COLOR]sv*sd*bc*sc*i*
Network controller [0280]: Ralink corp. RT2800 802.11n PCI [[COLOR=#ff0000]**1814**[/COLOR]:[COLOR=#ff0000]**0601**[/COLOR]] 
```
  Please run and post the wireless info again.
thanks

---

