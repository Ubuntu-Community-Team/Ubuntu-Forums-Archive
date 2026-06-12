---
title: "wifi connection issues (slow or not connecting at all)"
date: 2019-12-29
forum: Networking &amp; Wireless
---

### Post by mvp245 on 2019-12-29
So first time Linux user from a lifetime of windows. I got a Jumper EZ 6 Pro tablet laptop over the holiday and decided to replace windows 10 and install Ubuntu 18.4.3 LTS as the OS. i started it up on windows 10 just to make sure everything worked out of the box and to remind myself why i didn't want windows as my OS. everything worked fine, wifi connection was full bars. i was able to install and download everything i needed to create a bootable usb drive.
i'm very new to linux so i'm having a hard time navigating the waters.
the installation of ubuntu went fine. the wifi connected but was at one bar and i didn't think much of it. i tried installing applications but everything i tried to install gave me an error saying download failed. i disconnected and tried to reconnect to the wifi but it would not reconnect. i restarted my laptop, still no connection. it can see the router and i can make a connection one out of every 5 reboots but when it is connected it's too slow to install anything but connected enough to load web pages at a very slow rate.
sorry if this has already been answered but i've done a fair amount of searching but haven't come across anyone with the issue i've been having. through my searching i've found some of the common commands that show some of the info in my system and it's posted below so i hope that can offer some insight on what's going on.
thank you for taking the time to read.
```
iwconfig
lo no wireless extensions.
wlx3420031cc8bc IEEE 802.11 ESSID:off/any
      Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   

      Retry short limit:7   RTS thr=2347 B   Fragment thr:off

      Power Management:off
```
```
lspci
00:00.0 Host bridge: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900
Series Host Bridge (rev 0b)
00:00.1 Signal processing controller: Intel Corporation Device 5a8c (rev 0b)
00:02.0 VGA compatible controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series Integrated Graphics Controller (rev 0b)
00:03.0 Multimedia controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series Imaging Unit (rev 0b)
00:0e.0 Audio device: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series Audio Cluster (rev 0b)
00:0f.0 Communication controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series Trusted Execution Engine (rev 0b)
00:12.0 SATA controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series SATA AHCI Controller (rev 0b)
00:15.0 USB controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series USB xHCI (rev 0b)
00:16.0 Signal processing controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series I2C Controller #1 (rev 0b)
00:16.1 Signal processing controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series I2C Controller #2 (rev 0b)
00:16.2 Signal processing controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series I2C Controller #3 (rev 0b)
00:16.3 Signal processing controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series I2C Controller #4 (rev 0b)
00:17.0 Signal processing controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series I2C Controller #5 (rev 0b)
00:17.1 Signal processing controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series I2C Controller #6 (rev 0b)
00:17.2 Signal processing controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series I2C Controller #7 (rev 0b)
00:17.3 Signal processing controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series I2C Controller #8 (rev 0b)
00:18.0 Signal processing controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series HSUART Controller #1 (rev 0b)
00:18.1 Signal processing controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series HSUART Controller #2 (rev 0b)
00:18.2 Signal processing controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series HSUART Controller #3 (rev 0b)
00:18.3 Signal processing controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series HSUART Controller #4 (rev 0b)
00:19.0 Signal processing controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series SPI Controller #1 (rev 0b)
00:19.1 Signal processing controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series SPI Controller #2 (rev 0b)
00:19.2 Signal processing controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series SPI Controller #3 (rev 0b)
00:1b.0 SD Host controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series SDXC/MMC Host Controller (rev 0b)
00:1c.0 SD Host controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series eMMC Controller (rev 0b)
00:1e.0 SD Host controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series SDIO Controller (rev 0b)
00:1f.0 ISA bridge: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series Low Pin Count Interface (rev 0b)
00:1f.1 SMBus: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series SMBus Controller (rev 0b)
```
```
lshw -class network
*-network
   description: Wireless interface

   physical id: 1

   bus info: usb@1:7

   logical name: wlx3420031cc8bc

   serial: 34:20:03:1c:c8:bc

   capabilities: ethernet physical wireless

   configuration: broadcast=yes driver=rtl8xxxu driverversion=5.0.0-37-
generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11
```

---

### Post by howefield on 2019-12-29
Thread moved to the "*Networking & Wireless*" forum for a better fit.

---

### Post by jeremy31 on 2019-12-29
Post results for ```
lsusb
```

---

### Post by mvp245 on 2019-12-29
**lsusb**


