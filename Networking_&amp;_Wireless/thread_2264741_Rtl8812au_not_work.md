---
title: "Rtl8812au not work"
date: 2015-02-09
forum: Networking &amp; Wireless
---

### Post by emmo-30 on 2015-02-09
Hi, firstly excuse my bad english, i try to post on Ubuntu Fr forum but is not working.
2 week ago i buy [Wi-Fi USB adapter AC600 | WLA-2104]("https://www.sitecom.com/be-fr/wi-fi-usb-adapter-ac600/wla-2104/p/1687") and i tried it on my Ubuntu 12.04 LTS, 

Bon premièrement j'ai fait tout un tas de rechercher sur le chipset et je suis tomber sur le fameux chipset de Realtek le RTL8812AU qui me revenait souvent.

So, I follow [this thread posted by leo18]("http://ubuntuforums.org/showthread.php?t=2228244"), and it not d'like work... fallow 

firstly install dependecies: 

```
sudo apt-get install linux-headers-generic build-essential git

```
result of Uname

```
$ uname -r
3.13.0-45-generic
```

then &#305; Clean, Make and Make install, see result :

```
$ make clean
cd hal/OUTSRC/ ; rm -fr */*.mod.c */*.mod */*.o */.*.cmd */*.ko
cd hal/OUTSRC/ ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd hal/led ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd hal ; rm -fr */*/*.mod.c */*/*.mod */*/*.o */*/.*.cmd */*/*.ko
cd hal ; rm -fr */*.mod.c */*.mod */*.o */.*.cmd */*.ko
cd hal ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd core/efuse ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd core ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd os_dep/linux ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd os_dep ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
rm -fr Module.symvers ; rm -fr Module.markers ; rm -fr modules.order
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
```
```
$ make
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/3.13.0-45-generic/build M=/home/emremonun/Bureau/rtl8812au  modules
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-45-generic'
  CC [M]  /home/emremonun/Bureau/rtl8812au/core/rtw_cmd.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/core/rtw_security.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/core/rtw_debug.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/core/rtw_io.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/core/rtw_ioctl_query.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/core/rtw_ioctl_set.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/core/rtw_ieee80211.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/core/rtw_mlme.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/core/rtw_mlme_ext.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/core/rtw_wlan_util.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/core/rtw_vht.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/core/rtw_pwrctrl.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/core/rtw_rf.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/core/rtw_recv.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/core/rtw_sta_mgt.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/core/rtw_ap.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/core/rtw_xmit.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/core/rtw_p2p.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/core/rtw_tdls.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/core/rtw_br_ext.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/core/rtw_iol.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/core/rtw_sreset.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/core/efuse/rtw_efuse.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/os_dep/osdep_service.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/os_dep/linux/os_intfs.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/os_dep/linux/usb_intf.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/os_dep/linux/usb_ops_linux.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/os_dep/linux/ioctl_linux.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/os_dep/linux/xmit_linux.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/os_dep/linux/mlme_linux.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/os_dep/linux/recv_linux.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/os_dep/linux/ioctl_cfg80211.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/os_dep/linux/rtw_android.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/hal/hal_intf.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/hal/hal_com.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/hal/hal_com_phycfg.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/hal/hal_phy.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/hal/led/hal_usb_led.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/hal/HalPwrSeqCmd.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/hal/rtl8812a/Hal8812PwrSeq.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/hal/rtl8812a/Hal8821APwrSeq.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/hal/rtl8812a/rtl8812a_xmit.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/hal/rtl8812a/rtl8812a_sreset.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/hal/rtl8812a/rtl8812a_hal_init.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/hal/rtl8812a/rtl8812a_phycfg.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/hal/rtl8812a/rtl8812a_rf6052.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/hal/rtl8812a/rtl8812a_dm.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/hal/rtl8812a/rtl8812a_rxdesc.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/hal/rtl8812a/rtl8812a_cmd.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/hal/rtl8812a/usb/usb_halinit.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/hal/rtl8812a/usb/rtl8812au_led.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/hal/rtl8812a/usb/rtl8812au_xmit.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/hal/rtl8812a/usb/rtl8812au_recv.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/hal/rtl8812a/usb/usb_ops_linux.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/hal/rtl8812a/rtl8812a_mp.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/hal/OUTSRC/odm_debug.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/hal/OUTSRC/odm_interface.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/hal/OUTSRC/odm_HWConfig.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/hal/OUTSRC/odm.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/hal/OUTSRC/HalPhyRf.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/hal/OUTSRC/rtl8812a/HalHWImg8812A_FW.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/hal/OUTSRC/rtl8812a/HalHWImg8812A_MAC.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/hal/OUTSRC/rtl8812a/HalHWImg8812A_BB.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/hal/OUTSRC/rtl8812a/HalHWImg8812A_RF.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/hal/OUTSRC/rtl8812a/HalHWImg8812A_TestChip_FW.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/hal/OUTSRC/rtl8812a/HalHWImg8812A_TestChip_MAC.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/hal/OUTSRC/rtl8812a/HalHWImg8812A_TestChip_BB.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/hal/OUTSRC/rtl8812a/HalHWImg8812A_TestChip_RF.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/hal/OUTSRC/rtl8812a/HalPhyRf_8812A.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/hal/OUTSRC/rtl8812a/odm_RegConfig8812A.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/hal/OUTSRC/rtl8821a/HalHWImg8821A_FW.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/hal/OUTSRC/rtl8821a/HalHWImg8821A_MAC.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/hal/OUTSRC/rtl8821a/HalHWImg8821A_BB.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/hal/OUTSRC/rtl8821a/HalHWImg8821A_RF.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/hal/OUTSRC/rtl8821a/HalHWImg8821A_TestChip_MAC.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/hal/OUTSRC/rtl8821a/HalHWImg8821A_TestChip_BB.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/hal/OUTSRC/rtl8821a/HalHWImg8821A_TestChip_RF.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/hal/OUTSRC/rtl8821a/HalPhyRf_8821A.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/hal/OUTSRC/rtl8821a/odm_RegConfig8821A.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/core/rtw_mp.o
  CC [M]  /home/emremonun/Bureau/rtl8812au/core/rtw_mp_ioctl.o
  LD [M]  /home/emremonun/Bureau/rtl8812au/8812au.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/emremonun/Bureau/rtl8812au/8812au.mod.o
  LD [M]  /home/emremonun/Bureau/rtl8812au/8812au.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-45-generic'
```

