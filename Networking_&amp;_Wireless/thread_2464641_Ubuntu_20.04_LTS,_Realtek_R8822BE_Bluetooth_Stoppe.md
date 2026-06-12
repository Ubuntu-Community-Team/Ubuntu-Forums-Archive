---
title: "Ubuntu 20.04 LTS, Realtek R8822BE Bluetooth Stopped Working"
date: 2021-07-07
forum: Networking &amp; Wireless
---

### Post by revm on 2021-07-07
Okay so I am at a loss here. I have Googled this to death, searched more forums than I ever knew existed, and still cannot figure this out. I am hoping I am just missing something super obvious...

So I have an ASUS laptop with a Realtek R8822BE Wi-Fi/Bluetooth card. I installed Ubuntu 20.04 LTS about 2-3 weeks ago and everything has been working amazing. Then today, I ran out to get lunch and when I got back the icon for Bluetooth showed like it was off (even though in the drop down turning it on was not an option). I rebooted and when it came back up, under Settings->Bluetooth shows no bluetooth installed. I have installed anything other than system and software updates that I get prompted for. I have not messed with any of the settings or config files for Bluetooth. And nothing seems to bring it back. Any suggestions are greatly appreciated, and please let me know what (if any) I can post to help in figuring this out. Thanks in advance!

Blessings,

RevM

---

### Post by praseodym on 2021-07-09
Please show
```

lspci -nnk
lsusb
lsmod
rfkill list
hciconfig --all
```

---

### Post by revm on 2021-07-10
It seems like it is working again, and the Wi-Fi was acting up for a few minutes, but now everything seems okay again...I think...but here is the info you asked for. Thank you for any help you can offer.

