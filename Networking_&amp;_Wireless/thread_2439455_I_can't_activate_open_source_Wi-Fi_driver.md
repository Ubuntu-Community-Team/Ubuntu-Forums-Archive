---
title: "I can't activate open source Wi-Fi driver"
date: 2020-03-28
forum: Networking &amp; Wireless
---

### Post by kevin-2020 on 2020-03-28
I'm Japanese man who are about to entrance University, so if my English is little strange, please excuse me.
I can't install Wi-Fi driver in my Ubuntu 18.04.4 LTS PC because "Use Open source driver" option is unable. (Picture 1)
And I can select the option: "continue using manual install driver", but I can't push Revert button. That's why when I reopen the window, nothing is changed. (Picture 2)
And when I typed "ubnutu-drivers devices" on terminal, "manual_install:True" is written there. (Picture 3)
Please teach me how to activate Wi-Fi.[IMG]http://sendanywhe.re/C593IJWS[/IMG][IMG]http://sendanywhe.re/C593IJWS[/IMG]

- Spec details -
PC : HP ENVY aq-1005tu
OS : Windows 10 PRO & Ubuntu 18.04.4 LTS (Dual boot)
CPU : intel core i5-10210U[IMG]http://sendanywhe.re/C593IJWS[/IMG]
Wi-Fi : intel Wireless-AC 9560

P.S.
I can use Bluetooth on Ubuntu from OS installation.
"secure boot" turns on in Ubuntu.
[IMG]https://box.c.yimg.jp/res/box-l-h43ena5tc4mx264sfay7347rua-1001?uid=a05854e1-60f3-428f-8881-f170de2d7ffa&etag=b9cf4c983e58a4a97a418fc29d50b1fb[/IMG]

---

### Post by Andrew F in Australia on 2020-03-28
HI Kevin,

The AC9560 driver works well in Ubuntu 19.10.

I'm in Windows at the moment, will boot across into Ubuntu and let you know the settings.

Regards,

A

---

### Post by Andrew F in Australia on 2020-03-28
Hi Kevin,

No problems with your English - I wish I could speak more than one language.

Details of the driver you need are here:

