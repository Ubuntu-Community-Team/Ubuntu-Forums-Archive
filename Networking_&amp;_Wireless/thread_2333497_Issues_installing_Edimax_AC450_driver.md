---
title: "Issues installing Edimax AC450 driver"
date: 2016-08-10
forum: Networking &amp; Wireless
---

### Post by beedrilldyl on 2016-08-10
I've been trying for hours to install the driver for my Edimax Wifi USB adapter, and I need to connect to my 5G internet (the 2.4 disconnects regularly and is atrociously slow).

I have the Edimax AC450 EW-7711ULC, and I'm running Ubuntu 16.04. I've tried two methods to install the driver, both to no avail.

At first, I tried installing using the official driver from the Edimax website ([http://www.edimax.com/edimax/download/download/data/edimax/au/download/for_home/wireless_adapters/wireless_adapters_ac450/ew-7711ulc](http://www.edimax.com/edimax/download/download/data/edimax/au/download/for_home/wireless_adapters/wireless_adapters_ac450/ew-7711ulc)). I got a date-time error, which I resolved, but more and more errors occured when I used 'make', so I had to try a different method.

I used ndiswrapper to install the driver for Windows. Ndiswrapper installed it and detected the adapter, but the adapter itself will not work.

Just for reference, here are my outputs for ifconfig, iwconfig, lsmod, and lshw -C network.
```

**timelord@timelord-radius11:~$** ifconfig

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2889 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2889 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:275877 (275.8 KB)  TX bytes:275877 (275.8 KB)

wlp2s0    Link encap:Ethernet  HWaddr ac:b5:7d:d2:70:57  
          inet addr:192.168.1.114  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::1d83:aa93:162:7515/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:279463 errors:0 dropped:0 overruns:0 frame:0
          TX packets:131774 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:366895533 (366.8 MB)  TX bytes:12662591 (12.6 MB)
```

```
**timelord@timelord-radius11:~$** iwconfig
lo        no wireless extensions.

wlp2s0    IEEE 802.11bgn  ESSID:"8443 linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 14:CC:20:3D:27:F1   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-40 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1063   Missed beacon:0
```

```
**timelord@timelord-radius11:~$** sudo lsmod
Module                  Size  Used by
ndiswrapper           286720  0
8812au                991232  0
binfmt_misc            20480  1
btrfs                 987136  0
xor                    24576  1 btrfs
raid6_pq              102400  1 btrfs
ufs                    73728  0
qnx4                   16384  0
hfsplus               106496  0
hfs                    57344  0
minix                  36864  0
ntfs                   98304  0
msdos                  20480  0
jfs                   180224  0
xfs                   970752  0
libcrc32c              16384  1 xfs
cpuid                  16384  0
drbg                   32768  1
ansi_cprng             16384  0
ctr                    16384  2
ccm                    20480  2
rfcomm                 69632  0
bnep                   20480  2
nls_iso8859_1          16384  1
rtsx_usb_ms            20480  0
memstick               20480  1 rtsx_usb_ms
toshiba_wmi            16384  0
intel_rapl             20480  0
arc4                   16384  2
uvcvideo               90112  0
intel_soc_dts_thermal    16384  0
rtl8723be              90112  0
intel_powerclamp       16384  0
btcoexist              53248  1 rtl8723be
videobuf2_vmalloc      16384  1 uvcvideo
rtl8723_common         24576  1 rtl8723be
coretemp               16384  0
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         28672  1 uvcvideo
kvm_intel             172032  0
videobuf2_core         36864  2 uvcvideo,videobuf2_v4l2
rtl_pci                28672  1 rtl8723be
v4l2_common            16384  1 videobuf2_v4l2
kvm                   536576  1 kvm_intel
rtlwifi                77824  2 rtl_pci,rtl8723be
mac80211              737280  3 rtl_pci,rtlwifi,rtl8723be
videodev              176128  4 uvcvideo,v4l2_common,videobuf2_core,videobuf2_v4l2
btusb                  45056  0
irqbypass              16384  1 kvm
media                  24576  2 uvcvideo,videodev
btrtl                  16384  1 btusb
hid_multitouch         20480  0
btbcm                  16384  1 btusb
punit_atom_debug       16384  0
btintel                16384  1 btusb
cfg80211              565248  2 mac80211,rtlwifi
crct10dif_pclmul       16384  0
bluetooth             520192  29 bnep,btbcm,btrtl,btusb,rfcomm,btintel
crc32_pclmul           16384  0
snd_hda_codec_hdmi     53248  1
cryptd                 20480  0
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
joydev                 20480  0
input_leds             16384  0
serio_raw              16384  0
lpc_ich                24576  0
toshiba_bluetooth      16384  0
toshiba_acpi           40960  0
sparse_keymap          16384  2 toshiba_wmi,toshiba_acpi
snd_hda_intel          36864  5
snd_intel_sst_acpi     16384  0
snd_soc_rt5640        114688  0
snd_intel_sst_core     73728  1 snd_intel_sst_acpi
snd_soc_sst_mfld_platform    90112  1 snd_intel_sst_core
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
snd_soc_core          212992  2 snd_soc_rt5640,snd_soc_sst_mfld_platform
snd_hda_core           73728  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
snd_compress           20480  1 snd_soc_core
ac97_bus               16384  1 snd_soc_core
snd_hwdep              16384  1 snd_hda_codec
snd_pcm_dmaengine      16384  1 snd_soc_core
snd_pcm               106496  9 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_soc_sst_mfld_platform,snd_pcm_dmaengine,snd_hda_core
snd_seq_midi           16384  0
8250_fintek            16384  0
dw_dmac                16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
dw_dmac_core           24576  1 dw_dmac
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
int3400_thermal        16384  0
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
acpi_thermal_rel       16384  1 int3400_thermal
processor_thermal_device    16384  0
rfkill_gpio            16384  0
snd_timer              32768  2 snd_pcm,snd_seq
intel_soc_dts_iosf     16384  2 intel_soc_dts_thermal,processor_thermal_device
int3403_thermal        16384  0
int340x_thermal_zone    16384  2 processor_thermal_device,int3403_thermal
snd                    81920  23 snd_hda_codec_realtek,snd_soc_core,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_soc_sst_mfld_platform,snd_seq_device,snd_compress
snd_soc_sst_acpi       16384  0
soundcore              16384  1 snd
8250_dw                16384  0
shpchp                 36864  0
i2c_designware_platform    16384  0
i2c_designware_core    20480  1 i2c_designware_platform
spi_pxa2xx_platform    24576  0
mei_txe                20480  0
mei                    98304  1 mei_txe
pwm_lpss_platform      16384  0
mac_hid                16384  0
pwm_lpss               16384  1 pwm_lpss_platform
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
usbhid                 49152  0
rtsx_usb_sdmmc         28672  0
rtsx_usb               24576  2 rtsx_usb_sdmmc,rtsx_usb_ms
i915                 1208320  5
psmouse               126976  0
i2c_algo_bit           16384  1 i915
drm_kms_helper        147456  1 i915
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   360448  6 i915,drm_kms_helper
ahci                   36864  4
libahci                32768  1 ahci
wmi                    20480  2 toshiba_wmi,toshiba_acpi
video                  40960  2 i915,toshiba_acpi
fjes                   28672  0
i2c_hid                20480  0
hid                   118784  3 i2c_hid,hid_multitouch,usbhid
sdhci_acpi             16384  0
sdhci                  45056  1 sdhci_acpi
```

```
**timelord@timelord-radius11:~$ **sudo lshw -C network
  *-network               
       description: Wireless interface
       product: RTL8723BE PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: 00
       serial: ac:b5:7d:d2:70:57
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8723be driverversion=4.4.0-31-generic firmware=N/A ip=192.168.1.114 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 ioport:e000(size=256) memory:d0600000-d0603fff

```

---

### Post by chili555 on 2016-08-10
Where do I start?

You have THREE wireless drivers loaded; ndiswrapper, 8812au and rtl8723be. I am confident that they conflict.

Why are you using the USB when you have a working perfectly, as far as we can see, PCI device? Is that the device that disconnects and is slow? Frankly, I'd rather troubleshoot the internal rather than band-aid a USB over it.

C'mon, tell us the whole story.

---

### Post by beedrilldyl on 2016-08-10
We have a security camera connected to our 2.4Ghz wifi, which makes it really slow. It disconnects on phones and on Windows as well. Using the 5Ghz wifi is the only way to browse the internet without major issues. We're considering buying a new camera that doesn't completely ruin our regular internet, but for now, we're stuck with dual-band USB adapters.

---

### Post by chili555 on 2016-08-11
If you want to use the USB and not the internal, I suggest that you blacklist its driver so it can't conflict. As well, I doubt that ndiswrapper is useful here, as the Linux-specific driver 8812au is loaded. Let's blacklist it, too:```
sudo -i
echo "blacklist rtl8723be"  >>  /etc/modprobe.d/blacklist.conf
echo "blacklist ndiswrapper"  >>  /etc/modprobe.d/blacklist.conf
exit
```Reboot and let us hear your report.

---

