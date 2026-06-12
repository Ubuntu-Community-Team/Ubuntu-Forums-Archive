---
title: "How to connect Huawai E303F Dongle in Ubuntu 14.04"
date: 2016-03-18
forum: Networking &amp; Wireless
---

### Post by vigneshwaran2 on 2016-03-18
I am having a Huawai E303F dongle, its not getting detected on my ubuntu 14.04. I tried some solutions but nothing worked. What is the problem with this? Please suggest a solution. Thank you.

---

### Post by jeremy31 on 2016-03-18
It would help if you post the results of this command 20 seconds after plugging in the dongle ```
lsusb; dmesg | tail -20
```

---

### Post by slickymaster on 2016-03-18
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by vigneshwaran2 on 2016-03-19
This is the output for the code:
```
lsusb; dmesg | tail -20
```
```
Bus 002 Device 004: ID 12d1:1506 Huawei Technologies Co., Ltd. E398 LTE/UMTS/GSM Modem/Networkcard
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[ 3154.119504] usb 2-3: GSM modem (1-port) converter now attached to ttyUSB2
[ 3154.119867] usb-storage 2-3:1.4: USB Mass Storage device detected
[ 3154.120273] scsi host8: usb-storage 2-3:1.4
[ 3154.120619] usb-storage 2-3:1.5: USB Mass Storage device detected
[ 3154.120859] scsi host9: usb-storage 2-3:1.5
[ 3154.214432] usbcore: registered new interface driver cdc_ncm
[ 3154.229877] usbcore: registered new interface driver cdc_wdm
[ 3154.291294] huawei_cdc_ncm 2-3:1.1: MAC-Address: 00:1e:10:1f:00:00
[ 3154.313429] huawei_cdc_ncm 2-3:1.1: cdc-wdm0: USB WDM device
[ 3154.314342] huawei_cdc_ncm 2-3:1.1 wwan0: register 'huawei_cdc_ncm' at usb-0000:00:1d.7-3, Huawei CDC NCM device, 00:1e:10:1f:00:00
[ 3154.314680] usbcore: registered new interface driver huawei_cdc_ncm
[ 3155.133448] scsi 9:0:0:0: Direct-Access     HUAWEI   TF CARD Storage  2.31 PQ: 0 ANSI: 2
[ 3155.136323] scsi 8:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[ 3155.136447] sd 9:0:0:0: Attached scsi generic sg1 type 0
[ 3155.139687] sr 8:0:0:0: [sr0] scsi-1 drive
[ 3155.139851] sr 8:0:0:0: Attached scsi CD-ROM sr0
[ 3155.139957] sr 8:0:0:0: Attached scsi generic sg2 type 5
[ 3155.141062] sd 9:0:0:0: [sdb] Attached SCSI removable disk
[ 3155.350792] ISO 9660 Extensions: Microsoft Joliet Level 1
[ 3155.351178] ISOFS: changing to secondary root


```

---

### Post by jeremy31 on 2016-03-19
Post ```
sudo blkid
``` after the USB dongle has been plugged in

---

### Post by vigneshwaran2 on 2016-03-19
```
/dev/sda1: UUID="c7bf7ed2-694f-4f38-809c-7aceabd26bf6" TYPE="ext4" 
/dev/sda2: LABEL="System Reserved" UUID="D0363930363918C4" TYPE="ntfs" 
/dev/sda3: LABEL="DISK I" UUID="1E5E3BE85E3BB77D" TYPE="ntfs" 
/dev/sda5: LABEL="DISK II" UUID="01D118A025644FA0" TYPE="ntfs" 
/dev/sda6: UUID="b1822412-1b45-4881-a44b-8cb8d98a463b" TYPE="swap" 
/dev/sr0: LABEL="Mobile Partner" TYPE="iso9660" 


```

---

### Post by jeremy31 on 2016-03-19
The dongle may show in Network Manager after ```
eject /dev/sr0
```

---

### Post by vigneshwaran2 on 2016-03-19
Network manager is already showing the dongle, my problem is, its not  getting connected. I have read some blogs and it says to install drivers  for huawai, but even after installing drivers its not getting  connected.

---

### Post by jeremy31 on 2016-03-19
What drivers are loaded ```
lsmod
```

---

### Post by vigneshwaran2 on 2016-03-24
```
Module                  Size  Used by
huawei_cdc_ncm         16384  0 
cdc_wdm                20480  1 huawei_cdc_ncm
cdc_ncm                28672  1 huawei_cdc_ncm
usbnet                 40960  2 huawei_cdc_ncm,cdc_ncm
nls_utf8               16384  1 
isofs                  40960  1 
option                 40960  2 
ppp_deflate            16384  0 
bsd_comp               16384  0 
ppp_async              20480  1 
crc_ccitt              16384  1 ppp_async
usb_wwan               20480  1 option
usbserial              40960  7 option,usb_wwan
uas                    24576  0 
usb_storage            57344  2 uas
bnep                   20480  2 
rfcomm                 61440  0 
bluetooth             430080  10 bnep,rfcomm
binfmt_misc            20480  1 
acer_wmi               20480  0 
snd_hda_codec_conexant    20480  1 
sparse_keymap          16384  1 acer_wmi
snd_hda_codec_generic    65536  1 snd_hda_codec_conexant
gpio_ich               16384  0 
snd_hda_intel          32768  3 
snd_hda_controller     32768  1 snd_hda_intel
snd_hda_codec         122880  4 snd_hda_codec_conexant,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              16384  1 snd_hda_codec
coretemp               16384  0 
snd_pcm                94208  3 snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_seq_midi           16384  0 
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            28672  1 snd_seq_midi
joydev                 20480  0 
snd_seq                57344  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
serio_raw              16384  0 
snd_timer              28672  2 snd_pcm,snd_seq
snd                    69632  16 snd_hwdep,snd_timer,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
lpc_ich                20480  0 
shpchp                 32768  0 
soundcore              16384  2 snd,snd_hda_codec
parport_pc             32768  0 
ppdev                  20480  0 
lp                     16384  0 
parport                40960  3 lp,ppdev,parport_pc
mac_hid                16384  0 
psmouse               102400  0 
wmi                    20480  1 acer_wmi
i915                  921600  3 
r8169                  73728  0 
ahci                   28672  1 
libahci                32768  1 ahci
mii                    16384  2 r8169,usbnet
i2c_algo_bit           16384  1 i915
video                  20480  2 i915,acer_wmi
drm_kms_helper        114688  1 i915
drm                   286720  5 i915,drm_kms_helper


```

---

### Post by jeremy31 on 2016-03-24
```
sudo -i
echo 12d1 1506 > /sys/bus/usb-serial/drivers/option1/new_id 
exit
```

---

### Post by vigneshwaran2 on 2016-03-24
Now I used another E303F dongle, its getting connected. I don't know the case for old one. Anyway thankyou so much for your guidance.

---

