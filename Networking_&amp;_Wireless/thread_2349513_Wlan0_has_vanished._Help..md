---
title: "Wlan0 has vanished. Help."
date: 2017-01-15
forum: Networking &amp; Wireless
---

### Post by theend66 on 2017-01-15
Hello all,

Few days back i had posted an issue stating that my ubuntu couldnt detect my wireless networks, and also that my wlan0 is missing. Well after fixing it by luck, i started having issues where my internet goes down ever 5mins after connecting. That requires me to disconnect/reconnect just to get internet goinng back on. So as i was trying to fix that issue, my wlan0 went missing again. 

Please help. I am so sick of this :(

```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```

```
lspci
00:00.0 Host bridge: Intel Corporation Device 5904 (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Device 5916 (rev 02)
00:14.0 USB controller: Intel Corporation Device 9d2f (rev 21)
00:14.2 Signal processing controller: Intel Corporation Device 9d31 (rev 21)
00:15.0 Signal processing controller: Intel Corporation Device 9d60 (rev 21)
00:15.1 Signal processing controller: Intel Corporation Device 9d61 (rev 21)
00:16.0 Communication controller: Intel Corporation Device 9d3a (rev 21)
00:17.0 SATA controller: Intel Corporation Device 9d03 (rev 21)
00:1c.0 PCI bridge: Intel Corporation Device 9d10 (rev f1)
00:1c.4 PCI bridge: Intel Corporation Device 9d14 (rev f1)
00:1c.5 PCI bridge: Intel Corporation Device 9d15 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Device 9d58 (rev 21)
00:1f.2 Memory controller: Intel Corporation Device 9d21 (rev 21)
00:1f.3 Audio device: Intel Corporation Device 9d71 (rev 21)
00:1f.4 SMBus: Intel Corporation Device 9d23 (rev 21)
01:00.0 Display controller: Advanced Micro Devices, Inc. [AMD/ATI] Topaz XT [Radeon R7 M260/M265] (rev ff)
02:00.0 Network controller: Qualcomm Atheros Device 0042 (rev 31)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller (rev 07)


```

```
 lsmod
Module                  Size  Used by
bnep                   20480  2 
rfcomm                 69632  4 
nfsd                  315392  2 
auth_rpcgss            57344  1 nfsd
nfs_acl                16384  1 nfsd
nfs                   249856  0 
lockd                  90112  2 nfs,nfsd
grace                  16384  2 nfsd,lockd
sunrpc                331776  6 nfs,nfsd,auth_rpcgss,lockd,nfs_acl
fscache                61440  1 nfs
uvcvideo               90112  0 
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         28672  1 uvcvideo
videobuf2_core         36864  2 uvcvideo,videobuf2_v4l2
v4l2_common            16384  1 videobuf2_v4l2
videodev              180224  4 uvcvideo,v4l2_common,videobuf2_core,videobuf2_v4l2
media                  24576  2 uvcvideo,videodev
rtsx_usb_ms            20480  0 
memstick               20480  1 rtsx_usb_ms
snd_hda_codec_hdmi     53248  1 
dell_led               16384  1 
x86_pkg_temp_thermal    16384  0 
hid_multitouch         20480  0 
snd_hda_codec_realtek    86016  1 
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
coretemp               16384  0 
kvm_intel             167936  0 
dell_laptop            20480  0 
kvm                   536576  1 kvm_intel
i2c_designware_platform    16384  0 
i2c_designware_core    20480  1 i2c_designware_platform
dcdbas                 16384  1 dell_laptop
dell_wmi               16384  0 
dell_smm_hwmon         16384  0 
sparse_keymap          16384  1 dell_wmi
snd_hda_intel          36864  3 
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
snd_hda_core           73728  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
snd_hwdep              16384  1 snd_hda_codec
irqbypass              16384  1 kvm
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
snd_seq_midi           16384  0 
ath10k_pci             40960  0 
ath10k_core           311296  1 ath10k_pci
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
ath                    32768  1 ath10k_core
hci_uart               77824  0 
mac80211              733184  1 ath10k_core
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
btbcm                  16384  1 hci_uart
cfg80211              557056  3 ath,mac80211,ath10k_core
btqca                  16384  1 hci_uart
btintel                16384  1 hci_uart
joydev                 20480  0 
input_leds             16384  0 
serio_raw              16384  0 
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
bluetooth             516096  14 bnep,btbcm,btqca,hci_uart,rfcomm,btintel
i2c_hid                20480  0 
idma64                 20480  0 
pinctrl_sunrisepoint    28672  0 
dell_rbtn              16384  0 
shpchp                 36864  0 
pinctrl_intel          20480  1 pinctrl_sunrisepoint
hid                   118784  2 i2c_hid,hid_multitouch
virt_dma               16384  1 idma64
snd                    81920  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
mei_me                 36864  0 
soundcore              16384  1 snd
acpi_als               16384  0 
parport_pc             36864  0 
intel_lpss_pci         16384  0 
ppdev                  20480  0 
kfifo_buf              16384  1 acpi_als
mei                    98304  1 mei_me
tpm_crb                16384  0 
intel_lpss_acpi        16384  0 
lp                     20480  0 
industrialio           57344  2 acpi_als,kfifo_buf
intel_lpss             16384  2 intel_lpss_pci,intel_lpss_acpi
mac_hid                16384  0 
acpi_pad               20480  0 
parport                49152  3 lp,ppdev,parport_pc
drbg                   28672  1 
ansi_cprng             16384  0 
dm_crypt               28672  1 
rtsx_usb_sdmmc         28672  0 
rtsx_usb               24576  2 rtsx_usb_sdmmc,rtsx_usb_ms
amdkfd                131072  1 
amd_iommu_v2           20480  1 amdkfd
amdgpu                983040  1 
i915_bpo             1306624  4 
crct10dif_pclmul       16384  0 
crc32_pclmul           16384  0 
ghash_clmulni_intel    16384  0 
aesni_intel           167936  1025 
intel_ips              20480  1 i915_bpo
aes_x86_64             20480  1 aesni_intel
i2c_algo_bit           16384  2 i915_bpo,amdgpu
lrw                    16384  1 aesni_intel
ttm                    94208  1 amdgpu
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
drm_kms_helper        151552  2 i915_bpo,amdgpu
cryptd                 20480  515 ghash_clmulni_intel,aesni_intel,ablk_helper
syscopyarea            16384  1 drm_kms_helper
psmouse               126976  0 
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   360448  8 ttm,i915_bpo,drm_kms_helper,amdgpu
r8169                  81920  0 
ahci                   36864  2 
mii                    16384  1 r8169
libahci                32768  1 ahci
wmi                    20480  2 dell_led,dell_wmi
video                  40960  3 i915_bpo,dell_wmi,dell_laptop
fjes                   28672  0 

```


Please help me, i cant take it no more. Iv been sleeping 3 hours each night fighting the wifi lol. Help. Thank you

---

### Post by jeremy31 on 2017-01-15
theend66

I would try this to begin with ```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Reboot
The command will disable wireless power management and should cure the issue, if not see the wireless script link in my signature and post results

---

### Post by theend66 on 2017-01-15
This is what it returned on my end,,,

```


h@the:~/$ sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
[sudo] password for the: 
sed: can't read /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf: No such file or directory
```

I am using Wicd if that helps but nada...not working but thank you for ur attention jeremy, could u advise further?

---

### Post by jeremy31 on 2017-01-15
See the wireless script link and post results

---

### Post by wildmanne39 on 2017-01-15
Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using code tags. 

Please edit your posts to remove the bad language, it is not allowed here.

---

### Post by theend66 on 2017-01-15
This is what shows : 


```


########## wireless info START ##########

Report from: 16 Jan 2017 07:02 SGT +0800

Booted last: 16 Jan 2017 05:50 SGT +0800

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.5 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 4.4.0-51-generic #72~14.04.1-Ubuntu SMP Thu Nov 24 19:22:30 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

sed: can't read /home/themessiah/.dmrc: No such file or directory

Could not be determined.

##### lspci #############################

02:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0042] (rev 31)
    Subsystem: Dell Device [1028:1810]
    Kernel driver in use: ath10k_pci

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Dell Device [1028:07ad]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 064e:920b Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

