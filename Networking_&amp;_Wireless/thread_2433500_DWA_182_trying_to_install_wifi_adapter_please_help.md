---
title: "DWA 182 trying to install wifi adapter please help"
date: 2019-12-19
forum: Networking &amp; Wireless
---

### Post by dahookup on 2019-12-19
tried doing this and i couldn't manage to get anything to work, first time using ubuntu and bought and got this adapter for christmas early, i dont know what im doing, could someone please walk me through what i need to do, ive been trying for a few hours but i cant.

---

### Post by praseodym on 2019-12-20
Hi,

lets check the chipset. Open a terminal with CTRL+ALT+T and hit these 2 commands
```

lsusb
lsmod
```
After that we know which driver is suitable. Do you have a working LAN connection?

---

### Post by dahookup on 2019-12-20
```
darrell@darrell-Inspiron-One-19A:~$ lsusb
Bus 001 Device 005: ID 2001:3315 D-Link Corp. 
Bus 001 Device 002: ID 0c45:6310 Microdia Sonix USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 248a:00da Maxxter 
Bus 003 Device 002: ID 248a:8366 Maxxter Wireless Optical Mouse ACT-MUSW-002
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```
```
darrell@darrell-Inspiron-One-19A:~$ lsmod
Module                  Size  Used by
btrfs                1175552  0
zstd_compress         155648  1 btrfs
xor                    24576  1 btrfs
raid6_pq              114688  1 btrfs
ufs                    81920  0
qnx4                   16384  0
hfsplus               110592  0
hfs                    61440  0
minix                  36864  0
ntfs                  106496  0
msdos                  20480  0
jfs                   188416  0
xfs                  1232896  0
libcrc32c              16384  2 btrfs,xfs
cpuid                  16384  0
nls_utf8               16384  1
isofs                  49152  1
i915                 1814528  15
kvmgt                  28672  0
snd_hda_codec_conexant    24576  1
snd_hda_codec_generic    77824  1 snd_hda_codec_conexant
uvcvideo               98304  0
ledtrig_audio          16384  2 snd_hda_codec_generic,snd_hda_codec_conexant
vfio_mdev              16384  0
mdev                   24576  2 kvmgt,vfio_mdev
snd_hda_intel          40960  3
vfio_iommu_type1       28672  0
videobuf2_vmalloc      20480  1 uvcvideo
videobuf2_memops       20480  1 videobuf2_vmalloc
vfio                   32768  3 kvmgt,vfio_mdev,vfio_iommu_type1
videobuf2_v4l2         24576  1 uvcvideo
snd_hda_codec         131072  3 snd_hda_codec_generic,snd_hda_codec_conexant,snd_hda_intel
video                  45056  1 i915
videobuf2_common       49152  2 videobuf2_v4l2,uvcvideo
snd_hda_core           86016  4 snd_hda_codec_generic,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec
videodev              200704  3 videobuf2_v4l2,uvcvideo,videobuf2_common
drm_kms_helper        180224  1 i915
snd_hwdep              20480  1 snd_hda_codec
drm                   475136  7 drm_kms_helper,i915
snd_pcm               102400  3 snd_hda_intel,snd_hda_codec,snd_hda_core
media                  53248  4 videodev,videobuf2_v4l2,uvcvideo,videobuf2_common
snd_seq_midi           20480  0
i2c_algo_bit           16384  1 i915
snd_seq_midi_event     16384  1 snd_seq_midi
fb_sys_fops            16384  1 drm_kms_helper
snd_rawmidi            36864  1 snd_seq_midi
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
dcdbas                 20480  0
coretemp               20480  0
snd_seq                69632  2 snd_seq_midi,snd_seq_midi_event
joydev                 24576  0
input_leds             16384  0
sysimgblt              16384  1 drm_kms_helper
dell_smm_hwmon         16384  0
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
snd_timer              36864  2 snd_seq,snd_pcm
snd                    81920  16 snd_hda_codec_generic,snd_seq,snd_hda_codec_conexant,snd_seq_device,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_timer,snd_pcm,snd_rawmidi
kvm_intel             241664  0
kvm                   626688  2 kvmgt,kvm_intel
soundcore              16384  1 snd
irqbypass              16384  1 kvm
mac_hid                16384  0
serio_raw              20480  0
sch_fq_codel           20480  2
parport_pc             40960  1
ppdev                  24576  0
lp                     20480  0
parport                53248  3 parport_pc,lp,ppdev
ip_tables              28672  0
x_tables               40960  1 ip_tables
autofs4                45056  2
hid_generic            16384  0
usbhid                 53248  0
hid                   126976  2 usbhid,hid_generic
gpio_ich               16384  0
firewire_ohci          40960  0
psmouse               151552  0
lpc_ich                24576  0
r8169                  81920  0
sdhci_pci              45056  0
pata_acpi              16384  0
i2c_i801               32768  0
realtek                20480  1
firewire_core          65536  1 firewire_ohci
cqhci                  28672  1 sdhci_pci
sdhci                  57344  1 sdhci_pci
crc_itu_t              16384  1 firewire_core
```


