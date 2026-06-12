---
title: "Ethernet connection problem"
date: 2017-10-30
forum: Networking &amp; Wireless
---

### Post by ordak on 2017-10-30
Hi,

I have two recent problems with Ethernet connection. The problems did not exist a few days ago.


[LIST=1]
[*]Some-times after turning on my ASUS laptop, it takes minutes for Ethernet connection to be established. 
[*]After some minutes of Internet usage, the computer stops "receiving" data, I have to disconnect and connect again. 
[/LIST]

Ubuntu 16.04.3 LTS

---

### Post by TheFu on 2017-10-31
Lacking any other information, I would check the switch port and cables.

---

### Post by praseodym on 2017-10-31
Which hardware is in use?
```

lspci -nnk
lsmod
```

---

### Post by litlesam on 2017-10-31
With little information, you may want to unplug your router ( if you have one ) for 2 min and try again.

I have had this happen a few times over the years.

---

### Post by ordak on 2017-11-01
> **TheFu said:**
> Lacking any other information, I would check the switch port and cables.

It appears your idea does not work well for me.

Some info:

I  am connecting through a modem(router?) With TD_LTE SIM card, fixed   position. My other laptop with Windows 7 OS connecting to this modem  using  WiFi seemed to work fine.

---

### Post by ordak on 2017-11-01
> **praseodym said:**
> Which hardware is in use?
```

lspci -nnk
lsmod
```

```

mehdi@mehdi-X556UQK:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation Device [8086:5904] (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1490]
00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:5916] (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1490]
    Kernel driver in use: i915_bpo
    Kernel modules: i915_bpo
00:04.0 Signal processing controller [1180]: Intel Corporation Skylake Processor Thermal Subsystem [8086:1903] (rev 02)
    Subsystem: ASUSTeK Computer Inc. Skylake Processor Thermal Subsystem [1043:1490]
    Kernel driver in use: proc_thermal
    Kernel modules: processor_thermal_device
00:14.0 USB controller [0c03]: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller [8086:9d2f] (rev 21)
    Subsystem: ASUSTeK Computer Inc. Sunrise Point-LP USB 3.0 xHCI Controller [1043:201f]
    Kernel driver in use: xhci_hcd
00:14.2 Signal processing controller [1180]: Intel Corporation Sunrise Point-LP Thermal subsystem [8086:9d31] (rev 21)
    Subsystem: ASUSTeK Computer Inc. Sunrise Point-LP Thermal subsystem [1043:1490]
00:15.0 Signal processing controller [1180]: Intel Corporation Sunrise Point-LP Serial IO I2C Controller [8086:9d60] (rev 21)
    Subsystem: ASUSTeK Computer Inc. Sunrise Point-LP Serial IO I2C Controller [1043:1490]
    Kernel driver in use: intel-lpss
    Kernel modules: intel_lpss_pci
00:15.1 Signal processing controller [1180]: Intel Corporation Sunrise Point-LP Serial IO I2C Controller [8086:9d61] (rev 21)
    Subsystem: ASUSTeK Computer Inc. Sunrise Point-LP Serial IO I2C Controller [1043:1490]
    Kernel driver in use: intel-lpss
    Kernel modules: intel_lpss_pci
00:16.0 Communication controller [0780]: Intel Corporation Sunrise Point-LP CSME HECI [8086:9d3a] (rev 21)
    Subsystem: ASUSTeK Computer Inc. Sunrise Point-LP CSME HECI [1043:1490]
    Kernel driver in use: mei_me
    Kernel modules: mei_me
00:17.0 SATA controller [0106]: Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode] [8086:9d03] (rev 21)
    Subsystem: ASUSTeK Computer Inc. Sunrise Point-LP SATA Controller [AHCI mode] [1043:1490]
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1c.0 PCI bridge [0604]: Intel Corporation Device [8086:9d10] (rev f1)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.4 PCI bridge [0604]: Intel Corporation Sunrise Point-LP PCI Express Root Port [8086:9d14] (rev f1)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.5 PCI bridge [0604]: Intel Corporation Sunrise Point-LP PCI Express Root Port [8086:9d15] (rev f1)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1f.0 ISA bridge [0601]: Intel Corporation Device [8086:9d58] (rev 21)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1490]
00:1f.2 Memory controller [0580]: Intel Corporation Sunrise Point-LP PMC [8086:9d21] (rev 21)
    Subsystem: ASUSTeK Computer Inc. Sunrise Point-LP PMC [1043:1490]
00:1f.3 Audio device [0403]: Intel Corporation Device [8086:9d71] (rev 21)
    Subsystem: ASUSTeK Computer Inc. Device [1043:11c0]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
00:1f.4 SMBus [0c05]: Intel Corporation Sunrise Point-LP SMBus [8086:9d23] (rev 21)
    Subsystem: ASUSTeK Computer Inc. Sunrise Point-LP SMBus [1043:1490]
    Kernel modules: i2c_i801
01:00.0 3D controller [0302]: NVIDIA Corporation GM108M [GeForce 940MX] [10de:134d] (rev a2)
    Subsystem: ASUSTeK Computer Inc. GM108M [GeForce 940MX] [1043:1490]
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_387_drm, nvidia_387
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:200f]
    Kernel driver in use: r8169
    Kernel modules: r8169
03:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
    Subsystem: Lite-On Communications Inc QCA9565 / AR9565 Wireless Network Adapter [11ad:1823]
    Kernel driver in use: ath9k
    Kernel modules: ath9k



```