```
$ make install 
install -p -m 644 8812au.ko  /lib/modules/3.13.0-45-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 3.13.0-45-generic
```
and finally, 
```
$ sudo modprobe 8812au
$ lsmod
Module                  Size  Used by
8812au               1010131  0 
ctr                    13025  0 
ccm                    17596  0 
rfcomm                 59026  0 
bnep                   19107  2 
bluetooth             356727  10 rfcomm,bnep
arc4                   12509  0 
rt73usb                31360  0 
crc_itu_t              12627  1 rt73usb
nouveau               992130  1 
rt2x00usb              20161  1 rt73usb
rt2x00lib              49566  2 rt73usb,rt2x00usb
snd_intel8x0           37556  0 
snd_ac97_codec        110336  1 snd_intel8x0
mac80211              564463  2 rt2x00usb,rt2x00lib
ac97_bus               12642  1 snd_ac97_codec
ttm                    77707  1 nouveau
snd_pcm                90501  2 snd_intel8x0,snd_ac97_codec
drm_kms_helper         49282  1 nouveau
snd_seq_midi           13132  0 
snd_rawmidi            25198  1 snd_seq_midi
drm                   249595  3 nouveau,ttm,drm_kms_helper
cfg80211              423921  2 rt2x00lib,mac80211
gpio_ich               13278  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                55716  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28971  2 snd_pcm,snd_seq
ppdev                  17423  0 
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
i2c_algo_bit           13316  1 nouveau
hid_generic            12492  0 
mxm_wmi                12893  1 nouveau
video                  19330  1 nouveau
psmouse                97606  0 
snd                    61383  8 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi                    18827  2 nouveau,mxm_wmi
serio_raw              13230  0 
soundcore              12600  1 snd
snd_page_alloc         18398  2 snd_intel8x0,snd_pcm
parport_pc             32114  1 
lpc_ich                16987  0 
shpchp                 32265  0 
mac_hid                13077  0 
lp                     13359  0 
parport                40945  3 ppdev,parport_pc,lp
e100                   36323  0 
mii                    13693  1 e100
usbhid                 47442  0 
hid                    92101  2 hid_generic,usbhid
floppy                 60183  0 
```
but when i inspect 
```
$ iwconfig 
lo        no wireless extensions.


eth0      no wireless extensions.
```
Rien, Niet, NADA... :(
[B]But...
[/B]```
$ lsusb
**Bus 002 Device 003: ID 0df6:007a Sitecom Europe B.V.**
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

So, I have an hypothese, My interface id is  **[COLOR=#ff0000]ID 0df6:007a[/COLOR] Sitecom Europe B.V.**
if i convert for infomod style, is equals to **usb:v0df6p007a*dc*dsc*dp*ic*isc*ip*in*** 

```
$ modinfo 8812au 
filename:       /lib/modules/3.13.0-45-generic/kernel/drivers/net/wireless/8812au.ko
version:        v4.2.2_7502.20130517
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     3424792CB6F8055CE7AE336
[I]alias:          usb:v2019pAB32d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p9052d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3314d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392pA812d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392pA811d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8822d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp0821d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp0811d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2357p0101d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v20F4p805Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3316d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3315d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p8812d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB30d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p0100d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13B1p003Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1058p0632d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3313d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0586p3426d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0022d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p17D2d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0409p0408d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0789p016Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp0952d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0074d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392pA822d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p330Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp1106d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp881Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp881Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp881Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8812d*dc*dsc*dp*ic*isc*ip*in*[/I]
depends:        
vermagic:       3.13.0-45-generic SMP mod_unload modversions 686 
parm:           rtw_ips_mode:The default IPS mode (int)
parm:           rtw_regulatory_id:int
parm:           ifname:The default name to allocate for first interface (charp)
parm:           if2name:The default name to allocate for second interface (charp)
parm:           rtw_initmac:charp
parm:           rtw_channel_plan:int
parm:           rtw_chip_version:int
parm:           rtw_rfintfs:int
parm:           rtw_lbkmode:int
parm:           rtw_network_mode:int
parm:           rtw_channel:int
parm:           rtw_mp_mode:int
parm:           rtw_wmm_enable:int
parm:           rtw_vrtl_carrier_sense:int
parm:           rtw_vcs_type:int
parm:           rtw_busy_thresh:int
parm:           rtw_ht_enable:int
parm:           rtw_bw_mode:int
parm:           rtw_ampdu_enable:int
parm:           rtw_rx_stbc:int
parm:           rtw_ampdu_amsdu:int
parm:           rtw_vht_enable:int
parm:           rtw_lowrate_two_xmit:int
parm:           rtw_rf_config:int
parm:           rtw_power_mgnt:int
parm:           rtw_smart_ps:int
parm:           rtw_low_power:int
parm:           rtw_wifi_spec:int
parm:           rtw_antdiv_cfg:int
parm:           rtw_antdiv_type:int
parm:           rtw_enusbss:int
parm:           rtw_hwpdn_mode:int
parm:           rtw_hwpwrp_detect:int
parm:           rtw_hw_wps_pbc:int
parm:           rtw_max_roaming_times:The max roaming times to try (uint)
parm:           rtw_mc2u_disable:int
parm:           rtw_80211d:Enable 802.11d mechanism (int)
parm:           rtw_notch_filter:0:Disable, 1:Enable, 2:Enable only for P2P (uint)

```
But i can't find it in infomod 8812au 
i just see **alias:          usb:v0DF6p0074d*dc*dsc*dp*ic*isc*ip*in* **but produce id is not god...:(

i fund [this one]("https://wikidevi.com/wiki/Sitecom_WLA-3100") he descry same id but code name WLA-3100 is not same of mine, is WLA-2104.
Not: 
my Ubuntu work No Gui mode so i not have network-manager,
my network interface work correctly on my macbook,
and i try my ubuntu with another usb adapter work perfectly:
```
[FONT=Andale Mono]$ lsusb[/FONT]
[FONT=Andale Mono]Bus 001 Device 003: ID 0df6:007a Sitecom Europe B.V. [/FONT]
**[FONT=Andale Mono]Bus 002 Device 004: ID 14b2:3c22 Ralink Technology, Corp. Conceptronic C54RU 802.11bg Wireless Adapter [Ralink RT73][/FONT]**
[FONT=Andale Mono]Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]
[FONT=Andale Mono]Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[/FONT]
[FONT=Andale Mono]$ iwconfig[/FONT]
[B][FONT=Andale Mono]wlan0     IEEE 802.11bg  ESSID: off/any  [/FONT]
[FONT=Andale Mono]          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   [/FONT]
[FONT=Andale Mono]          Retry  long limit:7   RTS thr:off   Fragment thr:off[/FONT]
[FONT=Andale Mono]          Power Management:on[/FONT][/B]

