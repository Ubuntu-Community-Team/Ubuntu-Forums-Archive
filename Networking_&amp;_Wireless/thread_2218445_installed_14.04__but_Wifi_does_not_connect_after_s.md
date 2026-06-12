---
title: "installed 14.04  but Wifi does not connect after suspend, ralink RT5370"
date: 2014-04-20
forum: Networking &amp; Wireless
---

### Post by parker-hugh on 2014-04-20
installed 14.04 (daily build of 25th March since the latest release of 17th April didn't recognise my wireless adapter). The daily build of 25th March does recognise my wireless, but Wifi does not connect after suspend, ralink RT5370

hp pavillion dv2036ea this old laptop has a 802.11g wireless adapter built in. But I have new 802.11n USB wireless adapter. The wireless adapter is Ralink Tech Corp RT5370.

this is similar to anoher post, [http://ubuntuforums.org/showthread.php?t=2218043](http://ubuntuforums.org/showthread.php?t=2218043)

 but I couldn't follow the instructions. I am unsure how to fix this as I am very new to linux. Is it possible to explain step-by-step instructions?  I can use the terminal window but please explain clearly and I will follow instructions.

thanks

---

### Post by varunendra on 2014-04-22
To give us a complete picture of your current (problematic) wireless setup, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

If you have the Live DVD of the daily build that works, also post the outputs of the following commands from its (working) live session -
```
nm-tool
lsusb
lsmod
modinfo rt2800usb
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by risva on 2014-04-26
Hello all,
i'm also using Lubuntu14.04. 
i ve recetly purchased a usb wifi adapter.  the lsusb says its a ralink 5370 device.
based on previous helps on ralink 5370...i did following:
- added  blacklist rt2800usb blacklist rt2870sta blacklist rt2x00
- changed to download folder where ive downloaded the driver for 5370.
- after make clean i ran make
- make cmd is giving two errors:


```

root@john-Presario-2200-PR557PC-UUF:/home/john/Downloads/ralink# make clean
cp -f os/linux/Makefile.clean os/linux/Makefile
make -C os/linux clean
make[1]: Entering directory `/home/john/Downloads/ralink/os/linux'
rm -f ../../common/*.o
rm -f ../../common/.*.{cmd,flags,d}
rm -f ../../os/linux/*.{o,ko,mod.{o,c}}
rm -f ../../os/linux/.*.{cmd,flags,d}
rm -fr ../../os/linux/.tmp_versions
rm -f ../../os/linux/Module.symvers
rm -f ../../os/linux/Modules.symvers
rm -f ../../os/linux/Module.markers
rm -f ../../os/linux/modules.order
rm -f ../../chips/*.o
rm -f ../../chips/.*.{cmd,flags,d}
rm -f ../../rate_ctrl/*.o
rm -f ../../rate_ctrl/.*.{cmd,flags,d}
rm -f ../../ate/common/*.o
rm -f ../../ate/common/.*.{cmd,flags,d}
rm -f ../../ate/chips/*.o
rm -f ../../ate/chips/.*.{cmd,flags,d}
rm -f ../../sta/*.o
rm -f ../../sta/.*.{cmd,flags,d}
make[1]: Leaving directory `/home/john/Downloads/ralink/os/linux'
rm -rf os/linux/Makefile
root@john-Presario-2200-PR557PC-UUF:/home/john/Downloads/ralink# make
make -C tools
make[1]: Entering directory `/home/john/Downloads/ralink/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/john/Downloads/ralink/tools'
/home/john/Downloads/ralink/tools/bin2h
cp -f os/linux/Makefile.6 /home/john/Downloads/ralink/os/linux/Makefile
make -C /lib/modules/3.13.0-24-generic/build SUBDIRS=/home/john/Downloads/ralink/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-24-generic'
  CC [M]  /home/john/Downloads/ralink/os/linux/../../common/crypt_md5.o
  CC [M]  /home/john/Downloads/ralink/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/john/Downloads/ralink/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/john/Downloads/ralink/os/linux/../../common/crypt_aes.o
  CC [M]  /home/john/Downloads/ralink/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/john/Downloads/ralink/os/linux/../../common/mlme.o
  CC [M]  /home/john/Downloads/ralink/os/linux/../../common/cmm_wep.o
  CC [M]  /home/john/Downloads/ralink/os/linux/../../common/action.o
  CC [M]  /home/john/Downloads/ralink/os/linux/../../common/cmm_data.o
/home/john/Downloads/ralink/os/linux/../../common/cmm_data.c: In function &#8216;RtmpPrepareHwNullFrame&#8217;:
/home/john/Downloads/ralink/os/linux/../../common/cmm_data.c:3142:4: warning: passing argument 2 of &#8216;hex_dump&#8217; from incompatible pointer type [enabled by default]
    hex_dump("null frame before", &longValue, 4);
    ^
In file included from /home/john/Downloads/ralink/include/rt_config.h:66:0,
                 from /home/john/Downloads/ralink/os/linux/../../common/cmm_data.c:28:
/home/john/Downloads/ralink/include/rt_os_util.h:679:6: note: expected &#8216;unsigned char *&#8217; but argument is of type &#8216;UINT32 *&#8217;
 void hex_dump(char *str, unsigned char *pSrcBufVA, unsigned int SrcBufLen);
      ^
/home/john/Downloads/ralink/os/linux/../../common/cmm_data.c:3150:4: warning: passing argument 2 of &#8216;RTUSBReadMACRegister&#8217; makes integer from pointer without a cast [enabled by default]
    RTMP_IO_READ32(pAd, pAd->NullBufOffset + TXWISize+ i, &longValue);
    ^
In file included from /home/john/Downloads/ralink/include/rt_config.h:61:0,
                 from /home/john/Downloads/ralink/os/linux/../../common/cmm_data.c:28:
/home/john/Downloads/ralink/include/rtmp.h:7214:10: note: expected &#8216;USHORT&#8217; but argument is of type &#8216;USHORT *&#8217;
 NTSTATUS RTUSBReadMACRegister(
          ^
/home/john/Downloads/ralink/os/linux/../../common/cmm_data.c:3151:4: warning: passing argument 2 of &#8216;hex_dump&#8217; from incompatible pointer type [enabled by default]
    hex_dump("null frame after", &longValue, 4);
    ^
In file included from /home/john/Downloads/ralink/include/rt_config.h:66:0,
                 from /home/john/Downloads/ralink/os/linux/../../common/cmm_data.c:28:
/home/john/Downloads/ralink/include/rt_os_util.h:679:6: note: expected &#8216;unsigned char *&#8217; but argument is of type &#8216;UINT32 *&#8217;
 void hex_dump(char *str, unsigned char *pSrcBufVA, unsigned int SrcBufLen);
      ^
/home/john/Downloads/ralink/os/linux/../../common/cmm_data.c:3021:8: warning: unused variable &#8216;MlmeRate&#8217; [-Wunused-variable]
  UCHAR MlmeRate;
        ^
  CC [M]  /home/john/Downloads/ralink/os/linux/../../common/rtmp_init.o
/home/john/Downloads/ralink/os/linux/../../common/rtmp_init.c: In function &#8216;NICInitializeAsic&#8217;:
/home/john/Downloads/ralink/os/linux/../../common/rtmp_init.c:1826:11: warning: unused variable &#8216;apidx&#8217; [-Wunused-variable]
  INT    i,apidx;
           ^
/home/john/Downloads/ralink/os/linux/../../common/rtmp_init.c:1826:9: warning: unused variable &#8216;i&#8217; [-Wunused-variable]
  INT    i,apidx;
         ^
  CC [M]  /home/john/Downloads/ralink/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /home/john/Downloads/ralink/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/john/Downloads/ralink/os/linux/../../common/cmm_aes.o
  CC [M]  /home/john/Downloads/ralink/os/linux/../../common/cmm_sync.o
  CC [M]  /home/john/Downloads/ralink/os/linux/../../common/eeprom.o
  CC [M]  /home/john/Downloads/ralink/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/john/Downloads/ralink/os/linux/../../common/cmm_info.o
  CC [M]  /home/john/Downloads/ralink/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/john/Downloads/ralink/os/linux/../../common/cmm_wpa.o
/home/john/Downloads/ralink/os/linux/../../common/cmm_wpa.c: In function &#8216;PeerPairMsg3Action&#8217;:
/home/john/Downloads/ralink/os/linux/../../common/cmm_wpa.c:1031:13: warning: unused variable &#8216;Cancelled&#8217; [-Wunused-variable]
  BOOLEAN    Cancelled;
             ^
  CC [M]  /home/john/Downloads/ralink/os/linux/../../common/cmm_radar.o
  CC [M]  /home/john/Downloads/ralink/os/linux/../../common/spectrum.o
  CC [M]  /home/john/Downloads/ralink/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/john/Downloads/ralink/os/linux/../../common/rt_channel.o
  CC [M]  /home/john/Downloads/ralink/os/linux/../../common/cmm_profile.o
  CC [M]  /home/john/Downloads/ralink/os/linux/../../common/cmm_asic.o
/home/john/Downloads/ralink/os/linux/../../common/cmm_asic.c: In function &#8216;AsicGetAutoAgcOffsetForTemperatureSensor&#8217;:
/home/john/Downloads/ralink/os/linux/../../common/cmm_asic.c:1188:28: warning: assignment discards &#8216;const&#8217; qualifier from pointer target type [enabled by default]
   TxPowerTuningTableEntry0 = &TxPowerTuningTable[TuningTableIndex0 + TX_POWER_TUNING_ENTRY_OFFSET];
                            ^
/home/john/Downloads/ralink/os/linux/../../common/cmm_asic.c:1201:28: warning: assignment discards &#8216;const&#8217; qualifier from pointer target type [enabled by default]
   TxPowerTuningTableEntry1 = &TxPowerTuningTable[TuningTableIndex1 + TX_POWER_TUNING_ENTRY_OFFSET];
                            ^
  CC [M]  /home/john/Downloads/ralink/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/john/Downloads/ralink/os/linux/../../common/ps.o
  CC [M]  /home/john/Downloads/ralink/os/linux/../../common/uapsd.o
  CC [M]  /home/john/Downloads/ralink/os/linux/../../rate_ctrl/ra_ctrl.o
  CC [M]  /home/john/Downloads/ralink/os/linux/../../rate_ctrl/alg_legacy.o
  CC [M]  /home/john/Downloads/ralink/os/linux/../../rate_ctrl/alg_ags.o
  CC [M]  /home/john/Downloads/ralink/os/linux/../../chips/rtmp_chip.o
/home/john/Downloads/ralink/os/linux/../../chips/rtmp_chip.c: In function &#8216;RTMPReadChannelPwr&#8217;:
/home/john/Downloads/ralink/os/linux/../../chips/rtmp_chip.c:1380:2: warning: ISO C90 forbids mixed declarations and code [-Wdeclaration-after-statement]
  UCHAR  Tx2ALC = 0, Tx2FinePowerCtrl = 0;
  ^
  CC [M]  /home/john/Downloads/ralink/os/linux/../../sta/assoc.o
  CC [M]  /home/john/Downloads/ralink/os/linux/../../sta/auth.o
  CC [M]  /home/john/Downloads/ralink/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/john/Downloads/ralink/os/linux/../../sta/sync.o
  CC [M]  /home/john/Downloads/ralink/os/linux/../../sta/sanity.o
  CC [M]  /home/john/Downloads/ralink/os/linux/../../sta/rtmp_data.o
/home/john/Downloads/ralink/os/linux/../../sta/rtmp_data.c: In function &#8216;STAHandleRxDataFrame&#8217;:
/home/john/Downloads/ralink/os/linux/../../sta/rtmp_data.c:284:17: warning: unused variable &#8216;pFmeCtrl&#8217; [-Wunused-variable]
  FRAME_CONTROL *pFmeCtrl = &pHeader->FC;
                 ^
/home/john/Downloads/ralink/os/linux/../../sta/rtmp_data.c:283:8: warning: unused variable &#8216;OldPwrMgmt&#8217; [-Wunused-variable]
  UCHAR OldPwrMgmt = PWR_ACTIVE;
        ^
/home/john/Downloads/ralink/os/linux/../../sta/rtmp_data.c: In function &#8216;STAFindCipherAlgorithm&#8217;:
/home/john/Downloads/ralink/os/linux/../../sta/rtmp_data.c:1740:4: warning: suggest parentheses around &#8216;&&&#8217; within &#8216;||&#8217; [-Wparentheses]
    && (!ADHOC_ON(pAd))) || (ADHOC_ON(pAd) && (pAd->SharedKey[BSS0][KeyIdx].KeyLen == 0)))
    ^
  CC [M]  /home/john/Downloads/ralink/os/linux/../../sta/connect.o
  CC [M]  /home/john/Downloads/ralink/os/linux/../../sta/wpa.o
  CC [M]  /home/john/Downloads/ralink/os/linux/../../sta/sta_cfg.o
/home/john/Downloads/ralink/os/linux/../../sta/sta_cfg.c: In function &#8216;set_quality&#8217;:
/home/john/Downloads/ralink/os/linux/../../sta/sta_cfg.c:5548:2: warning: ISO C90 forbids mixed declarations and code [-Wdeclaration-after-statement]
  BOOLEAN bInitial = FALSE;
  ^
  CC [M]  /home/john/Downloads/ralink/os/linux/../../common/rt_os_util.o
  CC [M]  /home/john/Downloads/ralink/os/linux/../../os/linux/rt_linux.o
/home/john/Downloads/ralink/os/linux/../../os/linux/rt_linux.c: In function &#8216;__RtmpOSFSInfoChange&#8217;:
/home/john/Downloads/ralink/os/linux/../../os/linux/rt_linux.c:1141:20: error: incompatible types when assigning to type &#8216;int&#8217; from type &#8216;kuid_t&#8217;
   pOSFSInfo->fsuid = current_fsuid();
                    ^
/home/john/Downloads/ralink/os/linux/../../os/linux/rt_linux.c:1142:20: error: incompatible types when assigning to type &#8216;int&#8217; from type &#8216;kgid_t&#8217;
   pOSFSInfo->fsgid = current_fsgid();
                    ^
make[2]: *** [/home/john/Downloads/ralink/os/linux/../../os/linux/rt_linux.o] Error 1
make[1]: *** [_module_/home/john/Downloads/ralink/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-24-generic'
make: *** [LINUX] Error 2

```




can anyone please help me getting my wifi adapter running??

---

### Post by chili555 on 2014-04-27
> Hello all,
i'm also using Lubuntu14.04. 
i ve recetly purchased a usb wifi adapter. the lsusb says its a ralink 5370 device.
based on previous helps on ralink 5370...i did following:
- added blacklist rt2800usb blacklist rt2870sta blacklist rt2x00
- changed to download folder where ive downloaded the driver for 5370.
- after make clean i ran make
- make cmd is giving two errors:The errors you list suggest you are trying to compile a driver that's much too old for your 3.13.0-xx kernel, gcc version, etc., included in Ubuntu 14.04. As I like to put it, you are trying to put wooden wheels on your sleek black 2014 BMW. It will never work. Ever.

In fact, your device is driven by the driver rt2800usb that you blacklisted. Doesn't it work as expected? Shouldn't we troubleshoot from there? What are the symptoms when the proper rt2800usb is loaded? Does it try to connect or what?

Incidentally, there is no driver rt2870sta nor rt2x00 in Ubuntu 14.04. Your blacklists are meaningless.

---

### Post by varunendra on 2014-04-27
+1 to trying the native one first. I have a couple of reference posts that report the native drivers (actually backported from kernel 12.8) to be working nicely. Your driver, risva, is even newer.

I suggest you post the same stuff as I asked in my first post above *(wireless_script report + outputs from Live DVD if it works there + description of problem you are having)*, so we can see if there is some obvious culprit that can be easily fixed.

**PS:**
@risva,
I noticed your post much before you PM'ed me, but chose to ignore it for a while since I had no time to look into it. But you are in the best hands now. I don't get much time to troubleshoot problems on the forums these days, and I certainly can't go as far as Dr. chili can and would go to get your problem solved. :)

---

### Post by risva on 2014-04-28
the output of wireless script when run through live cd is as under
```


########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux lubuntu 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:08:14 UTC 2014 i686 i686 i686 GNU/Linux

##### lspci #####

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [10ec:8139] (rev 10)
    Subsystem: Hewlett-Packard Company Device [103c:3084]
    Kernel driver in use: 8139too

##### lsusb #####

Bus 001 Device 003: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA Card Info #####

##### rfkill #####

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### iw reg get #####

##### interfaces #####

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

##### iwconfig #####

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #####

nameserver 127.0.1.1

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800usb
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    JOHN-PC_Network: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 65 WPA2

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### iwlist #####

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"JOHN-PC_Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000036bd0e08f
                    Extra: Last beacon: 20ms ago
                    IE: Unknown: 000F4A4F484E2D50435F4E6574776F726B
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601050700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706555300010B10
                    IE: Unknown: DD9D0050F204104A0001001044000102103B00010310470010BC329E001DD811B28601F81A6754DCEE1021001852616C696E6B20546563686E6F6C6F67792C20436F72702E1023001C52616C696E6B20576972656C6573732041636365737320506F696E74102400065254323836301042000831323334353637381054000800060050F20400011011000952616C696E6B415053100800020004103C000100

##### iwlist channel #####

wlan0     14 channels in total; available frequencies :
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

##### lsmod #####

rt2800usb              26581  0 
rt2x00usb              20041  1 rt2800usb
rt2800lib              83150  1 rt2800usb
rt2x00lib              48886  3 rt2x00usb,rt2800lib,rt2800usb
mac80211              545990  3 rt2x00lib,rt2x00usb,rt2800lib
cfg80211              409394  2 mac80211,rt2x00lib
crc_ccitt              12627  1 rt2800lib

##### modinfo #####

filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
license:        GPL
firmware:       rt2870.bin
description:    Ralink RT2800 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     D6F814DAF78F2BEA3DA12CB
alias:          usb:vF201p5370d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v177Fp0254d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApF511d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApD522d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApC522d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApA512d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p006Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0069d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0053d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p004Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p004Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p003Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v08B9p1197d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v18E8p6259d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB29d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB24d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1D4Dp0010d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05A6p0101d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v100Dp9032d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0789p0169d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0789p0168d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p0615d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p0605d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp094Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148FpF101d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v06F8pE036d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1044p800Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v15A9p0010d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p0602d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p0600d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v203Dp14A1d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C0Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v18C5p0008d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07AAp0042d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07AAp0041d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p0150d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p0148d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p012Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp1003d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3401d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3400d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3399d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3340d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3322d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3284d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3262d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p17A7d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1790d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1761d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1760d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p166Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E0Bp9041d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E0Bp9031d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C11d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C08d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p3074d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p3073d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v20F4p724Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp5572d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v043Ep7A13d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3C21d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3C1Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p0241d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v057Cp8501d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v043Ep7A32d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp5372d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp5370d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0471p2182d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0471p2181d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0471p2180d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0471p2126d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0471p2104d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04DAp23F6d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04DAp1800d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04DAp1801d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v043Ep7A42d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v043Ep7A22d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3C23d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3C22d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3C20d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3C1Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3C1Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3C1Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3C19d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3C15d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3365d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3329d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v043Ep7A32d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v043Ep7A12d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0586p3421d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p006Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p006Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0067d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp3573d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pED19d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p9019d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p9013d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p9012d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0789p016Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13B1p003Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp094Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0021d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0020d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p7733d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3C1Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148FpF301d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp1103d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p17ADd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p17BCd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B75p7733d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5A57p0284d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0930p0A07d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0068d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0066d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0065d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0062d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0041d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp3572d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0789p0170d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1737p0079d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13B1p002Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp0944d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9801d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v167Bp4001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p179Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1690p0764d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1690p0761d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1690p0744d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v8516p3572d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v177Fp0165d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v177Fp0163d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0050d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp8070d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp3370d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0471p20DDd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApB511d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3C17d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp945Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0586p343Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0586p341Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0586p341Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0586p3418d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0586p3416d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5A57p5257d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5A57p0283d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5A57p0280d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CDEp0025d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CDEp0022d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v157Ep3013d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v157Ep300Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v177Fp0324d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v177Fp0323d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v177Fp0313d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v177Fp0302d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v177Fp0164d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v177Fp0153d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v15A9p0006d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApB522d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApA703d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApA702d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApA701d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApA618d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083Ap8522d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083Ap7522d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083Ap7512d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083Ap7511d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083Ap6618d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0060d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p005Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0051d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0048d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0047d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0042d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0040d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p003Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p003Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p003Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p003Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0039d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p002Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p002Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p002Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0017d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v129Bp1828d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04E8p2018d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp3072d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp3071d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp2870d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp2770d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp2070d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1A32p0304d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pED06d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB25d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019p5201d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0471p200Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1D4Dp0011d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1D4Dp000Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1D4Dp000Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1D4Dp0002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v20B8p8888d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B75p3072d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B75p3071d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p899Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p871Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p871Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p871Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p870Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p822Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p822Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p822Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p821Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p6899d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p3871d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p3870d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p3822d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p3821d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p3820d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v100Dp9031d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0789p0166d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0789p0164d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0789p0163d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0789p0162d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1737p0078d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1737p0077d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1737p0071d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1737p0070d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13B1p0031d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp0948d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp0947d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp0945d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0018d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0017d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0013d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p000Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0009d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0003d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1044p800Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1044p800Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v15A9p0012d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9709d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9708d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9707d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9706d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9705d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9703d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9702d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9701d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v203Dp14A9d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v203Dp1480d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p7722d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p7718d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p7717d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p7711d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p4085d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0FE9pB307d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07FAp7712d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3C1Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C17d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C16d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C15d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C13d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C11d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C0Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C0Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C0Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C0Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C09d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v18C5p0012d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07AAp003Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07AAp003Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07AAp002Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p01A8d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p01EEd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p01A2d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p016Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p015Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p0158d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p00E8d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp935Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp935Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp825Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp825Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp805Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp8053d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3321d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3307d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3305d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3273d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3247d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1761p0B05d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1784d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1742d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1732d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1731d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1690p0740d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v15C5p0008d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C2Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C28d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C27d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C25d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C23d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C12d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C09d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C07d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C06d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v8516p3072d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v8516p3071d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v8516p3070d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v8516p2870d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v8516p2770d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v8516p2070d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1EDAp2310d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1EDAp2210d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1EDAp2012d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1482p3C09d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p3072d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p3071d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p2770d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p2870d*dc*dsc*dp*ic*isc*ip*in*
depends:        rt2x00lib,rt2800lib,rt2x00usb
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:96:DC:92:B0:1D:75:9D:3E:85:62:EA:32:A1:C7
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)

filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
license:        GPL
description:    rt2x00 usb library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     44768071492503F8EFE1EED
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:96:DC:92:B0:1D:75:9D:3E:85:62:EA:32:A1:C7
sig_hashalgo:   sha512

filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     9BD0087B6943A41E7FD8EDA
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:96:DC:92:B0:1D:75:9D:3E:85:62:EA:32:A1:C7
sig_hashalgo:   sha512

filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     C57F87A3569F5363E79FD42
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:96:DC:92:B0:1D:75:9D:3E:85:62:EA:32:A1:C7
sig_hashalgo:   sha512

##### modules #####

##### blacklist #####

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

[/etc/modprobe.d/fbdev-blacklist.conf]
blacklist arkfb
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist gx1fb
blacklist gxfb
blacklist kyrofb
blacklist matroxfb_base
blacklist mb862xxfb
blacklist neofb
blacklist nvidiafb
blacklist pm2fb
blacklist pm3fb
blacklist s3fb
blacklist savagefb
blacklist sisfb
blacklist tdfxfb
blacklist tridentfb
blacklist viafb
blacklist vt8623fb

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

##### udev rules #####

# PCI device 0x10ec:0x8139 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[  116.618683] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 5390, rev 0502 detected
[  116.646931] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 5370 detected
[  124.828480] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  125.251195] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  125.494028] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  125.495082] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  164.944156] Modules linked in: arc4 rt2800usb rt2x00usb rt2800lib zram(C) rt2x00lib mac80211 cfg80211 snd_intel8x0 snd_ac97_codec dm_crypt ac97_bus snd_pcm crc_ccitt snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi joydev snd_seq lpc_ich pcmcia snd_seq_device yenta_socket dm_multipath psmouse snd_timer scsi_dh pcmcia_rsrc pcmcia_core snd serio_raw soundcore shpchp bnep rfcomm parport_pc mac_hid ppdev bluetooth lp parport squashfs overlayfs nls_utf8 isofs dm_mirror dm_region_hash dm_log hid_logitech ff_memless usbhid hid i915 firewire_ohci i2c_algo_bit drm_kms_helper firewire_core 8139too drm 8139cp mii crc_itu_t wmi video
[  164.944778] Modules linked in: arc4 rt2800usb rt2x00usb rt2800lib zram(C) rt2x00lib mac80211 cfg80211 snd_intel8x0 snd_ac97_codec dm_crypt ac97_bus snd_pcm crc_ccitt snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi joydev snd_seq lpc_ich pcmcia snd_seq_device yenta_socket dm_multipath psmouse snd_timer scsi_dh pcmcia_rsrc pcmcia_core snd serio_raw soundcore shpchp bnep rfcomm parport_pc mac_hid ppdev bluetooth lp parport squashfs overlayfs nls_utf8 isofs dm_mirror dm_region_hash dm_log hid_logitech ff_memless usbhid hid i915 firewire_ohci i2c_algo_bit drm_kms_helper firewire_core 8139too drm 8139cp mii crc_itu_t wmi video
[  164.945319] Modules linked in: arc4 rt2800usb rt2x00usb rt2800lib zram(C) rt2x00lib mac80211 cfg80211 snd_intel8x0 snd_ac97_codec dm_crypt ac97_bus snd_pcm crc_ccitt snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi joydev snd_seq lpc_ich pcmcia snd_seq_device yenta_socket dm_multipath psmouse snd_timer scsi_dh pcmcia_rsrc pcmcia_core snd serio_raw soundcore shpchp bnep rfcomm parport_pc mac_hid ppdev bluetooth lp parport squashfs overlayfs nls_utf8 isofs dm_mirror dm_region_hash dm_log hid_logitech ff_memless usbhid hid i915 firewire_ohci i2c_algo_bit drm_kms_helper firewire_core 8139too drm 8139cp mii crc_itu_t wmi video
[  164.945857] Modules linked in: arc4 rt2800usb rt2x00usb rt2800lib zram(C) rt2x00lib mac80211 cfg80211 snd_intel8x0 snd_ac97_codec dm_crypt ac97_bus snd_pcm crc_ccitt snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi joydev snd_seq lpc_ich pcmcia snd_seq_device yenta_socket dm_multipath psmouse snd_timer scsi_dh pcmcia_rsrc pcmcia_core snd serio_raw soundcore shpchp bnep rfcomm parport_pc mac_hid ppdev bluetooth lp parport squashfs overlayfs nls_utf8 isofs dm_mirror dm_region_hash dm_log hid_logitech ff_memless usbhid hid i915 firewire_ohci i2c_algo_bit drm_kms_helper firewire_core 8139too drm 8139cp mii crc_itu_t wmi video
[  164.946391] Modules linked in: arc4 rt2800usb rt2x00usb rt2800lib zram(C) rt2x00lib mac80211 cfg80211 snd_intel8x0 snd_ac97_codec dm_crypt ac97_bus snd_pcm crc_ccitt snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi joydev snd_seq lpc_ich pcmcia snd_seq_device yenta_socket dm_multipath psmouse snd_timer scsi_dh pcmcia_rsrc pcmcia_core snd serio_raw soundcore shpchp bnep rfcomm parport_pc mac_hid ppdev bluetooth lp parport squashfs overlayfs nls_utf8 isofs dm_mirror dm_region_hash dm_log hid_logitech ff_memless usbhid hid i915 firewire_ohci i2c_algo_bit drm_kms_helper firewire_core 8139too drm 8139cp mii crc_itu_t wmi video
[  164.988124] Modules linked in: arc4 rt2800usb rt2x00usb rt2800lib zram(C) rt2x00lib mac80211 cfg80211 snd_intel8x0 snd_ac97_codec dm_crypt ac97_bus snd_pcm crc_ccitt snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi joydev snd_seq lpc_ich pcmcia snd_seq_device yenta_socket dm_multipath psmouse snd_timer scsi_dh pcmcia_rsrc pcmcia_core snd serio_raw soundcore shpchp bnep rfcomm parport_pc mac_hid ppdev bluetooth lp parport squashfs overlayfs nls_utf8 isofs dm_mirror dm_region_hash dm_log hid_logitech ff_memless usbhid hid i915 firewire_ohci i2c_algo_bit drm_kms_helper firewire_core 8139too drm 8139cp mii crc_itu_t wmi video
[  164.988648] Modules linked in: arc4 rt2800usb rt2x00usb rt2800lib zram(C) rt2x00lib mac80211 cfg80211 snd_intel8x0 snd_ac97_codec dm_crypt ac97_bus snd_pcm crc_ccitt snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi joydev snd_seq lpc_ich pcmcia snd_seq_device yenta_socket dm_multipath psmouse snd_timer scsi_dh pcmcia_rsrc pcmcia_core snd serio_raw soundcore shpchp bnep rfcomm parport_pc mac_hid ppdev bluetooth lp parport squashfs overlayfs nls_utf8 isofs dm_mirror dm_region_hash dm_log hid_logitech ff_memless usbhid hid i915 firewire_ohci i2c_algo_bit drm_kms_helper firewire_core 8139too drm 8139cp mii crc_itu_t wmi video
[  164.989105] Modules linked in: arc4 rt2800usb rt2x00usb rt2800lib zram(C) rt2x00lib mac80211 cfg80211 snd_intel8x0 snd_ac97_codec dm_crypt ac97_bus snd_pcm crc_ccitt snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi joydev snd_seq lpc_ich pcmcia snd_seq_device yenta_socket dm_multipath psmouse snd_timer scsi_dh pcmcia_rsrc pcmcia_core snd serio_raw soundcore shpchp bnep rfcomm parport_pc mac_hid ppdev bluetooth lp parport squashfs overlayfs nls_utf8 isofs dm_mirror dm_region_hash dm_log hid_logitech ff_memless usbhid hid i915 firewire_ohci i2c_algo_bit drm_kms_helper firewire_core 8139too drm 8139cp mii crc_itu_t wmi video
[  164.989560] Modules linked in: arc4 rt2800usb rt2x00usb rt2800lib zram(C) rt2x00lib mac80211 cfg80211 snd_intel8x0 snd_ac97_codec dm_crypt ac97_bus snd_pcm crc_ccitt snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi joydev snd_seq lpc_ich pcmcia snd_seq_device yenta_socket dm_multipath psmouse snd_timer scsi_dh pcmcia_rsrc pcmcia_core snd serio_raw soundcore shpchp bnep rfcomm parport_pc mac_hid ppdev bluetooth lp parport squashfs overlayfs nls_utf8 isofs dm_mirror dm_region_hash dm_log hid_logitech ff_memless usbhid hid i915 firewire_ohci i2c_algo_bit drm_kms_helper firewire_core 8139too drm 8139cp mii crc_itu_t wmi video
[  164.990013] Modules linked in: arc4 rt2800usb rt2x00usb rt2800lib zram(C) rt2x00lib mac80211 cfg80211 snd_intel8x0 snd_ac97_codec dm_crypt ac97_bus snd_pcm crc_ccitt snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi joydev snd_seq lpc_ich pcmcia snd_seq_device yenta_socket dm_multipath psmouse snd_timer scsi_dh pcmcia_rsrc pcmcia_core snd serio_raw soundcore shpchp bnep rfcomm parport_pc mac_hid ppdev bluetooth lp parport squashfs overlayfs nls_utf8 isofs dm_mirror dm_region_hash dm_log hid_logitech ff_memless usbhid hid i915 firewire_ohci i2c_algo_bit drm_kms_helper firewire_core 8139too drm 8139cp mii crc_itu_t wmi video

########## wireless info END ############



```

---

### Post by varunendra on 2014-04-28
Report from Live session would have been helpful if wifi was working in that mode. If not, it is probably not going to help anything other than testing, but I think even testing would make more sense on the installed system.

---

### Post by risva on 2014-04-28
**The output of wireless script having booted from hard disk** is as under:
```


########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux john-Presario-2200-PR557PC-UUF 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:08:14 UTC 2014 i686 i686 i686 GNU/Linux

##### lspci #####

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [10ec:8139] (rev 10)
    Subsystem: Hewlett-Packard Company Device [103c:3084]
    Kernel driver in use: 8139too

##### lsusb #####

Bus 001 Device 002: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA Card Info #####

##### rfkill #####

##### iw reg get #####

##### interfaces #####

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

##### iwconfig #####

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #####

nameserver 127.0.1.1

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### iwlist #####

##### iwlist channel #####

##### lsmod #####

##### modinfo #####

##### modules #####

lp

##### blacklist #####

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
blacklist rt2800usb
blacklist rt2870sta
blacklist rt2x00

[/etc/modprobe.d/blaclist.conf]
blacklist rt2800usb
blacklist rt2870sta 

[/etc/modprobe.d/fbdev-blacklist.conf]
blacklist arkfb
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist gx1fb
blacklist gxfb
blacklist kyrofb
blacklist matroxfb_base
blacklist mb862xxfb
blacklist neofb
blacklist nvidiafb
blacklist pm2fb
blacklist pm3fb
blacklist s3fb
blacklist savagefb
blacklist sisfb
blacklist tdfxfb
blacklist tridentfb
blacklist viafb
blacklist vt8623fb

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

##### udev rules #####

# PCI device 0x10ec:0x8139 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

########## wireless info END ############



```


_**My Problem:**_

I ve a celeron M Pressario 2200.
Im using Lubuntu in forced pae config. the laptop doesnot have a wifi adapter, so i ve recently purchased "himax usb wifi adapter"


while trying to install it on my machine started from forum help....
i believe the mistake is that i followed what was actually meant for previous versions of (L)ubuntu.

I need help in activating this wifi adapter on my machine.

---

### Post by chili555 on 2014-04-28
After suspend, is the required driver loaded or dropped?```
lsmod | grep rt2
```

---

### Post by risva on 2014-04-28
sorry Chili555, im a very superficial user of ubuntu. i do not understand anything, when u ask " After suspend, is the required driver loaded or dropped?"

i simply opened the terminal and executed the above comd.... there was no reply.....just the next $ prompt appeared.

i request u 2 please walk me through the steps for whatever im supposed to do.

thanx

---

### Post by chili555 on 2014-04-28
> i simply opened the terminal and executed the above comd.... there was no reply.....just the next $ prompt appeared.The command simply meant 'list all the loaded modules (lsmod) but only print out the ones with rt2 in their name.' You got nothing, nada, zippo. That means that your relevant driver was *NOT* loaded when you resumed from suspend:> # USB device 0x:0x ([COLOR="#FF0000"]rt2800usb[/COLOR])
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
Let's try an old trick to see if you can get it to reload upon resume. Please open a terminal and do:```
sudo gedit /etc/pm/config.d/config
```A new empty file will open; add a single line:```
SUSPEND_MODULES="rt2800usb"
```Proofread carefully, save and close gedit. Reboot and tell us if it is working.

---

### Post by praseodym on 2014-04-28
Hi there,

my collegue "flash63" brought up a revised driver rt5370sta:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget media.cdn.ubuntu-de.org/forum/attachments/13/16/4365112-Ralink_5370sta-2.5.0.3_dkms.tar.gz
sudo tar xvf 4365112-Ralink_5370sta-2.5.0.3_dkms.tar.gz -C /usr/src
sudo dkms add -m Ralink_5370sta -v 2.5.0.3
sudo dkms build -m Ralink_5370sta -v 2.5.0.3
sudo dkms install -m Ralink_5370sta -v 2.5.0.3 
sudo mkdir -p /etc/Wireless/RT2870STA
sudo cp /usr/src/Ralink_5370sta-2.5.0.3/src/RT2870STA.dat /etc/Wireless/RT2870STA 
echo "blacklist rt2800usb" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot and check the S/H settings with this one

---

### Post by risva on 2014-04-28
running the wireless sript(above), after 
 	```


 	SUSPEND_MODULES="rt2800usb" 
```

is 

```


########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux john-Presario-2200-PR557PC-UUF 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:08:14 UTC 2014 i686 i686 i686 GNU/Linux

##### lspci #####

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [10ec:8139] (rev 10)
    Subsystem: Hewlett-Packard Company Device [103c:3084]
    Kernel driver in use: 8139too

##### lsusb #####

Bus 001 Device 003: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA Card Info #####

##### rfkill #####

##### iw reg get #####

##### interfaces #####

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

##### iwconfig #####

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #####

nameserver 127.0.1.1

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### iwlist #####

##### iwlist channel #####

##### lsmod #####

##### modinfo #####

##### modules #####

lp

##### blacklist #####

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
blacklist rt2800usb
blacklist rt2870sta
blacklist rt2x00

[/etc/modprobe.d/blaclist.conf]
blacklist rt2800usb
blacklist rt2870sta 

[/etc/modprobe.d/fbdev-blacklist.conf]
blacklist arkfb
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist gx1fb
blacklist gxfb
blacklist kyrofb
blacklist matroxfb_base
blacklist mb862xxfb
blacklist neofb
blacklist nvidiafb
blacklist pm2fb
blacklist pm3fb
blacklist s3fb
blacklist savagefb
blacklist sisfb
blacklist tdfxfb
blacklist tridentfb
blacklist viafb
blacklist vt8623fb

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

##### udev rules #####

# PCI device 0x10ec:0x8139 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

########## wireless info END ############



```

---

### Post by risva on 2014-04-28
Dear Praseodym,

on running the commands given by you, 
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget media.cdn.ubuntu-de.org/forum/attachments/13/16/4365112-Ralink_5370sta-2.5.0.3_dkms.tar.gz
sudo tar xvf 4365112-Ralink_5370sta-2.5.0.3_dkms.tar.gz -C /usr/src
sudo dkms add -m Ralink_5370sta -v 2.5.0.3
sudo dkms build -m Ralink_5370sta -v 2.5.0.3
sudo dkms install -m Ralink_5370sta -v 2.5.0.3 
sudo mkdir -p /etc/Wireless/RT2870STA
sudo cp /usr/src/Ralink_5370sta-2.5.0.3/src/RT2870STA.dat /etc/Wireless/RT2870STA 
echo "blacklist rt2800usb" | sudo tee -a /etc/modprobe.d/blacklist.conf

```

there  was no error, on rebooting and running the wireless script reffered in this thread above the output recieved is a s under:

```


########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux john-Presario-2200-PR557PC-UUF 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:08:14 UTC 2014 i686 i686 i686 GNU/Linux

##### lspci #####

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [10ec:8139] (rev 10)
    Subsystem: Hewlett-Packard Company Device [103c:3084]
    Kernel driver in use: 8139too

##### lsusb #####

Bus 001 Device 003: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA Card Info #####

##### rfkill #####

##### iw reg get #####

##### interfaces #####

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

##### iwconfig #####

ra0       Ralink STA  ESSID:""  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #####

nameserver 127.0.1.1

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

- Device: ra0 ------------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            usb
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    JOHN-PC_Network: Infra, <MAC address removed>, Freq 2412 MHz, Rate 22 Mb/s, Strength 74 WPA2

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### iwlist #####

ra0       Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Protocol:802.11b/g/n
                    ESSID:"JOHN-PC_Network"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality=81/100  Signal level=-58 dBm  Noise level=-92 dBm
                    Encryption key:on
                    Bit Rates:150 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD270050F204104A000100104400010210470010BC329E001DD811B28601F81A6754DCEE103C000101

##### iwlist channel #####

ra0       11 channels in total; available frequencies :
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
          Current Frequency=2.412 GHz (Channel 1)

##### lsmod #####

rt5370sta             722559  1 

##### modinfo #####

filename:       /lib/modules/3.13.0-24-generic/updates/dkms/rt5370sta.ko
version:        2.5.0.3
license:        GPL
description:    RT2870 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
srcversion:     0F52661CC478B626332AAF0
alias:          usb:v043Ep7A22d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v043Ep7A12d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3C1Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3C1Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3C19d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3C15d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3329d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3365d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp5372d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp5370d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0050d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp3370d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1EDAp2012d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0586p343Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0586p341Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0586p341Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0789p0166d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07FAp7712d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3321d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3307d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApA703d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p821Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p3821d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p822Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p871Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p3871d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p3822d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p6899d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p870Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p3870d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p899Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v203Dp14A9d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1784d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v20B8p8888d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v203Dp1480d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp0948d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp0947d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp0945d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5A57p0283d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5A57p5257d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1D4Dp0011d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1D4Dp000Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1D4Dp000Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C17d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C16d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C0Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C0Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C0Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C0Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1EDAp2310d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1A32p0304d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p4085d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p7711d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p3072d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p3071d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019p5201d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB25d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1044p800Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3305d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3273d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9709d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9708d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9707d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9706d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9705d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9703d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApA702d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApA701d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083Ap7511d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v18C5p0012d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C12d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p005Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0047d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0048d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0042d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p003Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p822Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p871Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p822Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p871Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p3820d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp3072d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp3071d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip*in*
depends:        
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
parm:           mac:rt28xx: wireless mac addr (charp)

##### modules #####

lp

##### blacklist #####

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
blacklist rt2800usb
blacklist rt2870sta
blacklist rt2x00
blacklist rt2800usb

[/etc/modprobe.d/blaclist.conf]
blacklist rt2800usb
blacklist rt2870sta 

[/etc/modprobe.d/fbdev-blacklist.conf]
blacklist arkfb
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist gx1fb
blacklist gxfb
blacklist kyrofb
blacklist matroxfb_base
blacklist mb862xxfb
blacklist neofb
blacklist nvidiafb
blacklist pm2fb
blacklist pm3fb
blacklist s3fb
blacklist savagefb
blacklist sisfb
blacklist tdfxfb
blacklist tridentfb
blacklist viafb
blacklist vt8623fb

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

##### udev rules #####

# PCI device 0x10ec:0x8139 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[   18.517502] Modules linked in: bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm rt5370sta(OF) snd_page_alloc snd_seq_midi snd_seq_midi_event joydev snd_rawmidi pcmcia snd_seq psmouse snd_seq_device snd_timer serio_raw yenta_socket snd pcmcia_rsrc pcmcia_core lpc_ich soundcore i915 shpchp drm_kms_helper wmi drm i2c_algo_bit video mac_hid parport_pc ppdev lp parport hid_logitech ff_memless usbhid hid firewire_ohci 8139too 8139cp firewire_core mii crc_itu_t
[   18.518064] Modules linked in: bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm rt5370sta(OF) snd_page_alloc snd_seq_midi snd_seq_midi_event joydev snd_rawmidi pcmcia snd_seq psmouse snd_seq_device snd_timer serio_raw yenta_socket snd pcmcia_rsrc pcmcia_core lpc_ich soundcore i915 shpchp drm_kms_helper wmi drm i2c_algo_bit video mac_hid parport_pc ppdev lp parport hid_logitech ff_memless usbhid hid firewire_ohci 8139too 8139cp firewire_core mii crc_itu_t
[   18.518619] Modules linked in: bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm rt5370sta(OF) snd_page_alloc snd_seq_midi snd_seq_midi_event joydev snd_rawmidi pcmcia snd_seq psmouse snd_seq_device snd_timer serio_raw yenta_socket snd pcmcia_rsrc pcmcia_core lpc_ich soundcore i915 shpchp drm_kms_helper wmi drm i2c_algo_bit video mac_hid parport_pc ppdev lp parport hid_logitech ff_memless usbhid hid firewire_ohci 8139too 8139cp firewire_core mii crc_itu_t
[   18.576153] Modules linked in: bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm rt5370sta(OF) snd_page_alloc snd_seq_midi snd_seq_midi_event joydev snd_rawmidi pcmcia snd_seq psmouse snd_seq_device snd_timer serio_raw yenta_socket snd pcmcia_rsrc pcmcia_core lpc_ich soundcore i915 shpchp drm_kms_helper wmi drm i2c_algo_bit video mac_hid parport_pc ppdev lp parport hid_logitech ff_memless usbhid hid firewire_ohci 8139too 8139cp firewire_core mii crc_itu_t
[   18.576707] Modules linked in: bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm rt5370sta(OF) snd_page_alloc snd_seq_midi snd_seq_midi_event joydev snd_rawmidi pcmcia snd_seq psmouse snd_seq_device snd_timer serio_raw yenta_socket snd pcmcia_rsrc pcmcia_core lpc_ich soundcore i915 shpchp drm_kms_helper wmi drm i2c_algo_bit video mac_hid parport_pc ppdev lp parport hid_logitech ff_memless usbhid hid firewire_ohci 8139too 8139cp firewire_core mii crc_itu_t
[   18.577198] Modules linked in: bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm rt5370sta(OF) snd_page_alloc snd_seq_midi snd_seq_midi_event joydev snd_rawmidi pcmcia snd_seq psmouse snd_seq_device snd_timer serio_raw yenta_socket snd pcmcia_rsrc pcmcia_core lpc_ich soundcore i915 shpchp drm_kms_helper wmi drm i2c_algo_bit video mac_hid parport_pc ppdev lp parport hid_logitech ff_memless usbhid hid firewire_ohci 8139too 8139cp firewire_core mii crc_itu_t
[   18.577688] Modules linked in: bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm rt5370sta(OF) snd_page_alloc snd_seq_midi snd_seq_midi_event joydev snd_rawmidi pcmcia snd_seq psmouse snd_seq_device snd_timer serio_raw yenta_socket snd pcmcia_rsrc pcmcia_core lpc_ich soundcore i915 shpchp drm_kms_helper wmi drm i2c_algo_bit video mac_hid parport_pc ppdev lp parport hid_logitech ff_memless usbhid hid firewire_ohci 8139too 8139cp firewire_core mii crc_itu_t
[   18.578176] Modules linked in: bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm rt5370sta(OF) snd_page_alloc snd_seq_midi snd_seq_midi_event joydev snd_rawmidi pcmcia snd_seq psmouse snd_seq_device snd_timer serio_raw yenta_socket snd pcmcia_rsrc pcmcia_core lpc_ich soundcore i915 shpchp drm_kms_helper wmi drm i2c_algo_bit video mac_hid parport_pc ppdev lp parport hid_logitech ff_memless usbhid hid firewire_ohci 8139too 8139cp firewire_core mii crc_itu_t
[   20.945563] <==== rt28xx_init, Status=0
[   21.900278] Modules linked in: cfg80211 rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm rt5370sta(OF) snd_page_alloc snd_seq_midi snd_seq_midi_event joydev snd_rawmidi pcmcia snd_seq psmouse snd_seq_device snd_timer serio_raw yenta_socket snd pcmcia_rsrc pcmcia_core lpc_ich soundcore i915 shpchp drm_kms_helper wmi drm i2c_algo_bit video mac_hid parport_pc ppdev lp parport hid_logitech ff_memless usbhid hid firewire_ohci 8139too 8139cp firewire_core mii crc_itu_t
[   21.900903] Modules linked in: cfg80211 rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm rt5370sta(OF) snd_page_alloc snd_seq_midi snd_seq_midi_event joydev snd_rawmidi pcmcia snd_seq psmouse snd_seq_device snd_timer serio_raw yenta_socket snd pcmcia_rsrc pcmcia_core lpc_ich soundcore i915 shpchp drm_kms_helper wmi drm i2c_algo_bit video mac_hid parport_pc ppdev lp parport hid_logitech ff_memless usbhid hid firewire_ohci 8139too 8139cp firewire_core mii crc_itu_t
[   21.901481] Modules linked in: cfg80211 rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm rt5370sta(OF) snd_page_alloc snd_seq_midi snd_seq_midi_event joydev snd_rawmidi pcmcia snd_seq psmouse snd_seq_device snd_timer serio_raw yenta_socket snd pcmcia_rsrc pcmcia_core lpc_ich soundcore i915 shpchp drm_kms_helper wmi drm i2c_algo_bit video mac_hid parport_pc ppdev lp parport hid_logitech ff_memless usbhid hid firewire_ohci 8139too 8139cp firewire_core mii crc_itu_t
[   21.902034] Modules linked in: cfg80211 rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm rt5370sta(OF) snd_page_alloc snd_seq_midi snd_seq_midi_event joydev snd_rawmidi pcmcia snd_seq psmouse snd_seq_device snd_timer serio_raw yenta_socket snd pcmcia_rsrc pcmcia_core lpc_ich soundcore i915 shpchp drm_kms_helper wmi drm i2c_algo_bit video mac_hid parport_pc ppdev lp parport hid_logitech ff_memless usbhid hid firewire_ohci 8139too 8139cp firewire_core mii crc_itu_t
[   21.902584] Modules linked in: cfg80211 rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm rt5370sta(OF) snd_page_alloc snd_seq_midi snd_seq_midi_event joydev snd_rawmidi pcmcia snd_seq psmouse snd_seq_device snd_timer serio_raw yenta_socket snd pcmcia_rsrc pcmcia_core lpc_ich soundcore i915 shpchp drm_kms_helper wmi drm i2c_algo_bit video mac_hid parport_pc ppdev lp parport hid_logitech ff_memless usbhid hid firewire_ohci 8139too 8139cp firewire_core mii crc_itu_t
[   21.956833] Modules linked in: cfg80211 rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm rt5370sta(OF) snd_page_alloc snd_seq_midi snd_seq_midi_event joydev snd_rawmidi pcmcia snd_seq psmouse snd_seq_device snd_timer serio_raw yenta_socket snd pcmcia_rsrc pcmcia_core lpc_ich soundcore i915 shpchp drm_kms_helper wmi drm i2c_algo_bit video mac_hid parport_pc ppdev lp parport hid_logitech ff_memless usbhid hid firewire_ohci 8139too 8139cp firewire_core mii crc_itu_t
[   21.957411] Modules linked in: cfg80211 rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm rt5370sta(OF) snd_page_alloc snd_seq_midi snd_seq_midi_event joydev snd_rawmidi pcmcia snd_seq psmouse snd_seq_device snd_timer serio_raw yenta_socket snd pcmcia_rsrc pcmcia_core lpc_ich soundcore i915 shpchp drm_kms_helper wmi drm i2c_algo_bit video mac_hid parport_pc ppdev lp parport hid_logitech ff_memless usbhid hid firewire_ohci 8139too 8139cp firewire_core mii crc_itu_t
[   21.957896] Modules linked in: cfg80211 rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm rt5370sta(OF) snd_page_alloc snd_seq_midi snd_seq_midi_event joydev snd_rawmidi pcmcia snd_seq psmouse snd_seq_device snd_timer serio_raw yenta_socket snd pcmcia_rsrc pcmcia_core lpc_ich soundcore i915 shpchp drm_kms_helper wmi drm i2c_algo_bit video mac_hid parport_pc ppdev lp parport hid_logitech ff_memless usbhid hid firewire_ohci 8139too 8139cp firewire_core mii crc_itu_t
[   21.958382] Modules linked in: cfg80211 rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm rt5370sta(OF) snd_page_alloc snd_seq_midi snd_seq_midi_event joydev snd_rawmidi pcmcia snd_seq psmouse snd_seq_device snd_timer serio_raw yenta_socket snd pcmcia_rsrc pcmcia_core lpc_ich soundcore i915 shpchp drm_kms_helper wmi drm i2c_algo_bit video mac_hid parport_pc ppdev lp parport hid_logitech ff_memless usbhid hid firewire_ohci 8139too 8139cp firewire_core mii crc_itu_t
[   21.958883] Modules linked in: cfg80211 rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm rt5370sta(OF) snd_page_alloc snd_seq_midi snd_seq_midi_event joydev snd_rawmidi pcmcia snd_seq psmouse snd_seq_device snd_timer serio_raw yenta_socket snd pcmcia_rsrc pcmcia_core lpc_ich soundcore i915 shpchp drm_kms_helper wmi drm i2c_algo_bit video mac_hid parport_pc ppdev lp parport hid_logitech ff_memless usbhid hid firewire_ohci 8139too 8139cp firewire_core mii crc_itu_t
[   22.000261] Modules linked in: cfg80211 rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm rt5370sta(OF) snd_page_alloc snd_seq_midi snd_seq_midi_event joydev snd_rawmidi pcmcia snd_seq psmouse snd_seq_device snd_timer serio_raw yenta_socket snd pcmcia_rsrc pcmcia_core lpc_ich soundcore i915 shpchp drm_kms_helper wmi drm i2c_algo_bit video mac_hid parport_pc ppdev lp parport hid_logitech ff_memless usbhid hid firewire_ohci 8139too 8139cp firewire_core mii crc_itu_t
[   22.000901] Modules linked in: cfg80211 rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm rt5370sta(OF) snd_page_alloc snd_seq_midi snd_seq_midi_event joydev snd_rawmidi pcmcia snd_seq psmouse snd_seq_device snd_timer serio_raw yenta_socket snd pcmcia_rsrc pcmcia_core lpc_ich soundcore i915 shpchp drm_kms_helper wmi drm i2c_algo_bit video mac_hid parport_pc ppdev lp parport hid_logitech ff_memless usbhid hid firewire_ohci 8139too 8139cp firewire_core mii crc_itu_t
[   22.001465] Modules linked in: cfg80211 rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm rt5370sta(OF) snd_page_alloc snd_seq_midi snd_seq_midi_event joydev snd_rawmidi pcmcia snd_seq psmouse snd_seq_device snd_timer serio_raw yenta_socket snd pcmcia_rsrc pcmcia_core lpc_ich soundcore i915 shpchp drm_kms_helper wmi drm i2c_algo_bit video mac_hid parport_pc ppdev lp parport hid_logitech ff_memless usbhid hid firewire_ohci 8139too 8139cp firewire_core mii crc_itu_t
[   22.002028] Modules linked in: cfg80211 rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm rt5370sta(OF) snd_page_alloc snd_seq_midi snd_seq_midi_event joydev snd_rawmidi pcmcia snd_seq psmouse snd_seq_device snd_timer serio_raw yenta_socket snd pcmcia_rsrc pcmcia_core lpc_ich soundcore i915 shpchp drm_kms_helper wmi drm i2c_algo_bit video mac_hid parport_pc ppdev lp parport hid_logitech ff_memless usbhid hid firewire_ohci 8139too 8139cp firewire_core mii crc_itu_t
[   22.002588] Modules linked in: cfg80211 rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm rt5370sta(OF) snd_page_alloc snd_seq_midi snd_seq_midi_event joydev snd_rawmidi pcmcia snd_seq psmouse snd_seq_device snd_timer serio_raw yenta_socket snd pcmcia_rsrc pcmcia_core lpc_ich soundcore i915 shpchp drm_kms_helper wmi drm i2c_algo_bit video mac_hid parport_pc ppdev lp parport hid_logitech ff_memless usbhid hid firewire_ohci 8139too 8139cp firewire_core mii crc_itu_t
[   22.048305] Modules linked in: cfg80211 rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm rt5370sta(OF) snd_page_alloc snd_seq_midi snd_seq_midi_event joydev snd_rawmidi pcmcia snd_seq psmouse snd_seq_device snd_timer serio_raw yenta_socket snd pcmcia_rsrc pcmcia_core lpc_ich soundcore i915 shpchp drm_kms_helper wmi drm i2c_algo_bit video mac_hid parport_pc ppdev lp parport hid_logitech ff_memless usbhid hid firewire_ohci 8139too 8139cp firewire_core mii crc_itu_t
[   22.048875] Modules linked in: cfg80211 rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm rt5370sta(OF) snd_page_alloc snd_seq_midi snd_seq_midi_event joydev snd_rawmidi pcmcia snd_seq psmouse snd_seq_device snd_timer serio_raw yenta_socket snd pcmcia_rsrc pcmcia_core lpc_ich soundcore i915 shpchp drm_kms_helper wmi drm i2c_algo_bit video mac_hid parport_pc ppdev lp parport hid_logitech ff_memless usbhid hid firewire_ohci 8139too 8139cp firewire_core mii crc_itu_t
[   22.049371] Modules linked in: cfg80211 rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm rt5370sta(OF) snd_page_alloc snd_seq_midi snd_seq_midi_event joydev snd_rawmidi pcmcia snd_seq psmouse snd_seq_device snd_timer serio_raw yenta_socket snd pcmcia_rsrc pcmcia_core lpc_ich soundcore i915 shpchp drm_kms_helper wmi drm i2c_algo_bit video mac_hid parport_pc ppdev lp parport hid_logitech ff_memless usbhid hid firewire_ohci 8139too 8139cp firewire_core mii crc_itu_t
[   22.049866] Modules linked in: cfg80211 rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm rt5370sta(OF) snd_page_alloc snd_seq_midi snd_seq_midi_event joydev snd_rawmidi pcmcia snd_seq psmouse snd_seq_device snd_timer serio_raw yenta_socket snd pcmcia_rsrc pcmcia_core lpc_ich soundcore i915 shpchp drm_kms_helper wmi drm i2c_algo_bit video mac_hid parport_pc ppdev lp parport hid_logitech ff_memless usbhid hid firewire_ohci 8139too 8139cp firewire_core mii crc_itu_t
[   22.050378] Modules linked in: cfg80211 rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm rt5370sta(OF) snd_page_alloc snd_seq_midi snd_seq_midi_event joydev snd_rawmidi pcmcia snd_seq psmouse snd_seq_device snd_timer serio_raw yenta_socket snd pcmcia_rsrc pcmcia_core lpc_ich soundcore i915 shpchp drm_kms_helper wmi drm i2c_algo_bit video mac_hid parport_pc ppdev lp parport hid_logitech ff_memless usbhid hid firewire_ohci 8139too 8139cp firewire_core mii crc_itu_t
[   22.493525] <==== rt28xx_init, Status=0
[   24.186369] <==== rt28xx_init, Status=0
[  124.592234] Modules linked in: cfg80211 rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm rt5370sta(OF) snd_page_alloc snd_seq_midi snd_seq_midi_event joydev snd_rawmidi pcmcia snd_seq psmouse snd_seq_device snd_timer serio_raw yenta_socket snd pcmcia_rsrc pcmcia_core lpc_ich soundcore i915 shpchp drm_kms_helper wmi drm i2c_algo_bit video mac_hid parport_pc ppdev lp parport hid_logitech ff_memless usbhid hid firewire_ohci 8139too 8139cp firewire_core mii crc_itu_t
[  124.592808] Modules linked in: cfg80211 rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm rt5370sta(OF) snd_page_alloc snd_seq_midi snd_seq_midi_event joydev snd_rawmidi pcmcia snd_seq psmouse snd_seq_device snd_timer serio_raw yenta_socket snd pcmcia_rsrc pcmcia_core lpc_ich soundcore i915 shpchp drm_kms_helper wmi drm i2c_algo_bit video mac_hid parport_pc ppdev lp parport hid_logitech ff_memless usbhid hid firewire_ohci 8139too 8139cp firewire_core mii crc_itu_t
[  124.593308] Modules linked in: cfg80211 rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm rt5370sta(OF) snd_page_alloc snd_seq_midi snd_seq_midi_event joydev snd_rawmidi pcmcia snd_seq psmouse snd_seq_device snd_timer serio_raw yenta_socket snd pcmcia_rsrc pcmcia_core lpc_ich soundcore i915 shpchp drm_kms_helper wmi drm i2c_algo_bit video mac_hid parport_pc ppdev lp parport hid_logitech ff_memless usbhid hid firewire_ohci 8139too 8139cp firewire_core mii crc_itu_t
[  124.593807] Modules linked in: cfg80211 rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm rt5370sta(OF) snd_page_alloc snd_seq_midi snd_seq_midi_event joydev snd_rawmidi pcmcia snd_seq psmouse snd_seq_device snd_timer serio_raw yenta_socket snd pcmcia_rsrc pcmcia_core lpc_ich soundcore i915 shpchp drm_kms_helper wmi drm i2c_algo_bit video mac_hid parport_pc ppdev lp parport hid_logitech ff_memless usbhid hid firewire_ohci 8139too 8139cp firewire_core mii crc_itu_t
[  124.594303] Modules linked in: cfg80211 rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm rt5370sta(OF) snd_page_alloc snd_seq_midi snd_seq_midi_event joydev snd_rawmidi pcmcia snd_seq psmouse snd_seq_device snd_timer serio_raw yenta_socket snd pcmcia_rsrc pcmcia_core lpc_ich soundcore i915 shpchp drm_kms_helper wmi drm i2c_algo_bit video mac_hid parport_pc ppdev lp parport hid_logitech ff_memless usbhid hid firewire_ohci 8139too 8139cp firewire_core mii crc_itu_t
[  124.644219] Modules linked in: cfg80211 rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm rt5370sta(OF) snd_page_alloc snd_seq_midi snd_seq_midi_event joydev snd_rawmidi pcmcia snd_seq psmouse snd_seq_device snd_timer serio_raw yenta_socket snd pcmcia_rsrc pcmcia_core lpc_ich soundcore i915 shpchp drm_kms_helper wmi drm i2c_algo_bit video mac_hid parport_pc ppdev lp parport hid_logitech ff_memless usbhid hid firewire_ohci 8139too 8139cp firewire_core mii crc_itu_t
[  124.644738] Modules linked in: cfg80211 rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm rt5370sta(OF) snd_page_alloc snd_seq_midi snd_seq_midi_event joydev snd_rawmidi pcmcia snd_seq psmouse snd_seq_device snd_timer serio_raw yenta_socket snd pcmcia_rsrc pcmcia_core lpc_ich soundcore i915 shpchp drm_kms_helper wmi drm i2c_algo_bit video mac_hid parport_pc ppdev lp parport hid_logitech ff_memless usbhid hid firewire_ohci 8139too 8139cp firewire_core mii crc_itu_t
[  124.645164] Modules linked in: cfg80211 rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm rt5370sta(OF) snd_page_alloc snd_seq_midi snd_seq_midi_event joydev snd_rawmidi pcmcia snd_seq psmouse snd_seq_device snd_timer serio_raw yenta_socket snd pcmcia_rsrc pcmcia_core lpc_ich soundcore i915 shpchp drm_kms_helper wmi drm i2c_algo_bit video mac_hid parport_pc ppdev lp parport hid_logitech ff_memless usbhid hid firewire_ohci 8139too 8139cp firewire_core mii crc_itu_t
[  124.645587] Modules linked in: cfg80211 rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm rt5370sta(OF) snd_page_alloc snd_seq_midi snd_seq_midi_event joydev snd_rawmidi pcmcia snd_seq psmouse snd_seq_device snd_timer serio_raw yenta_socket snd pcmcia_rsrc pcmcia_core lpc_ich soundcore i915 shpchp drm_kms_helper wmi drm i2c_algo_bit video mac_hid parport_pc ppdev lp parport hid_logitech ff_memless usbhid hid firewire_ohci 8139too 8139cp firewire_core mii crc_itu_t
[  124.646006] Modules linked in: cfg80211 rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm rt5370sta(OF) snd_page_alloc snd_seq_midi snd_seq_midi_event joydev snd_rawmidi pcmcia snd_seq psmouse snd_seq_device snd_timer serio_raw yenta_socket snd pcmcia_rsrc pcmcia_core lpc_ich soundcore i915 shpchp drm_kms_helper wmi drm i2c_algo_bit video mac_hid parport_pc ppdev lp parport hid_logitech ff_memless usbhid hid firewire_ohci 8139too 8139cp firewire_core mii crc_itu_t

########## wireless info END ############



```

---

### Post by praseodym on 2014-04-29
Tra a fixed channel and pure WPA2-AES encryption.

---

### Post by risva on 2014-04-29
I dont believe it, i just opened network connections, included m wifi SSID and password...
removed the ethernet cable and.... i'm through....on wifi.

Thanx a ton Praseodym, Chili555 and Varunendra !!

....there is no system tray icon for network connectivity in Lubuntu14.04, also it does not tell available wifi connections....could you you help please.

---

### Post by praseodym on 2014-04-29
Glad its working. For the icon, check this:

[http://www.webupd8.org/2014/04/fix-lubuntu-1404-network-manager.html](http://www.webupd8.org/2014/04/fix-lubuntu-1404-network-manager.html)

---

### Post by risva on 2014-04-29
Solved!!

---

### Post by varunendra on 2014-04-30
To mark the Thread as [SOLVED] so that it appears as its prefix in search results : [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Hope you'll enjoy Ubuntu and the forums. :)

---

### Post by risva on 2014-08-28
Hello all,

while the above had helped activate the wifi usb, recently im facing a problem with same wifi usb.

after the recent linux generic updates the wifi has stopped working. i tried following steps given at #12 above; but for every command typed, the reply was "it(add/build/install) already exists".

running the wifi script gave following output:
```

======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

john-Presario-2200-PR557PC-UUF 3.13.0-34-generic i686,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Celeron(R) M processor         1400MHz
Memory : 715 MB
Uptime : 10:22:36 up 55 min,  2 users,  load average: 0.40, 0.51, 0.58


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [10ec:8139] (rev 10)
    Subsystem: Hewlett-Packard Company Device [103c:3084]
    Kernel driver in use: 8139too


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 002: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

wmi                    18673  0 


module parameters ~~~~~~~~~~~~~~~~~~

wmi           (2): 


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
===============================o=======o=========o===========o=========o===========o==============o===========
 Interface & ID                | Type  | Driver  | State     | Default | Speed     | Support      | HW Addr   
===============================o=======o=========o===========o=========o===========o==============o===========
 eth0  [Ethernet connection 1] | Wired | 8139too | connected | yes     | 100 Mb/s  |              | <MAC eth0>

    Address:         192.168.1.101
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             192.168.1.1
-------------------------------+-------+---------+-----------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

no-auto-default=<MAC eth0>,

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~

DIAT_GUEST           : ssid=DIAT_GUEST | ipv6=auto | ipv4=auto 
Wi-Fi connection 1   : ssid=JOHN-PC_Network | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.289/0.296/0.303/0.007 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.064/0.065/0.066/0.001 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_IN")


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

           - 


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~



blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist rt2800usb
blacklist rt2870sta
blacklist rt2x00
blacklist rt2800usb

[/etc/modprobe.d/blaclist.conf]
blacklist rt2800usb
blacklist rt2870sta 

[/etc/modprobe.d/libpisock9.conf]
blacklist visor


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[wmi]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8139 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Not Default

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en

[/etc/pm/config.d/config]
SUSPEND_MODULES="RT2800USB"


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-34-generic root=UUID=7d5b7dd7-0daf-451c-adbf-764c73286e22 ro forcepae quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[   19.740658] Modules linked in: snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   19.741065] Modules linked in: snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   19.741471] Modules linked in: snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   19.741875] Modules linked in: snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   19.804207] Modules linked in: snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   19.804834] Modules linked in: snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   19.805385] Modules linked in: snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   19.805935] Modules linked in: snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   19.806482] Modules linked in: snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   19.856193] Modules linked in: snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   19.856744] Modules linked in: snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   19.857229] Modules linked in: snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   19.857714] Modules linked in: snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   19.858196] Modules linked in: snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   21.458169] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   23.604185] Modules linked in: rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   23.604799] Modules linked in: rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   23.605350] Modules linked in: rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   23.605900] Modules linked in: rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   23.606446] Modules linked in: rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   23.684189] Modules linked in: rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   23.684734] Modules linked in: rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   23.685221] Modules linked in: rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   23.685705] Modules linked in: rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   23.686185] Modules linked in: rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   23.752303] Modules linked in: rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   23.752920] Modules linked in: rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   23.753472] Modules linked in: rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   23.754021] Modules linked in: rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   23.754568] Modules linked in: rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   23.832180] Modules linked in: rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   23.832726] Modules linked in: rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   23.833212] Modules linked in: rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   23.833695] Modules linked in: rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   23.834174] Modules linked in: rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   46.104182] Modules linked in: pci_stub vboxpci(OF) vboxnetadp(OF) vboxnetflt(OF) vboxdrv(OF) rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   46.104742] Modules linked in: pci_stub vboxpci(OF) vboxnetadp(OF) vboxnetflt(OF) vboxdrv(OF) rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   46.105242] Modules linked in: pci_stub vboxpci(OF) vboxnetadp(OF) vboxnetflt(OF) vboxdrv(OF) rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   46.105740] Modules linked in: pci_stub vboxpci(OF) vboxnetadp(OF) vboxnetflt(OF) vboxdrv(OF) rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   46.106235] Modules linked in: pci_stub vboxpci(OF) vboxnetadp(OF) vboxnetflt(OF) vboxdrv(OF) rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   46.164224] Modules linked in: pci_stub vboxpci(OF) vboxnetadp(OF) vboxnetflt(OF) vboxdrv(OF) rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   46.164716] Modules linked in: pci_stub vboxpci(OF) vboxnetadp(OF) vboxnetflt(OF) vboxdrv(OF) rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   46.165143] Modules linked in: pci_stub vboxpci(OF) vboxnetadp(OF) vboxnetflt(OF) vboxdrv(OF) rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   46.165569] Modules linked in: pci_stub vboxpci(OF) vboxnetadp(OF) vboxnetflt(OF) vboxdrv(OF) rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   46.165991] Modules linked in: pci_stub vboxpci(OF) vboxnetadp(OF) vboxnetflt(OF) vboxdrv(OF) rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii

    ======== Done ========


```

please help me re-activate the wifi usb.

---

### Post by varunendra on 2014-08-29
@risva,

Just replied in your own thread : [http://ubuntuforums.org/showthread.php?t=2241068](http://ubuntuforums.org/showthread.php?t=2241068)

Please continue the conversation there. I'm sure both dr. chili555 and praseodym would be curious to follow its progress and would post in it wherever required.

---

### Post by risva on 2014-08-29
Thanks Varunendra and all other forum friends,

the query at #20 has been resolved. for solution refer:

[http://ubuntuforums.org/showthread.php?t=2241068](http://ubuntuforums.org/showthread.php?t=2241068)

thanks once again.

---

### Post by risva on 2014-08-29
Dear chili555,

you may change the status of the thread as solved please.

thanks a lot for instant and ever available help.

---

### Post by chili555 on 2014-08-29
Only the original poster may reach up to thread tools at the top of the thread and mark Solved. The searchers will appreciate it.

---