dell_laptop            20480  0 
dcdbas                 16384  1 dell_laptop
dell_wmi               16384  0 
sparse_keymap          16384  1 dell_wmi
ath10k_pci             40960  0 
ath10k_core           311296  1 ath10k_pci
ath                    32768  1 ath10k_core
mac80211              733184  1 ath10k_core
cfg80211              557056  3 ath,mac80211,ath10k_core
wmi                    20480  2 dell_led,dell_wmi
video                  40960  3 i915_bpo,dell_wmi,dell_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          inet addr:192.168.1.135  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF1]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:492558 errors:0 dropped:0 overruns:0 frame:0
          TX packets:441956 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:577633248 (577.6 MB)  TX bytes:32953210 (32.9 MB)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0

##### resolv.conf #######################

nameserver 192.168.1.254
search singnet.com.sg

##### network managers ##################

Installed:

    NetworkManager
    Wicd

Running:

    None found.

##### NetworkManager info ###############

** (process:5584): WARNING **: Could not initialize NMClient /org/freedesktop/NetworkManager: The name org.freedesktop.NetworkManager was not provided by any .service files

** (process:5584): WARNING **: error: could not connect to NetworkManager

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
plugins=ifupdown,keyfile,ofono

[ifupdown]
managed=false

##### NetworkManager profiles ###########

