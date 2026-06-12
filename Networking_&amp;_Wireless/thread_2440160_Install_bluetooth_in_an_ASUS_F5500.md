---
title: "Install bluetooth in an ASUS F5500"
date: 2020-04-06
forum: Networking &amp; Wireless
---

### Post by rubencioak on 2020-04-06
Hi there,

I am completelly new to Ubuntu and I was just wondering if sb could help me with this one. The issue is that Ubuntu seems not to detect the bluetooth, when I go to settings the message is "No bluetooth found".

Any help would be much appreciated.

KR

---

### Post by praseodym on 2020-04-06
Hi and welcome here.

Please open a terminal console with CTRL+ALT+T and run the following commands

```
lspci -nnk
lsusb
usb-devices
lsmod
dmesg | grep blue # that pipe '|' is AltGr+<
```

---

### Post by rubencioak on 2020-04-07
Many thanks for your reply, I am leaving the outpus downhere[B]

Out put of comand [/B][COLOR=#000000][FONT=&amp]**lspci -nnk:**
[/FONT][/COLOR]```
00:00.0 Host bridge [0600]: Intel Corporation 3rd Gen Core processor DRAM Controller [8086:0154] (rev 09)    Subsystem: ASUSTeK Computer Inc. 3rd Gen Core processor DRAM Controller [1043:124d]
    Kernel driver in use: ivb_uncore
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
    Subsystem: ASUSTeK Computer Inc. 3rd Gen Core processor Graphics Controller [1043:124d]
    Kernel driver in use: i915
    Kernel modules: i915
00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04)
    Subsystem: ASUSTeK Computer Inc. 7 Series/C210 Series Chipset Family USB xHCI Host Controller [1043:124d]
    Kernel driver in use: xhci_hcd
00:16.0 Communication controller [0780]: Intel Corporation 7 Series/C216 Chipset Family MEI Controller #1 [8086:1e3a] (rev 04)
    Subsystem: ASUSTeK Computer Inc. 7 Series/C216 Chipset Family MEI Controller [1043:124d]
    Kernel driver in use: mei_me
    Kernel modules: mei_me
00:1a.0 USB controller [0c03]: Intel Corporation 7 Series/C216 Chipset Family USB Enhanced Host Controller #2 [8086:1e2d] (rev 04)
    Subsystem: ASUSTeK Computer Inc. 7 Series/C216 Chipset Family USB Enhanced Host Controller [1043:124d]
    Kernel driver in use: ehci-pci
00:1b.0 Audio device [0403]: Intel Corporation 7 Series/C216 Chipset Family High Definition Audio Controller [8086:1e20] (rev 04)
    Subsystem: ASUSTeK Computer Inc. 7 Series/C216 Chipset Family High Definition Audio Controller [1043:118f]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation 7 Series/C216 Chipset Family PCI Express Root Port 1 [8086:1e10] (rev c4)
    Kernel driver in use: pcieport
00:1c.1 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 [8086:1e12] (rev c4)
    Kernel driver in use: pcieport
00:1c.3 PCI bridge [0604]: Intel Corporation 7 Series/C216 Chipset Family PCI Express Root Port 4 [8086:1e16] (rev c4)
    Kernel driver in use: pcieport
00:1d.0 USB controller [0c03]: Intel Corporation 7 Series/C216 Chipset Family USB Enhanced Host Controller #1 [8086:1e26] (rev 04)
    Subsystem: ASUSTeK Computer Inc. 7 Series/C216 Chipset Family USB Enhanced Host Controller [1043:124d]
    Kernel driver in use: ehci-pci
00:1f.0 ISA bridge [0601]: Intel Corporation HM76 Express Chipset LPC Controller [8086:1e59] (rev 04)
    Subsystem: ASUSTeK Computer Inc. HM76 Express Chipset LPC Controller [1043:124d]
    Kernel driver in use: lpc_ich
    Kernel modules: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] [8086:1e03] (rev 04)
    Subsystem: ASUSTeK Computer Inc. 7 Series Chipset Family 6-port SATA Controller [AHCI mode] [1043:124d]
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 7 Series/C216 Chipset Family SMBus Controller [8086:1e22] (rev 04)
    Subsystem: ASUSTeK Computer Inc. 7 Series/C216 Chipset Family SMBus Controller [1043:124d]
    Kernel driver in use: i801_smbus
    Kernel modules: i2c_i801
02:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: AzureWave AW-NE186H [1a3b:1186]
    Kernel driver in use: ath9k
    Kernel modules: ath9k
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTL8411 PCI Express Card Reader [10ec:5289] (rev 01)
    Subsystem: ASUSTeK Computer Inc. RTL8411 PCI Express Card Reader [1043:202f]
    Kernel driver in use: rtsx_pci
    Kernel modules: rtsx_pci
03:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0a)
    Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:200f]
    Kernel driver in use: r8169
    Kernel modules: r8169

```[COLOR=#000000][FONT=&amp]

**Output of the command **[/FONT][/COLOR][COLOR=#000000][FONT=&amp]**lsusb:**
[/FONT][/COLOR]```

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f2:b40a Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 003 Device 002: ID 3938:1166 MOSART Semi. 2.4GHz Wireless Keyboard
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```[COLOR=#000000][FONT=&amp]

**Output of the command **[/FONT][/COLOR][COLOR=#000000][FONT=&amp]**usb-devices**
[/FONT][/COLOR]```
[COLOR=#000000][FONT=&amp]
T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1P:  Vendor=1d6b ProdID=0002 Rev=05.03S:  Manufacturer=Linux 5.3.0-45-generic ehci_hcdS:  Product=EHCI Host ControllerS:  SerialNumber=0000:00:1a.0C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mAI:  If#=0x0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 6D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1P:  Vendor=8087 ProdID=0024 Rev=00.00C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mAI:  If#=0x0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
T:  Bus=01 Lev=02 Prnt=02 Port=02 Cnt=01 Dev#=  3 Spd=480 MxCh= 0D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1P:  Vendor=04f2 ProdID=b40a Rev=69.64S:  Manufacturer=Chicony Electronics Co.,Ltd.S:  Product=USB2.0 HD UVC WebCamS:  SerialNumber=0x0001C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mAI:  If#=0x0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideoI:  If#=0x1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo
T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1P:  Vendor=1d6b ProdID=0002 Rev=05.03S:  Manufacturer=Linux 5.3.0-45-generic ehci_hcdS:  Product=EHCI Host ControllerS:  SerialNumber=0000:00:1d.0C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mAI:  If#=0x0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 6D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1P:  Vendor=8087 ProdID=0024 Rev=00.00C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mAI:  If#=0x0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 4D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1P:  Vendor=1d6b ProdID=0002 Rev=05.03S:  Manufacturer=Linux 5.3.0-45-generic xhci-hcdS:  Product=xHCI Host ControllerS:  SerialNumber=0000:00:14.0C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mAI:  If#=0x0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
T:  Bus=03 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=12  MxCh= 0D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1P:  Vendor=3938 ProdID=1166 Rev=01.05S:  Manufacturer=MOSART Semi.S:  Product=2.4GHz Wireless KeyboardC:  #Ifs= 2 Cfg#= 1 Atr=a0 MxPwr=100mAI:  If#=0x0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhidI:  If#=0x1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid
T:  Bus=03 Lev=01 Prnt=01 Port=01 Cnt=02 Dev#=  3 Spd=1.5 MxCh= 0D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1P:  Vendor=093a ProdID=2510 Rev=01.00S:  Manufacturer=PixArtS:  Product=USB Optical MouseC:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mAI:  If#=0x0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid
T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 4D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1P:  Vendor=1d6b ProdID=0003 Rev=05.03S:  Manufacturer=Linux 5.3.0-45-generic xhci-hcdS:  Product=xHCI Host ControllerS:  SerialNumber=0000:00:14.0C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mAI:  If#=0x0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub[/FONT][/COLOR]
```[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR][COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]**[COLOR=#000000][FONT=&amp]Output of the command [/FONT][/COLOR][COLOR=#000000][FONT=&amp]lsmod[/FONT][/COLOR]**[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]```

Module                  Size  Used by
ccm                    20480  6
nls_iso8859_1          16384  1
snd_hda_codec_hdmi     61440  1
snd_hda_codec_realtek   118784  1
snd_hda_codec_generic    81920  1 snd_hda_codec_realtek
ledtrig_audio          16384  2 snd_hda_codec_generic,snd_hda_codec_realtek
snd_hda_intel          49152  5
snd_intel_nhlt         20480  1 snd_hda_intel
snd_hda_codec         131072  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
snd_hda_core           90112  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
intel_rapl_msr         20480  0
intel_rapl_common      24576  1 intel_rapl_msr
snd_hwdep              20480  1 snd_hda_codec
uvcvideo               98304  0
snd_pcm               106496  5 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
snd_seq_midi           20480  0
snd_seq_midi_event     16384  1 snd_seq_midi
x86_pkg_temp_thermal    20480  0
snd_rawmidi            36864  1 snd_seq_midi
intel_powerclamp       20480  0
videobuf2_vmalloc      20480  1 uvcvideo
videobuf2_memops       20480  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
i915                 1949696  14
ath9k                 151552  0
drm_kms_helper        184320  1 i915
videobuf2_common       53248  2 videobuf2_v4l2,uvcvideo
snd_seq                69632  2 snd_seq_midi,snd_seq_midi_event
drm                   491520  6 drm_kms_helper,i915
videodev              208896  3 videobuf2_v4l2,uvcvideo,videobuf2_common
mc                     53248  4 videodev,videobuf2_v4l2,uvcvideo,videobuf2_common
coretemp               20480  0
ath9k_common           36864  1 ath9k
rtsx_pci_ms            24576  0
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
i2c_algo_bit           16384  1 i915
ath9k_hw              475136  2 ath9k_common,ath9k
memstick               20480  1 rtsx_pci_ms
ath                    36864  3 ath9k_common,ath9k,ath9k_hw
snd_timer              36864  2 snd_seq,snd_pcm
fb_sys_fops            16384  1 drm_kms_helper
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
mac80211              851968  1 ath9k
kvm_intel             278528  0
snd                    90112  20 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
cfg80211              712704  4 ath9k_common,ath9k,ath,mac80211
kvm                   659456  1 kvm_intel
sysimgblt              16384  1 drm_kms_helper
libarc4                16384  1 mac80211
irqbypass              16384  1 kvm
soundcore              16384  1 snd
mei_hdcp               24576  0
crct10dif_pclmul       16384  1
crc32_pclmul           16384  0
asus_nb_wmi            28672  0
ghash_clmulni_intel    16384  0
mei_me                 40960  1
mei                   110592  3 mei_hdcp,mei_me
aesni_intel           372736  4
asus_wmi               32768  1 asus_nb_wmi
aes_x86_64             20480  1 aesni_intel
crypto_simd            16384  1 aesni_intel
sparse_keymap          16384  1 asus_wmi
asus_wireless          20480  0
cryptd                 24576  2 crypto_simd,ghash_clmulni_intel
input_leds             16384  0
joydev                 28672  0
serio_raw              20480  0
glue_helper            16384  1 aesni_intel
mac_hid                16384  0
intel_cstate           20480  0
intel_rapl_perf        20480  0
sch_fq_codel           20480  2
parport_pc             40960  0
ppdev                  24576  0
lp                     20480  0
parport                53248  3 parport_pc,lp,ppdev
ip_tables              32768  0
x_tables               40960  1 ip_tables
autofs4                45056  2
hid_generic            16384  0
usbhid                 57344  0
hid                   131072  2 usbhid,hid_generic
rtsx_pci_sdmmc         28672  0
ahci                   40960  2
r8169                  81920  0
psmouse               155648  0
libahci                32768  1 ahci
lpc_ich                24576  0
i2c_i801               32768  0
realtek                20480  1
rtsx_pci               69632  2 rtsx_pci_sdmmc,rtsx_pci_ms
wmi                    32768  1 asus_wmi
video                  49152  2 asus_wmi,i915

```[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]
**[COLOR=#000000][FONT=&amp]Output of the command [/FONT][/COLOR][COLOR=#000000][FONT=&amp]dmesg | grep[/FONT][/COLOR]**[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]```
Usage: grep [OPTION]... PATTERNS [FILE]...Try 'grep --help' for more information.

```

---

### Post by praseodym on 2020-04-07
I dont see a BT device. Sure, there is one?!

---

### Post by rubencioak on 2020-04-07
I did use a wireless mouse in with the bluetooth when windows was installed, so 99% sure

---

### Post by rubencioak on 2020-04-08
could it be a problem with the drivers? and if so do you know where could I find them? KR

---

### Post by CelticWarrior on 2020-04-08
The Bluetooth could be included in the WiFi card as many are but it isn't: [https://h30434.www3.hp.com/t5/Notebooks-Archive-Read-Only/Does-my-Qualcomm-Atheros-AR9485-has-bluetooth/m-p/5390953/highlight/true#M1135967](https://h30434.www3.hp.com/t5/Notebooks-Archive-Read-Only/Does-my-Qualcomm-Atheros-AR9485-has-bluetooth/m-p/5390953/highlight/true#M1135967)

So, it can only be present as an additional module, typically in the USB bus. This is very unlikely in this kind of laptops.

>  			 				[INDENT] 					I did use a wireless mouse in with the bluetooth when windows was installed, so 99% sure 				[/INDENT] 			
  			   		


Do you remember the exact model of that mouse? Bluetooth keyboards and mice do exist but are sorta rare, the vast majority of this devices use a different, non-bluetooth, and often proprietary, RF transmitter/receiver dongle.

---

### Post by rubencioak on 2020-04-09
So, Is there no solution to this problem. The mouse I used to use was a XIAOMI MI, it has two modes, with the dongle and with the bluetooth, the latter was the one I used to work with.

Many thank to you both for your time and comments.

---