Bus 002 Device 002: ID 0781:5583 SanDisk Corp. 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 004: ID 0bda:b720 Realtek Semiconductor Corp. 
Bus 001 Device 005: ID 0603:0002 Novatek Microelectronics Corp. 
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 002: ID 058f:5608 Alcor Micro Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by praseodym on 2019-12-30
You need this driver

```
sudo apt-get install git build-essential
git clone https://github.com/lwfinger/rtl8723bu
cd rtl8723bu
make
sudo make install
sudo modprobe -rfv rtl8xxxu rtl8192cu
sudo modprobe -v 8723bu
```

---

### Post by mvp245 on 2019-12-30
installed the driver and still no luck :/ thanks though.

---

### Post by praseodym on 2019-12-31
Please run the wireless script again

---

### Post by mvp245 on 2019-12-31
first iwconfig is when i manage to connect second is after i lost connection. 


```
iwconfig
lo        no wireless extensions.

wlx3420031cc8bc  IEEE 802.11  ESSID:"Fios-HATGH"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 18:78:D4:02:61:EA   
          Bit Rate=1 Mb/s   Tx-Power=30 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=44/70  Signal level=-66 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2   Missed beacon:0

iwconfig
lo        no wireless extensions.

wlx3420031cc8bc  IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off




lshw -class network
  *-network                 
       description: Wireless interface
       physical id: 1
       bus info: usb@1:7
       logical name: wlx3420031cc8bc
       serial: 34:20:03:1c:c8:bc
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8xxxu driverversion=5.0.0-37-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11
```

---

### Post by praseodym on 2020-01-01
Please show
```

lsmod
sudo iwlist scan
```

---

