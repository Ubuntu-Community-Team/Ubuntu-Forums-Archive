---
title: "Bluetooth ath9k module works only after using Windows"
date: 2017-07-28
forum: Networking &amp; Wireless
---

### Post by realefab on 2017-07-28
Hello,
I have an ASUS F556UV with this BlueTooth card:
03:00.0 Network controller: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01)

The device is detected and assigned to the module ath9k.
But it does not scan and it is not discoverable.

If I use Windows and then restart the PC it starts working.
But if I shutdown and turn it on it stops working until I run it again on Windows.

I have not understood the reason of this behavior.
What can I check?

Thanks,
Fabrizio

---

### Post by praseodym on 2017-07-28
Hi,

that is the wireless card! Please show
```

lsusb
usb-devices
lsmod
```
as terminal outputs

---

### Post by realefab on 2017-07-28
Thanks, here it is:

```
$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 04ca:3018 Lite-On Technology Corp. 
Bus 001 Device 004: ID 0bda:57de Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

```
$ usb-devices

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh=12
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=04.08
S:  Manufacturer=Linux 4.8.0-59-generic xhci-hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=04 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ff(vend.) Sub=ff Prot=ff MxPS=64 #Cfgs=  1
P:  Vendor=0bda ProdID=0129 Rev=39.60
S:  Manufacturer=Generic
S:  Product=USB2.0-CRW
S:  SerialNumber=20100201396000000
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=06 Prot=50 Driver=rtsx_usb

T:  Bus=01 Lev=01 Prnt=01 Port=05 Cnt=02 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0bda ProdID=57de Rev=00.14
S:  Manufacturer=04081-0005610016241047120
S:  Product=USB2.0 VGA UVC WebCam
S:  SerialNumber=200901010001
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo

T:  Bus=01 Lev=01 Prnt=01 Port=07 Cnt=03 Dev#=  6 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=04ca ProdID=3018 Rev=00.01
C:  #Ifs= 2 Cfg#= 1 Atr=e0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 6
D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1
P:  Vendor=1d6b ProdID=0003 Rev=04.08
S:  Manufacturer=Linux 4.8.0-59-generic xhci-hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
```

```
$ lsmod
Module                  Size  Used by
ath9k                 147456  0
ath3k                  20480  0
ccm                    20480  1
rfcomm                 77824  14
rtsx_usb_ms            20480  0
memstick               20480  1 rtsx_usb_ms
snd_hrtimer            16384  1
joydev                 20480  0
bbswitch               16384  0
cmac                   16384  1
bnep                   20480  2
binfmt_misc            20480  1
i2c_designware_platform    16384  0
asus_nb_wmi            24576  0
i2c_designware_core    20480  1 i2c_designware_platform
asus_wmi               28672  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
mxm_wmi                16384  0
snd_hda_codec_hdmi     45056  1
snd_soc_skl            65536  0
snd_soc_skl_ipc        45056  1 snd_soc_skl
snd_soc_sst_ipc        16384  1 snd_soc_skl_ipc
snd_soc_sst_dsp        32768  1 snd_soc_skl_ipc
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
snd_hda_ext_core       28672  1 snd_soc_skl
snd_soc_sst_match      16384  1 snd_soc_skl
snd_soc_core          233472  1 snd_soc_skl
snd_compress           20480  1 snd_soc_core
ac97_bus               16384  1 snd_soc_core
snd_pcm_dmaengine      16384  1 snd_soc_core
arc4                   16384  2
snd_hda_intel          36864  5
snd_hda_codec         135168  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
snd_hda_core           86016  7 snd_hda_intel,snd_hda_codec,snd_hda_ext_core,snd_soc_skl,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
kvm_intel             188416  0
snd_hwdep              16384  1 snd_hda_codec
kvm                   598016  1 kvm_intel
snd_pcm               110592  9 snd_hda_intel,snd_hda_codec,snd_pcm_dmaengine,snd_hda_ext_core,snd_hda_core,snd_soc_skl,snd_hda_codec_hdmi,snd_soc_core
snd_seq_midi           16384  0
ath9k_common           36864  1 ath9k
snd_seq_midi_event     16384  1 snd_seq_midi
irqbypass              16384  1 kvm
ath9k_hw              475136  2 ath9k,ath9k_common
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
aesni_intel           167936  4
ath                    32768  3 ath9k_hw,ath9k,ath9k_common
aes_x86_64             20480  1 aesni_intel
snd_rawmidi            32768  1 snd_seq_midi
lrw                    16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
cryptd                 24576  3 ablk_helper,ghash_clmulni_intel,aesni_intel
intel_cstate           16384  0
mac80211              757760  1 ath9k
uvcvideo               90112  0
intel_rapl_perf        16384  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
snd_seq                69632  3 snd_seq_midi_event,snd_seq_midi
videobuf2_v4l2         24576  1 uvcvideo
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
videodev              180224  3 uvcvideo,videobuf2_core,videobuf2_v4l2
cfg80211              581632  4 mac80211,ath9k,ath,ath9k_common
snd_timer              32768  3 snd_seq,snd_hrtimer,snd_pcm
input_leds             16384  0
snd                    86016  23 snd_compress,snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_soc_core,snd_pcm
media                  40960  2 uvcvideo,videodev
serio_raw              16384  0
soundcore              16384  1 snd
btusb                  45056  0
btrtl                  16384  1 btusb
idma64                 20480  0
virt_dma               16384  1 idma64
processor_thermal_device    16384  0
mei_me                 40960  0
shpchp                 36864  0
intel_lpss_pci         16384  0
mei                   102400  1 mei_me
intel_soc_dts_iosf     16384  1 processor_thermal_device
intel_pch_thermal      16384  0
hci_uart               94208  0
elan_i2c               36864  0
btbcm                  16384  2 hci_uart,btusb
btqca                  16384  1 hci_uart
btintel                16384  2 hci_uart,btusb
int3403_thermal        16384  0
bluetooth             552960  44 btrtl,hci_uart,btintel,btqca,bnep,btbcm,rfcomm,ath3k,btusb
wmi                    16384  2 asus_wmi,mxm_wmi
tpm_crb                16384  0
int3406_thermal        16384  0
intel_lpss_acpi        16384  0
intel_lpss             16384  2 intel_lpss_pci,intel_lpss_acpi
int3402_thermal        16384  0
int340x_thermal_zone    16384  3 int3402_thermal,int3403_thermal,processor_thermal_device
int3400_thermal        16384  0
acpi_pad               24576  0
asus_wireless          16384  0
mac_hid                16384  0
acpi_thermal_rel       16384  1 int3400_thermal
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
ip_tables              28672  0
x_tables               36864  1 ip_tables
autofs4                40960  2
rtsx_usb_sdmmc         28672  0
rtsx_usb               24576  2 rtsx_usb_sdmmc,rtsx_usb_ms
i915                 1314816  36
i2c_algo_bit           16384  1 i915
drm_kms_helper        167936  1 i915
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   368640  16 i915,drm_kms_helper
r8169                  81920  0
ahci                   36864  3
mii                    16384  1 r8169
libahci                32768  1 ahci
i2c_hid                20480  0
hid                   118784  1 i2c_hid
pinctrl_sunrisepoint    28672  0
video                  40960  3 asus_wmi,int3406_thermal,i915
pinctrl_intel          20480  1 pinctrl_sunrisepoint
fjes                   28672  0


```

Fabrizio

---

### Post by praseodym on 2017-07-28
```
Bus 001 Device 006: ID 04ca:3018 Lite-On Technology Corp. 

T:  Bus=01 Lev=01 Prnt=01 Port=07 Cnt=03 Dev#=  6 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=04ca ProdID=3018 Rev=00.01
C:  #Ifs= 2 Cfg#= 1 Atr=e0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=[COLOR="#FF0000"]btusb[/COLOR]
I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
```
There it is. It loads the module **btusb**, however, the correct module is **ath3k** which is also loaded. Lets check
```