```
lspci -nnk00:00.0 Host bridge [0600]: Intel Corporation Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers [8086:5914] (rev 08)
	Subsystem: ASUSTeK Computer Inc. Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers [1043:1d70]
	Kernel driver in use: skl_uncore
00:02.0 VGA compatible controller [0300]: Intel Corporation UHD Graphics 620 [8086:5917] (rev 07)
	Subsystem: ASUSTeK Computer Inc. UHD Graphics 620 [1043:168e]
	Kernel driver in use: i915
	Kernel modules: i915
00:04.0 Signal processing controller [1180]: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem [8086:1903] (rev 08)
	Subsystem: ASUSTeK Computer Inc. Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem [1043:1d70]
	Kernel driver in use: proc_thermal
	Kernel modules: processor_thermal_device
00:14.0 USB controller [0c03]: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller [8086:9d2f] (rev 21)
	Subsystem: ASUSTeK Computer Inc. Sunrise Point-LP USB 3.0 xHCI Controller [1043:201f]
	Kernel driver in use: xhci_hcd
	Kernel modules: xhci_pci
00:14.2 Signal processing controller [1180]: Intel Corporation Sunrise Point-LP Thermal subsystem [8086:9d31] (rev 21)
	Subsystem: ASUSTeK Computer Inc. Sunrise Point-LP Thermal subsystem [1043:1d70]
	Kernel driver in use: intel_pch_thermal
	Kernel modules: intel_pch_thermal
00:15.0 Signal processing controller [1180]: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #0 [8086:9d60] (rev 21)
	Subsystem: ASUSTeK Computer Inc. Sunrise Point-LP Serial IO I2C Controller [1043:1d70]
	Kernel driver in use: intel-lpss
	Kernel modules: intel_lpss_pci
00:15.1 Signal processing controller [1180]: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #1 [8086:9d61] (rev 21)
	Subsystem: ASUSTeK Computer Inc. Sunrise Point-LP Serial IO I2C Controller [1043:1d70]
	Kernel driver in use: intel-lpss
	Kernel modules: intel_lpss_pci
00:16.0 Communication controller [0780]: Intel Corporation Sunrise Point-LP CSME HECI #1 [8086:9d3a] (rev 21)
	Subsystem: ASUSTeK Computer Inc. Sunrise Point-LP CSME HECI [1043:1d70]
	Kernel driver in use: mei_me
	Kernel modules: mei_me
00:17.0 SATA controller [0106]: Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode] [8086:9d03] (rev 21)
	Subsystem: ASUSTeK Computer Inc. Sunrise Point-LP SATA Controller [AHCI mode] [1043:1d70]
	Kernel driver in use: ahci
	Kernel modules: ahci
00:1c.0 PCI bridge [0604]: Intel Corporation Sunrise Point-LP PCI Express Root Port #1 [8086:9d10] (rev f1)
	Kernel driver in use: pcieport
00:1c.4 PCI bridge [0604]: Intel Corporation Sunrise Point-LP PCI Express Root Port #5 [8086:9d14] (rev f1)
	Kernel driver in use: pcieport
00:1c.5 PCI bridge [0604]: Intel Corporation Sunrise Point-LP PCI Express Root Port #6 [8086:9d15] (rev f1)
	Kernel driver in use: pcieport
00:1e.0 Signal processing controller [1180]: Intel Corporation Sunrise Point-LP Serial IO UART Controller #0 [8086:9d27] (rev 21)
	Subsystem: ASUSTeK Computer Inc. Sunrise Point-LP Serial IO UART Controller [1043:1d2d]
	Kernel driver in use: intel-lpss
	Kernel modules: intel_lpss_pci
00:1e.2 Signal processing controller [1180]: Intel Corporation Sunrise Point-LP Serial IO SPI Controller #0 [8086:9d29] (rev 21)
	Subsystem: ASUSTeK Computer Inc. Sunrise Point-LP Serial IO SPI Controller [1043:1d2d]
	Kernel driver in use: intel-lpss
	Kernel modules: intel_lpss_pci
00:1f.0 ISA bridge [0601]: Intel Corporation Sunrise Point LPC Controller/eSPI Controller [8086:9d4e] (rev 21)
	Subsystem: ASUSTeK Computer Inc. Sunrise Point LPC Controller/eSPI Controller [1043:1d70]
00:1f.2 Memory controller [0580]: Intel Corporation Sunrise Point-LP PMC [8086:9d21] (rev 21)
	Subsystem: ASUSTeK Computer Inc. Sunrise Point-LP PMC [1043:1d70]
00:1f.3 Audio device [0403]: Intel Corporation Sunrise Point-LP HD Audio [8086:9d71] (rev 21)
	Subsystem: ASUSTeK Computer Inc. Sunrise Point-LP HD Audio [1043:1a30]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel
00:1f.4 SMBus [0c05]: Intel Corporation Sunrise Point-LP SMBus [8086:9d23] (rev 21)
	Subsystem: ASUSTeK Computer Inc. Sunrise Point-LP SMBus [1043:1d70]
	Kernel driver in use: i801_smbus
	Kernel modules: i2c_i801
01:00.0 3D controller [0302]: NVIDIA Corporation GP107M [GeForce GTX 1050 Mobile] [10de:1c8d] (rev a1)
	Subsystem: ASUSTeK Computer Inc. GP107M [GeForce GTX 1050 Mobile] [1043:168e]
	Kernel driver in use: nvidia
	Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
	Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:200f]
	Kernel driver in use: r8169
	Kernel modules: r8169
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8822BE 802.11a/b/g/n/ac WiFi adapter [10ec:b822]
	Subsystem: AzureWave RTL8822BE 802.11a/b/g/n/ac WiFi adapter [1a3b:2950]
	Kernel driver in use: rtw_8822be
	Kernel modules: rtw88_8822be



```