### Post by mvp245 on 2020-01-01
```
[COLOR=#000000]lsmod[/COLOR]Module                  Size  Used by
rfcomm                 77824  4
ccm                    20480  0
bnep                   24576  2
nls_iso8859_1          16384  2
arc4                   16384  2
spi_pxa2xx_platform    28672  0
8250_dw                20480  0
intel_rapl             24576  0
intel_telemetry_pltdrv    20480  0
intel_punit_ipc        16384  1 intel_telemetry_pltdrv
intel_telemetry_core    16384  1 intel_telemetry_pltdrv
intel_pmc_ipc          20480  1 intel_telemetry_pltdrv
x86_pkg_temp_thermal    20480  0
intel_powerclamp       20480  0
coretemp               20480  0
kvm_intel             241664  0
crct10dif_pclmul       16384  1
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
rtl8xxxu              126976  0
aesni_intel           372736  0
aes_x86_64             20480  1 aesni_intel
crypto_simd            16384  1 aesni_intel
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
glue_helper            16384  1 aesni_intel
intel_cstate           20480  0
intel_rapl_perf        16384  0
serio_raw              20480  0
mac80211              819200  1 rtl8xxxu
rtsx_usb_ms            24576  0
lpc_ich                24576  0
memstick               20480  1 rtsx_usb_ms
snd_hda_codec_hdmi     53248  1
snd_hda_codec_realtek   114688  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
btusb                  49152  0
ledtrig_audio          16384  2 snd_hda_codec_generic,snd_hda_codec_realtek
btrtl                  20480  1 btusb
btbcm                  16384  1 btusb
cfg80211              679936  1 mac80211
btintel                24576  1 btusb
bluetooth             557056  33 btrtl,btintel,btbcm,bnep,btusb,rfcomm
ecdh_generic           28672  1 bluetooth
snd_soc_skl           106496  0
snd_soc_hdac_hda       24576  1 snd_soc_skl
snd_hda_ext_core       28672  2 snd_soc_hdac_hda,snd_soc_skl
snd_soc_skl_ipc        65536  1 snd_soc_skl
snd_soc_sst_ipc        20480  1 snd_soc_skl_ipc
snd_soc_sst_dsp        36864  1 snd_soc_skl_ipc
snd_soc_acpi_intel_match    28672  1 snd_soc_skl
snd_soc_acpi           16384  2 snd_soc_acpi_intel_match,snd_soc_skl
snd_soc_core          233472  2 snd_soc_hdac_hda,snd_soc_skl
i915                 1826816  21
snd_compress           24576  1 snd_soc_core
ac97_bus               16384  1 snd_soc_core
uvcvideo               94208  0
snd_pcm_dmaengine      16384  1 snd_soc_core
videobuf2_vmalloc      20480  1 uvcvideo
snd_hda_intel          49152  6
videobuf2_memops       20480  1 videobuf2_vmalloc
snd_hda_codec         135168  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek,snd_soc_hdac_hda
videobuf2_v4l2         24576  1 uvcvideo
input_leds             16384  0
videobuf2_common       45056  2 videobuf2_v4l2,uvcvideo
videodev              204800  3 videobuf2_v4l2,uvcvideo,videobuf2_common
media                  53248  4 videodev,videobuf2_v4l2,uvcvideo,videobuf2_common
kvmgt                  28672  0
vfio_mdev              16384  0
mdev                   24576  2 kvmgt,vfio_mdev
vfio_iommu_type1       28672  0
snd_hda_core           86016  8 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_ext_core,snd_hda_codec,snd_hda_codec_realtek,snd_soc_hdac_hda,snd_soc_skl
vfio                   32768  3 kvmgt,vfio_mdev,vfio_iommu_type1
snd_hwdep              20480  1 snd_hda_codec
kvm                   647168  2 kvmgt,kvm_intel
snd_pcm               102400  8 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_ext_core,snd_hda_codec,snd_soc_core,snd_soc_skl,snd_hda_core,snd_pcm_dmaengine
irqbypass              16384  1 kvm
drm_kms_helper        180224  1 i915
snd_seq_midi           20480  0
snd_seq_midi_event     16384  1 snd_seq_midi
idma64                 20480  0
drm                   483328  15 drm_kms_helper,i915
virt_dma               20480  1 idma64
snd_rawmidi            36864  1 snd_seq_midi
intel_lpss_pci         20480  6
intel_lpss             16384  1 intel_lpss_pci
snd_seq                69632  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
snd_timer              36864  2 snd_seq,snd_pcm
bmc150_accel_i2c       16384  0
bmc150_accel_core      28672  1 bmc150_accel_i2c
industrialio_triggered_buffer    16384  1 bmc150_accel_core
snd                    86016  25 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_compress,snd_soc_core,snd_pcm,snd_rawmidi
mac_hid                16384  0
i2c_algo_bit           16384  1 i915
kfifo_buf              16384  1 industrialio_triggered_buffer
fb_sys_fops            16384  1 drm_kms_helper
industrialio           73728  3 industrialio_triggered_buffer,kfifo_buf,bmc150_accel_core
intel_xhci_usb_role_switch    16384  0
syscopyarea            16384  1 drm_kms_helper
roles                  16384  1 intel_xhci_usb_role_switch
sysfillrect            16384  1 drm_kms_helper
silead                 20480  0
mei_me                 40960  0
mei                   106496  1 mei_me
processor_thermal_device    20480  0
soundcore              16384  1 snd
intel_soc_dts_iosf     20480  1 processor_thermal_device
sysimgblt              16384  1 drm_kms_helper
int3400_thermal        20480  0
int3403_thermal        16384  0
intel_hid              20480  0
sparse_keymap          16384  1 intel_hid
int340x_thermal_zone    16384  2 int3403_thermal,processor_thermal_device
acpi_thermal_rel       16384  1 int3400_thermal
sch_fq_codel           20480  5
parport_pc             36864  0
ppdev                  24576  0
lp                     20480  0
parport                53248  3 parport_pc,lp,ppdev
ip_tables              32768  0
x_tables               40960  1 ip_tables
autofs4                45056  2
hid_generic            16384  0
usbhid                 53248  0
hid                   126976  2 usbhid,hid_generic
rtsx_usb_sdmmc         28672  0
rtsx_usb               24576  2 rtsx_usb_sdmmc,rtsx_usb_ms
mmc_block              49152  3
uas                    24576  0
usb_storage            69632  2 uas
psmouse               151552  0
sdhci_pci              45056  0
ahci                   40960  0
cqhci                  28672  1 sdhci_pci
sdhci                  57344  1 sdhci_pci
libahci                32768  1 ahci
video                  49152  1 i915
pinctrl_broxton        40960  2
pinctrl_intel          28672  2 pinctrl_broxton




sudo iwlist scan
lo        Interface doesn't support scanning.

wlx3420031cc8bc  Scan completed :
          Cell 01 - Address: 18:78:D4:02:61:EA
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"Fios-HATGH"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000003f03c50219b
                    Extra: Last beacon: 1048ms ago
                    IE: Unknown: 000A46696F732D4841544748
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C121860
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 0B050000260000
                    IE: Unknown: 46050300000000
                    IE: Unknown: 2D1AAD091BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080000000000000000000000000000000000000000
                    IE: Unknown: 7F080400080000000040
                    IE: Unknown: DD310050F204104A0001101044000102104700109FA90BF52418B4BC514F76C08C89499E103C0001031049000600372A000120
                    IE: Unknown: DD090010180200001C0000
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00 
```

---

