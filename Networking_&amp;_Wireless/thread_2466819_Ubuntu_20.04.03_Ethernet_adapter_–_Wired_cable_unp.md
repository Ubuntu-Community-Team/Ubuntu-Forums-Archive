---
title: "Ubuntu 20.04.03 Ethernet adapter – Wired cable unplugged"
date: 2021-09-06
forum: Networking &amp; Wireless
---

### Post by iqdesigner on 2021-09-06
Hi,

I use Ubuntu 20.04.3 LTS and moving to another office that has a wired cable I failed to connect to the network with my laptop. It seems dead, the light in router does not open.I try the same wired port/cable in another laptop and the network is working fine.  The wireless card works in my laptop

 ```
sudo ip link show
  1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
     link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
  2: enp3s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN mode DEFAULT group default qlen 1000
     link/ether xx:xx:xx:xx:xx:xx brd ff:ff:ff:ff:ff:ff
  3: wlp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP mode DORMANT group default qlen 1000
     link/ether xx:xx:xx:xx:xx:xx brd ff:ff:ff:ff:ff:ff

``` 
 
 
 From the Settings/Network I create a wired connection but Cable is unplugged:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289129&stc=1[/IMG]
 
 
 So I removed it

 Searching a bit I found mentions about  
 
 ```
/etc/netplan/01-network-manager-all.yaml
``` 
 
 The original file is:
 
 ```

network:
  version: 2
  renderer: NetworkManager
``` 

I change to  
 ```

network:
    version: 2
    renderer: NetworkManager
    ethernets:
      enp3s0:
      dhcp4: true

``` 
 
 and give **sudo netplan apply**. Still cable unlugged
 
 I also restart NetworkManager (**sudo service network-manager restart**) but still nothing wired network does not work
 I read mentions about **/etc/network/interfaces** but there is no such file in my Ubuntu
 I tried **sudo ifconfig enp3s0 up** but still cable unplugged
Try reboot, etc but all fails
 

_**Hardware details: **_
 ```

lspci

 02:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
     Subsystem: Dell QCA9565 / AR9565 Wireless Network Adapter [1028:020e]
     Kernel driver in use: ath9k
     Kernel modules: ath9k

 03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL810xE PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
     Subsystem: Dell RTL810xE PCI Express Fast Ethernet controller [1028:078a]
     Kernel driver in use: r8169
     Kernel modules: r8169

``` 
 
 ```

ifconfig

 enp3s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
         ether xx:xx:xx:xx:xx:xx  txqueuelen 1000  (Ethernet)
         RX packets 0  bytes 0 (0.0 B)
         RX errors 0  dropped 0  overruns 0  frame 0
         TX packets 0  bytes 0 (0.0 B)


```