[https://www.intel.com/content/www/us/en/support/articles/000005511/network-and-i-o/wireless-networking.html](https://www.intel.com/content/www/us/en/support/articles/000005511/network-and-i-o/wireless-networking.html)

Make sure your kernel is newer than 4.14
(uname -a will give it to you, my machine has 5.3.0-42 installed) 

Maybe download and run the*.tgz from the above hyperlink to make sure it works.

Good luck,

A

See below for full settings

```
----------uname -a output ----------------
Linux horace-GE75-Raider-9SE 5.3.0-42-generic #34-Ubuntu SMP Fri Feb 28 05:49:40 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

----------------- lsmod output below ----------------------------
Module                  Size  Used by
rfcomm                 81920  4
ccm                    20480  6
bnep                   24576  2
nvidia_uvm            913408  0
intel_rapl_msr         20480  0
intel_rapl_common      24576  1 intel_rapl_msr
nvidia_drm             49152  8
x86_pkg_temp_thermal    20480  0
nvidia_modeset       1122304  9 nvidia_drm
intel_powerclamp       20480  0
coretemp               20480  0
snd_hda_codec_hdmi     61440  2
snd_hda_codec_realtek   118784  1
kvm_intel             278528  0
snd_hda_codec_generic    81920  1 snd_hda_codec_realtek
ledtrig_audio          16384  2 snd_hda_codec_generic,snd_hda_codec_realtek
kvm                   659456  1 kvm_intel
irqbypass              16384  1 kvm
nvidia              19517440  399 nvidia_uvm,nvidia_modeset
nls_iso8859_1          16384  1
sof_pci_dev            20480  0
snd_sof_intel_hda_common    73728  1 sof_pci_dev
snd_sof_intel_hda      20480  1 snd_sof_intel_hda_common
snd_sof_intel_byt      24576  1 sof_pci_dev
snd_sof_intel_ipc      20480  1 snd_sof_intel_byt
crct10dif_pclmul       16384  1
snd_sof               102400  4 snd_sof_intel_hda_common,snd_sof_intel_byt,snd_sof_intel_ipc,sof_pci_dev
crc32_pclmul           16384  0
snd_sof_xtensa_dsp     16384  1 sof_pci_dev
snd_soc_skl           106496  0
ghash_clmulni_intel    16384  0
snd_soc_hdac_hda       24576  2 snd_sof_intel_hda_common,snd_soc_skl
snd_hda_ext_core       32768  4 snd_sof_intel_hda_common,snd_soc_hdac_hda,snd_soc_skl,snd_sof_intel_hda
snd_soc_skl_ipc        65536  1 snd_soc_skl
iwlmvm                401408  0
snd_soc_sst_ipc        20480  1 snd_soc_skl_ipc
snd_soc_sst_dsp        36864  1 snd_soc_skl_ipc
snd_soc_acpi_intel_match    28672  3 snd_sof_intel_hda_common,sof_pci_dev,snd_soc_skl
snd_soc_acpi           16384  3 snd_soc_acpi_intel_match,sof_pci_dev,snd_soc_skl
mac80211              851968  1 iwlmvm
i915                 1949696  4
snd_soc_core          241664  4 snd_sof,snd_sof_intel_hda_common,snd_soc_hdac_hda,snd_soc_skl
snd_seq_midi           20480  0
snd_compress           24576  1 snd_soc_core
snd_seq_midi_event     16384  1 snd_seq_midi
ac97_bus               16384  1 snd_soc_core
uvcvideo               98304  0
snd_pcm_dmaengine      16384  1 snd_soc_core
snd_rawmidi            36864  1 snd_seq_midi
snd_hda_intel          49152  8
videobuf2_vmalloc      20480  1 uvcvideo
libarc4                16384  1 mac80211
videobuf2_memops       20480  1 videobuf2_vmalloc
snd_intel_nhlt         20480  2 snd_hda_intel,snd_soc_skl
videobuf2_v4l2         24576  1 uvcvideo
snd_hda_codec         131072  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek,snd_soc_hdac_hda
aesni_intel           372736  4
btusb                  57344  0
snd_seq                69632  2 snd_seq_midi,snd_seq_midi_event
btrtl                  20480  1 btusb
videobuf2_common       53248  2 videobuf2_v4l2,uvcvideo
snd_hda_core           90112  10 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_ext_core,snd_hda_codec,snd_hda_codec_realtek,snd_sof_intel_hda_common,snd_soc_hdac_hda,snd_soc_skl,snd_sof_intel_hda
iwlwifi               348160  1 iwlmvm
snd_hwdep              20480  1 snd_hda_codec
rtsx_usb_ms            24576  0
drm_kms_helper        184320  2 nvidia_drm,i915
aes_x86_64             20480  1 aesni_intel
btbcm                  16384  1 btusb
crypto_simd            16384  1 aesni_intel
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
videodev              208896  3 videobuf2_v4l2,uvcvideo,videobuf2_common
mei_hdcp               24576  0
input_leds             16384  0
btintel                24576  1 btusb
snd_pcm               106496  10 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_ext_core,snd_hda_codec,snd_sof,snd_sof_intel_hda_common,snd_soc_core,snd_soc_skl,snd_hda_core,snd_pcm_dmaengine
cryptd                 24576  2 crypto_simd,ghash_clmulni_intel
glue_helper            16384  1 aesni_intel
ucsi_ccg               20480  0
intel_cstate           20480  0
gpio_keys              20480  0
intel_rapl_perf        20480  0
typec_ucsi             40960  1 ucsi_ccg
msi_wmi                20480  0
wmi_bmof               16384  0
mxm_wmi                16384  0
drm                   491520  12 drm_kms_helper,nvidia_drm,i915
ipmi_devintf           20480  0
serio_raw              20480  0
sparse_keymap          16384  1 msi_wmi
memstick               20480  1 rtsx_usb_ms
snd_timer              36864  2 snd_seq,snd_pcm
joydev                 28672  0
bluetooth             581632  31 btrtl,btintel,btbcm,bnep,btusb,rfcomm
typec                  45056  1 typec_ucsi
mc                     53248  4 videodev,videobuf2_v4l2,uvcvideo,videobuf2_common
ipmi_msghandler       106496  2 ipmi_devintf,nvidia
i2c_algo_bit           16384  1 i915
snd                    90112  29https://www.intel.com/content/www/us/en/support/articles/000005511/network-and-i-o/wireless-networking.html snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_compress,snd_soc_core,snd_pcm,snd_rawmidi
fb_sys_fops            16384  1 drm_kms_helper
syscopyarea            16384  1 drm_kms_helper
cfg80211              712704  3 iwlmvm,iwlwifi,mac80211
hid_multitouch         28672  0
ecdh_generic           16384  1 bluetooth
sysfillrect            16384  1 drm_kms_helper
ecc                    28672  1 ecdh_generic
sysimgblt              16384  1 drm_kms_helper
mei_me                 40960  1
soundcore              16384  1 snd
idma64                 20480  0
mei                   110592  3 mei_hdcp,mei_me
intel_pch_thermal      16384  0
virt_dma               20480  1 idma64
soc_button_array       20480  0
acpi_pad              184320  0
mac_hid                16384  0
sch_fq_codel           20480  5
parport_pc             40960  0
ppdev                  24576  0
lp                     20480  0
parport                53248  3 parport_pc,lp,ppdev
ip_tables              32768  0
x_tables               40960  1 ip_tables
autofs4                45056  2
rtsx_usb_sdmmc         32768  0
usbhid                 57344  0
rtsx_usb               28672  2 rtsx_usb_sdmmc,rtsx_usb_ms
hid_generic            16384  0
nvme                   40960  3
alx                    49152  0
psmouse               155648  0
ahci                   40960  2
i2c_hid                28672  0
nvme_core             102400  6 nvme
i2c_i801               32768  0
intel_lpss_pci         20480  0
mdio                   16384  1 alx
libahci                32768  1 ahci
intel_lpss             16384  1 intel_lpss_pci
i2c_nvidia_gpu         16384  0
hid                   131072  4 i2c_hid,usbhid,hid_multitouch,hid_generic
pinctrl_cannonlake     36864  2
wmi                    32768  3 wmi_bmof,msi_wmi,mxm_wmi
video                  49152  2 msi_wmi,i915
pinctrl_intel          28672  2 pinctrl_cannonlake
---------
iwlmvm                401408  0
mac80211              851968  1 iwlmvm
iwlwifi               348160  1 iwlmvm
cfg80211              712704  3 iwlmvm,iwlwifi,mac80211

---------- iwconfig output below ----------------
wlo1      IEEE 802.11  ESSID:"not-you-5GHz"  
          Mode:Managed  Frequency:5.58 GHz  Access Point: A0:63:91:47:91:D5   
          Bit Rate=173.3 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:138   Missed beacon:0

-------------lspci output below-------------------

00:00.0 Host bridge: Intel Corporation 8th Gen Core Processor Host Bridge/DRAM Registers (rev 0d)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor PCIe Controller (x16) (rev 0d)
00:02.0 VGA compatible controller: Intel Corporation UHD Graphics 630 (Mobile) (rev 02)
00:12.0 Signal processing controller: Intel Corporation Cannon Lake PCH Thermal Controller (rev 10)
00:14.0 USB controller: Intel Corporation Cannon Lake PCH USB 3.1 xHCI Host Controller (rev 10)
00:14.2 RAM memory: Intel Corporation Cannon Lake PCH Shared SRAM (rev 10)
00:14.3 Network controller: Intel Corporation Wireless-AC 9560 [Jefferson Peak] (rev 10)
00:15.0 Serial bus controller [0c80]: Intel Corporation Cannon Lake PCH Serial IO I2C Controller #0 (rev 10)
00:15.2 Serial bus controller [0c80]: Intel Corporation Cannon Lake PCH Serial IO I2C Controller #2 (rev 10)
00:16.0 Communication controller: Intel Corporation Cannon Lake PCH HECI Controller (rev 10)
00:17.0 SATA controller: Intel Corporation Cannon Lake Mobile PCH SATA AHCI Controller (rev 10)
00:1b.0 PCI bridge: Intel Corporation Cannon Lake PCH PCI Express Root Port #17 (rev f0)
00:1b.4 PCI bridge: Intel Corporation Cannon Lake PCH PCI Express Root Port #21 (rev f0)
00:1d.0 PCI bridge: Intel Corporation Cannon Lake PCH PCI Express Root Port #9 (rev f0)
00:1d.6 PCI bridge: Intel Corporation Cannon Lake PCH PCI Express Root Port #15 (rev f0)
00:1f.0 ISA bridge: Intel Corporation Device a30d (rev 10)
00:1f.3 Audio device: Intel Corporation Cannon Lake PCH cAVS (rev 10)
00:1f.4 SMBus: Intel Corporation Cannon Lake PCH SMBus Controller (rev 10)
00:1f.5 Serial bus controller [0c80]: Intel Corporation Cannon Lake PCH SPI Controller (rev 10)
01:00.0 VGA compatible controller: NVIDIA Corporation TU106M [GeForce RTX 2060 Mobile] (rev a1)
01:00.1 Audio device: NVIDIA Corporation TU106 High Definition Audio Controller (rev a1)
01:00.2 USB controller: NVIDIA Corporation TU106 USB 3.1 Host Controller (rev a1)
01:00.3 Serial bus controller [0c80]: NVIDIA Corporation TU106 USB Type-C Port Policy Controller (rev a1)
03:00.0 Non-Volatile memory controller: Sandisk Corp Device 5006
04:00.0 Non-Volatile memory controller: Samsung Electronics Co Ltd NVMe SSD Controller SM981/PM981/PM983
05:00.0 Ethernet controller: Qualcomm Atheros Killer E2500 Gigabit Ethernet Controller (rev 10)
```

---

### Post by chili555 on 2020-03-28
> 
I'm Japanese man who are about to entrance University, so if my English is little strange, please excuse me.
You English is just fine. 

There is a probable firmware issue with the 9560. Let's take a look at the log and see if there are any clues. Please run and post the result of the terminal command:

```
dmesg | grep iwl
```

---

### Post by Andrew F in Australia on 2020-03-29
Hi Chili,

Just for reference - this is the same card working on another machine.

```

horace@horace-GE75-Raider-9SE:~$ dmesg | grep iwl
[    2.957945] iwlwifi 0000:00:14.3: enabling device (0000 -> 0002)
[    2.961294] iwlwifi 0000:00:14.3: Found debug destination: EXTERNAL_DRAM
[    2.961295] iwlwifi 0000:00:14.3: Found debug configuration: 0
[    2.961557] iwlwifi 0000:00:14.3: loaded firmware version 46.6bf1df06.0 op_mode iwlmvm
[    2.978933] iwlwifi 0000:00:14.3: Detected Killer (R) Wireless-AC 1550i Wireless Network Adapter (9560NGW), REV=0x318
[    2.987029] iwlwifi 0000:00:14.3: Applying debug destination EXTERNAL_DRAM
[    2.987283] iwlwifi 0000:00:14.3: Allocated 0x00400000 bytes for firmware monitor.
[    3.027744] iwlwifi 0000:00:14.3: base HW address: 08:71:90:a2:3d:cf
[    3.096927] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    3.098290] iwlwifi 0000:00:14.3 wlo1: renamed from wlan0
[    5.794269] iwlwifi 0000:00:14.3: Applying debug destination EXTERNAL_DRAM
[    5.910794] iwlwifi 0000:00:14.3: Applying debug destination EXTERNAL_DRAM
[    5.976446] iwlwifi 0000:00:14.3: FW already configured (0) - re-configuring
[    5.986444] iwlwifi 0000:00:14.3: BIOS contains WGDS but no WRDS
[    9.393206] iwlwifi 0000:00:14.3: Unhandled alg: 0x707
horace@horace-GE75-Raider-9SE:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 19.10
Release:    19.10
Codename:    eoan


```

---

### Post by kevin-2020 on 2020-03-31
```
*******@*******-HP-ENVY-Laptop:~$ dmesg | grep iwl
[    2.443182] iwlwifi 0000:00:14.3: TLV_FW_FSEQ_VERSION: FSEQ Version: 43.2.23.17
[    2.443188] iwlwifi 0000:00:14.3: Found debug destination: EXTERNAL_DRAM
[    2.443190] iwlwifi 0000:00:14.3: Found debug configuration: 0
[    2.443556] iwlwifi 0000:00:14.3: loaded firmware version 48.13675109.0 op_mode iwlmvm
[    2.538570] iwlwifi 0000:00:14.3: Detected Intel(R) Wireless-AC 9560, REV=0x354
[    2.545527] iwlwifi 0000:00:14.3: Applying debug destination EXTERNAL_DRAM
[    2.546187] iwlwifi 0000:00:14.3: Allocated 0x00400000 bytes for firmware monitor.
[    3.550465] iwlwifi 0000:00:14.3: Collecting data: trigger 15 fired.
[    3.550541] iwlwifi 0000:00:14.3: Start IWL Error Log Dump:
[    3.550544] iwlwifi 0000:00:14.3: Status: 0x00000000, count: 1883642492
[    3.550545] iwlwifi 0000:00:14.3: Loaded firmware version: 48.13675109.0
[    3.550547] iwlwifi 0000:00:14.3: 0xC9C5B082 | ADVANCED_SYSASSERT          
[    3.550549] iwlwifi 0000:00:14.3: 0x192B6607 | trm_hw_status0
[    3.550550] iwlwifi 0000:00:14.3: 0x84D52B78 | trm_hw_status1
[    3.550551] iwlwifi 0000:00:14.3: 0x75FCE7F7 | branchlink2
[    3.550553] iwlwifi 0000:00:14.3: 0x4EFA8D36 | interruptlink1
[    3.550554] iwlwifi 0000:00:14.3: 0x7DD08156 | interruptlink2
[    3.550555] iwlwifi 0000:00:14.3: 0x47472A60 | data1
[    3.550557] iwlwifi 0000:00:14.3: 0xF9067ECB | data2
[    3.550558] iwlwifi 0000:00:14.3: 0x8B7BB8C3 | data3
[    3.550559] iwlwifi 0000:00:14.3: 0x8C223D3A | beacon time
[    3.550561] iwlwifi 0000:00:14.3: 0x2BD76732 | tsf low
[    3.550562] iwlwifi 0000:00:14.3: 0x88739D73 | tsf hi
[    3.550563] iwlwifi 0000:00:14.3: 0x63859425 | time gp1
[    3.550565] iwlwifi 0000:00:14.3: 0x7B550582 | time gp2
[    3.550566] iwlwifi 0000:00:14.3: 0x6D4B4ABC | uCode revision type
[    3.550567] iwlwifi 0000:00:14.3: 0xF2DE70F4 | uCode version major
[    3.550569] iwlwifi 0000:00:14.3: 0xA1F1E827 | uCode version minor
[    3.550570] iwlwifi 0000:00:14.3: 0x930A9712 | hw version
[    3.550571] iwlwifi 0000:00:14.3: 0x884FF264 | board version
[    3.550572] iwlwifi 0000:00:14.3: 0x21C088C0 | hcmd
[    3.550574] iwlwifi 0000:00:14.3: 0x96A09AFD | isr0
[    3.550575] iwlwifi 0000:00:14.3: 0x4C278CBF | isr1
[    3.550576] iwlwifi 0000:00:14.3: 0x71320A85 | isr2
[    3.550577] iwlwifi 0000:00:14.3: 0x427D32BA | isr3
[    3.550579] iwlwifi 0000:00:14.3: 0x93C0B116 | isr4
[    3.550580] iwlwifi 0000:00:14.3: 0x153F73C7 | last cmd Id
[    3.550581] iwlwifi 0000:00:14.3: 0x7552D232 | wait_event
[    3.550583] iwlwifi 0000:00:14.3: 0x2793D2DD | l2p_control
[    3.550584] iwlwifi 0000:00:14.3: 0xFEBEFCA9 | l2p_duration
[    3.550585] iwlwifi 0000:00:14.3: 0xD23DEAFA | l2p_mhvalid
[    3.550587] iwlwifi 0000:00:14.3: 0x8C8967E5 | l2p_addr_match
[    3.550588] iwlwifi 0000:00:14.3: 0x325D8A55 | lmpm_pmg_sel
[    3.550589] iwlwifi 0000:00:14.3: 0x5FBCE4EB | timestamp
[    3.550590] iwlwifi 0000:00:14.3: 0x36446F45 | flow_handler
[    3.550623] iwlwifi 0000:00:14.3: Start IWL Error Log Dump:
[    3.550625] iwlwifi 0000:00:14.3: Status: 0x00000000, count: 7
[    3.550626] iwlwifi 0000:00:14.3: 0x201013F1 | ADVANCED_SYSASSERT
[    3.550628] iwlwifi 0000:00:14.3: 0x00000000 | umac branchlink1
[    3.550629] iwlwifi 0000:00:14.3: 0xC008CF5C | umac branchlink2
[    3.550630] iwlwifi 0000:00:14.3: 0x00000000 | umac interruptlink1
[    3.550631] iwlwifi 0000:00:14.3: 0x00000000 | umac interruptlink2
[    3.550633] iwlwifi 0000:00:14.3: 0x00000003 | umac data1
[    3.550634] iwlwifi 0000:00:14.3: 0x20000302 | umac data2
[    3.550635] iwlwifi 0000:00:14.3: 0x01300202 | umac data3
[    3.550637] iwlwifi 0000:00:14.3: 0x00000030 | umac major
[    3.550638] iwlwifi 0000:00:14.3: 0x13675109 | umac minor
[    3.550639] iwlwifi 0000:00:14.3: 0x00005D06 | frame pointer
[    3.550641] iwlwifi 0000:00:14.3: 0xC0887F58 | stack pointer
[    3.550642] iwlwifi 0000:00:14.3: 0x00000000 | last host cmd
[    3.550643] iwlwifi 0000:00:14.3: 0x00000000 | isr status reg
[    3.550660] iwlwifi 0000:00:14.3: Fseq Registers:
[    3.550663] iwlwifi 0000:00:14.3: 0x00000003 | FSEQ_ERROR_CODE
[    3.550665] iwlwifi 0000:00:14.3: 0x00000000 | FSEQ_TOP_INIT_VERSION
[    3.550668] iwlwifi 0000:00:14.3: 0x1B5D0088 | FSEQ_CNVIO_INIT_VERSION
[    3.550670] iwlwifi 0000:00:14.3: 0x0000A384 | FSEQ_OTP_VERSION
[    3.550673] iwlwifi 0000:00:14.3: 0xED865E71 | FSEQ_TOP_CONTENT_VERSION
[    3.550676] iwlwifi 0000:00:14.3: 0x6C20FA03 | FSEQ_ALIVE_TOKEN
[    3.550679] iwlwifi 0000:00:14.3: 0xB4A859BF | FSEQ_CNVI_ID
[    3.550682] iwlwifi 0000:00:14.3: 0x65E5E9F4 | FSEQ_CNVR_ID
[    3.550685] iwlwifi 0000:00:14.3: 0x20000302 | CNVI_AUX_MISC_CHIP
[    3.550690] iwlwifi 0000:00:14.3: 0x01300202 | CNVR_AUX_MISC_CHIP
[    3.550695] iwlwifi 0000:00:14.3: 0x0000485B | CNVR_SCU_SD_REGS_SD_REG_DIG_DCDC_VTRIM
[    3.550730] iwlwifi 0000:00:14.3: 0xA5A5A5A2 | CNVR_SCU_SD_REGS_SD_REG_ACTIVE_VDIG_MIRROR
[    3.550758] iwlwifi 0000:00:14.3: SecBoot CPU1 Status: 0x5c79, CPU2 Status: 0x3
[    3.550759] iwlwifi 0000:00:14.3: Failed to start RT ucode: -110
[    3.550762] iwlwifi 0000:00:14.3: Firmware not running - cannot dump error
[    3.562509] iwlwifi 0000:00:14.3: Failed to run INIT ucode: -110
```

Is this OK?

---

### Post by DuckHook on 2020-03-31
Please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

---

### Post by chili555 on 2020-04-01
> [    3.550759] iwlwifi 0000:00:14.3: Failed to start RT ucode: -110
[    3.550762] iwlwifi 0000:00:14.3: Firmware not running - cannot dump error
[    3.562509] iwlwifi 0000:00:14.3: Failed to run INIT ucode: -110Please undertake the steps here: [https://askubuntu.com/questions/1218141/dell-vostro-5490-no-wifi-in-ubuntu-18-04/1218262#1218262](https://askubuntu.com/questions/1218141/dell-vostro-5490-no-wifi-in-ubuntu-18-04/1218262#1218262)

Please copy and paste each command and enter them one at a time so as to avoid any typographical errors. If you have any questions or if you get stuck, stop and ask here before you proceed.

Reboot.

---

