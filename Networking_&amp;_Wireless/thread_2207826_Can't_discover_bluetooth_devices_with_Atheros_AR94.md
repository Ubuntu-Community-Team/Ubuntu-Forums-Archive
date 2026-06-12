---
title: "Can't discover bluetooth devices with Atheros AR9462"
date: 2014-02-25
forum: Networking &amp; Wireless
---

### Post by mr-lahorde on 2014-02-25
Hi,

I've an Atheros 9462 Wifi/Bluetooth devices. I cannot discover any bluetooth devices using graphical bluetooth manager or hcitool. Moreover I'm not visible for other devices. I upgraded kernel to 3.11.0 to have latest bug fixes [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1024884](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1024884)
Now I've spent enough time on this issue :confused: 

I need your help, any suggestions to have bluetooth working?

Here are some useful info :

```
~ :( $ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

```
```

~ $ uname -a
Linux 106326-HP-9470m 3.11.0-031100-generic #201309021735 SMP Mon Sep 2 21:36:21 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux




```

```
~ $ lspci
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation QM77 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
02:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 30)
02:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 30)
03:00.0 Network controller: Qualcomm Atheros AR9462 Wireless Network Adapter (rev 01)

```


```
~ $ lsmod
Module                  Size  Used by
ath9k                 105303  0 
cdc_acm                28807  0 
hid_generic            12548  0 
usbhid                 53329  0 
hid                   105557  2 hid_generic,usbhid
snd_hda_codec_hdmi     41688  1 
snd_hda_codec_idt      55053  1 
joydev                 17613  0 
pci_stub               12622  1 
vboxpci                23236  0 
vboxnetadp             13382  0 
vboxnetflt             23478  0 
vboxdrv               283008  3 vboxpci,vboxnetadp,vboxnetflt
uvcvideo               82247  0 
videobuf2_core         40785  1 uvcvideo
videodev              138443  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
btusb                  28277  0 
snd_hda_intel          53038  3 
snd_hda_codec         194727  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13613  1 snd_hda_codec
snd_pcm               107140  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
tpm_infineon           17410  0 
hp_wmi                 18202  0 
sparse_keymap          13890  1 hp_wmi
snd_seq_midi           13324  0 
snd_rawmidi            30416  1 snd_seq_midi
arc4                   12573  2 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                66061  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29989  2 snd_pcm,snd_seq
mac80211              538181  1 ath9k
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
ath9k_common           13550  1 ath9k
ath9k_hw              436819  2 ath9k,ath9k_common
snd                    69657  17 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ath                    28657  3 ath9k,ath9k_common,ath9k_hw
cfg80211              490880  3 ath9k,mac80211,ath
soundcore              12680  1 snd
mei_me                 18539  0 
bnep                   23966  2 
compat                 13991  5 ath9k,mac80211,ath9k_common,ath9k_hw,cfg80211
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
mei                    78448  1 mei_me
lpc_ich                21163  0 
psmouse               104064  0 
parport_pc             32866  0 
tpm_tis                19255  0 
serio_raw              13413  0 
rfcomm                 74589  12 
bluetooth             391564  24 btusb,bnep,rfcomm
ppdev                  17711  0 
i915                  682856  3 
hp_accel               26012  0 
drm_kms_helper         53178  1 i915
lis3lv02d              20280  1 hp_accel
input_polldev          13896  1 lis3lv02d
drm                   298236  4 i915,drm_kms_helper
mac_hid                13253  0 
wmi                    19256  1 hp_wmi
i2c_algo_bit           13564  1 i915
video                  19574  1 i915
binfmt_misc            17508  1 
lp                     17799  0 
parport                42466  3 parport_pc,ppdev,lp
e1000e                257364  0 
ahci                   30063  3 
libahci                32088  1 ahci
ptp                    18627  1 e1000e
pps_core               19027  1 ptp
sdhci_pci              19116  0 
sdhci                  43126  1 sdhci_pci

```

```
~ $ cat /etc/modprobe.d/ath9k.conf
options ath9k nohwcrypt=1

```
```
~ $ hcitool dev
Devices:
    hci0    70:18:8B:64:39:F2

```


```
~ $ hcitool inq
Inquiring ...



```

No devices are discovered...

Thanks for your help

---

### Post by varunendra on 2014-02-25
Welcome to the forums mr-lahorde !

Have you tried installing BlueMan manager? Try it if not -
```
sudo apt-get install blueman
```

It provides some extra controls which may help sometimes. But if the bluetooth can't be turned on at all, then it probably won't help. In that case, please post outputs of the following commands -
```
lsusb
usb-devices
```
The second command will produce a long output list. We are interested in only Bluetooth related information. If you can't identify it, post the whole output. If you can, post only that part.

---

### Post by mr-lahorde on 2014-02-26
Hi,

Thanks for your help.
I'm able to connect bluetooth but I cannot discover anty devices or be discovered from Atheros chipsed. I've tried blueman with same results. 

```
lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 006: ID 0424:5434 Standard Microsystems Corp. 
Bus 004 Device 003: ID 0424:5434 Standard Microsystems Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 138a:003d Validity Sensors, Inc. 
Bus 001 Device 004: ID 05c8:034b Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 002 Device 003: ID 0cf3:311e Atheros Communications, Inc. 
Bus 003 Device 007: ID 058f:9254 Alcor Micro Corp. Hub
Bus 003 Device 008: ID 03f0:0024 Hewlett-Packard KU-0316 Keyboard
Bus 003 Device 009: ID 046d:c077 Logitech, Inc.
```

