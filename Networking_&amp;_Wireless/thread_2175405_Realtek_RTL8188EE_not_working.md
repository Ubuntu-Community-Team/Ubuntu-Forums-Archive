---
title: "Realtek RTL8188EE not working"
date: 2013-09-19
forum: Networking &amp; Wireless
---

### Post by mitchell5 on 2013-09-19
Hi,

I tried to install the driver but it came up with 

```
insmod /lib/modules/3.2.0-53-generic/updates/cw-3.8/compat.ko 
insmod /lib/modules/3.2.0-53-generic/updates/cw-3.8/cfg80211.ko 
insmod /lib/modules/3.2.0-53-generic/updates/cw-3.8/mac80211.ko 
insmod /lib/modules/3.2.0-53-generic/updates/cw-3.8/rtlwifi.ko 
insmod /lib/modules/3.2.0-53-generic/kernel/drivers/net/wireless/rtlwifi/rtl8188ee/rtl8188ee.ko 
FATAL: Error inserting rtl8188ee (/lib/modules/3.2.0-53-generic/kernel/drivers/net/wireless/rtlwifi/rtl8188ee/rtl8188ee.ko): Invalid argument

```

```

*************** info trace ***************

***** uname -a *****

Linux BackBoxTest 3.2.0-53-generic #81-Ubuntu SMP Thu Aug 22 21:01:03 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise

***** lspci *****

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0191]
    Kernel modules: rtl8188ee
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Kernel driver in use: r8169

***** lsusb *****

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 002 Device 002: ID 064e:e374 Suyin Corp. 

***** PCMCIA Card Info *****


***** iwconfig *****


***** rfkill *****


***** lsmod *****

rtlwifi                79738  0 
mac80211              605725  1 rtlwifi
cfg80211              528435  2 rtlwifi,mac80211
compat                 25790  3 rtlwifi,mac80211,cfg80211

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.14
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1



***** NetworkManager.state *****

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

***** interfaces *****

auto lo
iface lo inet loopback


***** iwlist *****


***** resolv.conf *****

nameserver 192.168.1.1
search localdomain

***** blacklist *****

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

***** modinfo *****

filename:       /lib/modules/3.2.0-53-generic/updates/cw-3.8/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     CDF1BB36F7E3A953C939594
depends:        mac80211,cfg80211,compat
vermagic:       3.2.0-53-generic SMP mod_unload modversions 


***** udev rules *****

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:15.1/0000:06:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

***** dmesg *****

[  391.395765] rtl8188ee: disagrees about version of symbol efuse_read_1byte
[  391.395779] rtl8188ee: Unknown symbol efuse_read_1byte (err -22)
[  391.395792] rtl8188ee: disagrees about version of symbol rtl_process_phyinfo
[  391.395797] rtl8188ee: Unknown symbol rtl_process_phyinfo (err -22)
[  391.395803] rtl8188ee: disagrees about version of symbol rtl_cam_reset_all_entry
[  391.395808] rtl8188ee: Unknown symbol rtl_cam_reset_all_entry (err -22)
[  391.395819] rtl8188ee: disagrees about version of symbol rtl_cam_empty_entry
[  391.395824] rtl8188ee: Unknown symbol rtl_cam_empty_entry (err -22)
[  391.395830] rtl8188ee: disagrees about version of symbol rtl_cam_del_entry
[  391.395834] rtl8188ee: Unknown symbol rtl_cam_del_entry (err -22)
[  391.395843] rtl8188ee: disagrees about version of symbol rtl_cam_mark_invalid
[  391.395847] rtl8188ee: Unknown symbol rtl_cam_mark_invalid (err -22)
[  391.395867] rtl8188ee: disagrees about version of symbol ieee80211_find_sta
[  391.395872] rtl8188ee: Unknown symbol ieee80211_find_sta (err -22)
[  391.395886] rtl8188ee: disagrees about version of symbol rtl_pci_disconnect
[  391.395891] rtl8188ee: Unknown symbol rtl_pci_disconnect (err -22)
[  391.395896] rtl8188ee: disagrees about version of symbol rtl_pci_suspend
[  391.395901] rtl8188ee: Unknown symbol rtl_pci_suspend (err -22)
[  391.395909] rtl8188ee: disagrees about version of symbol rtl_signal_scale_mapping
[  391.395913] rtl8188ee: Unknown symbol rtl_signal_scale_mapping (err -22)
[  391.395935] rtl8188ee: disagrees about version of symbol rtl_ps_enable_nic
[  391.395939] rtl8188ee: Unknown symbol rtl_ps_enable_nic (err -22)
[  391.395945] rtl8188ee: disagrees about version of symbol rtl_pci_resume
[  391.395949] rtl8188ee: Unknown symbol rtl_pci_resume (err -22)
[  391.395964] rtl8188ee: disagrees about version of symbol rtl_cam_add_one_entry
[  391.395968] rtl8188ee: Unknown symbol rtl_cam_add_one_entry (err -22)
[  391.395981] rtl8188ee: disagrees about version of symbol rtl_efuse_shadow_map_update
[  391.395986] rtl8188ee: Unknown symbol rtl_efuse_shadow_map_update (err -22)
[  391.395991] rtl8188ee: disagrees about version of symbol rtl_get_tcb_desc
[  391.395995] rtl8188ee: Unknown symbol rtl_get_tcb_desc (err -22)
[  391.397338] rtl8188ee: disagrees about version of symbol rtl_ps_disable_nic
[  391.397347] rtl8188ee: Unknown symbol rtl_ps_disable_nic (err -22)
[  391.397358] rtl8188ee: disagrees about version of symbol rtl_cam_get_free_entry
[  391.397362] rtl8188ee: Unknown symbol rtl_cam_get_free_entry (err -22)
[  391.397367] rtl8188ee: disagrees about version of symbol rtl_pci_probe
[  391.397371] rtl8188ee: Unknown symbol rtl_pci_probe (err -22)
[  391.397376] rtl8188ee: disagrees about version of symbol rtl_cam_delete_one_entry
[  391.397381] rtl8188ee: Unknown symbol rtl_cam_delete_one_entry (err -22)

****************** done ******************
```