There are similar threads: [https://ubuntuforums.org/showthread.php?t=2453892&highlight=unplugged](https://ubuntuforums.org/showthread.php?t=2453892&highlight=unplugged), [https://ubuntuforums.org/showthread.php?t=2453892&highlight=unplugged](https://ubuntuforums.org/showthread.php?t=2453892&highlight=unplugged) but no solution.


Could someone help?

Thanks

---

### Post by praseodym on 2021-09-07
Please show the outputs of these commands:
```
sudo ethtool enp3s0
cat /etc/network/interfaces
lsmod
```

---

### Post by iqdesigner on 2021-09-07
> **praseodym said:**
> Please show the outputs of these commands:
```
sudo ethtool enp3s0
cat /etc/network/interfaces
lsmod
```

Hi praseodym,

As I mentioned, I have no /etc/network/interfaces file:
 
```
cat: /etc/network/interfaces: No such file or directory
```

This is a new Ubuntu 20.04 installation (some months old), but never  checked wired card just few days ago as I worked until now with WIFI. On  same laptop with previous Ubuntu version: 16.04 Ethernet with cable was  working fine.

The cable is plugged in my router and laptop but nothing works. I checked on another laptop same router and cable and eveything work fine.

[B]sudo apt-get install ethtool
sudo ethtool enp3s0
[/B]```
Settings for enp3s0:
  Supported ports: [ TP MII ]
  Supported link modes:   10baseT/Half 10baseT/Full 
                          100baseT/Half 100baseT/Full 
  Supported pause frame use: Symmetric Receive-only
  Supports auto-negotiation: Yes
  Supported FEC modes: Not reported
  Advertised link modes:  10baseT/Half 10baseT/Full 
                          100baseT/Half 100baseT/Full 
  Advertised pause frame use: Symmetric Receive-only
  Advertised auto-negotiation: Yes
  Advertised FEC modes: Not reported
  Speed: Unknown!
  Duplex: Unknown! (255)
  Port: Twisted Pair
  PHYAD: 0
  Transceiver: internal
  Auto-negotiation: on
  MDI-X: Unknown
  Supports Wake-on: pumbg
  Wake-on: d
  Link detected: no
```


**sudo ethtool -i enp3s0**
```
driver: r8169
version: 5.11.0-27-generic
firmware-version: rtl8106e-1_0.0.1 06/29/12
expansion-rom-version: 
bus-info: 0000:03:00.0
supports-statistics: yes
supports-test: no
supports-eeprom-access: no
supports-register-dump: yes
supports-priv-flags: no
```


**lsmod**
```
Module                  Size  Used by
rfcomm                 81920  4
vboxnetadp             28672  0
vboxnetflt             28672  0
vboxdrv               516096  2 vboxnetadp,vboxnetflt
ccm                    20480  3
cmac                   16384  2
algif_hash             16384  1
algif_skcipher         16384  1
af_alg                 28672  6 algif_hash,algif_skcipher
bnep                   24576  2
nls_iso8859_1          16384  1
snd_soc_skl           159744  0
snd_soc_sst_ipc        20480  1 snd_soc_skl
snd_soc_sst_dsp        36864  1 snd_soc_skl
snd_hda_ext_core       32768  1 snd_soc_skl
snd_soc_acpi_intel_match    49152  1 snd_soc_skl
snd_soc_acpi           16384  2 snd_soc_acpi_intel_match,snd_soc_skl
snd_hda_codec_hdmi     61440  1
snd_hda_codec_realtek   135168  1
snd_hda_codec_generic    81920  1 snd_hda_codec_realtek
snd_hda_intel          53248  3
snd_intel_dspcfg       28672  2 snd_hda_intel,snd_soc_skl
soundwire_intel        40960  1 snd_intel_dspcfg
soundwire_generic_allocation    16384  1 soundwire_intel
soundwire_cadence      32768  1 soundwire_intel
snd_hda_codec         147456  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
snd_hda_core           94208  7 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_ext_core,snd_hda_codec,snd_hda_codec_realtek,snd_soc_skl
snd_hwdep              16384  1 snd_hda_codec
soundwire_bus          77824  3 soundwire_intel,soundwire_generic_allocation,soundwire_cadence
snd_soc_core          286720  2 soundwire_intel,snd_soc_skl
snd_compress           28672  1 snd_soc_core
ac97_bus               16384  1 snd_soc_core
snd_pcm_dmaengine      16384  1 snd_soc_core
amdgpu               6053888  0
snd_pcm               114688  9 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,soundwire_intel,snd_compress,snd_soc_core,snd_soc_skl,snd_hda_core,snd_pcm_dmaengine
snd_seq_midi           20480  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            36864  1 snd_seq_midi
iommu_v2               24576  1 amdgpu
snd_seq                73728  2 snd_seq_midi,snd_seq_midi_event
gpu_sched              40960  1 amdgpu
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
snd_timer              40960  2 snd_seq,snd_pcm
snd                    94208  19 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_compress,snd_soc_core,snd_pcm,snd_rawmidi
soundcore              16384  1 snd
ath3k                  24576  0
mei_hdcp               24576  0
btusb                  61440  0
btrtl                  24576  1 btusb
btbcm                  16384  1 btusb
intel_rapl_msr         20480  0
btintel                28672  1 btusb
bluetooth             638976  32 btrtl,btintel,btbcm,bnep,ath3k,btusb,rfcomm
x86_pkg_temp_thermal    20480  0
ath9k                 151552  0
dell_laptop            24576  0
intel_powerclamp       20480  0
coretemp               20480  0
kvm_intel             294912  0
ecdh_generic           16384  1 bluetooth
ecc                    32768  1 ecdh_generic
ledtrig_audio          16384  2 snd_hda_codec_generic,dell_laptop
ath9k_common           36864  1 ath9k
uvcvideo               98304  0
dell_smm_hwmon         20480  0
kvm                   819200  1 kvm_intel
crct10dif_pclmul       16384  1
ghash_clmulni_intel    16384  0
aesni_intel           372736  5
rtsx_usb_ms            24576  0
ath9k_hw              483328  2 ath9k_common,ath9k
radeon               1474560  1
crypto_simd            16384  1 aesni_intel
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel
ath                    36864  3 ath9k_common,ath9k,ath9k_hw
memstick               24576  1 rtsx_usb_ms
drm_ttm_helper         16384  2 amdgpu,radeon
mac80211             1024000  1 ath9k
i915                 2297856  20
ttm                    73728  3 amdgpu,radeon,drm_ttm_helper
input_leds             16384  0
cfg80211              888832  4 ath9k_common,ath9k,ath,mac80211
serio_raw              20480  0
drm_kms_helper        237568  3 amdgpu,radeon,i915
glue_helper            16384  1 aesni_intel
rapl                   20480  0
cec                    53248  2 drm_kms_helper,i915
mei_me                 40960  1
intel_cstate           20480  0
libarc4                16384  1 mac80211
dell_wmi               20480  0
dell_smbios            28672  2 dell_wmi,dell_laptop
intel_hid              24576  0
ee1004                 20480  0
dcdbas                 20480  1 dell_smbios
processor_thermal_device    20480  0
efi_pstore             16384  0
rc_core                61440  1 cec
processor_thermal_rfim    16384  1 processor_thermal_device
sparse_keymap          16384  2 intel_hid,dell_wmi
intel_xhci_usb_role_switch    16384  0
processor_thermal_mbox    16384  1 processor_thermal_device
processor_thermal_rapl    20480  1 processor_thermal_device
intel_rapl_common      24576  2 intel_rapl_msr,processor_thermal_rapl
mei                   122880  3 mei_hdcp,mei_me
dell_wmi_descriptor    20480  2 dell_wmi,dell_smbios
joydev                 24576  0
i2c_algo_bit           16384  3 amdgpu,radeon,i915
fb_sys_fops            16384  1 drm_kms_helper
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
wmi_bmof               16384  0
mac_hid                16384  0
int3400_thermal        20480  0
int340x_thermal_zone    20480  1 processor_thermal_device
intel_pch_thermal      20480  0
acpi_thermal_rel       16384  1 int3400_thermal
intel_soc_dts_iosf     20480  1 processor_thermal_device
acpi_pad              184320  0
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
xt_limit               16384  13
xt_addrtype            16384  4
xt_tcpudp              20480  18
xt_conntrack           16384  16
nf_conntrack          147456  1 xt_conntrack
nf_defrag_ipv6         24576  1 nf_conntrack
nf_defrag_ipv4         16384  1 nf_conntrack
sch_fq_codel           20480  2
libcrc32c              16384  1 nf_conntrack
msr                    16384  0
ip6table_filter        16384  1
ip6_tables             32768  53 ip6table_filter
iptable_filter         16384  1
parport_pc             45056  0
bpfilter               16384  0
ppdev                  24576  0
lp                     20480  0
parport                65536  3 parport_pc,lp,ppdev
drm                   548864  13 gpu_sched,drm_kms_helper,amdgpu,radeon,drm_ttm_helper,i915,ttm
ip_tables              32768  9 iptable_filter
x_tables               49152  13 ip6table_filter,xt_conntrack,iptable_filter,xt_LOG,xt_tcpudp,xt_addrtype,ip6t_rt,ip6_tables,ipt_REJECT,ip_tables,xt_limit,xt_hl,ip6t_REJECT
autofs4                45056  2
rtsx_usb_sdmmc         32768  0
rtsx_usb               28672  2 rtsx_usb_sdmmc,rtsx_usb_ms
usbhid                 57344  0
hid_rmi                24576  0
rmi_core               86016  1 hid_rmi
videobuf2_vmalloc      20480  2 rmi_core,uvcvideo
videobuf2_memops       20480  1 videobuf2_vmalloc
videobuf2_v4l2         32768  2 rmi_core,uvcvideo
videobuf2_common       61440  3 rmi_core,videobuf2_v4l2,uvcvideo
videodev              245760  4 rmi_core,videobuf2_v4l2,uvcvideo,videobuf2_common
mc                     57344  4 videodev,videobuf2_v4l2,uvcvideo,videobuf2_common
hid_generic            16384  0
crc32_pclmul           16384  0
ahci                   40960  2
r8169                  77824  0
intel_lpss_pci         20480  0
intel_lpss             16384  1 intel_lpss_pci
idma64                 20480  0
i2c_hid                32768  0
realtek                28672  1
i2c_i801               32768  0
xhci_pci               20480  0
i2c_smbus              20480  1 i2c_i801
wmi                    32768  4 dell_wmi,wmi_bmof,dell_smbios,dell_wmi_descriptor
libahci                36864  1 ahci
psmouse               155648  0
xhci_pci_renesas       20480  1 xhci_pci
virt_dma               20480  1 idma64
hid                   135168  4 i2c_hid,usbhid,hid_generic,hid_rmi
pinctrl_sunrisepoint    28672  0
video                  49152  3 dell_wmi,dell_laptop,i915
```

Thank you

---

### Post by praseodym on 2021-09-08
Link detected: no

Cable broken?

---

### Post by kurt18947 on 2021-09-08
I have an inexpensive TP-Link ethernet-USB adapter for just such occasions. I know it's plug and play. If the built-in ethernet port doesn't work I'll try the USB-ethernet adapter. If the USB adapter works something is going on with the built-in port, either hardware or software. If neither ethernet port works I'd look long and hard at the router/cable. If the machine's port isn't working I might try booting a live USB drive and see if I have ethernet with that. If the live USB ethernet works, there is probably some sort of configuration problem with the installed OS.

---

### Post by iqdesigner on 2021-09-15
I tried with another laptop on same cable/router and network works. So the cable/router works
I put a live CD and still have no network.
I suppose that while my Ethernet card is identified actually is broken. Is this possible?

---