[FONT=Andale Mono]lo        no wireless extensions.[/FONT]
[FONT=Andale Mono]
[/FONT]
[FONT=Andale Mono]eth0      no wireless extensions.[/FONT]
```
[COLOR=#29F914][FONT=Andale Mono]

[/FONT][/COLOR][FONT=Andale Mono]Edit:
[/FONT]I'm sorry i forget my report:
```


########## wireless info START ##########


Report from: 10 Feb 2015 08:24 CET +0100


Booted last: 09 Feb 2015 17:35 CET +0100


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:    12.04
Codename:    precise


##### kernel ############################


Linux 3.13.0-45-generic #74~precise1-Ubuntu SMP Thu Jan 15 20:22:28 UTC 2015 i686 i686 i386 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu (from ~/.dmrc)


##### lspci #############################


02:08.0 Ethernet controller [0200]: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller [8086:2449] (rev 03)
    Subsystem: Compaq Computer Corporation EtherExpress PRO/100 VM [0e11:0012]
    Kernel driver in use: e100


##### lsusb #############################


Bus 001 Device 002: ID 0df6:007a Sitecom Europe B.V. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


##### rfkill ############################


##### lsmod #############################


mxm_wmi                12893  1 nouveau
wmi                    18827  2 nouveau,mxm_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


auto eth0
iface eth0 inet static
    address 192.168.1.254
    netmask 255.255.255.0
    gateway 192.168.1.1


up route del default


auto wlan0
iface wlan0 inet dhcp
    wpa-conf /etc/wpa_supplicant.conf


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.254  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::208:2ff:fe50:cac3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:64 errors:0 dropped:0 overruns:0 frame:0
          TX packets:83 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7861 (7.8 KB)  TX bytes:13959 (13.9 KB)


##### iwconfig ##########################


lo        no wireless extensions.


eth0      no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0


##### resolv.conf #######################


##### nm-tool ###########################


** (process:1181): WARNING **: Could not initialize NMClient /org/freedesktop/NetworkManager: The name org.freedesktop.NetworkManager was not provided by any .service files


** (process:1181): WARNING **: error: could not connect to NetworkManager


NetworkManager Tool


State: unknown


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile
dns=dnsmasq


no-auto-default=<MAC 'eth0' [IF]>,


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/MacBook Pro de Emre]] (600 root)
[connection] id=MacBook Pro de Emre | type=802-11-wireless
[802-11-wireless] ssid=MacBook Pro de Emre | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


'iw' is not installed (package "iw").


##### iwlist channels ###################


lo        no frequency information.


eth0      no frequency information.


##### iwlist scan #######################


lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


##### module infos ######################


##### module parameters #################


##### /etc/modules ######################


lp


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


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1e.0/0000:02:08.0 (e100)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x14b2:0x3c22 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[   89.952997] intel_rng: don't want to disable this in firmware setup, and if


########## wireless info END ############