```

mehdi@mehdi-X556UQK:~$ lsmod
Module                  Size  Used by
bbswitch               16384  0
rfcomm                 69632  4
bnep                   20480  2
binfmt_misc            20480  1
nvidia_uvm            675840  0
snd_hda_codec_hdmi     53248  1
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
arc4                   16384  2
snd_hda_intel          40960  3
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
snd_hda_core           73728  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
ath9k                 147456  0
i2c_designware_platform    16384  0
i2c_designware_core    20480  1 i2c_designware_platform
asus_nb_wmi            24576  0
asus_wmi               28672  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
mxm_wmi                16384  0
rtsx_usb_ms            20480  0
memstick               20480  1 rtsx_usb_ms
snd_hwdep              16384  1 snd_hda_codec
ath9k_common           36864  1 ath9k
ath9k_hw              466944  2 ath9k_common,ath9k
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
intel_rapl             20480  0
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
kvm_intel             172032  0
mac80211              737280  1 ath9k
kvm                   544768  1 kvm_intel
cfg80211              565248  4 ath,ath9k_common,ath9k,mac80211
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
uvcvideo               90112  0
irqbypass              16384  1 kvm
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
crct10dif_pclmul       16384  0
videobuf2_v4l2         28672  1 uvcvideo
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
videobuf2_core         36864  2 uvcvideo,videobuf2_v4l2
snd_timer              32768  2 snd_pcm,snd_seq
v4l2_common            16384  1 videobuf2_v4l2
videodev              176128  4 uvcvideo,v4l2_common,videobuf2_core,videobuf2_v4l2
snd                    81920  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
aesni_intel           167936  0
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
cryptd                 20480  3 ghash_clmulni_intel,aesni_intel,ablk_helper
soundcore              16384  1 snd
input_leds             16384  0
serio_raw              16384  0
media                  24576  2 uvcvideo,videodev
ath3k                  20480  0
btusb                  45056  0
hci_uart               77824  0
btrtl                  16384  1 btusb
btqca                  16384  1 hci_uart
btbcm                  16384  2 btusb,hci_uart
acpi_als               16384  0
kfifo_buf              16384  1 acpi_als
btintel                16384  2 btusb,hci_uart
mei_me                 36864  0
bluetooth             520192  34 bnep,ath3k,btbcm,btqca,btrtl,btusb,hci_uart,rfcomm,btintel
mei                    98304  1 mei_me
industrialio           61440  2 acpi_als,kfifo_buf
elan_i2c               36864  0
shpchp                 36864  0
idma64                 20480  0
virt_dma               16384  1 idma64
intel_lpss_acpi        16384  0
intel_lpss_pci         16384  0
wmi                    20480  2 mxm_wmi,asus_wmi
intel_lpss             16384  2 intel_lpss_pci,intel_lpss_acpi
int3403_thermal        16384  0
processor_thermal_device    16384  0
int340x_thermal_zone    16384  2 processor_thermal_device,int3403_thermal
intel_soc_dts_iosf     16384  1 processor_thermal_device
int3400_thermal        16384  0
acpi_thermal_rel       16384  1 int3400_thermal
tpm_crb                16384  0
acpi_pad               24576  0
mac_hid                16384  0
ip6t_REJECT            16384  1
nf_reject_ipv6         16384  1 ip6t_REJECT
nf_log_ipv6            16384  5
xt_hl                  16384  22
ip6t_rt                16384  3
nf_conntrack_ipv6      20480  8
nf_defrag_ipv6         36864  1 nf_conntrack_ipv6
ipt_REJECT             16384  1
nf_reject_ipv4         16384  1 ipt_REJECT
nf_log_ipv4            16384  5
nf_log_common          16384  2 nf_log_ipv4,nf_log_ipv6
xt_LOG                 16384  10
xt_limit               16384  13
xt_tcpudp              16384  18
xt_addrtype            16384  4
nf_conntrack_ipv4      16384  8
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
xt_conntrack           16384  16
ip6table_filter        16384  1
ip6_tables             28672  1 ip6table_filter
nf_conntrack_netbios_ns    16384  0
nf_conntrack_broadcast    16384  1 nf_conntrack_netbios_ns
nf_nat_ftp             16384  0
nf_nat                 24576  1 nf_nat_ftp
nf_conntrack_ftp       20480  1 nf_nat_ftp
nf_conntrack          106496  8 nf_nat_ftp,nf_conntrack_netbios_ns,nf_nat,xt_conntrack,nf_conntrack_broadcast,nf_conntrack_ftp,nf_conntrack_ipv4,nf_conntrack_ipv6
iptable_filter         16384  1
ip_tables              24576  1 iptable_filter
x_tables               36864  13 ip6table_filter,xt_hl,ip_tables,xt_tcpudp,xt_limit,xt_conntrack,xt_LOG,iptable_filter,ip6t_rt,ipt_REJECT,ip6_tables,xt_addrtype,ip6t_REJECT
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
rtsx_usb_sdmmc         28672  0
rtsx_usb               24576  2 rtsx_usb_sdmmc,rtsx_usb_ms
hid_generic            16384  0
usbhid                 49152  0
nvidia_drm             49152  4
nvidia_modeset        897024  3 nvidia_drm
i915_bpo             1306624  3
nvidia              13819904  168 nvidia_modeset,nvidia_uvm
intel_ips              20480  1 i915_bpo
i2c_algo_bit           16384  1 i915_bpo
drm_kms_helper        155648  2 i915_bpo,nvidia_drm
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
r8169                  81920  0
drm                   364544  6 i915_bpo,drm_kms_helper,nvidia_drm
ahci                   36864  3
mii                    16384  1 r8169
libahci                32768  1 ahci
i2c_hid                20480  0
hid                   118784  3 i2c_hid,hid_generic,usbhid
video                  40960  2 i915_bpo,asus_wmi
pinctrl_sunrisepoint    28672  0
pinctrl_intel          20480  1 pinctrl_sunrisepoint
fjes                   28672  0
mehdi@mehdi-X556UQK:~$ 



```