---

### Post by praseodym on 2013-09-19
Try this driver:
```

sudo apt-get install --reinstall build-essential linux-headers-$(uname -r) linux-headers-generic
wget media.cdn.ubuntu-de.org/forum/attachments/39/19/5443987-rtl_92ce_92se_92de_8723ae_88ee_0012.0207.2013.tar.gz
tar xvf 5443987-rtl_92ce_92se_92de_8723ae_88ee_0012.0207.2013.tar.gz
cd rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013 
make
sudo make install
sudo depmod -a
sudo update-initramfs -u
sudo cp -r firmware/* /lib/firmware  
```
Uninstall the other first:
```

make clean
make
sudo make uninstall
```

---

### Post by mitchell5 on 2013-09-19
I didn't seem to get any errors but my wlan0 still isn't showing up

---

### Post by varunendra on 2013-09-20
Please post the outputs of -
```
lspci -nnk | grep -iA2 net
rfkill list all
sudo iwlist scan
lsmod
dmesg | egrep '8188|8192|firm'
```

---

### Post by mitchell5 on 2013-09-21
lspci -nnk | grep -iA2 net```
 02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01) 

 	Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0191] 
 	Kernel modules: rtl8188ee 
 06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07) 
 	Subsystem: Toshiba America Info Systems Device [1179:ff1e] 
 	Kernel driver in use: r8169 
 mitch@BackBoxTest:~$ lspci -nnk | grep -iA2 net 
 02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01) 
 	Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0191] 
 	Kernel modules: rtl8188ee 
 06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07) 
 	Subsystem: Toshiba America Info Systems Device [1179:ff1e] 
 	Kernel driver in use: r8169 

``` 

 rfkill list all 

```
no output
```


