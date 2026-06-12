---
title: "RT3290 wireless in Ubuntu 12.04 LTS"
date: 2014-07-30
forum: Networking &amp; Wireless
---

### Post by ryan4 on 2014-07-30
I have been trying to get my RT3290 wireless working by following the instructions here:
[http://askubuntu.com/questions/253632/how-do-i-get-a-ralink-rt3290-wireless-card-working](http://askubuntu.com/questions/253632/how-do-i-get-a-ralink-rt3290-wireless-card-working)

I have received error messages and am not sure what do do next. Here is the output of my terminal:

ryan@ryan-X75A:~/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508$ make
make -C tools
make[1]: Entering directory `/home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/tools'
/home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/tools/bin2h
cp -f os/linux/Makefile.6 /home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/Makefile
make -C /lib/modules/3.13.0-32-generic/build SUBDIRS=/home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-32-generic'
  CC [M]  /home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/crypt_md5.o
  CC [M]  /home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/crypt_aes.o
/home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/crypt_aes.c: In function ‘AES_Key_Wrap’:
/home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/crypt_aes.c:1466:6: warning: format ‘%d’ expects argument of type ‘int’, but argument 2 has type ‘long unsigned int’ [-Wformat]
/home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/crypt_aes.c: In function ‘AES_Key_Unwrap’:
/home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/crypt_aes.c:1561:6: warning: format ‘%d’ expects argument of type ‘int’, but argument 2 has type ‘long unsigned int’ [-Wformat]
  CC [M]  /home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/mlme.o
/home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/mlme.c: In function ‘MlmeResetRalinkCounters’:
/home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/mlme.c:528:3: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/mlme.c:528:3: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
  CC [M]  /home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_wep.o
  CC [M]  /home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/action.o
  CC [M]  /home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_data.o
  CC [M]  /home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/rtmp_init.o
  CC [M]  /home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/rtmp_init_inf.o
/home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/rtmp_init_inf.c: In function ‘rt28xx_init’:
/home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/rtmp_init_inf.c:162:3: warning: format ‘%x’ expects argument of type ‘unsigned int’, but argument 2 has type ‘ULONG’ [-Wformat]
/home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/rtmp_init_inf.c:178:10: warning: ISO C90 forbids mixed declarations and code [-Wdeclaration-after-statement]
  CC [M]  /home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_aes.o
  CC [M]  /home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_sync.o
  CC [M]  /home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/eeprom.o
  CC [M]  /home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_info.o
  CC [M]  /home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_wpa.o
/home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_wpa.c: In function ‘PeerPairMsg3Action’:
/home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_wpa.c:1032:13: warning: unused variable ‘Cancelled’ [-Wunused-variable]
  CC [M]  /home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_radar.o
  CC [M]  /home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/spectrum.o
/home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/spectrum.c: In function ‘PeerMeasureReportAction’:
/home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/spectrum.c:1972:3: warning: format ‘%d’ expects argument of type ‘int’, but argument 3 has type ‘long unsigned int’ [-Wformat]
  CC [M]  /home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/rt_channel.o
  CC [M]  /home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_profile.o
  CC [M]  /home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_asic.o
  CC [M]  /home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/ps.o
  CC [M]  /home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/uapsd.o
  CC [M]  /home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../rate_ctrl/ra_ctrl.o
  CC [M]  /home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../rate_ctrl/alg_legacy.o
  CC [M]  /home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../rate_ctrl/alg_ags.o
  CC [M]  /home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_profile.o
/home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_profile.c: In function ‘STA_MonPktSend’:
/home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_profile.c:409:9: warning: format ‘%d’ expects argument of type ‘int’, but argument 3 has type ‘long unsigned int’ [-Wformat]
  CC [M]  /home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../chips/rtmp_chip.o
  CC [M]  /home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/assoc.o
  CC [M]  /home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/auth.o
  CC [M]  /home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/sync.o
  CC [M]  /home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/sanity.o
  CC [M]  /home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/rtmp_data.o
/home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/rtmp_data.c: In function ‘STAHandleRxDataFrame’:
/home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/rtmp_data.c:283:17: warning: unused variable ‘pFmeCtrl’ [-Wunused-variable]
/home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/rtmp_data.c:282:8: warning: unused variable ‘OldPwrMgmt’ [-Wunused-variable]
/home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/rtmp_data.c: In function ‘STAHandleRxMgmtFrame’:
/home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/rtmp_data.c:766:5: warning: ISO C90 forbids mixed declarations and code [-Wdeclaration-after-statement]
  CC [M]  /home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/connect.o
  CC [M]  /home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/wpa.o
  CC [M]  /home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/sta_cfg.o
/home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/sta_cfg.c: In function ‘RTMPQueryInformation’:
/home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/sta_cfg.c:3956:4: warning: format ‘%d’ expects argument of type ‘int’, but argument 2 has type ‘long unsigned int’ [-Wformat]
/home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/sta_cfg.c: In function ‘RtmpIoctl_rt_private_get_statistics’:
/home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/sta_cfg.c:7220:1: warning: format ‘%x’ expects argument of type ‘unsigned int’, but argument 3 has type ‘EEPROM_NIC_CONFIG3_STRUC’ [-Wformat]
  CC [M]  /home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/rt_os_util.o
  CC [M]  /home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/sta_ioctl.o
  CC [M]  /home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_linux.o
/home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_linux.c: In function ‘duplicate_pkt’:
/home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_linux.c:508:3: warning: passing argument 1 of ‘memmove’ makes pointer from integer without a cast [enabled by default]
/usr/src/linux-headers-3.13.0-32-generic/arch/x86/include/asm/string_64.h:58:7: note: expected ‘void *’ but argument is of type ‘sk_buff_data_t’
/home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_linux.c:510:3: warning: passing argument 1 of ‘memmove’ makes pointer from integer without a cast [enabled by default]
/usr/src/linux-headers-3.13.0-32-generic/arch/x86/include/asm/string_64.h:58:7: note: expected ‘void *’ but argument is of type ‘sk_buff_data_t’
/home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_linux.c: In function ‘ClonePacket’:
/home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_linux.c:662:20: warning: assignment makes integer from pointer without a cast [enabled by default]
/home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOsPktInit’:
/home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_linux.c:681:2: warning: assignment makes integer from pointer without a cast [enabled by default]
/home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_linux.c: In function ‘wlan_802_11_to_802_3_packet’:
/home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_linux.c:708:15: warning: assignment makes integer from pointer without a cast [enabled by default]
/home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_linux.c: In function ‘__RtmpOSFSInfoChange’:
/home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_linux.c:1136:20: error: incompatible types when assigning to type ‘int’ from type ‘kuid_t’
/home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_linux.c:1137:20: error: incompatible types when assigning to type ‘int’ from type ‘kgid_t’
make[2]: *** [/home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_linux.o] Error 1
make[1]: *** [_module_/home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-32-generic'
make: *** [LINUX] Error 2
ryan@ryan-X75A:~/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508$ sudo make install
[sudo] password for ryan: 
make -C /home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux'
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
cp /home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/RT2860STA.dat /etc/Wireless/RT2860STA/.
install -d /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/
install -m 644 -c rt3290sta.ko /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/
install: cannot stat `rt3290sta.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/ryan/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux'
make: *** [install] Error 2
ryan@ryan-X75A:~/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508$ modprobe rt3290sta
FATAL: Module rt3290sta not found.
ryan@ryan-X75A:~/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508$

---

### Post by chili555 on 2014-07-30
That creaky old file is never, ever going to compile on a 3.13.0-xx kernel. Moreover, isn't your device covered in the built-in driver rt2800pci? If it isn't working as expected, we're much better off to troubleshoot it than we are to try to shoehorn an older driver to fit, which it never will. 

Please tell us some details about your wireless:```
lspci -nn | grep 0280
lsmod | grep rt2
iwconfig
rfkill list all
```Thanks.

---

### Post by ryan4 on 2014-07-30
Here is what I get:

ryan@ryan-X75A:~$ sudo lspci -nn | grep 0280
[sudo] password for ryan: 
02:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
ryan@ryan-X75A:~$ lsmod | grep rt2
ryan@ryan-X75A:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

ryan@ryan-X75A:~$ rfkill list all
ryan@ryan-X75A:~$

---

### Post by ryan4 on 2014-07-30
How do I use the built-in driver rt2800pci?

---

### Post by praseodym on 2014-07-30
Run
```

sudo modprobe -v rt2800pci
dmesg | grep rt2
```
The device is supported in kernel 3.13:

```
modinfo rt2800pci | egrep 'filen|3290'
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
alias:          pci:v0000[COLOR="#FF0000"]1814[/COLOR]d0000[COLOR="#FF0000"]3290[/COLOR]sv*sd*bc*sc*i*
```

---

### Post by ryan4 on 2014-07-30
I ran the above code and got:

ryan@ryan-X75A:~$ sudo modprobe -v rt2800pci
[sudo] password for ryan: 
insmod /lib/modules/3.13.0-32-generic/kernel/drivers/misc/eeprom/eeprom_93cx6.ko 
insmod /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko 
insmod /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko 
insmod /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko 
insmod /lib/modules/3.13.0-32-generic/kernel/lib/crc-ccitt.ko 
insmod /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko 
insmod /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rt2x00/rt2800mmio.ko 
insmod /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko 
ryan@ryan-X75A:~$ dmesg | grep rt2
[  443.766126] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3290, rev 0013 detected
[  443.774401] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 3290 detected
[  443.941502] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt3290.bin'
[  443.993471] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.37
[  446.902313] rt2800pci 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  446.902317] rt2800pci 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
ryan@ryan-X75A:~$ 

The wireless started working after I ran the first command. Will it continue to work or do I need to make changes to the startup?

---

### Post by ryan4 on 2014-07-30
Here is the the contents of my 'modules' file:

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
rt3290
rt3290sta
b43


In addition to adding rt2800pci, which do I need to remove?

---

### Post by ryan4 on 2014-07-30
I removed rt3290 and rt3290sta, and added rt2800pci, and it seems to be working.

---

### Post by chili555 on 2014-07-30
Awesome. Please use thread tools at the top to mark Solved.

---

### Post by praseodym on 2014-07-30
You should remove "b43", too, its for a Broadcom PCI card

---

