---
title: "Ehternet and Wifi Not working on Ubuntu 14.04"
date: 2016-08-18
forum: Networking &amp; Wireless
---

### Post by mahi83 on 2016-08-18
Hi,

I recently updated my Ubuntu to 14.04. The wifi and ehternet stopped working. I am currently using the internet through a personal hotspot I created via usb. It would be great if my wifi started working again. I tried a bunch of things I read in forums and none of them worked. I am confused as what to do now.

I did the following: 

```
sudo apt-get update
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```

This is the output of 
```
lspci -nnk | grep -iA2 net
lsmod
rfkill list all
```


```
 ashkan@ashkan-ThinkPad-Twist:~$ lspci -nnk | grep -iA2 net
03:00.0 Network controller [0280]: Broadcom Corporation BCM43228 802.11a/b/g/n [14e4:4359]
    Subsystem: Broadcom Corporation Device [14e4:0607]
    Kernel driver in use: bcma-pci-bridge
ashkan@ashkan-ThinkPad-Twist:~$ lsmod
Module                  Size  Used by
b44                    40234  0 
mii                    13934  1 b44
b43                   387371  0 
mac80211              638901  1 b43
bcma                   52096  1 b43
ssb                    62379  2 b43,b44
rfcomm                 69160  8 
bnep                   19624  2 
binfmt_misc            17468  1 
nls_iso8859_1          12713  1 
ipheth                 13448  0 
snd_hda_codec_hdmi     46368  1 
snd_hda_codec_realtek    65904  1 
hid_sensor_als         13123  0 
hid_sensor_magn_3d     13209  0 
hid_sensor_gyro_3d     13209  0 
hid_sensor_accel_3d    13221  0 
hid_sensor_trigger     12916  8 hid_sensor_gyro_3d,hid_sensor_accel_3d,hid_sensor_als,hid_sensor_magn_3d
industrialio_triggered_buffer    12882  4 hid_sensor_gyro_3d,hid_sensor_accel_3d,hid_sensor_als,hid_sensor_magn_3d
kfifo_buf              13379  1 industrialio_triggered_buffer
industrialio           54069  7 hid_sensor_trigger,hid_sensor_gyro_3d,industrialio_triggered_buffer,hid_sensor_accel_3d,hid_sensor_als,kfifo_buf,hid_sensor_magn_3d
hid_sensor_iio_common    13755  4 hid_sensor_gyro_3d,hid_sensor_accel_3d,hid_sensor_als,hid_sensor_magn_3d
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
hid_sensor_hub         19536  6 hid_sensor_trigger,hid_sensor_gyro_3d,hid_sensor_accel_3d,hid_sensor_als,hid_sensor_magn_3d,hid_sensor_iio_common
videodev              134688  2 uvcvideo,videobuf2_core
btusb                  32412  0 
bluetooth             391136  22 bnep,btusb,rfcomm
intel_rapl             18773  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
snd_hda_intel          56611  3 
snd_hda_codec         193017  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
kvm                   455843  0 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  2 aesni_intel,ablk_helper
joydev                 17381  0 
serio_raw              13462  0 
i915                  788212  3 
rtsx_pci_ms            18151  0 
cfg80211              496328  2 b43,mac80211
drm_kms_helper         55071  1 i915
hid_multitouch         17407  0 
memstick               16966  1 rtsx_pci_ms
thinkpad_acpi          81013  1 
lpc_ich                21080  0 
drm                   303102  4 i915,drm_kms_helper
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
mei_me                 18627  0 
nvram                  14411  1 thinkpad_acpi
shpchp                 37032  0 
mei                    82276  1 mei_me
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
i2c_algo_bit           13413  1 i915
wmi                    19177  0 
snd_rawmidi            30731  1 snd_seq_midi
snd_seq                61616  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29549  2 snd_pcm,snd_seq
snd                    69416  18 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,thinkpad_acpi,snd_seq_device,snd_seq_midi
soundcore              12680  1 snd
video                  19476  1 i915
mac_hid                13205  0 
intel_rst              12890  0 
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 52659  0 
hid                   106148  4 hid_multitouch,hid_generic,hid_sensor_hub,usbhid
rtsx_pci_sdmmc         23274  0 
psmouse               106692  0 
ahci                   34091  2 
libahci                32716  1 ahci
rtsx_pci               46245  2 rtsx_pci_ms,rtsx_pci_sdmmc
ashkan@ashkan-ThinkPad-Twist:~$ rfkill list all
0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```

---

### Post by chili555 on 2016-08-18
This resource suggests that you have the wrong driver installed. I suggest you open a terminal and, with a working internet connection, do:```
sudo apt-get install bcmwl-kernel-source
```Reboot.

