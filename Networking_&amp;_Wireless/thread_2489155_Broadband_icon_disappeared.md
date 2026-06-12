---
title: "Broadband icon disappeared"
date: 2023-07-20
forum: Networking &amp; Wireless
---

### Post by dfrey76 on 2023-07-20
Hi all, I am trying to solve a problem on a Dell Latitude 7420, running Ubuntu 22.04.2 LTS.  All
of a sudden the broadband menu item disappeared from the menu.  I
checked and the Snapdragon modem is present in lsusb, however it isn't
there when I run nmcli, and mmcli gives a no-modem-found error.


I tried booting from a live ubuntu CD and the modem is correctly seen
by network manager, so I suspect this is due to some misconfiguration
or some update that broke things. 

Does anybody have any idea of the next steps to debug this?

Thanks!



Here are the outputs of nmcli, lsmod, and mmcli




**** nmcli**
```
enx747827e6f7de: connected to Wired connection 1
    "Realtek RTL8153"
    ethernet (r8152), 74:78:27:E6:F7:DE, hw, mtu 1500
    ip4 default
    inet4 131.254.11.148/17
    route4 131.254.0.0/17 metric 100
    route4 169.254.0.0/16 metric 1000
    route4 default via 131.254.1.1 metric 100
    inet6 fe80::1ca4:a34e:844c:7470/64
    route6 fe80::/64 metric 1024


wlp0s20f3: connected to iwifi-guest
    "Intel 6 AX201"
    wifi (iwlwifi), 7C:50:79:8B:8A:BC, hw, mtu 1500
    inet4 131.254.253.180/24
    route4 131.254.253.0/24 metric 600
    route4 default via 131.254.253.254 metric 20600
    inet6 fe80::2601:91c5:4b9e:c8f3/64
    route6 fe80::/64 metric 1024


docker0: connected (externally) to docker0
    "docker0"
    bridge, 02:42:21:1B:DF:C6, sw, mtu 1500
    inet4 172.17.0.1/16
    route4 172.17.0.0/16 metric 0


p2p-dev-wlp0s20f3: disconnected
    "p2p-dev-wlp0s20f3"
    wifi-p2p, hw


lo: unmanaged
    "lo"
    loopback (unknown), 00:00:00:00:00:00, sw, mtu 65536


DNS configuration:
    servers: 131.254.130.100
    domains: irisa.fr rennes.inria.fr inria.fr ad.inria.fr insa-rennes.fr
    interface: enx747827e6f7de


    servers: 131.254.253.254
    domains: rennes.inria.fr
    interface: wlp0s20f3


Use "nmcli device show" to get complete information about known devices and
"nmcli connection show" to get an overview on active connection profiles.


Consult nmcli(1) and nmcli-examples(7) manual pages for complete usage details.

```
**** lsmod **
```

Module                  Size  Used by
tls                   102400  0
snd_usb_audio         315392  3
snd_usbmidi_lib        36864  1 snd_usb_audio
r8153_ecm              16384  0
r8152                 110592  1 r8153_ecm
rfcomm                 81920  4
ppp_deflate            16384  0
bsd_comp               16384  0
ppp_async              20480  0
xt_conntrack           16384  1
nft_chain_nat          16384  3
xt_MASQUERADE          20480  1
nf_nat                 49152  2 nft_chain_nat,xt_MASQUERADE
nf_conntrack_netlink    49152  0
nf_conntrack          151552  4 xt_conntrack,nf_nat,nf_conntrack_netlink,xt_MASQUERADE
nf_defrag_ipv6         24576  1 nf_conntrack
nf_defrag_ipv4         16384  1 nf_conntrack
xfrm_user              36864  1
xfrm_algo              16384  1 xfrm_user
nft_counter            16384  15
xt_addrtype            16384  2
nft_compat             20480  4
nf_tables             212992  43 nft_compat,nft_counter,nft_chain_nat
libcrc32c              16384  3 nf_conntrack,nf_nat,nf_tables
nfnetlink              20480  4 nft_compat,nf_conntrack_netlink,nf_tables
br_netfilter           28672  0
bridge                266240  1 br_netfilter
stp                    16384  1 bridge
llc                    16384  2 bridge,stp
cmac                   16384  3
algif_hash             16384  1
algif_skcipher         16384  1
af_alg                 28672  6 algif_hash,algif_skcipher
bnep                   24576  2
overlay               126976  0
snd_hda_codec_hdmi     61440  1
binfmt_misc            24576  1
dell_rbtn              20480  0
snd_sof_pci_intel_tgl    16384  0
snd_sof_intel_hda_common    98304  1 snd_sof_pci_intel_tgl
soundwire_intel        40960  1 snd_sof_intel_hda_common
soundwire_generic_allocation    16384  1 soundwire_intel
soundwire_cadence      32768  1 soundwire_intel
snd_sof_intel_hda      20480  1 snd_sof_intel_hda_common
snd_sof_pci            20480  2 snd_sof_intel_hda_common,snd_sof_pci_intel_tgl
snd_sof_xtensa_dsp     16384  1 snd_sof_intel_hda_common
snd_sof               131072  2 snd_sof_pci,snd_sof_intel_hda_common
snd_soc_hdac_hda       24576  1 snd_sof_intel_hda_common
snd_hda_ext_core       32768  3 snd_sof_intel_hda_common,snd_soc_hdac_hda,snd_sof_intel_hda
snd_soc_acpi_intel_match    57344  2 snd_sof_intel_hda_common,snd_sof_pci_intel_tgl
snd_soc_acpi           16384  2 snd_soc_acpi_intel_match,snd_sof_intel_hda_common
soundwire_bus          81920  3 soundwire_intel,soundwire_generic_allocation,soundwire_cadence
snd_soc_core          290816  4 soundwire_intel,snd_sof,snd_sof_intel_hda_common,snd_soc_hdac_hda
snd_ctl_led            24576  0
snd_hda_codec_realtek   147456  1
snd_compress           28672  1 snd_soc_core
snd_hda_codec_generic    81920  1 snd_hda_codec_realtek
mei_hdcp               24576  0
ac97_bus               16384  1 snd_soc_core
snd_pcm_dmaengine      16384  1 snd_soc_core
dell_laptop            24576  0
intel_tcc_cooling      16384  0
snd_hda_intel          53248  3
intel_rapl_msr         20480  0
snd_intel_dspcfg       28672  2 snd_hda_intel,snd_sof_intel_hda_common
x86_pkg_temp_thermal    20480  0
snd_intel_sdw_acpi     20480  2 snd_sof_intel_hda_common,snd_intel_dspcfg
intel_powerclamp       20480  0
snd_hda_codec         147456  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek,snd_soc_hdac_hda
snd_hda_core           94208  9 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_ext_core,snd_hda_codec,snd_hda_codec_realtek,snd_sof_intel_hda_common,snd_soc_hdac_hda,snd_sof_intel_hda
coretemp               20480  0
nls_iso8859_1          16384  1
snd_hwdep              16384  2 snd_usb_audio,snd_hda_codec
kvm_intel             311296  0
snd_pcm               122880  12 snd_hda_codec_hdmi,snd_hda_intel,snd_usb_audio,snd_hda_codec,soundwire_intel,snd_sof,snd_sof_intel_hda_common,snd_compress,snd_soc_core,snd_hda_core,snd_pcm_dmaengine
iwlmvm                421888  0
kvm                   880640  1 kvm_intel
snd_seq_midi           20480  0
mac80211             1028096  1 iwlmvm
snd_seq_midi_event     16384  1 snd_seq_midi
joydev                 28672  0
cdc_mbim               20480  0
snd_rawmidi            40960  2 snd_seq_midi,snd_usbmidi_lib
cdc_ncm                40960  1 cdc_mbim
intel_cstate           20480  0
libarc4                16384  1 mac80211
snd_seq                73728  2 snd_seq_midi,snd_seq_midi_event
btusb                  65536  0
cdc_ether              20480  2 r8153_ecm,cdc_ncm
input_leds             16384  0
uvcvideo              106496  0
qmi_wwan               36864  0
cdc_wdm                28672  2 cdc_mbim,qmi_wwan
videobuf2_vmalloc      20480  1 uvcvideo
videobuf2_memops       20480  1 videobuf2_vmalloc
btrtl                  24576  1 btusb
videobuf2_v4l2         32768  1 uvcvideo
iwlwifi               389120  1 iwlmvm
btbcm                  24576  1 btusb
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
dell_wmi               20480  1 dell_laptop
serio_raw              20480  0
snd_timer              40960  2 snd_seq,snd_pcm
option                 61440  0
usbnet                 49152  5 cdc_mbim,r8153_ecm,cdc_ncm,qmi_wwan,cdc_ether
videobuf2_common       61440  4 videobuf2_vmalloc,videobuf2_v4l2,uvcvideo,videobuf2_memops
btintel                36864  1 btusb
ledtrig_audio          16384  5 snd_ctl_led,snd_hda_codec_generic,dell_wmi,snd_sof,dell_laptop
usb_wwan               24576  1 option
mii                    20480  2 usbnet,r8152
bluetooth             651264  33 btrtl,btintel,btbcm,bnep,btusb,rfcomm
dell_smbios            28672  2 dell_wmi,dell_laptop
hid_sensor_als         20480  1
hid_sensor_custom_intel_hinge    16384  0
usbserial              57344  2 usb_wwan,option
videodev              237568  3 videobuf2_v4l2,uvcvideo,videobuf2_common
hid_sensor_accel_3d    20480  0
hid_sensor_gyro_3d     20480  0
snd                    94208  27 snd_ctl_led,snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_usb_audio,snd_usbmidi_lib,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_compress,snd_soc_core,snd_pcm,snd_rawmidi
processor_thermal_device_pci_legacy    16384  0
processor_thermal_device    20480  1 processor_thermal_device_pci_legacy
dcdbas                 20480  1 dell_smbios
mc                     57344  5 videodev,snd_usb_audio,videobuf2_v4l2,uvcvideo,videobuf2_common
hid_sensor_trigger     20480  8 hid_sensor_gyro_3d,hid_sensor_custom_intel_hinge,hid_sensor_als,hid_sensor_accel_3d
dell_wmi_sysman        40960  0
industrialio_triggered_buffer    16384  1 hid_sensor_trigger
soundcore              16384  2 snd_ctl_led,snd
kfifo_buf              16384  1 industrialio_triggered_buffer
mei_me                 40960  1
dell_wmi_descriptor    20480  2 dell_wmi,dell_smbios
hid_sensor_iio_common    20480  5 hid_sensor_gyro_3d,hid_sensor_trigger,hid_sensor_custom_intel_hinge,hid_sensor_als,hid_sensor_accel_3d
processor_thermal_rfim    16384  1 processor_thermal_device
ecdh_generic           16384  2 bluetooth
firmware_attributes_class    16384  1 dell_wmi_sysman
wmi_bmof               16384  0
cfg80211              892928  3 iwlmvm,iwlwifi,mac80211
industrialio           86016  8 industrialio_triggered_buffer,hid_sensor_gyro_3d,hid_sensor_trigger,hid_sensor_custom_intel_hinge,kfifo_buf,hid_sensor_als,hid_sensor_accel_3d
hid_multitouch         28672  0
processor_thermal_mbox    16384  2 processor_thermal_rfim,processor_thermal_device
ecc                    36864  1 ecdh_generic
mei                   131072  3 mei_hdcp,mei_me
processor_thermal_rapl    20480  1 processor_thermal_device
intel_rapl_common      24576  2 intel_rapl_msr,processor_thermal_rapl
ucsi_acpi              16384  0
intel_pmt_telemetry    16384  0
cros_ec_ishtp          20480  0
typec_ucsi             40960  1 ucsi_acpi
intel_pmt_class        16384  1 intel_pmt_telemetry
intel_soc_dts_iosf     20480  1 processor_thermal_device_pci_legacy
igen6_edac             24576  0
typec                  57344  1 typec_ucsi
cros_ec                20480  1 cros_ec_ishtp
int3403_thermal        20480  0
soc_button_array       20480  0
int340x_thermal_zone    20480  2 int3403_thermal,processor_thermal_device
mac_hid                16384  0
intel_hid              24576  0
int3400_thermal        20480  0
acpi_thermal_rel       16384  1 int3400_thermal
sparse_keymap          16384  2 intel_hid,dell_wmi
acpi_pad              184320  0
acpi_tad               16384  0
sch_fq_codel           20480  2
msr                    16384  0
parport_pc             45056  0
ppdev                  24576  0
lp                     20480  0
parport                65536  3 parport_pc,lp,ppdev
ramoops                28672  0
pstore_blk             16384  0
reed_solomon           24576  1 ramoops
pstore_zone            28672  1 pstore_blk
efi_pstore             16384  0
ip_tables              32768  0
x_tables               49152  5 xt_conntrack,nft_compat,xt_addrtype,ip_tables,xt_MASQUERADE
autofs4                45056  2
dm_crypt               53248  1
usbhid                 57344  0
hid_sensor_custom      24576  0
hid_sensor_hub         24576  7 hid_sensor_gyro_3d,hid_sensor_trigger,hid_sensor_iio_common,hid_sensor_custom_intel_hinge,hid_sensor_als,hid_sensor_accel_3d,hid_sensor_custom
intel_ishtp_loader     20480  0
intel_ishtp_hid        24576  0
hid_generic            16384  0
rtsx_pci_sdmmc         28672  0
i915                 2478080  34
nvme                   49152  3
i2c_algo_bit           16384  1 i915
crct10dif_pclmul       16384  1
ttm                    69632  1 i915
crc32_pclmul           16384  0
drm_kms_helper        258048  1 i915
ghash_clmulni_intel    16384  0
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
psmouse               155648  0
sysimgblt              16384  1 drm_kms_helper
aesni_intel           376832  6
fb_sys_fops            16384  1 drm_kms_helper
cec                    53248  2 drm_kms_helper,i915
rc_core                61440  1 cec
rtsx_pci               94208  1 rtsx_pci_sdmmc
i2c_i801               36864  0
crypto_simd            16384  1 aesni_intel
drm                   557056  16 drm_kms_helper,i915,ttm
intel_lpss_pci         24576  0
intel_ish_ipc          24576  0
cryptd                 24576  4 crypto_simd,ghash_clmulni_intel
intel_lpss             16384  1 intel_lpss_pci
xhci_pci               24576  0
thunderbolt           278528  0
i2c_smbus              20480  1 i2c_i801
intel_ishtp            53248  4 cros_ec_ishtp,intel_ishtp_hid,intel_ish_ipc,intel_ishtp_loader
nvme_core             131072  4 nvme
idma64                 20480  0
xhci_pci_renesas       20480  1 xhci_pci
intel_pmt              16384  0
wmi                    32768  5 dell_wmi_sysman,dell_wmi,wmi_bmof,dell_smbios,dell_wmi_descriptor
i2c_hid_acpi           16384  0
i2c_hid                28672  1 i2c_hid_acpi
hid                   139264  6 i2c_hid,usbhid,hid_multitouch,hid_sensor_hub,intel_ishtp_hid,hid_generic
video                  53248  3 dell_wmi,dell_laptop,i915
pinctrl_tigerlake      32768  1

```and
**** mmcli**


```
for i in `seq 0 8`; do sudo mmcli -m $i;done


error: couldn't find modem
error: couldn't find modem
error: couldn't find modem
error: couldn't find modem
error: couldn't find modem
error: couldn't find modem
error: couldn't find modem
error: couldn't find modem
error: couldn't find modem

```

---