sudo iwlist scan
 

 ```
lo        Interface doesn't support scanning. 

  
 eth0      Interface doesn't support scanning. 

``` 

 lsmod
 

 ```
Module                  Size  Used by 

 joydev                 17693  0  
 snd_hda_codec_realtek   224173  1  
 snd_hda_codec_hdmi     32474  1  
 snd_hda_intel          33719  7  
 snd_hda_codec         127706  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel 
 snd_hwdep              17764  1 snd_hda_codec 
 rtlwifi                79738  0  
 snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec 
 mac80211              605725  1 rtlwifi 
 snd_seq_midi           13324  0  
 snd_rawmidi            30748  1 snd_seq_midi 
 snd_seq_midi_event     14899  1 snd_seq_midi 
 psmouse                97519  0  
 snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event 
 snd_timer              29990  2 snd_pcm,snd_seq 
 cfg80211              528435  2 rtlwifi,mac80211 
 rts5139               351188  0  
 uvcvideo               72627  0  
 snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq 
 videodev               98259  1 uvcvideo 
 serio_raw              13211  0  
 k10temp                13166  0  
 v4l2_compat_ioctl32    17128  1 videodev 
 rfcomm                 47604  0  
 snd                    79041  24 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 parport_pc             32866  0  
 bnep                   18281  2  
 compat                 25790  3 rtlwifi,mac80211,cfg80211 
 shpchp                 37201  0  
 bluetooth             180113  10 rfcomm,bnep 
 ppdev                  17113  0  
 i2c_piix4              13301  0  
 soundcore              15091  1 snd 
 snd_page_alloc         18529  2 snd_hda_intel,snd_pcm 
 binfmt_misc            17540  1  
 mac_hid                13253  0  
 lp                     17799  0  
 parport                46562  3 parport_pc,ppdev,lp 
 r8169                  62190  0  
 radeon                804577  2  

 video                  19651  0  
 ttm                    76949  1 radeon 
 drm_kms_helper         46978  1 radeon 
 drm                   241971  4 radeon,ttm,drm_kms_helper 
 i2c_algo_bit           13423  1 radeon 
 zram                   18642  1  

``` 

 dmesg | egrep '8188|8192|firm'
 

 ```
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff880106c00000 s83136 r8192 d23360 u524288 

 [    0.000000] pcpu-alloc: s83136 r8192 d23360 u524288 alloc=1*2097152 
 [   17.520776] rtl8188ee: disagrees about version of symbol efuse_read_1byte 
 [   17.520789] rtl8188ee: Unknown symbol efuse_read_1byte (err -22) 
 [   17.520802] rtl8188ee: disagrees about version of symbol rtl_process_phyinfo 
 [   17.520807] rtl8188ee: Unknown symbol rtl_process_phyinfo (err -22) 
 [   17.520814] rtl8188ee: disagrees about version of symbol rtl_cam_reset_all_entry 
 [   17.520819] rtl8188ee: Unknown symbol rtl_cam_reset_all_entry (err -22) 
 [   17.520831] rtl8188ee: disagrees about version of symbol rtl_cam_empty_entry 
 [   17.520835] rtl8188ee: Unknown symbol rtl_cam_empty_entry (err -22) 
 [   17.520842] rtl8188ee: disagrees about version of symbol rtl_cam_del_entry 
 [   17.520846] rtl8188ee: Unknown symbol rtl_cam_del_entry (err -22) 
 [   17.520855] rtl8188ee: disagrees about version of symbol rtl_cam_mark_invalid 
 [   17.520860] rtl8188ee: Unknown symbol rtl_cam_mark_invalid (err -22) 
 [   17.520882] rtl8188ee: disagrees about version of symbol ieee80211_find_sta 

 [   17.520887] rtl8188ee: Unknown symbol ieee80211_find_sta (err -22) 
 [   17.520902] rtl8188ee: disagrees about version of symbol rtl_pci_disconnect 
 [   17.520906] rtl8188ee: Unknown symbol rtl_pci_disconnect (err -22) 
 [   17.520912] rtl8188ee: disagrees about version of symbol rtl_pci_suspend 
 [   17.520916] rtl8188ee: Unknown symbol rtl_pci_suspend (err -22) 
 [   17.520924] rtl8188ee: disagrees about version of symbol rtl_signal_scale_mapping 
 [   17.520929] rtl8188ee: Unknown symbol rtl_signal_scale_mapping (err -22) 
 [   17.520951] rtl8188ee: disagrees about version of symbol rtl_ps_enable_nic 
 [   17.520955] rtl8188ee: Unknown symbol rtl_ps_enable_nic (err -22) 
 [   17.520960] rtl8188ee: disagrees about version of symbol rtl_pci_resume 
 [   17.520964] rtl8188ee: Unknown symbol rtl_pci_resume (err -22) 
 [   17.520980] rtl8188ee: disagrees about version of symbol rtl_cam_add_one_entry 
 [   17.520985] rtl8188ee: Unknown symbol rtl_cam_add_one_entry (err -22) 
 [   17.520998] rtl8188ee: disagrees about version of symbol rtl_efuse_shadow_map_update 
 [   17.521002] rtl8188ee: Unknown symbol rtl_efuse_shadow_map_update (err -22) 
 [   17.521007] rtl8188ee: disagrees about version of symbol rtl_get_tcb_desc 
 [   17.521011] rtl8188ee: Unknown symbol rtl_get_tcb_desc (err -22) 
 [   17.521018] rtl8188ee: disagrees about version of symbol rtl_ps_disable_nic 
 [   17.521022] rtl8188ee: Unknown symbol rtl_ps_disable_nic (err -22) 
 [   17.521032] rtl8188ee: disagrees about version of symbol rtl_cam_get_free_entry 
 [   17.521037] rtl8188ee: Unknown symbol rtl_cam_get_free_entry (err -22) 
 [   17.521041] rtl8188ee: disagrees about version of symbol rtl_pci_probe 
 [   17.521045] rtl8188ee: Unknown symbol rtl_pci_probe (err -22) 
 [   17.521050] rtl8188ee: disagrees about version of symbol rtl_cam_delete_one_entry 
 [   17.521055] rtl8188ee: Unknown symbol rtl_cam_delete_one_entry (err -22) 


```

---

### Post by praseodym on 2013-09-21
Did you install the backported modules before?
```

sudo apt-get remove --purge linux-backports-modules-cw-*
```

Edit after is was solved: Removing the backport-modules also removes new driver versions for the 80211-subsystem which disagree with the module needed here. See "dmesg"-output.

---

### Post by mitchell5 on 2013-09-21
OMG!!! Thank you. That worked!!!! Its working now!

---

