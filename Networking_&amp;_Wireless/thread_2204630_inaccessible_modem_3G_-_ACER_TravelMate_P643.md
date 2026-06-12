---
title: "inaccessible modem 3G - ACER TravelMate P643"
date: 2014-02-09
forum: Networking &amp; Wireless
---

### Post by zielos on 2014-02-09
I have a laptop with built-in 3G modem, and unfortunately it is not detected by the system. Perhaps this is related to an error that occurs during starting system 

```
usb 1-1.4: string descriptor 0 read error: -22
``` 

and, unfortunately, I do not know how to deal with it?

---

### Post by praseodym on 2014-02-09
Hi,

please have a look here:

[http://ubuntuforums.org/showthread.php?t=1831649&highlight=umts+checklist](http://ubuntuforums.org/showthread.php?t=1831649&highlight=umts+checklist)

and show those terminal outputs.

---

### Post by zielos on 2014-02-09
ok, my terminal outputs:

```
root@pawacer:~# lsusb
Bus 002 Device 003: ID 1c7a:0603 LighTuning Technology Inc. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 1bcf:2c17 Sunplus Innovation Technology Inc. 
Bus 001 Device 020: ID 0489:e04e Foxconn / Hon Hai 
Bus 001 Device 021: ID 12d1:1571 Huawei Technologies Co., Ltd. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
root@pawacer:~# 
root@pawacer:~# lsmod
Module                  Size  Used by
parport_pc             32701  0 
ppdev                  17671  0 
rfcomm                 69130  12 
bnep                   19704  2 
nls_iso8859_1          12713  1 
snd_hda_codec_hdmi     41117  1 
snd_hda_codec_conexant    56990  1 
x86_pkg_temp_thermal    14162  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm_intel             138567  0 
kvm                   431720  1 kvm_intel
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
cryptd                 20359  1 ghash_clmulni_intel
joydev                 17377  0 
acer_wmi               32522  0 
sparse_keymap          13948  1 acer_wmi
cdc_mbim               13176  0 
cdc_ncm                20024  1 cdc_mbim
cdc_wdm                18919  1 cdc_mbim
uvcvideo               80885  0 
usbnet                 39525  2 cdc_mbim,cdc_ncm
videobuf2_vmalloc      13216  1 uvcvideo
mii                    13934  1 usbnet
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40499  1 uvcvideo
videodev              133509  2 uvcvideo,videobuf2_core
snd_hda_intel          48171  3 
snd_hda_codec         188738  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
arc4                   12608  2 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
microcode              23576  0 
snd_rawmidi            30095  1 snd_seq_midi
ath9k                 155779  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
ath9k_common           13859  1 ath9k
ath9k_hw              444732  2 ath9k_common,ath9k
psmouse                97655  0 
ath                    23827  3 ath9k_common,ath9k,ath9k_hw
serio_raw              13413  0 
mac80211              597268  1 ath9k
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
ath3k                  13318  0 
rtsx_pci_ms            18151  0 
memstick               16760  1 rtsx_pci_ms
btusb                  28267  0 
cfg80211              480503  3 ath,ath9k,mac80211
bluetooth             372041  23 bnep,ath3k,btusb,rfcomm
snd_timer              29433  2 snd_pcm,snd_seq
snd                    69141  17 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
i915                  661261  3 
lpc_ich                21080  0 
soundcore              12680  1 snd
drm_kms_helper         52710  1 i915
mei_me                 18421  0 
drm                   297056  4 i915,drm_kms_helper
mei                    77782  1 mei_me
i2c_algo_bit           13413  1 i915
wmi                    19070  1 acer_wmi
tpm_tis                19123  0 
video                  19318  2 i915,acer_wmi
mac_hid                13205  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
rtsx_pci_sdmmc         23527  0 
tg3                   162318  0 
ahci                   25819  3 
libahci                31928  1 ahci
ptp                    18580  1 tg3
rtsx_pci               45546  2 rtsx_pci_ms,rtsx_pci_sdmmc
pps_core               19057  1 ptp
root@pawacer:~# usb-devices

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.11
S:  Manufacturer=Linux 3.11.0-15-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1a.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0024 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=02 Prnt=02 Port=00 Cnt=01 Dev#= 21 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  2
P:  Vendor=12d1 ProdID=1571 Rev=00.00
S:  Manufacturer=Huawei Technologies
S:  Product=HUAWEI MBIM Device
C:  #Ifs= 2 Cfg#= 2 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=02(commc) Sub=0e Prot=00 Driver=cdc_mbim
I:  If#= 1 Alt= 1 #EPs= 2 Cls=0a(data ) Sub=00 Prot=02 Driver=cdc_mbim

T:  Bus=01 Lev=02 Prnt=02 Port=03 Cnt=02 Dev#= 20 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0489 ProdID=e04e Rev=00.02
C:  #Ifs= 2 Cfg#= 1 Atr=e0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb

T:  Bus=01 Lev=02 Prnt=02 Port=04 Cnt=03 Dev#=  5 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1bcf ProdID=2c17 Rev=00.12
S:  Manufacturer=SunplusIT INC.
S:  Product=HD WebCam
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.11
S:  Manufacturer=Linux 3.11.0-15-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0024 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=02 Prnt=02 Port=05 Cnt=01 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1c7a ProdID=0603 Rev=02.00
S:  Manufacturer=EgisTec
S:  Product=EgisTec_ES603
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=00 Prot=00 Driver=(none)

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 4
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.11
S:  Manufacturer=Linux 3.11.0-15-generic xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 4
D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1
P:  Vendor=1d6b ProdID=0003 Rev=03.11
S:  Manufacturer=Linux 3.11.0-15-generic xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


```

---

### Post by praseodym on 2014-02-09
Try this driver:
```

sudo modprobe -rfv cdc_mbim
sudo modprobe -v cdc_ncn
```

---

### Post by zielos on 2014-02-10
thanks for the reply, bat unfortunately, it did not help: (
```
root@pawacer:~# modprobe -rfv cdc_mbim
rmmod cdc_mbim
rmmod cdc_wdm
rmmod cdc_ncm
rmmod usbnet
rmmod mii
root@pawacer:~# modprobe -v cdc_ncm
insmod /lib/modules/3.11.0-15-generic/kernel/drivers/net/mii.ko 
insmod /lib/modules/3.11.0-15-generic/kernel/drivers/net/usb/usbnet.ko 
insmod /lib/modules/3.11.0-15-generic/kernel/drivers/net/usb/cdc_ncm.ko 

```

any ideas ...?

---