```
thanks for your help.

---

### Post by emmo-30 on 2015-02-11
Up please I need some help... Thank you

---

### Post by chili555 on 2015-02-11
> So, I have an hypothese, My interface id is ID [COLOR="#FF0000"]**0df6:007a**[/COLOR] Sitecom Europe B.V.You are quite correct; the device identification 0df6:007a is the key to everything. If it is not listed in the aliases for 8812au, then 8812au is not the correct driver for your device. 

I found two references to your device on the internet, aside from this very thread. This one: [https://debianforum.de/forum/viewtopic.php?f=30&t=152695](https://debianforum.de/forum/viewtopic.php?f=30&t=152695) and this: [http://forum.ubuntu-it.org/viewtopic.php?f=9&t=588244&p=4681722](http://forum.ubuntu-it.org/viewtopic.php?f=9&t=588244&p=4681722)

Both of them suggest that the only known way to get this device working is ndiswrapper. Here on this forum, we believe ndiswrapper is the same as headache, pain and torture. I think you have two options. You and I can stumble through ndiswrapper and see if we maybe or maybe don't get the device working or you can return it to the place you bought it and buy a fully supported USB wireless that works the moment you plug it in.

Please tell me which you'd like to do.

---

### Post by emmo-30 on 2015-02-11
[COLOR=#000000]Re: Ok i finally resolve driver problem with ndiswrapper.first, i go to look real driver name in ".inf" file of windows installer
And i fund :
```
%Sitecom_007A.DeviceDesc%             = RTL8811au.ndi, USB\VID_0DF6&PID_007A
```
But i fund no driver for RTL8811au ... :mad: all google point on Rtl8812au... but is not correct.but i don't like ndiswrapper method because is not native...so i install
```
$ sudo apt-get install [FONT=Andale Mono]ndiswrapper-utils-1.9
[/FONT]$ sudo ndiswrapper -i netrtwlanu.inf
```

AND :
```
[FONT=Andale Mono]$ ndiswrapper -l
netrtwlanu_xp : driver installed[/FONT]
[FONT=Andale Mono]device (0DF6:007A) present[/FONT]
```
Bingooooooo
then i create the module and i mount this module on boot and reboot with
```
$ sudo ndiswrapper -m
$ echo ndiswrapper|sudo tee -a /etc/modules
$ sudo reboot
```

And i see my usb adaptater
```
[FONT=Andale Mono]$ iwconfig 
lo        no wireless extensions.[/FONT]
[FONT=Andale Mono]
[/FONT]
[FONT=Andale Mono]eth0      no wireless extensions.[/FONT]
[FONT=Andale Mono]
[/FONT]
[FONT=Andale Mono]wlan1     IEEE 802.11g  ESSID:off/any  [/FONT]
[FONT=Andale Mono]          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   [/FONT]
[FONT=Andale Mono]          Bit Rate:39 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  [/FONT]
[FONT=Andale Mono]          RTS thr:off   Fragment thr:off[/FONT]
[FONT=Andale Mono]          Power Management:off[/FONT]
[FONT=Andale Mono]          Link Quality:0  Signal level:0  Noise level:0[/FONT]
[FONT=Andale Mono]          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0[/FONT]
[FONT=Andale Mono]          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/FONT]
```
and i can scan 
```
[FONT=Andale Mono]$ iwlist wlan1 scan[/FONT]
```[/COLOR]```
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]wlan1     Scan completed :[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]          Cell 01 - Address: 00:23:08:59:C3:A3[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    ESSID:"RIBIERO"[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Protocol:IEEE 802.11g[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Mode:Master[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Frequency:2.442 GHz (Channel 7)[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Quality:1/100  Signal level:-95 dBm  Noise level:-96 dBm[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Encryption key:on[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                              6 Mb/s; 9 Mb/s; 12 Mb/s[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Extra:bcn_int=100[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Extra:atim=0[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 00075249424945524F[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 010582848B962C[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 030107[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 050C000100000000000000000000[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 2A0100[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 32080C1218243048606C[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]          Cell 02 - Address: 68:15:90:12:7E:04[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    ESSID:"WiFi-2.4-7dfe"[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Protocol:IEEE 802.11g[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Mode:Master[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Frequency:2.437 GHz (Channel 6)[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Quality:51/100  Signal level:-63 dBm  Noise level:-96 dBm[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Encryption key:on[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                              24 Mb/s; 36 Mb/s; 54 Mb/s[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Extra:bcn_int=100[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Extra:atim=0[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 000D576946692D322E342D37646665[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 010882848B962430486C[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 030106[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 050400010000[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 2A0100[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 2F0100[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: IEEE 802.11i/WPA2 Version 1[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                        Group Cipher : TKIP[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                        Pairwise Ciphers (2) : CCMP TKIP[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                        Authentication Suites (1) : PSK[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 32040C121860[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 2D1ABC181BFFFF000000000000000000000000000000000000000000[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 3D1606081500000000000000000000000000000000000000[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 7F080000000000000040[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: DD180050F204104A00011010440001021049000600372A000120[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: DD090010180201000C0000[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]          Cell 03 - Address: 22:0C:C8:16:A7:F7[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    ESSID:"VOO_HOMESPOT"[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Protocol:IEEE 802.11g[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Mode:Master[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Frequency:2.412 GHz (Channel 1)[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Quality:50/100  Signal level:-64 dBm  Noise level:-96 dBm[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Encryption key:off[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                              24 Mb/s; 36 Mb/s; 54 Mb/s[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Extra:bcn_int=100[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Extra:atim=0[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 000C564F4F5F484F4D4553504F54[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 010882848B962430486C[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 030101[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 050400010000[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 2A0100[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 2F0100[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 32040C121860[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 3D1601081100000000000000000000000000000000000000[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: DD090010180200F02C0000[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]          Cell 04 - Address: 20:0C:C8:16:A7:F6[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    ESSID:"VOO-198621"[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Protocol:IEEE 802.11g[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Mode:Master[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Frequency:2.412 GHz (Channel 1)[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Quality:50/100  Signal level:-64 dBm  Noise level:-96 dBm[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Encryption key:on[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                              24 Mb/s; 36 Mb/s; 54 Mb/s[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Extra:bcn_int=100[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Extra:atim=0[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 000A564F4F2D313938363231[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 010882848B962430486C[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 030101[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 050400010000[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 2A0100[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 2F0100[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: IEEE 802.11i/WPA2 Version 1[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                        Group Cipher : TKIP[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                        Pairwise Ciphers (2) : CCMP TKIP[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                        Authentication Suites (1) : PSK[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 32040C121860[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 3D1601081100000000000000000000000000000000000000[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: DD180050F204104A00011010440001021049000600372A000120[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: DD090010180200F02C0000[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: WPA Version 1[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                        Group Cipher : TKIP[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                        Pairwise Ciphers (2) : CCMP TKIP[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                        Authentication Suites (1) : PSK[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]          Cell 05 - Address: 12:0D:7F:77:BB:3A[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    ESSID:"VOO_HOMESPOT"[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Protocol:IEEE 802.11g[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Mode:Master[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Frequency:2.412 GHz (Channel 1)[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Quality:50/100  Signal level:-64 dBm  Noise level:-96 dBm[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Encryption key:off[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                              24 Mb/s; 36 Mb/s; 54 Mb/s[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Extra:bcn_int=100[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Extra:atim=0[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 000C564F4F5F484F4D4553504F54[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 010882848B962430486C[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 030101[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 050400010000[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 2A0104[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 2F0104[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 32040C121860[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 3D1601081100000000000000000000000000000000000000[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: DD090010180200F02C0000[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]          Cell 06 - Address: 12:0D:7F:77:BB:3B[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    ESSID:"\x00"[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Protocol:IEEE 802.11g[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Mode:Master[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Frequency:2.412 GHz (Channel 1)[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Quality:50/100  Signal level:-64 dBm  Noise level:-96 dBm[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Encryption key:on[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                              24 Mb/s; 36 Mb/s; 54 Mb/s[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Extra:bcn_int=100[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Extra:atim=0[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 00110000000000000000000000000000000000[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 010882848B962430486C[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 030101[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 050400010000[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 2A0104[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 2F0104[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: IEEE 802.11i/WPA2 Version 1[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                        Group Cipher : TKIP[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                        Pairwise Ciphers (2) : CCMP TKIP[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                        Authentication Suites (1) : 802.1x[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 32040C121860[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 3D1601081100000000000000000000000000000000000000[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: DD090010180200F02C0000[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]          Cell 07 - Address: 10:0D:7F:77:BB:39[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    ESSID:"VOO-085667"[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Protocol:IEEE 802.11g[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Mode:Master[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Frequency:2.412 GHz (Channel 1)[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Quality:48/100  Signal level:-65 dBm  Noise level:-96 dBm[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Encryption key:on[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                              24 Mb/s; 36 Mb/s; 54 Mb/s[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Extra:bcn_int=100[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Extra:atim=0[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 000A564F4F2D303835363637[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 010882848B962430486C[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 030101[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 050400010000[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 2A0104[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 2F0104[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: IEEE 802.11i/WPA2 Version 1[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                        Group Cipher : TKIP[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                        Pairwise Ciphers (2) : CCMP TKIP[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                        Authentication Suites (1) : PSK[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 32040C121860[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 3D1601081500000000000000000000000000000000000000[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: DD180050F204104A00011010440001021049000600372A000120[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: DD090010180204F02C0000[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: WPA Version 1[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                        Group Cipher : TKIP[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                        Pairwise Ciphers (2) : CCMP TKIP[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                        Authentication Suites (1) : PSK[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]          Cell 08 - Address: 68:15:90:12:7E:05[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    ESSID:"WiFi-5.0-7dfe"[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Protocol:IEEE 802.11a[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Mode:Master[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Frequency:5.18 GHz[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Quality:48/100  Signal level:-65 dBm  Noise level:-96 dBm[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Encryption key:on[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                              36 Mb/s; 48 Mb/s; 54 Mb/s[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Extra:bcn_int=29[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Extra:atim=0[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 000D576946692D352E302D37646665[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 01088C129824B048606C[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 030124[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 050B0203000000000000000000[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 2D1A4F0017FFFFFFFFFEFFFFFFFF1F000001000000000018E6E71900[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 3D16240D0000000000000000000000000000000000000000[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: IEEE 802.11i/WPA2 Version 1[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                        Group Cipher : CCMP[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                        Pairwise Ciphers (1) : CCMP[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                        Authentication Suites (1) : PSK[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: DD0A002686010300DD000001[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: DD180050F204104A00011010440001021049000600372A000120[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]          Cell 09 - Address: 22:0C:C8:16:A7:F8[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    ESSID:"\x00"[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Protocol:IEEE 802.11g[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Mode:Master[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Frequency:2.412 GHz (Channel 1)[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Quality:39/100  Signal level:-71 dBm  Noise level:-96 dBm[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Encryption key:on[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                              24 Mb/s; 36 Mb/s; 54 Mb/s[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Extra:bcn_int=100[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Extra:atim=0[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 00110000000000000000000000000000000000[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 010882848B962430486C[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 030101[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 050400010000[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 2A0100[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 2F0100[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: IEEE 802.11i/WPA2 Version 1[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                        Group Cipher : TKIP[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                        Pairwise Ciphers (2) : CCMP TKIP[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                        Authentication Suites (1) : 802.1x[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 32040C121860[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 3D1601081100000000000000000000000000000000000000[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: DD090010180200F02C0000[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]          Cell 10 - Address: 00:18:F8:B8:E3:A2[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    ESSID:"R2-D2"[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Protocol:IEEE 802.11g[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Mode:Master[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Frequency:2.462 GHz (Channel 11)[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Quality:35/100  Signal level:-73 dBm  Noise level:-96 dBm[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Encryption key:on[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                              24 Mb/s; 36 Mb/s; 54 Mb/s[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Extra:bcn_int=100[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Extra:atim=0[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 000552322D4432[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 010882848B962430486C[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 03010B[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 050400010000[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 2A0104[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 2F0104[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: IEEE 802.11i/WPA2 Version 1[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                        Group Cipher : TKIP[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                        Pairwise Ciphers (2) : CCMP TKIP[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                        Authentication Suites (1) : PSK[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 32040C121860[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: DD09001018020017000000[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: WPA Version 1[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                        Group Cipher : TKIP[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                        Pairwise Ciphers (2) : CCMP TKIP[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                        Authentication Suites (1) : PSK[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]          Cell 11 - Address: 00:19:70:39:B4:EF[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    ESSID:"Bgm Consult 1"[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Protocol:IEEE 802.11g[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Mode:Master[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Frequency:2.412 GHz (Channel 1)[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Quality:35/100  Signal level:-73 dBm  Noise level:-96 dBm[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Encryption key:on[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                              9 Mb/s; 12 Mb/s; 18 Mb/s[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Extra:bcn_int=100[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Extra:atim=0[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 000D42676D20436F6E73756C742031[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 010882848B960C121824[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 030101[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 050400010000[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 0706424520010D14[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 2A0100[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: WPA Version 1[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                        Group Cipher : TKIP[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                        Pairwise Ciphers (1) : TKIP[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                        Authentication Suites (1) : PSK[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 32043048606C[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: DD0900037F01010000FF7F[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: DD0A00037F04010000000000[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]          Cell 12 - Address: 06:19:70:39:B4:EF[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    ESSID:"PROXIMUS_FON"[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Protocol:IEEE 802.11g[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Mode:Master[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Frequency:2.412 GHz (Channel 1)[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Quality:35/100  Signal level:-73 dBm  Noise level:-96 dBm[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Encryption key:off[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                              9 Mb/s; 12 Mb/s; 18 Mb/s[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Extra:bcn_int=100[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Extra:atim=0[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 000C50524F58494D55535F464F4E[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 010882848B968C129824[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 030101[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 050400010000[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 0706424520010D14[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 2A0100[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 3204B048606C[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: DD0900037F01010000FF7F[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: DD0A00037F04010000000000[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]          Cell 13 - Address: 6E:B0:CE:BD:1D:7B[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    ESSID:"\x00"[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Protocol:IEEE 802.11g[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Mode:Master[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Frequency:2.437 GHz (Channel 6)[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Quality:21/100  Signal level:-82 dBm  Noise level:-96 dBm[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Encryption key:on[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                              24 Mb/s; 36 Mb/s; 54 Mb/s[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Extra:bcn_int=100[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Extra:atim=0[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 00110000000000000000000000000000000000[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 010882848B962430486C[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 030106[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 050400010000[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 2A0104[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 2F0104[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: IEEE 802.11i/WPA2 Version 1[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                        Group Cipher : TKIP[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                        Pairwise Ciphers (2) : CCMP TKIP[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                        Authentication Suites (1) : 802.1x[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 32040C121860[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 3D1606081100000000000000000000000000000000000000[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: DD090010180200F02C0000[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]          Cell 14 - Address: 50:CC:F8:B9:D1:55[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    ESSID:"Android"[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Protocol:IEEE 802.11g[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Mode:Master[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Frequency:2.437 GHz (Channel 6)[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Quality:73/100  Signal level:-49 dBm  Noise level:-96 dBm[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Encryption key:on[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                              24 Mb/s; 36 Mb/s; 54 Mb/s[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Extra:bcn_int=100[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    Extra:atim=0[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 0007416E64726F6964[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 010882848B962430486C[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 030106[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 050400020000[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 2A0100[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 2F0100[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: IEEE 802.11i/WPA2 Version 1[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                        Group Cipher : CCMP[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                        Pairwise Ciphers (1) : CCMP[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                        Authentication Suites (1) : PSK[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 32040C121860[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 2D1A2C181BFF00000000000000000000000000000000000000000000[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: 3D1606080400000000000000000000000000000000000000[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: DD09001018020100040000[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: DD1E00904C332C181BFF00000000000000000000000000000000000000000000[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]                    IE: Unknown: DD1A00904C3406080400000000000000000000000000000000000000[/COLOR][/FONT][/COLOR]

```
but i can't associate on a wireless connection... so this is another problem... ;) thanks you [COLOR=#000000]chili555[/COLOR]

---

### Post by chili555 on 2015-02-11
> but i can't associate on a wireless connectionWhich access point are you trying to connect to? Maybe there is something we can do.

---

### Post by emmo-30 on 2015-02-11
> **chili555 said:**
> Which access point are you trying to connect to? Maybe there is something we can do.
&#304; try with VOO_HOMESPOT by editing my /etc/network/interfaces file:
```

[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]auto lo[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]iface lo inet loopback[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]
[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]auto eth0[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]iface eth0 inet static[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]        address 192.168.1.254[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]        netmask 255.255.255.0[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]        gateway 192.168.1.1[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]
[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]up route del default[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]
[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]auto wlan1[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]iface wlan1 inet dhcp[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]        wireless-essid VOO_HOMESPOT[/COLOR][/FONT][/COLOR]

```
[COLOR=#000000]```

[FONT=Andale Mono]$ iwconfig [/FONT]
```[/COLOR]```
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]lo        no wireless extensions.[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]
[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]eth0      no wireless extensions.[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]
[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]wlan1     IEEE 802.11g  ESSID:off/any  [/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   [/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]          Bit Rate:39 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  [/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]          RTS thr:off   Fragment thr:off[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]          Power Management:off[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]          Link Quality:0  Signal level:0  Noise level:0[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Andale Mono]          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/FONT][/COLOR]
```[COLOR=#000000]
not assosiate...
and manually
```
[FONT=Andale Mono]$ sudo iwconfig wlan1 essid VOO_HOMESPOT[/FONT]
```[/COLOR]```
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]emremonun@EVO:~$ sudo dhclient wlan1[/COLOR][/FONT][/COLOR]



```[COLOR=#000000]
when i send dhcp request ... i not have anything ... wait... wait... [/COLOR][COLOR=#000000]boring... nothing... Oo

edit: I send you my new wireless status...
```
[/COLOR]

########## wireless info START ##########


Report from: 12 Feb 2015 01:05 CET +0100


Booted last: 12 Feb 2015 00:37 CET +0100


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.5 LTS
Release:	12.04
Codename:	precise


##### kernel ############################


Linux 3.13.0-45-generic #74~precise1-Ubuntu SMP Thu Jan 15 20:22:28 UTC 2015 i686 i686 i386 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu (from ~/.dmrc)


##### lspci #############################


02:08.0 Ethernet controller [0200]: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller [8086:2449] (rev 03)
	Subsystem: Compaq Computer Corporation EtherExpress PRO/100 VM [0e11:0012]
	Kernel driver in use: e100


##### lsusb #############################


Bus 001 Device 002: ID 046d:c045 Logitech, Inc. Optical Mouse
Bus 001 Device 003: ID 0df6:007a Sitecom Europe B.V. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


##### rfkill ############################


##### lsmod #############################


mxm_wmi                12893  1 nouveau
wmi                    18827  2 nouveau,mxm_wmi
ndiswrapper           192977  0 


##### interfaces ########################


auto lo
iface lo inet loopback


auto eth0
iface eth0 inet static
	address 192.168.1.254
	netmask 255.255.255.0
	gateway 192.168.1.1


up route del default


auto wlan1
iface wlan1 inet dhcp
	wireless-essid VOO_HOMESPOT


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.254  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::208:2ff:fe50:cac3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:674 errors:0 dropped:0 overruns:0 frame:0
          TX packets:433 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:60937 (60.9 KB)  TX bytes:57199 (57.1 KB)


wlan1     Link encap:Ethernet  HWaddr <MAC 'wlan1' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan1:avahi Link encap:Ethernet  HWaddr <MAC 'wlan1' [IF]>  
          inet addr:169.254.10.37  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1


##### iwconfig ##########################


lo        no wireless extensions.


eth0      no wireless extensions.


wlan1     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:13 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         0.0.0.0         0.0.0.0         U     1003   0        0 wlan1
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 wlan1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0


##### resolv.conf #######################


##### nm-tool ###########################


** (process:1673): WARNING **: Could not initialize NMClient /org/freedesktop/NetworkManager: Rejected send message, 2 matched rules; type="method_call", sender=":1.13" (uid=1000 pid=1673 comm="nm-tool ") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination="org.freedesktop.NetworkManager" (uid=0 pid=1564 comm="NetworkManager ")


** (process:1673): WARNING **: error: could not connect to NetworkManager


NetworkManager Tool


State: unknown


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile
dns=dnsmasq


no-auto-default=<MAC 'eth0' [IF]>,


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/MacBook Pro de Emre]] (600 root)
[connection] id=MacBook Pro de Emre | type=802-11-wireless
[802-11-wireless] ssid=MacBook Pro de Emre | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


'iw' is not installed (package "iw").


##### iwlist channels ###################


lo        no frequency information.


eth0      no frequency information.


wlan1     14 channels in total; available frequencies :
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
          Current Frequency:2.412 GHz (Channel 1)


##### iwlist scan #######################


Channel occupancy:


      8   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:5.18 GHz


lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


wlan1     Scan completed :
          Cell 01 - Address: <MAC 'R2-D2' [AC1]>
                    ESSID:"R2-D2"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality:76/100  Signal level:-47 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Android' [AC2]>
                    ESSID:"Android"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:60/100  Signal level:-57 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'WiFi-2.4-7dfe' [AC3]>
                    ESSID:"WiFi-2.4-7dfe"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:51/100  Signal level:-63 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'VOO-085667' [AC4]>
                    ESSID:"VOO-085667"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:50/100  Signal level:-64 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC '' [AC5]>
                    ESSID:"\x00"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:50/100  Signal level:-64 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 06 - Address: <MAC 'VOO_HOMESPOT' [AC6]>
                    ESSID:"VOO_HOMESPOT"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:50/100  Signal level:-64 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 07 - Address: <MAC 'WiFi-5.0-7dfe' [AC7]>
                    ESSID:"WiFi-5.0-7dfe"
                    Protocol:IEEE 802.11a
                    Mode:Master
                    Frequency:5.18 GHz
                    Quality:48/100  Signal level:-65 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=48
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'VOO_HOMESPOT' [AC8]>
                    ESSID:"VOO_HOMESPOT"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:37/100  Signal level:-72 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 09 - Address: <MAC 'VOO-198621' [AC9]>
                    ESSID:"VOO-198621"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:35/100  Signal level:-73 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC '' [AC10]>
                    ESSID:"\x00"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:35/100  Signal level:-73 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 11 - Address: <MAC 'PROXIMUS_FON' [AC11]>
                    ESSID:"PROXIMUS_FON"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:35/100  Signal level:-73 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 12 - Address: <MAC 'PROXIMUS_AUTO_FON' [AC12]>
                    ESSID:"PROXIMUS_AUTO_FON"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:34/100  Signal level:-74 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x


##### module infos ######################


[ndiswrapper]
filename:       /lib/modules/3.13.0-45-generic/misc/ndiswrapper.ko
license:        GPL
version:        1.59
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     61EDC02F8B884C063E14A06
depends:        
vermagic:       3.13.0-45-generic SMP mod_unload modversions 686 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)


##### module parameters #################


grep: /sys/module/ndiswrapper/parameters/debug: Permission denied
grep: /sys/module/ndiswrapper/parameters/hangcheck_interval: Permission denied
grep: /sys/module/ndiswrapper/parameters/if_name: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_gid: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_uid: Permission denied
grep: /sys/module/ndiswrapper/parameters/utils_version: Permission denied
[ndiswrapper]


##### /etc/modules ######################


lp
ndiswrapper


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


[/etc/modprobe.d/ndiswrapper.conf]
alias wlan0 ndiswrapper


##### rc.local ##########################


ifconfig wlan1 up
iwconfig wlan1 rate 54M


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1e.0/0000:02:08.0 (e100)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x14b2:0x3c22 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x0df6:0x007a (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan1' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


##### dmesg #############################


[   95.752612] wlan0: ethernet device <MAC 'wlan1' [IF]> using NDIS driver: netrtwlanu_xp, version: 0x1, NDIS version: 0x500, vendor: 'Realtek RTL8812AU Wireless LAN USB NIC                                     ', 0DF6:007A.F.conf
[   95.752727] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[   96.328484] ndiswrapper: interface renamed to 'wlan1'
[   97.938188] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready


########## wireless info END ############


[COLOR=#000000]
```
[/COLOR]

---

### Post by chili555 on 2015-02-11
> when i send dhcp request ... i not have anything ... wait... wait... boring... nothing... Oo
We'd like to see more:```
cat /var/log/syslog | grep wlan | tail -n20
```No encryption?? Oh, my, that's very insecure; I don't recommend it.

Is Network Manager running here? ```
ps aux | grep etwork
```If you are using wireless, stop ethernet from trying to connect:```
auto lo
iface lo inet loopback


[COLOR="#FF0000"]#[/COLOR]auto eth0
iface eth0 inet static
        address 192.168.1.254
        netmask 255.255.255.0
        gateway 192.168.1.1


up route del default


auto wlan1
iface wlan1 inet dhcp
        wireless-essid VOO_HOMESPOT
```And then try again:```
sudo ifdown wlan1 && sudo ifup -v wlan1
```

---

### Post by emmo-30 on 2015-02-12
> cat /var/log/syslog | grep wlan | tail -n20

```
[FONT=Andale Mono]$ cat /var/log/syslog | grep wlan | tail -n20
[/FONT][COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]Feb 12 05:54:03 EVO dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port .. interval 8[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]Feb 12 05:54:10 EVO dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port .. interval 12[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]Feb 12 05:54:11 EVO dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port .. interval 12[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]Feb 12 05:54:22 EVO dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port .. interval 19[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]Feb 12 05:54:23 EVO dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port .. interval 13[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]Feb 12 05:54:36 EVO dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port .. interval 21[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]Feb 12 05:54:41 EVO dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port .. interval 9[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]Feb 12 05:54:50 EVO dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port .. interval 13[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]Feb 12 05:54:57 EVO dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port .. interval 17[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]Feb 12 05:55:03 EVO dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port .. interval 19[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]Feb 12 05:55:14 EVO dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port .. interval 14[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]Feb 12 05:55:22 EVO dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port .. interval 14[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]Feb 12 05:55:28 EVO dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port .. interval 21[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]Feb 12 05:55:36 EVO dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port .. interval 12[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]Feb 12 05:55:48 EVO dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port .. interval 21[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]Feb 12 05:55:49 EVO dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port .. interval 9[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]Feb 12 05:56:09 EVO dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port .. interval 8[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]Feb 12 05:56:16 EVO dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port .. interval 4[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]Feb 12 05:56:17 EVO dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port .. interval 14[/COLOR][/FONT][/COLOR]
[FONT=Andale Mono]Feb 12 05:56:31 EVO dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port .. interval 11[/FONT]
```
I have Broadcast dhcp repetition...

> ps aux | grep etwork
```
[FONT=Andale Mono]$ ps aux | grep etwork
[/FONT][COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]root      1564  0.0  0.6  24300  6256 ?        Ssl  00:40   0:00 NetworkManager[/COLOR][/FONT][/COLOR]
[FONT=Andale Mono]1000      2645  0.0  0.0   4396   796 pts/0    S+   05:57   0:00 grep --color=auto [/FONT][FONT=Andale Mono]etwork[/FONT]
```

> [COLOR=#000000]If you are using wireless, stop ethernet from trying to connect:[/COLOR]

```
[FONT=Andale Mono]$ sudo ifdown wlan1 && sudo ifup -v wlan1
[/FONT][COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]Configuring interface wlan1=wlan1 (inet)[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]run-parts --verbose /etc/network/if-pre-up.d[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]run-parts: executing /etc/network/if-pre-up.d/wireless-tools[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]run-parts: executing /etc/network/if-pre-up.d/wpasupplicant[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]
[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.wlan1.pid -lf /var/lib/dhcp/dhclient.wlan1.leases -1 wlan1[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]run-parts --verbose /etc/network/if-up.d[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]run-parts: executing /etc/network/if-up.d/000resolvconf[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]run-parts: executing /etc/network/if-up.d/avahi-autoipd[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]run-parts: executing /etc/network/if-up.d/avahi-daemon[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]run-parts: executing /etc/network/if-up.d/ntpdate[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]run-parts: executing /etc/network/if-up.d/openssh-server[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]ssh stop/waiting[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]ssh start/running, process 2784[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]run-parts: executing /etc/network/if-up.d/upstart[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]run-parts: executing /etc/network/if-up.d/wpasupplicant[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]emremonun@EVO:~$ iwconfig [/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]lo        no wireless extensions.[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]
[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]eth0      no wireless extensions.[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]
[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]wlan1     IEEE 802.11g  ESSID:off/any  [/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   [/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]          Bit Rate:39 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  [/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]          RTS thr:off   Fragment thr:off[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]          Power Management:off[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]          Link Quality:0  Signal level:0  Noise level:0[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]
[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]emremonun@EVO:~$ sudo iwconfig wlan1 essid VOO_HOMESPOT[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono][COLOR=#000000]emremonun@EVO:~$ sudo dhclient wlan1[/COLOR][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono]
[/FONT][/COLOR]

```
Nothing... :confused:

---

### Post by chili555 on 2015-02-12
I notice there are two access points named VOO_HOMESPOT. This one:> Cell 06 - Address: <MAC 'VOO_HOMESPOT' [AC6]>
                    ESSID:"VOO_HOMESPOT"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:50/100  Signal level:-64 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0And this one:> Cell 08 - Address: <MAC 'VOO_HOMESPOT' [AC8]>
                    ESSID:"VOO_HOMESPOT"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:37/100  Signal level:-72 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0I wonder if it would help to specify which we want to connect to. You can do so in /etc/network/interfaces like this:```
auto lo
iface lo inet loopback


#auto eth0
iface eth0 inet static
        address 192.168.1.254
        netmask 255.255.255.0
        gateway 192.168.1.1


up route del default


auto wlan1
iface wlan1 inet dhcp
        wireless-essid VOO_HOMESPOT
        wireless-ap 11:22:33:44:55:66
```Of course, substitute the MAC address of the stronger of the two. For privacy and security purposes, the wireless_script obscures all MAC addresses as you see. 

Then try again:```
sudo ifdown wlan1 && sudo ifup -v wlan1
```

---

### Post by emmo-30 on 2015-02-12
You Are the Big Boss Chili555 it's work perfectly :) thank you very much ;)

---

### Post by chili555 on 2015-02-12
Awesome! Glad it's working. Have fun!

---

### Post by beats2 on 2015-03-14
Hi.
Thanks for your information.
I have the same problem with 8812au driver in the Japanese forums here [https://forums.ubuntulinux.jp/viewtopic.php?id=17383](https://forums.ubuntulinux.jp/viewtopic.php?id=17383).

And I'm on the process of another solution, rebuilding the 8812au module.

The procedure I'm taking is adding a line in your case 
/home/emremonun/Bureau/rtl8812au/os_dep/linux/usb_intf.c like following, and rebuild it.
```
{USB_DEVICE(0x0DF6, 0x0074),.driver_info = RTL8812}, /* Sitecom - Edimax*/
{USB_DEVICE(0x2019, 0x007a),.driver_info = RTL8812}, /* Sitecom - Edimax*/    <-- added

```Now my Xubuntu is identifying the USB network adapter with Hotplug, though I still need some tweaks to get it work.[COLOR=#000000][FONT=Ubuntu Mono]

HTH[/FONT][/COLOR]

---

