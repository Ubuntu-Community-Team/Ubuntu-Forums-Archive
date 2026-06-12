---
title: "Wireless not showing up on Lenovo Flex 3 install"
date: 2015-08-26
forum: Networking &amp; Wireless
---

### Post by Sam_Fels on 2015-08-26
Hi everyone! New to the forum, but not really new to Ubuntu

So, my wireless card isn't showing up at all in a new Ubuntu 14.04 install. It's not an issue connecting, just no option showing anywhere to acknowledge there's a wireless card present. Wired connections are fine but I don't have that option at work, unfortunately.

What I've tried so far:
--Looking for special drivers. I don't remember having to do this for various desktop Ubuntu installations before, but it's been a while. This is my first time installing Ubuntu on a laptop myself.
--After searching around, a common problem with Lenovo laptops (not necessarily the Flex 3) seems to be the airplane-button (F7) automatically disabling all RF function in Linux. I verified this is NOT the problem here, by using the rfkill command as follows:

Flex-3-1470:~$ rfkill list all
0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no

So that's the only reference I've found to actually having a wireless adapter. 
Lenovo model number: [COLOR=#212121][FONT=Helvetica Neue]80JK001GUS

Thanks in advance!!![/FONT][/COLOR]

---

### Post by slickymaster on 2015-08-26
Moved to the Networking & Wireless sub-forum.

Please download and run the [wireless info script]("https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info"), which will gather information to help diagnose your system. It will create the file "wireless-info.txt" at the location it is run from, and depending on its size, an additional archive called "wireless-info.tar.gz", for attaching on this thread.

---

### Post by Sam_Fels on 2015-08-26
Okay sorry about the wrong forum post. Should have seen the wireless info thing, the output is attached now.

Thanks!!!!

---

### Post by praseodym on 2015-08-26
Well, can you read German?

[https://forum.ubuntuusers.de/topic/kein-treiber-fuer-qualcomm-atheros-qca61x4-wir/#post-7677658](https://forum.ubuntuusers.de/topic/kein-treiber-fuer-qualcomm-atheros-qca61x4-wir/#post-7677658)

Done with 15.04!

---

### Post by Sam_Fels on 2015-08-26
> **praseodym said:**
> Well, can you read German?

[https://forum.ubuntuusers.de/topic/kein-treiber-fuer-qualcomm-atheros-qca61x4-wir/#post-7677658](https://forum.ubuntuusers.de/topic/kein-treiber-fuer-qualcomm-atheros-qca61x4-wir/#post-7677658)

Done with 15.04!

No, but the translation looks pretty good and I have multiple German coworkers to translate tomorrow if I can't figure it out.

I'll at least take a crack at it. Thanks!

---

### Post by praseodym on 2015-08-27
So, I recommend upgrading the kernel in 14.04 to 3.19 first with the LTS enablement stack

---

### Post by Sam_Fels on 2015-08-28
> **praseodym said:**
> Well, can you read German?

[https://forum.ubuntuusers.de/topic/kein-treiber-fuer-qualcomm-atheros-qca61x4-wir/#post-7677658](https://forum.ubuntuusers.de/topic/kein-treiber-fuer-qualcomm-atheros-qca61x4-wir/#post-7677658)

Done with 15.04!

Made it pretty far through this, but I can't get the firmware he links to at Step 5. 404'ed when I try the first github link there.
:icon_frown:

Are the drivers available in 15.04 if I want to go to that instead of doing the backport thing?

Thanks

---

### Post by praseodym on 2015-08-28
[https://github.com/sumdog/ath10k-firmware/](https://github.com/sumdog/ath10k-firmware/)

The location changed, please check the paths from there on and rename the files to board.bin and firmware-4.bin. E.g. here

[https://github.com/sumdog/ath10k-firmware/tree/master/ath10k/QCA6174/hw2.1](https://github.com/sumdog/ath10k-firmware/tree/master/ath10k/QCA6174/hw2.1)

---

### Post by praseodym on 2015-08-28
I contacted the user from there, please stay tuned. Maybe he can verify the correct paths

---

### Post by Sam_Fels on 2015-08-28
Okay thanks, will do!!

---

### Post by praseodym on 2015-08-28
Lets try:

```
wget https://github.com/sumdog/ath10k-firmware/tree/master/ath10k/QCA6174/hw2.1/board.bin
wget https://github.com/sumdog/ath10k-firmware/tree/master/ath10k/QCA6174/hw2.1/firmware-4.bin
sudo mkdir -p /lib/firmware/ath10k/QCA6174/hw2.1/
sudo cp board.bin /lib/firmware/ath10k/QCA6174/hw2.1/
sudo cp firmware-4.bin /lib/firmware/ath10k/QCA6174/hw2.1/
```
Then continue as described

---

### Post by Sam_Fels on 2015-08-28
Hmm, I can do all that and it downloads the files fine (thanks!)

Getting this error after Step 6, though:

```
bash: /etc/modprobe.d/ath10k.conf: Permission denied
```

---

### Post by Hadaka on 2015-08-28
Hi this code..
```
sudo echo "options ath10k_core skip_otp=y" > /etc/modprobe.d/ath10k.conf
```
please replace with..
```
echo "options ath10k_core skip_otp=y" |  sudo tee -a /etc/modprobe.d/ath10k.conf
```
thanks

---

### Post by Sam_Fels on 2015-08-31
> **Hadaka said:**
> Hi this code..
```
sudo echo "options ath10k_core skip_otp=y" > /etc/modprobe.d/ath10k.conf
```
please replace with..
```
echo "options ath10k_core skip_otp=y" |  sudo tee -a /etc/modprobe.d/ath10k.conf
```
thanks

Hmm so this worked (returned "options ath10k_core skip_otp=y" instead of permission denied).

I finished out the last step from the previous link though, and rebooted, still no wireless. So I followed the directions and they seemed to work... but this is all a bit over my head as far as figuring out where the problem would be.

---

### Post by praseodym on 2015-08-31
So, it is working?! Please check
```

lspci -nnk | grep -iA2 net
lsmod
dmesg | egrep 'ath|wlan|firm|error|country'
iwconfig
iwlist chan
sudo iwlist scan
modinfo ath10k_pci
rfkill list
```

---

### Post by Sam_Fels on 2015-08-31
No, the wireless card still isn't visible in the default connections or through another network management program. Here's what those commands turn up:

lspci -nnk | grep -iA2 net
```
02:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0041] (rev 20)
    Subsystem: Lenovo Device [17aa:3545]
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo Device [17aa:381e]
    Kernel driver in use: r8169

```

lsmod:
```
Module                  Size  Used by
uas                    24576  0 
usb_storage            69632  1 uas
rfcomm                 69632  0 
bnep                   20480  2 
nls_iso8859_1          16384  1 
uvcvideo               90112  0 
hid_multitouch         20480  0 
videobuf2_vmalloc      16384  1 uvcvideo
hid_generic            16384  0 
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_core         53248  1 uvcvideo
v4l2_common            16384  1 videobuf2_core
videodev              159744  3 uvcvideo,v4l2_common,videobuf2_core
media                  24576  2 uvcvideo,videodev
usbhid                 53248  0 
btusb                  40960  0 
bluetooth             491520  11 bnep,btusb,rfcomm
hid_sensor_accel_3d    16384  0 
hid_sensor_trigger     16384  2 hid_sensor_accel_3d
industrialio_triggered_buffer    16384  1 hid_sensor_accel_3d
kfifo_buf              16384  1 industrialio_triggered_buffer
industrialio           57344  4 hid_sensor_trigger,industrialio_triggered_buffer,hid_sensor_accel_3d,kfifo_buf
hid_sensor_iio_common    16384  1 hid_sensor_accel_3d
snd_hda_codec_hdmi     53248  1 
hid_sensor_hub         20480  3 hid_sensor_trigger,hid_sensor_accel_3d,hid_sensor_iio_common
intel_rapl             20480  0 
iosf_mbi               16384  1 intel_rapl
x86_pkg_temp_thermal    16384  0 
intel_powerclamp       20480  0 
coretemp               16384  0 
kvm                   479232  0 
crct10dif_pclmul       16384  0 
crc32_pclmul           16384  0 
ghash_clmulni_intel    16384  0 
aesni_intel           172032  0 
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
nouveau              1368064  0 
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
cryptd                 20480  3 ghash_clmulni_intel,aesni_intel,ablk_helper
mxm_wmi                16384  1 nouveau
snd_soc_rt5640         94208  0 
joydev                 20480  0 
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_hda_codec_realtek    81920  1 
serio_raw              16384  0 
snd_hda_codec_generic    69632  1 snd_hda_codec_realtek
snd_soc_core          196608  1 snd_soc_rt5640
snd_compress           20480  1 snd_soc_core
snd_pcm_dmaengine      16384  1 snd_soc_core
i915                 1048576  5 
ttm                    94208  1 nouveau
drm_kms_helper        126976  2 i915,nouveau
lpc_ich                24576  0 
mei_me                 20480  0 
shpchp                 40960  0 
drm                   344064  8 ttm,i915,drm_kms_helper,nouveau
mei                    90112  1 mei_me
snd_hda_intel          32768  5 
snd_hda_controller     32768  1 snd_hda_intel
snd_hda_codec         143360  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
i2c_algo_bit           16384  2 i915,nouveau
snd_hwdep              20480  1 snd_hda_codec
wmi                    20480  2 mxm_wmi,nouveau
ideapad_laptop         20480  0 
sparse_keymap          16384  1 ideapad_laptop
snd_pcm               106496  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
snd_seq_midi           16384  0 
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
snd                    86016  23 snd_hda_codec_realtek,snd_soc_core,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_compress
video                  20480  2 i915,nouveau
i2c_hid                20480  0 
hid                   110592  5 i2c_hid,hid_multitouch,hid_generic,hid_sensor_hub,usbhid
soundcore              16384  2 snd,snd_hda_codec
snd_soc_sst_acpi       16384  0 
dw_dmac                16384  0 
i2c_designware_platform    16384  0 
dw_dmac_core           24576  1 dw_dmac
i2c_designware_core    16384  1 i2c_designware_platform
8250_dw                16384  0 
mac_hid                16384  0 
spi_pxa2xx_platform    24576  0 
acpi_pad               20480  0 
parport_pc             32768  0 
ppdev                  20480  0 
lp                     20480  0 
parport                45056  3 lp,ppdev,parport_pc
psmouse               114688  0 
ahci                   36864  3 
r8169                  81920  0 
libahci                32768  1 ahci
mii                    16384  1 r8169
sdhci_acpi             16384  0 
sdhci                  45056  1 sdhci_acpi

```
dmesg | egrep 'ath|wlan|firm|error|country'
```
[    0.880957] Loaded X.509 cert 'Magrathea: Glacier signing key: ed8339fd1a2f8dc0efdc5df7129dfb170a6f6dab'
[    2.440004] usb 1-1: device descriptor read/64, error -71
[    2.656168] usb 1-1: device descriptor read/64, error -71
[    2.984472] usb 1-1: device descriptor read/64, error -71
[    3.200660] usb 1-1: device descriptor read/64, error -71
[    3.825150] usb 1-1: device not accepting address 8, error -71
[    4.345568] usb 1-1: device not accepting address 9, error -71
[    7.876413] usb 1-1: device descriptor read/64, error -71
[    8.077517] EXT4-fs (sda9): re-mounted. Opts: errors=remount-ro
[    8.092593] usb 1-1: device descriptor read/64, error -71
[    8.141026] nouveau: probe of 0000:04:00.0 failed with error -22
[    8.420820] usb 1-1: device descriptor read/64, error -71
[    8.637025] usb 1-1: device descriptor read/64, error -71
[    9.261537] usb 1-1: device not accepting address 12, error -71
[    9.781940] usb 1-1: device not accepting address 13, error -71
[    9.792633] Bluetooth: hci0: don't support firmware rome 0x200
[   13.530837] audit: type=1400 audit(1441030187.130:17): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/telepathy/mission-control-5" pid=853 comm="apparmor_parser"
[   25.102367] usb 1-1: device descriptor read/64, error -71
[   25.318475] usb 1-1: device descriptor read/64, error -71
[   25.646780] usb 1-1: device descriptor read/64, error -71
[   25.862978] usb 1-1: device descriptor read/64, error -71
[   26.487427] usb 1-1: device not accepting address 16, error -71
[   27.007890] usb 1-1: device not accepting address 17, error -71
[   44.030434] usb 1-1: device descriptor read/64, error -71
[   44.246426] usb 1-1: device descriptor read/64, error -71
[   44.574617] usb 1-1: device descriptor read/64, error -71
[   44.790647] usb 1-1: device descriptor read/64, error -71
[   45.414858] usb 1-1: device not accepting address 21, error -71
[   45.935212] usb 1-1: device not accepting address 22, error -71
[   51.900072] usb 1-1: device descriptor read/64, error -71
[   52.116249] usb 1-1: device descriptor read/64, error -71
[   52.444509] usb 1-1: device descriptor read/64, error -71
[   52.660682] usb 1-1: device descriptor read/64, error -71
[   53.285164] usb 1-1: device not accepting address 25, error -71
[   53.805584] usb 1-1: device not accepting address 26, error -71
[   89.970700] usb 1-1: device descriptor read/64, error -71
[   90.186891] usb 1-1: device descriptor read/64, error -71
[   90.515154] usb 1-1: device descriptor read/64, error -71
[   90.731412] usb 1-1: device descriptor read/64, error -71
[   91.355835] usb 1-1: device not accepting address 30, error -71
[   91.876224] usb 1-1: device not accepting address 31, error -71
[  151.990004] usb 1-1: device descriptor read/64, error -71
[  152.206256] usb 1-1: device descriptor read/64, error -71
[  152.534741] usb 1-1: device descriptor read/64, error -71
[  152.750997] usb 1-1: device descriptor read/64, error -71
[  153.375823] usb 1-1: device not accepting address 34, error -71
[  153.896391] usb 1-1: device not accepting address 35, error -71
[  206.798295] usb 1-1: device descriptor read/64, error -71
[  207.014447] usb 1-1: device descriptor read/64, error -71
[  207.342791] usb 1-1: device descriptor read/64, error -71
[  207.558961] usb 1-1: device descriptor read/64, error -71
[  208.183392] usb 1-1: device not accepting address 38, error -71
[  208.703853] usb 1-1: device not accepting address 39, error -71
[  210.417312] usb 1-1: device descriptor read/64, error -71
[  210.633454] usb 1-1: device descriptor read/64, error -71
[  210.961701] usb 1-1: device descriptor read/64, error -71
[  211.177800] usb 1-1: device descriptor read/64, error -71
[  211.802373] usb 1-1: device not accepting address 42, error -71
[  212.322792] usb 1-1: device not accepting address 43, error -71
[  212.907198] usb 1-1: device descriptor read/64, error -71
[  213.123450] usb 1-1: device descriptor read/64, error -71
[  213.451705] usb 1-1: device descriptor read/64, error -71
[  213.667900] usb 1-1: device descriptor read/64, error -71
[  214.292334] usb 1-1: device not accepting address 46, error -71
[  214.812831] usb 1-1: device not accepting address 47, error -71
[  518.794090] usb 1-1: device descriptor read/64, error -71
[  519.010208] usb 1-1: device descriptor read/64, error -71
[  519.338441] usb 1-1: device descriptor read/64, error -71
[  519.554585] usb 1-1: device descriptor read/64, error -71
[  520.179097] usb 1-1: device not accepting address 50, error -71
[  520.699531] usb 1-1: device not accepting address 51, error -71
[  611.046371] usb 1-1: device descriptor read/64, error -71
[  611.262490] usb 1-1: device descriptor read/64, error -71
[  611.590777] usb 1-1: device descriptor read/64, error -71
[  611.806969] usb 1-1: device descriptor read/64, error -71
[  612.431496] usb 1-1: device not accepting address 54, error -71
[  612.951917] usb 1-1: device not accepting address 55, error -71
[  778.601581] usb 1-1: device descriptor read/64, error -71
[  778.817699] usb 1-1: device descriptor read/64, error -71
[  779.145923] usb 1-1: device descriptor read/64, error -71
[  779.362187] usb 1-1: device descriptor read/64, error -71
[  779.986587] usb 1-1: device not accepting address 58, error -71
[  782.672881] usb 1-1: device not accepting address 60, error -71
[  808.537773] usb 1-1: device descriptor read/64, error -71
[  808.753846] usb 1-1: device descriptor read/64, error -71
[  809.082170] usb 1-1: device descriptor read/64, error -71
[  809.298378] usb 1-1: device descriptor read/64, error -71
[  809.922821] usb 1-1: device not accepting address 64, error -71
[  810.443285] usb 1-1: device not accepting address 65, error -71
[  943.882864] usb 1-1: device descriptor read/64, error -71
[  944.099075] usb 1-1: device descriptor read/64, error -71
[  944.427287] usb 1-1: device descriptor read/64, error -71
[  944.643513] usb 1-1: device descriptor read/64, error -71
[  945.267921] usb 1-1: device not accepting address 68, error -71
[  945.788459] usb 1-1: device not accepting address 69, error -71
[ 1028.415032] usb 1-1: device descriptor read/64, error -71
[ 1028.631190] usb 1-1: device descriptor read/64, error -71
[ 1028.959460] usb 1-1: device descriptor read/64, error -71
[ 1029.175636] usb 1-1: device descriptor read/64, error -71
[ 1029.800142] usb 1-1: device not accepting address 73, error -71
[ 1030.320594] usb 1-1: device not accepting address 74, error -71
[ 1032.790561] usb 1-1: device descriptor read/64, error -71
[ 1033.006719] usb 1-1: device descriptor read/64, error -71
[ 1033.334995] usb 1-1: device descriptor read/64, error -71
[ 1033.551187] usb 1-1: device descriptor read/64, error -71
[ 1034.175662] usb 1-1: device not accepting address 77, error -71
[ 1049.600102] usb 1-1: device descriptor read/64, error -71
[ 1049.816302] usb 1-1: device descriptor read/64, error -71
[ 1050.144623] usb 1-1: device descriptor read/64, error -71
[ 1050.360717] usb 1-1: device descriptor read/64, error -71
[ 1050.985224] usb 1-1: device not accepting address 81, error -71
[ 1051.505643] usb 1-1: device not accepting address 82, error -71
[ 1906.719558] usb 1-1: device descriptor read/64, error -71
[ 1906.935735] usb 1-1: device descriptor read/64, error -71
[ 2021.692300] usb 1-1: device not accepting address 85, error -71
[ 2709.599260] usb 1-1: device descriptor read/64, error -71
[ 2709.815432] usb 1-1: device descriptor read/64, error -71
[ 2710.143696] usb 1-1: device descriptor read/64, error -71
[ 2710.359868] usb 1-1: device descriptor read/64, error -71
[ 2710.984369] usb 1-1: device not accepting address 91, error -71
[ 2711.504781] usb 1-1: device not accepting address 92, error -71
[ 2733.390449] usb 1-1: device descriptor read/64, error -71
[ 2733.606629] usb 1-1: device descriptor read/64, error -71
[ 2733.934889] usb 1-1: device descriptor read/64, error -71
[ 2734.151071] usb 1-1: device descriptor read/64, error -71
[ 2734.775553] usb 1-1: device not accepting address 95, error -71
[ 2735.295977] usb 1-1: device not accepting address 96, error -71
[ 2897.526868] usb 1-1: device descriptor read/64, error -71
[ 3620.273913] usb 1-1: device descriptor read/64, error -71
[ 3620.490091] usb 1-1: device descriptor read/64, error -71
[ 3621.278724] usb 1-1: device descriptor read/64, error -71
[ 3621.494898] usb 1-1: device descriptor read/64, error -71
[ 3621.823169] usb 1-1: device descriptor read/64, error -71
[ 3622.447667] usb 1-1: device descriptor read/64, error -71
[ 3622.663845] usb 1-1: device descriptor read/64, error -71
[ 3638.300455] usb 1-1: device descriptor read/64, error -71
[ 3638.516631] usb 1-1: device descriptor read/64, error -71
[ 3638.844897] usb 1-1: device descriptor read/64, error -71
[ 3639.061069] usb 1-1: device descriptor read/64, error -71
[ 3639.685567] usb 1-1: device not accepting address 110, error -71
[ 3640.205985] usb 1-1: device not accepting address 111, error -71
[ 3642.023480] usb 1-1: device descriptor read/64, error -71
[ 3642.239636] usb 1-1: device descriptor read/64, error -71
[ 3642.567904] usb 1-1: device descriptor read/64, error -71
[ 3642.784072] usb 1-1: device descriptor read/64, error -71
[ 3643.408566] usb 1-1: device not accepting address 115, error -71
[ 5293.523837] usb 1-1: device descriptor read/64, error -71
[ 5294.116336] usb 1-1: device descriptor read/64, error -71
[ 5294.332518] usb 1-1: device descriptor read/64, error -71
[ 5294.660774] usb 1-1: device descriptor read/64, error -71
[ 5294.876950] usb 1-1: device descriptor read/64, error -71
[ 5295.501458] usb 1-1: device not accepting address 123, error -71
[ 5296.021878] usb 1-1: device not accepting address 124, error -71
[ 5661.372617] usb 1-1: device descriptor read/64, error -71
[ 5676.897171] usb 1-1: device descriptor read/64, error -71
[ 5677.113299] usb 1-1: device descriptor read/64, error -71
[ 5677.441504] usb 1-1: device descriptor read/64, error -71
[ 5677.657782] usb 1-1: device descriptor read/64, error -71
[ 5678.282146] usb 1-1: device not accepting address 4, error -71
[ 5678.802649] usb 1-1: device not accepting address 6, error -71
[ 5979.545289] usb 1-1: device descriptor read/64, error -71
[ 5979.761376] usb 1-1: device descriptor read/64, error -71
[ 5980.089760] usb 1-1: device descriptor read/64, error -71
[ 5980.305851] usb 1-1: device descriptor read/64, error -71
[ 8544.830795] usb 1-1: device descriptor read/64, error -71
[ 8545.046917] usb 1-1: device descriptor read/64, error -71
[ 8545.375169] usb 1-1: device descriptor read/64, error -71
[ 8545.591381] usb 1-1: device descriptor read/64, error -71
[ 8546.215874] usb 1-1: device not accepting address 15, error -71
[ 8546.736175] usb 1-1: device not accepting address 16, error -71
[ 8550.535355] usb 1-1: device descriptor read/64, error -71
[ 8550.751567] usb 1-1: device descriptor read/64, error -71
[ 8551.079832] usb 1-1: device descriptor read/64, error -71
[ 8551.296002] usb 1-1: device descriptor read/64, error -71
[ 8551.920356] usb 1-1: device not accepting address 19, error -71
[ 8552.440882] usb 1-1: device not accepting address 20, error -71

```



iwconfig
```
eth0      no wireless extensions.

lo        no wireless extensions.

```

iwlist chan
```

eth0      no frequency information.


lo        no frequency information.

```
 sudo iwlist scan


```
eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.

```
modinfo ath10k_pci

```
filename:       /lib/modules/3.19.0-26-generic/updates/drivers/net/wireless/ath/ath10k/ath10k_pci.kofirmware:       ath10k/QCA6174/hw3.0/board.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-4.bin
firmware:       ath10k/QCA6174/hw2.1/board.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-5.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
firmware:       ath10k/QCA988X/hw2.0/firmware.bin
license:        Dual BSD/GPL
description:    Driver support for Atheros QCA988X PCIe devices
author:         Qualcomm Atheros
version:        backported from Linux (v4.2-rc1-0-gd770e55) using backports v4.2-rc1-1-0-g83a2518
srcversion:     51D77BB171261CA0793236B
alias:          pci:v0000168Cd0000003Esv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000003Csv*sd*bc*sc*i*
depends:        ath10k_core,compat
vermagic:       3.19.0-26-generic SMP mod_unload modversions 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)

```

rfkill list
```
0: ideapad_wlan: Wireless LAN    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
```

---

### Post by Hadaka on 2015-08-31
Hi, found this..seems logical..
[https://paulphilippov.com/arthttps://paulphilippov.com/articles/how-to-fix-device-not-accepting-address-erroricles/how-to-fix-device-not-accepting-address-error](https://paulphilippov.com/arthttps://paulphilippov.com/articles/how-to-fix-device-not-accepting-address-erroricles/how-to-fix-device-not-accepting-address-error)
Basically what is is saying is to, saftely remove the wifi usb..power down the computer, change the wifi usb to a different usb port and try again.
its close..its showing the frmware loaded..

---

### Post by Sam_Fels on 2015-08-31
Hmm yeah, I just tried again to shut everything down, dis-connect anything and reboot.

There's no USB wifi adapter to unplug though, it's an internal wifi card

---

### Post by praseodym on 2015-08-31
> ```
alias:          pci:v0000168Cd0000003Esv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000003Csv*sd*bc*sc*i*
```
The device ID 168c:0041 is not part of the driver. Did you create the file

**copy-list.ath** in the backports folder with this content before compiling?
```

COPYING
MAINTAINERS

drivers/net/wireless/Kconfig
drivers/net/wireless/Makefile

include/linux/ieee80211.h
include/linux/pci_ids.h
include/linux/ath9k_platform.h
include/uapi/linux/nl80211.h

include/net/cfg80211.h
include/net/cfg80211-wext.h
include/net/ieee80211_radiotap.h
include/net/lib80211.h
include/net/mac80211.h
include/net/regulatory.h

net/Makefile
net/Kconfig
net/wireless/
net/mac80211/

drivers/net/wireless/ath/
drivers/net/wireless/mac80211_hwsim.c
drivers/net/wireless/mac80211_hwsim.h
```

---

### Post by Sam_Fels on 2015-09-01
Yep, I think that was covered in Part 5 of the tutorial. Looks like the same exact file I had in there.

---

### Post by allanz on 2015-09-07
This may not be the optimal solution but I just purchased a Lenovo Flex 3 and wiped the drive clean then installed Linux Mint 17.2 64 bit and everything is working fine including the Sound Card, volume buttons, brightness, touchpad on off and wireless. So in case you cannot get it to work with the current version of Ubuntu this may be an option. You can always change it over later on if you desire.

---

### Post by Sam_Fels on 2015-09-08
> **allanz said:**
> This may not be the optimal solution but I just purchased a Lenovo Flex 3 and wiped the drive clean then installed Linux Mint 17.2 64 bit and everything is working fine including the Sound Card, volume buttons, brightness, touchpad on off and wireless. So in case you cannot get it to work with the current version of Ubuntu this may be an option. You can always change it over later on if you desire.

Hey thanks I appreciate the tip! That other stuff all works fine in Ubuntu 14.04, but my stuff is on an external anyway so I'll probably give that a shot when I have time. 

Goodbye to Unity I guess... was just finally getting used to it but Cinnamon looks pretty cool.

---