---

### Post by TheFu on 2017-11-01
How is the ubuntu machine connected to the modem?  PCMCIA?  USB?

---

### Post by ordak on 2017-11-01
> **TheFu said:**
> How is the ubuntu machine connected to the modem?  PCMCIA?  USB?

LAN ports, LAN cable.

---

### Post by ordak on 2017-11-06
> **TheFu said:**
> How is the ubuntu machine connected to the modem?  PCMCIA?  USB?

I could try WiFi connection to Ubuntu laptop, but that would be a work-around not a solution.

Bump.

---

### Post by TheFu on 2017-11-06
```
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:200f]
    Kernel driver in use: r8169
    Kernel modules: r8169

```
Is a hint where to start.  There have been issues with the r8169 driver on RTL8111/8168/8411 PCI Express Gigabit Ethernet devices.  A little google over that is where I'd start.

I always prefer Intel PRO/1000 NICs over Realtek.

---

### Post by ordak on 2017-11-07
> **TheFu said:**
> ```
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:200f]
    Kernel driver in use: r8169
    Kernel modules: r8169

```
Is a hint where to start.  There have been issues with the r8169 driver on RTL8111/8168/8411 PCI Express Gigabit Ethernet devices.  A little google over that is where I'd start.

I always prefer Intel PRO/1000 NICs over Realtek.