##### iw reg get ########################


    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

##### module infos ######################

[ath10k_pci]
filename:       /lib/modules/4.4.0-51-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA9377/hw1.0/board.bin
firmware:       ath10k/QCA9377/hw1.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/board-2.bin
firmware:       ath10k/QCA6174/hw3.0/board.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-4.bin
firmware:       ath10k/QCA6174/hw2.1/board-2.bin
firmware:       ath10k/QCA6174/hw2.1/board.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-5.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/board-2.bin
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
firmware:       ath10k/QCA988X/hw2.0/firmware.bin
license:        Dual BSD/GPL
description:    Driver support for Atheros QCA988X PCIe devices
author:         Qualcomm Atheros
srcversion:     8CBDAC7980FC042032AE6A6
depends:        ath10k_core
intree:         Y
vermagic:       4.4.0-51-generic SMP mod_unload modversions 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)

[ath10k_core]
filename:       /lib/modules/4.4.0-51-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for QCA988X PCIe devices.
author:         Qualcomm Atheros
srcversion:     F5C0E3964FCD86D0F5FE986
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       4.4.0-51-generic SMP mod_unload modversions 
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)
parm:           cryptmode:Crypto mode: 0-hardware, 1-software (uint)
parm:           rawmode:Use raw 802.11 frame datapath (bool)

[ath]
filename:       /lib/modules/4.4.0-51-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     3FCDBF7CE71CB8FB980D59D
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-51-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.4.0-51-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     F1176862D12ECD05A1066CF
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-51-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.4.0-51-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     FD4B9DA2F385F0531B5CB0B
depends:        
intree:         Y
vermagic:       4.4.0-51-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath10k_pci]
irq_mode: 0
reset_mode: 0

[ath10k_core]
cryptmode: 0
debug_mask: 0
rawmode: N
skip_otp: Y
uart_print: N

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
rtc
ath10k

##### modprobe options ##################