sudo modprobe -rfv btusb ath3k
sudo modprobe -v ath3k
dmesg | egrep 'ath|blue'
hciconfig --all
```

---

### Post by realefab on 2017-07-28
Hi praseodym,
unfortunately using the commands you suggested makes the device disappear.
KDE says that there are no Bluetooth device anymore.

> [    3.864510] ath: phy0: Set BT/WLAN RX diversity capability
[    3.871377] ath: phy0: Enable LNA combining
[    3.873451] ath: phy0: ASPM enabled: 0x42
[    3.873472] ath: EEPROM regdomain: 0x6c
[    3.873473] ath: EEPROM indicates we should expect a direct regpair map
[    3.873474] ath: Country alpha2 being used: 00
[    3.873474] ath: Regpair used: 0x6c
[    3.994612] ath9k 0000:03:00.0 wlp3s0: renamed from wlan0
[    4.227549] audit: type=1400 audit(1501272666.569:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/telepathy/mission-control-5" pid=784 comm="apparmor_parser"
[    4.227553] audit: type=1400 audit(1501272666.569:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/telepathy/telepathy-*" pid=784 comm="apparmor_parser"
[    4.227557] audit: type=1400 audit(1501272666.569:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/telepathy/telepathy-*//pxgsettings" pid=784 comm="apparmor_parser"
[    4.227560] audit: type=1400 audit(1501272666.569:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/telepathy/telepathy-*//sanitized_helper" pid=784 comm="apparmor_parser"
[    4.227564] audit: type=1400 audit(1501272666.569:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/telepathy/telepathy-ofono" pid=784 comm="apparmor_parser"
[   50.977768] usbcore: registered new interface driver ath3k



What do you suggest?

Thanks,
Fabrizio

---

### Post by praseodym on 2017-07-28
Lets try the other one only
```

sudo modprobe -rfv ath3k
sudo modprobe -v btusb
dmesg | grep blue
```

---

### Post by realefab on 2017-07-28
Now the device is detected, but it can not scan neither discovered.
It only works after a reboot from Windows.

```
$ dmesg | grep Blue
[    3.675797] Bluetooth: Core ver 2.21
[    3.675807] Bluetooth: HCI device and connection manager initialized
[    3.675810] Bluetooth: HCI socket layer initialized
[    3.675811] Bluetooth: L2CAP socket layer initialized
[    3.675815] Bluetooth: SCO socket layer initialized
[    3.688103] Bluetooth: HCI UART driver ver 2.3
[    3.688104] Bluetooth: HCI UART protocol H4 registered
[    3.688105] Bluetooth: HCI UART protocol BCSP registered
[    3.688105] Bluetooth: HCI UART protocol LL registered
[    3.688106] Bluetooth: HCI UART protocol ATH3K registered
[    3.688106] Bluetooth: HCI UART protocol Three-wire (H5) registered
[    3.688131] Bluetooth: HCI UART protocol Intel registered
[    3.688144] Bluetooth: HCI UART protocol BCM registered
[    3.688145] Bluetooth: HCI UART protocol QCA registered
[    3.688145] Bluetooth: HCI UART protocol AG6XX registered
[    4.405642] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    4.405643] Bluetooth: BNEP filters: protocol multicast
[    4.405646] Bluetooth: BNEP socket layer initialized
[   15.163259] Bluetooth: RFCOMM TTY layer initialized
[   15.163308] Bluetooth: RFCOMM socket layer initialized
[   15.163322] Bluetooth: RFCOMM ver 1.11
[   45.316526] Bluetooth: hci0 urb ffff99956699e840 failed to resubmit (2)


```

Thanks,
Fabrizio

---

### Post by praseodym on 2017-07-28
Maybe the Windows firmware unloads pretty slow. Does it work after a cold start in Linux after waiting for some minutes?

---

### Post by realefab on 2017-07-29
No. If it is started directly in Linux it does not work (device detected, but not scan or discovery).

I thought it was not working at all then by chance I discover it works if reboot in Linux after Windows.
But it is enough to suspend it and it stops working.

Thanks,
Fabrizio

---