I followed [this link]("https://unixblogger.com/2016/08/11/how-to-get-your-realtek-rtl8111rtl8168-working-updated-guide/"). I tried:

```
sudo apt install r8168-dkms
```

Now I get:

```
mehdi@mehdi-X556UQK:~$ dkms status
bbswitch, 0.8, 4.4.0-98-generic, x86_64: installed
nvidia-387, 387.12, 4.4.0-98-generic, x86_64: installed
r8168, 8.041.00, 4.4.0-98-generic, x86_64: installed
```

But the problem still persists. What can I do now ?

---

### Post by praseodym on 2017-11-07
Please check

```
lsmod
```

---

### Post by ordak on 2017-11-08
> **praseodym said:**
> Please check

```
lsmod
```

```
mehdi@mehdi-X556UQK:~$ lsmod
Module                  Size  Used by
rfcomm                 69632  4
bnep                   20480  2
bbswitch               16384  0
binfmt_misc            20480  1
nvidia_uvm            675840  0
snd_hda_codec_hdmi     53248  1
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
snd_hda_intel          40960  3
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
snd_hda_core           73728  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
i2c_designware_platform    16384  0
snd_hwdep              16384  1 snd_hda_codec
i2c_designware_core    20480  1 i2c_designware_platform
asus_nb_wmi            24576  0
mxm_wmi                16384  0
asus_wmi               28672  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
arc4                   16384  2
ath9k                 147456  0
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
ath9k_common           36864  1 ath9k
ath9k_hw              466944  2 ath9k_common,ath9k
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
mac80211              737280  1 ath9k
kvm_intel             172032  0
kvm                   544768  1 kvm_intel
cfg80211              565248  4 ath,ath9k_common,ath9k,mac80211
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
aesni_intel           167936  0
snd_timer              32768  2 snd_pcm,snd_seq
snd                    81920  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
rtsx_usb_ms            20480  0
memstick               20480  1 rtsx_usb_ms
soundcore              16384  1 snd
cryptd                 20480  3 ghash_clmulni_intel,aesni_intel,ablk_helper
input_leds             16384  0
serio_raw              16384  0
hci_uart               77824  0
ath3k                  20480  0
btusb                  45056  0
uvcvideo               90112  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         28672  1 uvcvideo
videobuf2_core         36864  2 uvcvideo,videobuf2_v4l2
v4l2_common            16384  1 videobuf2_v4l2
btrtl                  16384  1 btusb
btbcm                  16384  2 btusb,hci_uart
btqca                  16384  1 hci_uart
btintel                16384  2 btusb,hci_uart
bluetooth             520192  34 bnep,ath3k,btbcm,btqca,btrtl,btusb,hci_uart,rfcomm,btintel
videodev              176128  4 uvcvideo,v4l2_common,videobuf2_core,videobuf2_v4l2
media                  24576  2 uvcvideo,videodev
mei_me                 36864  0
acpi_als               16384  0
kfifo_buf              16384  1 acpi_als
mei                    98304  1 mei_me
industrialio           61440  2 acpi_als,kfifo_buf
elan_i2c               36864  0
idma64                 20480  0
wmi                    20480  2 mxm_wmi,asus_wmi
virt_dma               16384  1 idma64
int3403_thermal        16384  0
processor_thermal_device    16384  0
intel_lpss_acpi        16384  0
intel_lpss_pci         16384  0
intel_lpss             16384  2 intel_lpss_pci,intel_lpss_acpi
shpchp                 36864  0
mac_hid                16384  0
tpm_crb                16384  0
acpi_pad               24576  0
int3400_thermal        16384  0
int340x_thermal_zone    16384  2 processor_thermal_device,int3403_thermal
acpi_thermal_rel       16384  1 int3400_thermal
intel_soc_dts_iosf     16384  1 processor_thermal_device
ip6t_REJECT            16384  1
nf_reject_ipv6         16384  1 ip6t_REJECT
nf_log_ipv6            16384  5
xt_hl                  16384  22
ip6t_rt                16384  3
nf_conntrack_ipv6      20480  8
nf_defrag_ipv6         36864  1 nf_conntrack_ipv6
ipt_REJECT             16384  1
nf_reject_ipv4         16384  1 ipt_REJECT
nf_log_ipv4            16384  5
nf_log_common          16384  2 nf_log_ipv4,nf_log_ipv6
xt_LOG                 16384  10
xt_limit               16384  13
xt_tcpudp              16384  18
xt_addrtype            16384  4
nf_conntrack_ipv4      16384  8
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
xt_conntrack           16384  16
ip6table_filter        16384  1
ip6_tables             28672  1 ip6table_filter
nf_conntrack_netbios_ns    16384  0
nf_conntrack_broadcast    16384  1 nf_conntrack_netbios_ns
nf_nat_ftp             16384  0
nf_nat                 24576  1 nf_nat_ftp
nf_conntrack_ftp       20480  1 nf_nat_ftp
nf_conntrack          106496  8 nf_nat_ftp,nf_conntrack_netbios_ns,nf_nat,xt_conntrack,nf_conntrack_broadcast,nf_conntrack_ftp,nf_conntrack_ipv4,nf_conntrack_ipv6
iptable_filter         16384  1
ip_tables              24576  1 iptable_filter
x_tables               36864  13 ip6table_filter,xt_hl,ip_tables,xt_tcpudp,xt_limit,xt_conntrack,xt_LOG,iptable_filter,ip6t_rt,ipt_REJECT,ip6_tables,xt_addrtype,ip6t_REJECT
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
rtsx_usb_sdmmc         28672  0
rtsx_usb               24576  2 rtsx_usb_sdmmc,rtsx_usb_ms
hid_generic            16384  0
usbhid                 49152  0
nvidia_drm             49152  4
nvidia_modeset        897024  3 nvidia_drm
i915_bpo             1306624  3
nvidia              13819904  168 nvidia_modeset,nvidia_uvm
intel_ips              20480  1 i915_bpo
i2c_algo_bit           16384  1 i915_bpo
drm_kms_helper        155648  2 i915_bpo,nvidia_drm
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   364544  6 i915_bpo,drm_kms_helper,nvidia_drm
ahci                   36864  3
r8168                 487424  0
libahci                32768  1 ahci
i2c_hid                20480  0
hid                   118784  3 i2c_hid,hid_generic,usbhid
video                  40960  2 i915_bpo,asus_wmi
pinctrl_sunrisepoint    28672  0
pinctrl_intel          20480  1 pinctrl_sunrisepoint
fjes                   28672  0
mehdi@mehdi-X556UQK:~$ 
```

---

### Post by praseodym on 2017-11-08
Why do you use a firewall? Deactivate it, if it is active in your router thats enough

---

### Post by ordak on 2017-11-11
> **praseodym said:**
> Why do you use a firewall? Deactivate it, if it is active in your router thats enough

Before doing what you say, can I do this :

```
sudo apt remove r8168-dkms

sudo apt install r8411-dkms

dkms status

```

Since this may give better functionality of Ethernet device.

---

### Post by ordak on 2017-11-13
> **praseodym said:**
> Why do you use a firewall? Deactivate it, if it is active in your router thats enough

First of all, it seems the r8411 driver is not supplied on Ubuntu site yet. So I stick to r8168. 

Now, I disabled the _Gufw_ firewall, by setting it's profile to _Home_. The router's firewall is on. Unfortunately I still have idle connection (number 2 in my first post in this thread) problem.

---

### Post by ordak on 2017-11-16
I tried to use WiFi of this router on this Ubuntu laptop. That did not work. Getting "Wi-Fi Network Authentication Required" message, again and again. Both with LAN connected and disconnected. Note that I use this WiFi on two Windows 7 laptops without this problem.

Bump.

---

### Post by ordak on 2017-11-20
Bump.

---