[https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by mahi83 on 2016-08-19
I did that. It's still not working.

```

03:00.0 Network controller [0280]: Broadcom Corporation BCM43228 802.11a/b/g/n [14e4:4359]
    Subsystem: Broadcom Corporation Device [14e4:0607]
    Kernel driver in use: bcma-pci-bridge
ashkan@ashkan-ThinkPad-Twist:~$ lsmod
Module                  Size  Used by
b43                   387371  0 
mac80211              638901  1 b43
bcma                   52096  1 b43
rfcomm                 69160  8 
bnep                   19624  2 
binfmt_misc            17468  1 
nls_iso8859_1          12713  1 
b44                    40234  0 
ssb                    62379  2 b43,b44
ipheth                 13448  0 
mii                    13934  1 b44
snd_hda_codec_hdmi     46368  1 
snd_hda_codec_realtek    65904  1 
rtsx_pci_ms            18151  0 
memstick               16966  1 rtsx_pci_ms
cfg80211              496328  2 b43,mac80211
hid_sensor_als         13123  0 
hid_sensor_magn_3d     13209  0 
hid_sensor_accel_3d    13221  0 
hid_sensor_gyro_3d     13209  0 
hid_sensor_trigger     12916  8 hid_sensor_gyro_3d,hid_sensor_accel_3d,hid_sensor_als,hid_sensor_magn_3d
industrialio_triggered_buffer    12882  4 hid_sensor_gyro_3d,hid_sensor_accel_3d,hid_sensor_als,hid_sensor_magn_3d
kfifo_buf              13379  1 industrialio_triggered_buffer
industrialio           54069  7 hid_sensor_trigger,hid_sensor_gyro_3d,industrialio_triggered_buffer,hid_sensor_accel_3d,hid_sensor_als,kfifo_buf,hid_sensor_magn_3d
hid_sensor_iio_common    13755  4 hid_sensor_gyro_3d,hid_sensor_accel_3d,hid_sensor_als,hid_sensor_magn_3d
btusb                  32412  0 
uvcvideo               80885  0 
bluetooth             391136  22 bnep,btusb,rfcomm
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
hid_sensor_hub         19536  6 hid_sensor_trigger,hid_sensor_gyro_3d,hid_sensor_accel_3d,hid_sensor_als,hid_sensor_magn_3d,hid_sensor_iio_common
intel_rapl             18773  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm                   455843  0 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  2 aesni_intel,ablk_helper
joydev                 17381  0 
serio_raw              13462  0 
thinkpad_acpi          81013  1 
nvram                  14411  1 thinkpad_acpi
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30731  1 snd_seq_midi
snd_hda_intel          56611  3 
hid_multitouch         17407  0 
snd_hda_codec         193017  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
lpc_ich                21080  0 
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_seq                61616  2 snd_seq_midi_event,snd_seq_midi
shpchp                 37032  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29549  2 snd_pcm,snd_seq
mei_me                 18627  0 
mei                    82276  1 mei_me
snd                    69416  18 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,thinkpad_acpi,snd_seq_device,snd_seq_midi
i915                  788212  3 
wmi                    19177  0 
soundcore              12680  1 snd
video                  19476  1 i915
drm_kms_helper         55071  1 i915
intel_rst              12890  0 
drm                   303102  4 i915,drm_kms_helper
mac_hid                13205  0 
i2c_algo_bit           13413  1 i915
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 52659  0 
hid                   106148  4 hid_multitouch,hid_generic,hid_sensor_hub,usbhid
rtsx_pci_sdmmc         23274  0 
psmouse               106692  0 
ahci                   34091  2 
libahci                32716  1 ahci
rtsx_pci               46245  2 rtsx_pci_ms,rtsx_pci_sdmmc
ashkan@ashkan-ThinkPad-Twist:~$ rfkill list all
0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


```

---

### Post by chili555 on 2016-08-19
Did you reboot?

What is the result of:```
cat /etc/modprobe.d/blacklist-bcm43.conf
```Also:```
sudo modprobe wl
sudo dpkg -s bcmwl-kernel-source
```

---

### Post by mahi83 on 2016-08-20
I did reboot. It still hasn't worked. 

```
ashkan@ashkan-ThinkPad-Twist:~$ cat /etc/modprobe.d/blacklist-bcm43.conf
# Warning: This file is autogenerated by bcmwl. All changes to this file will be lost.
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma
blacklist b44
install wl modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install wl ; modprobe --ignore-install b44

ashkan@ashkan-ThinkPad-Twist:~$ sudo modprobe wl
modprobe: ERROR: could not insert 'wl': Required key not available

ashkan@ashkan-ThinkPad-Twist:~$ sudo dpkg -s bcmwl-kernel-source
Package: bcmwl-kernel-source
Status: install ok installed
Priority: optional
Section: admin
Installed-Size: 7856
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: bcmwl
Version: 6.30.223.248+bdcom-0ubuntu0.2
Replaces: bcmwl-modaliases
Depends: dkms, linux-libc-dev, libc6-dev
Conflicts: bcmwl-modaliases
Description: Broadcom 802.11 Linux STA wireless driver source
 This package contains Broadcom 802.11 Linux STA wireless driver
 for use with Broadcom's BCM4311-, BCM4312-, BCM4313-, BCM4321-,
 BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228-based
 hardware.
Modaliases: wl(pci:v000014E4d*sv*sd*bc02sc80i*)
Original-Maintainer: Alberto Milone <alberto.milone@canonical.com>

```

---

### Post by chili555 on 2016-08-21
> modprobe: ERROR: could not insert 'wl': Required key not availablePlease check here: [http://askubuntu.com/questions/760075/cant-view-wifi-networks-after-upgrading-to-ubuntu-16-04](http://askubuntu.com/questions/760075/cant-view-wifi-networks-after-upgrading-to-ubuntu-16-04)

---