[/etc/modprobe.d/ath10k_core.conf]
options ath10k_core skip_otp=y

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
blacklist rtl8192cu

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
options iwlwifi 11n_disable=1 wd_disable=1

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/rtl8723be.conf]
options rtl8723be fwlps=N

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x0042 (ath10k_pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

########## wireless info END ############
```

---

### Post by wildmanne39 on 2017-01-15
You have wicd and network manager installed, you can only have one or the other right now neither one is running.

The interfaces file should only have:
```

auto lo
iface lo inet loopback

```
in it but it has:
```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp

```
Which means if you are going to use a network manger then you need to set that file to default and then there is this:
```
nameserver 192.168.1.254
search singnet.com.sg

```
I suggest we set that to default also if you did not make them changes yourself.

---

### Post by theend66 on 2017-01-16
Hi there, 


Yes /etc/network/interfaces was madified manually by me and i have reset it as you advised.

but the result below was not set by me, it was automatically set. But i am currently connected wireless through my Wicd GUI interface. I thouught i uninstalled and purged my network manager. Please advise.

Also i am using Wicd if that helps.

```
nameserver 192.168.1.254
search singnet.com.sg
```

---

### Post by jeremy31 on 2017-01-16
Please post results for ```
dmesg | grep ath10; dpkg -l | grep linux-firmware
```

---

### Post by theend66 on 2017-01-16
```


 dmesg | grep ath10; dpkg -l | grep linux-firmware
[   31.265258] ath10k_pci 0000:02:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[   32.395545] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/cal-pci-0000:02:00.0.bin failed with error -2
[   32.419808] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/QCA9377/hw1.0/firmware-5.bin failed with error -2
[   32.419811] ath10k_pci 0000:02:00.0: could not fetch firmware file 'ath10k/QCA9377/hw1.0/firmware-5.bin': -2
[   32.419820] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/QCA9377/hw1.0/firmware-4.bin failed with error -2
[   32.419821] ath10k_pci 0000:02:00.0: could not fetch firmware file 'ath10k/QCA9377/hw1.0/firmware-4.bin': -2
[   32.419827] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/QCA9377/hw1.0/firmware-3.bin failed with error -2
[   32.419829] ath10k_pci 0000:02:00.0: could not fetch firmware file 'ath10k/QCA9377/hw1.0/firmware-3.bin': -2
[   32.419834] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/QCA9377/hw1.0/firmware-2.bin failed with error -2
[   32.419836] ath10k_pci 0000:02:00.0: could not fetch firmware file 'ath10k/QCA9377/hw1.0/firmware-2.bin': -2
[   32.419841] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/QCA9377/hw1.0/firmware.bin failed with error -2
[   32.419843] ath10k_pci 0000:02:00.0: could not fetch firmware (-2)
[   32.419844] ath10k_pci 0000:02:00.0: could not fetch firmware files (-2)
[   32.419846] ath10k_pci 0000:02:00.0: could not probe fw (-2)
ii  linux-firmware-nonfree                      1.14ubuntu3                             all          Non-free firmware for Linux kernel drivers



```

---

### Post by jeremy31 on 2017-01-16
Strange that those errors didn't show in the script results
```
wget http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.157.6_all.deb
sudo dpkg -i linux-firmware_1.157.6_all.deb
```

Reboot

---

### Post by theend66 on 2017-01-16
```
dpkg -i linux-firmware_1.157.6_all.deb
[sudo] password for the: 
Selecting previously unselected package linux-firmware.
(Reading database ... 289732 files and directories currently installed.)
Preparing to unpack linux-firmware_1.157.6_all.deb ...
Unpacking linux-firmware (1.157.6) ...
Setting up linux-firmware (1.157.6) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-59-generic
W: Possible missing firmware /lib/firmware/i915/kbl_dmc_ver1.bin for module i915_bpo
update-initramfs: Generating /boot/initrd.img-4.4.0-51-generic
W: Possible missing firmware /lib/firmware/i915/kbl_dmc_ver1.bin for module i915_bpo
update-initramfs: Generating /boot/initrd.img-4.2.0-42-generic
W: Possible missing firmware /lib/firmware/radeon/boniare_mc.bin for module amdgpu


```

---

### Post by jeremy31 on 2017-01-16
What is the result for ```
ls /lib/firmware/ath10k/QCA9377/hw1.0/
```

---

### Post by theend66 on 2017-01-17
```

$ ls /lib/firmware/ath10k/QCA9377/hw1.0/
board-2.bin  firmware-5.bin                      notice_ath10k_firmware-5.txt
board.bin    firmware-5.bin_WLAN.TF.1.0-00267-1  notice.txt_WLAN.TF.1.0-00267-1


```

Thank you for your help Jeremy31

---

### Post by theend66 on 2017-01-17
Jereym31, something strange is now happening. 

On my Wicd by default i am unable to scan for any wireless networks. 

But when i click on the "switch off/on" a few times i am then able to scan and get all my available wireless listing. 

But! I am mostly unable to connect to my wifi though its the correct password. And that one time when i did manage to connect  and the internet lasted 3 mins and it just froze though the status showed that its connected.

```

sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 18:db:f2:06:16:9f  
          inet addr:192.168.1.135  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::1adb:f2ff:fe06:169f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6728 errors:0 dropped:1 overruns:0 frame:0
          TX packets:6377 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5975286 (5.9 MB)  TX bytes:828728 (828.7 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:278 errors:0 dropped:0 overruns:0 frame:0
          TX packets:278 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:59953 (59.9 KB)  TX bytes:59953 (59.9 KB)

wlan0     Link encap:Ethernet  HWaddr 94:53:30:71:8d:87  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:452 (452.0 B)  TX bytes:5265 (5.2 KB)


```

---

### Post by jeremy31 on 2017-01-17
Does ```
iwlist scan | egrep -i 'ssid|cipher'
```
Show any access points?  Does your AP show TKIP being used as a cipher?

---

### Post by theend66 on 2017-01-17
By the way, My wifi is able to scan the networks but it keeps stating that i am using the wrong password when i am not. This is the output.

```

$ iwlist scan | egrep -i 'ssid|cipher'
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

                    ESSID:"Aries"
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                    ESSID:"SINGTEL-2995"
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                    ESSID:"SINGTEL-12ED"
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP



```

---

### Post by jeremy31 on 2017-01-17
Can you change the wifi router encryption setting to WPA2 only?  TKIP usually causes problems and makes the network less secure

---

### Post by theend66 on 2017-01-17
The only options i have are :  

WPA1/2 HEX [0-9/A-F]

\WPA PEAP

WPA 1/2 [Passphrase]

WPA2 LEAP

WPA2 PEAP

---

### Post by theend66 on 2017-01-17
HI Jeremy31, The attempt to connect hangs at " validating authentication"

also 

```

-1 /etc/modprobe.d/
alsa-base.conf
ath10k_core.conf
b43.conf
blacklist-ath_pci.conf
blacklist.conf
blacklist-firewire.conf
blacklist-framebuffer.conf
blacklist-modem.conf
blacklist-oss.conf
blacklist-rare-network.conf
blacklist-watchdog.conf
dkms.conf
fbdev-blacklist.conf
iwlwifi.conf
mlx4.conf
rtl8723be.conf
vmwgfx-fbdev.conf


```

---

### Post by theend66 on 2017-01-18
Jeremy31, i just wanted to inform you that my wifi now connects and obtains an ip address. I am able to surf the net smoothly for 10mins and then the internet access stops though WICD shows the wifi connected. Any idea why?

---

### Post by jeremy31 on 2017-01-18
What does ```
iwconfig
```
report when the internet fails.  You could also check ```
cat /var/log/kern.log | tail -20
```
To see if there isn't something else causing the issue

---

### Post by theend66 on 2017-01-19
```

$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"Aries"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: 16:0C:C3:F1:2F:68   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-35 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:36   Missed beacon:0

eth0      no wireless extensions.


```

```


~$ cat /var/log/kern.log | tail -20
Jan 20 00:46:13 the kernel: [ 1280.923662] IPv4: martian source 192.168.1.83 from 192.168.1.254, on dev eth0
Jan 20 00:46:13 the kernel: [ 1280.923684] ll header: 00000000: ff ff ff ff ff ff 00 0c c3 f1 2f 68 08 06        ........../h..
Jan 20 00:46:14 the kernel: [ 1281.963615] IPv4: martian source 192.168.1.83 from 192.168.1.254, on dev eth0
Jan 20 00:46:14 the kernel: [ 1281.963644] ll header: 00000000: ff ff ff ff ff ff 00 0c c3 f1 2f 68 08 06        ........../h..
Jan 20 00:46:15 the kernel: [ 1282.963435] IPv4: martian source 192.168.1.83 from 192.168.1.254, on dev eth0
Jan 20 00:46:15 the kernel: [ 1282.963449] ll header: 00000000: ff ff ff ff ff ff 00 0c c3 f1 2f 68 08 06        ........../h..
Jan 20 00:46:16 the kernel: [ 1283.963340] IPv4: martian source 192.168.1.83 from 192.168.1.254, on dev eth0
Jan 20 00:46:16 the kernel: [ 1283.963350] ll header: 00000000: ff ff ff ff ff ff 00 0c c3 f1 2f 68 08 06        ........../h..
Jan 20 00:46:30 the kernel: [ 1297.952257] IPv4: martian source 192.168.1.83 from 192.168.1.254, on dev eth0
Jan 20 00:46:30 the kernel: [ 1297.952278] ll header: 00000000: ff ff ff ff ff ff 00 0c c3 f1 2f 68 08 06        ........../h..
Jan 20 00:46:31 the kernel: [ 1298.952198] IPv4: martian source 192.168.1.83 from 192.168.1.254, on dev eth0
Jan 20 00:46:31 the kernel: [ 1298.952226] ll header: 00000000: ff ff ff ff ff ff 00 0c c3 f1 2f 68 08 06        ........../h..
Jan 20 00:46:32 the kernel: [ 1299.952108] IPv4: martian source 192.168.1.83 from 192.168.1.254, on dev eth0
Jan 20 00:46:32 the kernel: [ 1299.952121] ll header: 00000000: ff ff ff ff ff ff 00 0c c3 f1 2f 68 08 06        ........../h..
Jan 20 00:46:46 the kernel: [ 1313.440930] IPv4: martian source 192.168.1.83 from 192.168.1.254, on dev eth0
Jan 20 00:46:46 the kernel: [ 1313.440939] ll header: 00000000: ff ff ff ff ff ff 00 0c c3 f1 2f 68 08 06        ........../h..
Jan 20 00:46:47 the kernel: [ 1314.440826] IPv4: martian source 192.168.1.83 from 192.168.1.254, on dev eth0
Jan 20 00:46:47 the kernel: [ 1314.440831] ll header: 00000000: ff ff ff ff ff ff 00 0c c3 f1 2f 68 08 06        ........../h..
Jan 20 00:46:48 the kernel: [ 1315.440736] IPv4: martian source 192.168.1.83 from 192.168.1.254, on dev eth0
Jan 20 00:46:48 the kernel: [ 1315.440744] ll header: 00000000: ff ff ff ff ff ff 00 0c c3 f1 2f 68 08 06        ........../h..

```

And i am seated beside my modem. What could be happening?

---

### Post by jeremy31 on 2017-01-19
You might want to move farther away from the wifi router in case it is overloading the wifi card

See if the problem is still there after ```
sudo iwconfig wlan0 power off
```

You may want to check iwconfig results after a reboot to see if power management is back on

---

### Post by theend66 on 2017-01-20
Done the above command but things remain the same. I have tried it at various distance. This is making life so hard for me to get to work :(

---

### Post by jeremy31 on 2017-01-20
Are you actually using ethernet at the same time as those errors are from the ethernet device

---

### Post by theend66 on 2017-01-20
Sorry about that, my bad.

```

cat /var/log/kern.log | tail -20
Jan 21 11:45:32 themessiah kernel: [  188.315920] ath: EEPROM regdomain: 0x82be
Jan 21 11:45:32 themessiah kernel: [  188.315922] ath: EEPROM indicates we should expect a country code
Jan 21 11:45:32 themessiah kernel: [  188.315923] ath: doing EEPROM country->regdmn map search
Jan 21 11:45:32 themessiah kernel: [  188.315924] ath: country maps to regdmn code: 0x5b
Jan 21 11:45:32 themessiah kernel: [  188.315925] ath: Country alpha2 being used: SG
Jan 21 11:45:32 themessiah kernel: [  188.315925] ath: Regpair used: 0x5b
Jan 21 11:45:32 themessiah kernel: [  188.315926] ath: regdomain 0x82be dynamically updated by country IE
Jan 21 11:45:32 themessiah kernel: [  188.315934] cfg80211: Regulatory domain changed to country: SG
Jan 21 11:45:32 themessiah kernel: [  188.315935] cfg80211:  DFS Master region: unset
Jan 21 11:45:32 themessiah kernel: [  188.315936] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Jan 21 11:45:32 themessiah kernel: [  188.315937] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Jan 21 11:45:32 themessiah kernel: [  188.315939] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Jan 21 11:45:32 themessiah kernel: [  188.315940] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm), (0 s)
Jan 21 11:45:32 themessiah kernel: [  188.315941] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Jan 21 11:46:01 themessiah kernel: [  217.928808] Valid eCryptfs headers not found in file header region or xattr region, inode 57280010
Jan 21 11:46:01 themessiah kernel: [  217.928902] Valid eCryptfs headers not found in file header region or xattr region, inode 57280011
Jan 21 11:46:07 themessiah kernel: [  223.425065] Valid eCryptfs headers not found in file header region or xattr region, inode 57280010
Jan 21 11:46:07 themessiah kernel: [  223.425113] Valid eCryptfs headers not found in file header region or xattr region, inode 57280011
Jan 21 11:47:21 themessiah kernel: [  297.883550] Valid eCryptfs headers not found in file header region or xattr region, inode 57152892
Jan 21 11:47:23 themessiah kernel: [  299.736100] mce: [Hardware Error]: Machine check events logged


```

---