```
~ $ usb-devices 


T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 3
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.11
S:  Manufacturer=Linux 3.11.0-031100-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1a.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0024 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=01 Lev=02 Prnt=02 Port=00 Cnt=01 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=ff(vend.) Sub=11 Prot=ff MxPS= 8 #Cfgs=  1
P:  Vendor=138a ProdID=003d Rev=01.04
S:  SerialNumber=00b0a60d4990
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 4 Cls=ff(vend.) Sub=00 Prot=00 Driver=(none)


T:  Bus=01 Lev=02 Prnt=02 Port=02 Cnt=02 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=05c8 ProdID=034b Rev=01.12
S:  Manufacturer=SPCA2062 PC Camera
S:  Product=HP HD Webcam [Fixed]
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo


T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 3
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.11
S:  Manufacturer=Linux 3.11.0-031100-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0024 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


[COLOR=#b22222]T:  Bus=02 Lev=02 Prnt=02 Port=05 Cnt=01 Dev#=  3 Spd=12  MxCh= 0[/COLOR]
[COLOR=#b22222]D:  Ver= 1.10 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1[/COLOR]
[COLOR=#b22222]P:  Vendor=0cf3 ProdID=311e Rev=00.01[/COLOR]
[COLOR=#b22222]C:  #Ifs= 2 Cfg#= 1 Atr=e0 MxPwr=100mA[/COLOR]
[COLOR=#b22222]I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb[/COLOR]
[COLOR=#b22222]I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb[/COLOR]


T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 4
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.11
S:  Manufacturer=Linux 3.11.0-031100-generic xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=03 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  6 Spd=480 MxCh= 4
D:  Ver= 2.10 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0424 ProdID=5434 Rev=30.82
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=2mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=03 Lev=02 Prnt=06 Port=00 Cnt=01 Dev#=  7 Spd=12  MxCh= 4
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=058f ProdID=9254 Rev=03.12
S:  Manufacturer=ALCOR
S:  Product=Generic USB Hub
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=03 Lev=02 Prnt=06 Port=02 Cnt=02 Dev#=  8 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=03f0 ProdID=0024 Rev=03.00
S:  Manufacturer=CHICONY
S:  Product=HP Basic USB Keyboard
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid


T:  Bus=03 Lev=02 Prnt=06 Port=03 Cnt=03 Dev#=  9 Spd=1.5 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=046d ProdID=c077 Rev=67.00
S:  Manufacturer=Logitech
S:  Product=USB Optical Mouse
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=98mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid


T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 4
D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1
P:  Vendor=1d6b ProdID=0003 Rev=03.11
S:  Manufacturer=Linux 3.11.0-031100-generic xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=04 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  3 Spd=5000 MxCh= 4
D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1
P:  Vendor=0424 ProdID=5434 Rev=30.82
S:  Manufacturer=SMSC
S:  Product=USB5534
S:  SerialNumber=1239567
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub



```

I've just tried with some USB dongle and discovery works fine...

Lah

---

### Post by varunendra on 2014-02-26
Hmm.. let's try an old trick to reset the entire USB hub on which the bluetooth resides. It will simulate a logical reset of the bluetooth adapter without really unplugging it, works 100% for me here (yes, I had the same problem, still happens often, this one always works for me). In a terminal, run these commands -
```
echo -n "0000:00:1a.0" | sudo tee /sys/bus/pci/drivers/ehci_hcd/unbind
echo -n "0000:00:1a.0" | sudo tee /sys/bus/pci/drivers/ehci_hcd/bind
```
Keep a gap of about 4 seconds or more between the two commands. Does it help enabling the bluetooth? Post back if you get any error messages.

If this works, we can make it easier. If not, or if you get errors, please post back the output of -
```
find /sys/bus/pci/drivers -maxdepth 2 -type l -name "*00:1a.0"
```

---

### Post by mr-lahorde on 2014-02-27
Hi Varun,

Thanks for your help.
I've typed both commands :

```
echo -n "0000:00:1a.0" |sudo tee  /sys/bus/pci/drivers/ehci-pci/unbind
echo -n "0000:00:1a.0" |sudo tee  /sys/bus/pci/drivers/ehci-pci/bind 
```

After, I still cannot discover some bluetooth devices.

```
find /sys/bus/pci/drivers -maxdepth 2 -type l -name "*00:1a.0"
/sys/bus/pci/drivers/ehci-pci/0000:00:1a.0

```

Bluetooth is enabled, it just can't discover some devices. 


```
$ hcitool dev
Devices:
    hci0    70:18:8B:64:39:F2




```
Lah

---

### Post by varunendra on 2014-02-27
In BlueMan drop-down menu > Adapters..., is the Visibility set to "Always visible" ?

In the "Local Services" from the same menu, are all the four options enabled?

If yes, then I'm out of ideas now. I've tried whatever bit I knew about bluetooth (and I don't know much), and it's probably time to file a bug report or add yourself to the "Affects Me too" list of one of the existing ones : [https://launchpad.net/ubuntu/+source/bluez/+bugs](https://launchpad.net/ubuntu/+source/bluez/+bugs)

Probably you may find a workaround in one of those reports too, I didn't try too hard to find one.

---