yes on a lan connection now, i appreciate your assistance :)

---

### Post by praseodym on 2019-12-20
Try the driver from the repos

```
sudo apt-get install rtl8812au-dkms build-essential dkms
```
Reboot and disable SecureBoot

---

### Post by dahookup on 2019-12-20
THANK YOU~!

it instantly started working, and im about to reboot now

how to disable secure boot?
i stopped after reboot

im back on LAN after reboot it isnt found again.

tried

```
darrell@darrell-Inspiron-One-19A:~$ sudo mokutil --disable-validation
[sudo] password for darrell: 
sudo: mokutil: command not found
darrell@darrell-Inspiron-One-19A:~$ sudo mokutil --disable-validation.
sudo: mokutil: command not found
darrell@darrell-Inspiron-One-19A:~$ 
```


sorry idk how to do code tags

unable to get my pc to find it again ive tried redoing the process, unplugging and reinserting the adapter  sad face

```
 darrell@darrell-Inspiron-One-19A:~$ sudo apt-get install rtl8812au-dkms build-essential dkms[sudo] password for darrell: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version (12.6ubuntu1).
rtl8812au-dkms is already the newest version (4.3.8.12175.20140902+dfsg-0ubuntu10).
dkms is already the newest version (2.6.1-4ubuntu2.5).
0 upgraded, 0 newly installed, 0 to remove and 178 not upgraded.
darrell@darrell-Inspiron-One-19A:~$
```

---

### Post by praseodym on 2019-12-20
I suggest to update your system first
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
Reboot

---

### Post by jeremy31 on 2019-12-20
How about results for ```
dmesg | grep 8812; modinfo 8812au; locate 8812au.ko
```

---

### Post by dahookup on 2019-12-20
done, the adapter is not found.

```
@darrell-Inspiron-One-19A:~$ dmesg | grep 8812; modinfo 8812au; locate 8812au.ko
[    0.293098] audit: type=2000 audit(1576881281.148:1): state=initialized audit_enabled=0 res=1
[    1.139452] rtc_cmos 00:01: setting system clock to 2019-12-20T22:34:42 UTC (1576881282)
[   12.765128] audit: type=1400 audit(1576881294.121:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="nvidia_modprobe" pid=377 comm="apparmor_parser"
[   12.765132] audit: type=1400 audit(1576881294.121:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="nvidia_modprobe//kmod" pid=377 comm="apparmor_parser"
[   12.913706] audit: type=1400 audit(1576881294.269:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/tcpdump" pid=376 comm="apparmor_parser"
[   12.977918] audit: type=1400 audit(1576881294.337:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=378 comm="apparmor_parser"
[   12.977924] audit: type=1400 audit(1576881294.337:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=378 comm="apparmor_parser"
[   12.977927] audit: type=1400 audit(1576881294.337:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=378 comm="apparmor_parser"
[   12.977930] audit: type=1400 audit(1576881294.337:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=378 comm="apparmor_parser"
[   13.043283] audit: type=1400 audit(1576881294.397:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="libreoffice-xpdfimport" pid=380 comm="apparmor_parser"
[   13.175760] audit: type=1400 audit(1576881294.529:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=381 comm="apparmor_parser"
[   13.175765] audit: type=1400 audit(1576881294.529:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=381 comm="apparmor_parser"
[   24.738523] 8812au: version magic '5.0.0-13-generic SMP mod_unload ' should be '5.0.0-37-generic SMP mod_unload '
[   99.546727] 8812au: version magic '5.0.0-13-generic SMP mod_unload ' should be '5.0.0-37-generic SMP mod_unload '
[  168.974144] 8812au: version magic '5.0.0-13-generic SMP mod_unload ' should be '5.0.0-37-generic SMP mod_unload '
filename:       /lib/modules/5.0.0-37-generic/updates/dkms/8812au.ko
version:        v4.3.8_12175.20140902
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     141DD6D3AA57134D210FEB5
alias:          usb:v056Ep4007d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p0242d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB32d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p9052d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0023d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3318d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3314d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp0953d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392pA813d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392pA812d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392pA811d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp0820d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDAp8822d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp0821d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp0811d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p025Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2357p0103d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2357p0101d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v20F4p805Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3316d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3315d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p8812d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB30d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p0100d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp9097d*dc*dsc*dp*ic*isc*ip*in*
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
alias:          usb:v050Dp1109d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp1106d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp881Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp881Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp881Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8812d*dc*dsc*dp*ic*isc*ip*in*
depends:        cfg80211
retpoline:      Y
name:           8812au
vermagic:       5.0.0-13-generic SMP mod_unload 
parm:           rtw_ips_mode:The default IPS mode (int)
parm:           rtw_usb_rxagg_mode:int
parm:           rtw_qos_opt_enable:int
parm:           ifname:The default name to allocate for first interface (charp)
parm:           if2name:The default name to allocate for second interface (charp)
parm:           rtw_initmac:charp
parm:           rtw_channel_plan:int
parm:           rtw_special_rf_path:int
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
parm:           rtw_hiq_filter:0:allow all, 1:allow special, 2:deny all (uint)
parm:           rtw_adaptivity_en:0:disable, 1:enable, 2:auto (uint)
parm:           rtw_adaptivity_mode:0:normal, 1:carrier sense (uint)
parm:           rtw_nhm_en:0:disable, 1:enable (uint)
parm:           rtw_amplifier_type_2g:BIT3:2G ext-PA, BIT4:2G ext-LNA (uint)
parm:           rtw_amplifier_type_5g:BIT6:5G ext-PA, BIT7:5G ext-LNA (uint)
parm:           rtw_RFE_type:default init value:64 (uint)
parm:           rtw_TxBBSwing_2G:default init value:0xFF (uint)
parm:           rtw_TxBBSwing_5G:default init value:0xFF (uint)
parm:           rtw_tx_pwr_lmt_enable:0:Disable, 1:Enable, 2: Depend on efuse (int)
parm:           rtw_tx_pwr_by_rate:0:Disable, 1:Enable, 2: Depend on efuse (int)
parm:           rtw_phy_file_path:The path of phy parameter (charp)
parm:           rtw_load_phy_file:PHY File Bit Map (int)
parm:           rtw_decrypt_phy_file:Enable Decrypt PHY File (int) 
```

