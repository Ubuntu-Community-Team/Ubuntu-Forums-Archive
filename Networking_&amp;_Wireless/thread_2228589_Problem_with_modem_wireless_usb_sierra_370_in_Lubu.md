---
title: "Problem with modem wireless usb sierra 370 in Lubuntu 14.04 LTS"
date: 2014-06-08
forum: Networking &amp; Wireless
---

### Post by LMdMiguel on 2014-06-08
I've just install Lubuntu 14.04 LTS on a netbook Acer Aspire One. All the components work in a proper way except my modem wireless usb sierra 370 provided for Telefónica/Movistar. I've tried to install it by two differents methods:
[LIST=1]
[*] Downloading and installing the "escritorio movistar" from the Web of Movistar. This way doesn't work because there is no version of the escritorio movistar compatible with Lubuntu 14.04 LTS. 
[*]Making a manual instalation of the usb modem by creating a new network connetion this way: 
[/LIST]
[INDENT]Window "Network connection"
Press button "Add"
Type of connection: Mobile broadband + press "Create"
The install assistantant detect my usb modem Sierra Wireless USB 307 + "Continue"
Country: Spain + "Continue"
Supplier: Movistar (Telefónica + "Continue"
Plan: Movistar (USB modems)
Plan APN: movistar.es + "Continue" + "Apply"
Then a new window appears with this information:
Númber: *99#
User: movistar
Password: movistar
AP: movistar.es
Type: anyone
PIN: "my PIN code"
Save
but this way doesn't work either.
[/INDENT]
[INDENT]
[/INDENT]
Could you help me with the correct way for installing/configurating my usb modem?
Thanks for your help.

Luis

---

### Post by praseodym on 2014-06-08
Hi,

please show the outputs of:
```

lsusb
lsmod
usb-devices
rfkill list
```
Please check also:

[http://ubuntuforums.org/showthread.php?t=1831649&highlight=umts+checklist](http://ubuntuforums.org/showthread.php?t=1831649&highlight=umts+checklist)

---

### Post by LMdMiguel on 2014-06-08
Hi,

The outputs are:

```
jmap@JMAP:~$ lsusb
Bus 001 Device 002: ID 04f2:b084 Chicony Electronics Co., Ltd 
Bus 001 Device 007: ID 1199:68a3 Sierra Wireless, Inc. MC8700 Modem
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04d9:0499 Holtek Semiconductor, Inc. Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
jmap@JMAP:~$ lsmod
Module                  Size  Used by
sierra_net             18289  0 
usbnet                 37865  1 sierra_net
mii                    13654  1 usbnet
sierra                 18756  0 
usbserial              38902  1 sierra
usb_storage            48417  0 
michael_mic            12540  4 
arc4                   12536  2 
rfcomm                 53664  0 
bnep                   18895  2 
bluetooth             342263  10 bnep,rfcomm
snd_hda_codec_realtek    51029  1 
snd_hda_intel          42730  1 
snd_hda_codec         164067  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                85501  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
acer_wmi               31735  0 
sparse_keymap          13708  1 acer_wmi
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
lib80211_crypt_tkip    17456  0 
snd_rawmidi            25135  1 snd_seq_midi
wl                   3999690  0 
uvcvideo               71309  0 
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
i915                  705396  3 
videobuf2_vmalloc      13048  1 uvcvideo
joydev                 17101  0 
videobuf2_memops       13170  1 videobuf2_vmalloc
coretemp               13195  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
serio_raw              13230  0 
videobuf2_core         39258  1 uvcvideo
snd_timer              28584  2 snd_pcm,snd_seq
lib80211               14040  2 wl,lib80211_crypt_tkip
videodev              108503  2 uvcvideo,videobuf2_core
snd                    60871  12 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
lpc_ich                16864  0 
drm_kms_helper         46907  1 i915
cfg80211              409394  1 wl
soundcore              12600  1 snd
drm                   243792  4 i915,drm_kms_helper
i2c_algo_bit           13197  1 i915
parport_pc             31981  0 
ppdev                  17391  0 
lp                     13299  0 
wmi                    18673  1 acer_wmi
video                  18903  2 i915,acer_wmi
mac_hid                13037  0 
parport                40836  3 lp,ppdev,parport_pc
hid_generic            12492  0 
usbhid                 46997  0 
hid                    87604  2 hid_generic,usbhid
psmouse                91033  0 
ahci                   25579  2 
libahci                26754  1 ahci
atl1c                  40949  0 
jmap@JMAP:~$ usb-devices

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.13
S:  Manufacturer=Linux 3.13.0-27-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.7
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  7 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1199 ProdID=68a3 Rev=00.06
S:  Manufacturer=Sierra Wireless, Incorporated
S:  Product=USB 307
S:  SerialNumber=353255030037983
C:  #Ifs= 5 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=sierra
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=sierra
I:  If#= 3 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=sierra
I:  If#= 4 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=sierra
I:  If#= 7 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)

T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=02 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=04f2 ProdID=b084 Rev=78.03
S:  Manufacturer=Chicony Electronics Co., Ltd.
S:  Product=Webcam
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.13
S:  Manufacturer=Linux 3.13.0-27-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.13
S:  Manufacturer=Linux 3.13.0-27-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=04d9 ProdID=0499 Rev=02.90
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.13
S:  Manufacturer=Linux 3.13.0-27-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.13
S:  Manufacturer=Linux 3.13.0-27-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.3
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
jmap@JMAP:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
jmap@JMAP:~$
```

---

### Post by praseodym on 2014-06-08
Looks good in the 1st place. Check the checklist

---

### Post by wildmanne39 on 2014-06-08
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by LMdMiguel on 2014-06-08
Hi Praseodym,

I've checked the most items of the checklist (I can´t find where is the option "Enable Mobile Broadband" is set -click on the icon in the panel-) but the modem still not working.

Thanks.

---