```
lsusbBus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 13d3:3526 IMC Networks Bluetooth Radio 
Bus 001 Device 003: ID 13d3:5a01 IMC Networks USB2.0 VGA UVC WebCam
Bus 001 Device 002: ID 047d:8002 Kensington Orbit Wireless Mobile Trackball
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

```
lsmodModule                  Size  Used by
usb_storage            73728  0
ip6table_security      16384  0
ip6table_raw           16384  0
ip6table_mangle        16384  0
ip6table_nat           16384  0
iptable_security       16384  0
iptable_raw            16384  0
rfcomm                 81920  16
ccm                    20480  6
ashmem_linux           20480  0
binder_linux          188416  0
iptable_mangle         16384  1
xt_CHECKSUM            16384  1
iptable_nat            16384  1
xt_comment             16384  8
xt_MASQUERADE          20480  1
nf_nat                 45056  3 ip6table_nat,iptable_nat,xt_MASQUERADE
vboxnetadp             28672  0
vboxnetflt             28672  0
cmac                   16384  7
algif_hash             16384  3
vboxdrv               516096  2 vboxnetadp,vboxnetflt
algif_skcipher         16384  3
af_alg                 28672  14 algif_hash,algif_skcipher
bnep                   24576  2
binfmt_misc            24576  1
nls_iso8859_1          16384  1
snd_hda_codec_hdmi     61440  1
snd_hda_codec_realtek   131072  1
snd_hda_codec_generic    81920  1 snd_hda_codec_realtek
ledtrig_audio          16384  1 snd_hda_codec_generic
nvidia_uvm           1019904  0
nvidia_drm             57344  10
nvidia_modeset       1228800  7 nvidia_drm
snd_hda_intel          53248  6
snd_intel_dspcfg       28672  1 snd_hda_intel
snd_hda_codec         139264  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
mei_hdcp               24576  0
snd_hda_core           94208  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
snd_hwdep              20480  1 snd_hda_codec
x86_pkg_temp_thermal    20480  0
intel_powerclamp       20480  0
snd_pcm               114688  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
coretemp               20480  0
kvm_intel             286720  0
snd_seq_midi           20480  0
uvcvideo               98304  0
snd_seq_midi_event     16384  1 snd_seq_midi
intel_rapl_msr         20480  0
kvm                   712704  1 kvm_intel
videobuf2_vmalloc      20480  1 uvcvideo
snd_rawmidi            36864  1 snd_seq_midi
rtw88_8822be           16384  0
crct10dif_pclmul       16384  1
rtw88_8822b           225280  1 rtw88_8822be
videobuf2_memops       20480  1 videobuf2_vmalloc
btusb                  57344  0
ghash_clmulni_intel    16384  0
btrtl                  24576  1 btusb
videobuf2_v4l2         24576  1 uvcvideo
btbcm                  16384  1 btusb
nvidia              34140160  662 nvidia_uvm,nvidia_modeset
aesni_intel           372736  14
btintel                28672  1 btusb
videobuf2_common       57344  2 videobuf2_v4l2,uvcvideo
rtw88_pci              24576  1 rtw88_8822be
snd_seq                69632  2 snd_seq_midi,snd_seq_midi_event
crypto_simd            16384  1 aesni_intel
bluetooth             581632  41 btrtl,btintel,btbcm,bnep,btusb,rfcomm
rtw88_core            167936  2 rtw88_pci,rtw88_8822b
videodev              241664  3 videobuf2_v4l2,uvcvideo,videobuf2_common
cryptd                 24576  5 crypto_simd,ghash_clmulni_intel
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
ecdh_generic           16384  2 bluetooth
glue_helper            16384  1 aesni_intel
mc                     57344  4 videodev,videobuf2_v4l2,uvcvideo,videobuf2_common
snd_timer              40960  2 snd_seq,snd_pcm
joydev                 24576  0
ecc                    32768  1 ecdh_generic
mac80211              905216  2 rtw88_pci,rtw88_core
snd                    94208  23 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
asus_nb_wmi            32768  0
rapl                   20480  0
cfg80211              778240  2 rtw88_core,mac80211
intel_cstate           20480  0
asus_wmi               36864  1 asus_nb_wmi
soundcore              16384  1 snd
input_leds             16384  0
serio_raw              20480  0
ee1004                 20480  0
efi_pstore             16384  0
sparse_keymap          16384  1 asus_wmi
wmi_bmof               16384  0
libarc4                16384  1 mac80211
i915                 2203648  6
mxm_wmi                16384  0
8250_dw                16384  0
mei_me                 40960  1
intel_xhci_usb_role_switch    16384  0
processor_thermal_device    24576  0
mei                   106496  3 mei_hdcp,mei_me
roles                  16384  1 intel_xhci_usb_role_switch
hid_multitouch         28672  0
intel_rapl_common      28672  2 intel_rapl_msr,processor_thermal_device
intel_pch_thermal      20480  0
intel_soc_dts_iosf     20480  1 processor_thermal_device
i2c_algo_bit           16384  1 i915
int3403_thermal        20480  0
int340x_thermal_zone    20480  2 int3403_thermal,processor_thermal_device
asus_wireless          20480  0
int3400_thermal        20480  0
acpi_pad              184320  0
acpi_thermal_rel       16384  1 int3400_thermal
mac_hid                16384  0
sch_fq_codel           20480  2
nf_log_ipv6            16384  5
ip6t_REJECT            16384  1
nf_reject_ipv6         20480  1 ip6t_REJECT
xt_hl                  16384  22
ip6t_rt                20480  3
nf_log_ipv4            16384  5
nf_log_common          16384  2 nf_log_ipv4,nf_log_ipv6
ipt_REJECT             16384  1
nf_reject_ipv4         16384  1 ipt_REJECT
xt_LOG                 20480  10
xt_multiport           20480  4
br_netfilter           28672  0
xt_limit               16384  13
bridge                192512  1 br_netfilter
xt_addrtype            16384  4
stp                    16384  1 bridge
xt_tcpudp              20480  29
llc                    16384  2 bridge,stp
arp_tables             24576  0
evdi                   61440  8
xt_conntrack           16384  16
drm_kms_helper        217088  3 evdi,nvidia_drm,i915
nf_conntrack          147456  3 xt_conntrack,nf_nat,xt_MASQUERADE
nf_defrag_ipv6         24576  1 nf_conntrack
cec                    53248  2 drm_kms_helper,i915
nf_defrag_ipv4         16384  1 nf_conntrack
rc_core                61440  1 cec
fb_sys_fops            16384  1 drm_kms_helper
syscopyarea            16384  2 drm_kms_helper,evdi
sysfillrect            16384  2 drm_kms_helper,evdi
sysimgblt              16384  2 drm_kms_helper,evdi
ip6table_filter        16384  1
ip6_tables             32768  57 ip6table_filter,ip6table_raw,ip6table_nat,ip6table_mangle,ip6table_security
iptable_filter         16384  1
parport_pc             45056  0
bpfilter              884736  0
ppdev                  24576  0
lp                     20480  0
drm                   552960  24 drm_kms_helper,evdi,nvidia_drm,i915
parport                65536  3 parport_pc,lp,ppdev
ip_tables              32768  13 iptable_filter,iptable_security,iptable_raw,iptable_nat,iptable_mangle
x_tables               49152  24 ip6table_filter,xt_conntrack,ip6table_raw,iptable_filter,iptable_security,xt_LOG,xt_multiport,xt_tcpudp,xt_addrtype,xt_CHECKSUM,ip6t_rt,xt_comment,ip6_tables,ipt_REJECT,iptable_raw,ip_tables,xt_limit,xt_hl,ip6table_mangle,ip6table_security,xt_MASQUERADE,ip6t_REJECT,iptable_mangle,arp_tables
autofs4                45056  2
btrfs                1294336  0
blake2b_generic        20480  0
xor                    24576  1 btrfs
raid6_pq              114688  1 btrfs
libcrc32c              16384  3 nf_conntrack,nf_nat,btrfs
usbhid                 57344  0
spi_pxa2xx_platform    32768  0
dw_dmac                16384  0
hid_generic            16384  0
dw_dmac_core           32768  1 dw_dmac
crc32_pclmul           16384  0
i2c_i801               32768  0
r8169                  77824  0
i2c_smbus              20480  1 i2c_i801
realtek                24576  1
intel_lpss_pci         20480  2
intel_lpss             16384  1 intel_lpss_pci
ahci                   40960  3
idma64                 20480  0
xhci_pci               20480  0
libahci                36864  1 ahci
virt_dma               20480  1 idma64
i2c_hid                28672  0
xhci_pci_renesas       20480  1 xhci_pci
hid                   135168  4 i2c_hid,usbhid,hid_multitouch,hid_generic
wmi                    32768  3 asus_wmi,wmi_bmof,mxm_wmi
pinctrl_sunrisepoint    28672  0
video                  49152  2 asus_wmi,i915
pinctrl_intel          28672  1 pinctrl_sunrisepoint



```

```
rfkill list0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no



```

```
hciconfig --allhci0:	Type: Primary  Bus: USB
	BD Address: 80:C5:F2:DA:28:B0  ACL MTU: 1021:8  SCO MTU: 255:16
	UP RUNNING 
	RX bytes:1994 acl:0 sco:0 events:181 errors:0
	TX bytes:26152 acl:0 sco:0 commands:181 errors:0
	Features: 0xff 0xff 0xff 0xfe 0xdb 0xfd 0x7b 0x87
	Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
	Link policy: RSWITCH HOLD SNIFF PARK 
	Link mode: SLAVE ACCEPT 
	Name: 'revm-X705UDR'
	Class: 0x1c010c
	Service Classes: Rendering, Capturing, Object Transfer
	Device Class: Computer, Laptop
	HCI Version: 4.2 (0x8)  Revision: 0xab6b
	LMP Version: 4.2 (0x8)  Subversion: 0x705c
	Manufacturer: Realtek Semiconductor Corporation (93)



```

---