```
darrell@darrell-Inspiron-One-19A:~$ sudo apt install pastebinit[sudo] password for darrell: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  pastebinit
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 14.6 kB of archives.
After this operation, 160 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu disco/main amd64 pastebinit all 1.5-2 [14.6 kB]
Fetched 14.6 kB in 0s (46.1 kB/s)     
Selecting previously unselected package pastebinit.
(Reading database ... 173336 files and directories currently installed.)
Preparing to unpack .../pastebinit_1.5-2_all.deb ...
Unpacking pastebinit (1.5-2) ...
Setting up pastebinit (1.5-2) ...
Processing triggers for man-db (2.8.5-2) ...

```

---

### Post by jeremy31 on 2019-12-20
See if this works ```
sudo apt-get install --reinstall rtl8812au-dkms
```
Reboot, if it works do
```
gedit admin:///usr/src/rtl8812au-4.3.8.12175.20140902+dfsg/dkms.conf
```
Change the line with ```
MAKE="'make' all"
```
to
```
MAKE="'make' all KVER=${kernelver}"
```
Save an exit gedit and it should work for the next kernel update

---

### Post by dahookup on 2019-12-20
[COLOR=#000000]See if this works[/COLOR][COLOR=#000000]Code:
sudo apt-get install --reinstall rtl8812au-dkms[/COLOR]
its on and working right now, going to reboot and do next step your provided.

its found still, but there is no visible networks like before reboot.
before reboot i had many networks to chose from, after reboot, no networks.

```
darrell@darrell-Inspiron-One-19A:~$ gedit admin:///usr/src/rtl8812au-4.3.8.12175.20140902+dfsg/dkms.conf

** (org.gnome.gedit:2539): WARNING **: 17:01:00.420: The specified location is not mounted
darrell@darrell-Inspiron-One-19A:~$ 

```

```
PACKAGE_NAME="rtl8812au"
PACKAGE_VERSION="4.3.8.12175.20140902+dfsg"
BUILT_MODULE_NAME[0]="8812au"
MAKE="'make' all KVER=${kernelver}"
CLEAN="'make' clean"
DEST_MODULE_LOCATION[0]="/updates/dkms"
AUTOINSTALL="YES"
```

says wifi not connected at the top right should i [COLOR=#000000][FONT=&quot]sudo apt-get install --reinstall rtl8812au-dkms ?[/FONT][/COLOR]

---

### Post by jeremy31 on 2019-12-20
Try ```
sudo dkms install rtl8812au/4.3.8.12175.20140902+dfsg -k $(uname -r)
```
Reboot

---

### Post by dahookup on 2019-12-20
```
arrell@darrell-Inspiron-One-19A:~$ sudo dkms install rtl8812au/4.3.8.12175.20140902+dfsg -k $(uname -r)[sudo] password for darrell: 
Module rtl8812au/4.3.8.12175.20140902+dfsg already installed on kernel 5.0.0-37-generic/x86_64

```


no change, its found and the adapter blinks with power...which is new :)
but no networks are found, and at the top right of my screen on the network button, it says wifi not connected.

---

### Post by jeremy31 on 2019-12-20
Ok, see the wireless script link in my signature and post results.  Also post results for ```
dkms status
```

---

### Post by dahookup on 2019-12-20
i removed the adapter and plugged it back it, and it works and im on wifi connection, going to reboot now to see if that solved it :)!

ok posting status before i reboot

```
darrell@darrell-Inspiron-One-19A:~$ dkms status
rtl8812au, 4.3.8.12175.20140902+dfsg, 5.0.0-37-generic, x86_64: installed
```

it works!

thank you so much!!!

---

