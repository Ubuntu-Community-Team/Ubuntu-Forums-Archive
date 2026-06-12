---
title: "Bluetooth not working on Asus x551ma-sx090D"
date: 2014-08-25
forum: Networking &amp; Wireless
---

### Post by rene14 on 2014-08-25
I'm using Ubuntu 14.04 64bit on my newly bought Asus X551MA-SX090D and I can't manage my bluetooth interface to get working, though wifi is functioning well. On Windows everything is OK, so it must be some driver issue.
lspci reports:
$ lspci -nn -d 14e4:02:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
 
Please give me a hint how to get this done.
Thanks!

---

### Post by varunendra on 2014-08-25
Welcome to the forums rene14!

Please post back the outputs of -
```
rfkill list all
usb-devices | grep -A2 -B6 btusb
lsusb
lspci
```
While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by rene14 on 2014-08-26
```

rene@notebook:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
-----------------------------------
rene@notebook:~$ usb-devices | grep -A2 -B6 btusb
- has no output whatsoever
-----------------------------------
rene@notebook:~$ lsusb
Bus 001 Device 005: ID 04f2:b404 Chicony Electronics Co., Ltd 
Bus 001 Device 007: ID 04ca:2006 Lite-On Technology Corp. 
Bus 001 Device 003: ID 1c4f:0034 SiGma Micro 
Bus 001 Device 002: ID 8087:07e6 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
---------------------------------------------------------------------------
rene@notebook:~$ lspci
00:00.0 Host bridge: Intel Corporation Atom Processor Z36xxx/Z37xxx Series SoC Transaction Register (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Graphics & Display (rev 0c)
00:13.0 SATA controller: Intel Corporation Device 0f23 (rev 0c)
00:1a.0 Encryption controller: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Trusted Execution Engine (rev 0c)
00:1b.0 Audio device: Intel Corporation Atom Processor Z36xxx/Z37xxx Series High Definition Audio Controller (rev 0c)
00:1c.0 PCI bridge: Intel Corporation Device 0f48 (rev 0c)
00:1c.1 PCI bridge: Intel Corporation Device 0f4a (rev 0c)
00:1c.3 PCI bridge: Intel Corporation Device 0f4e (rev 0c)
00:1d.0 USB controller: Intel Corporation Atom Processor Z36xxx/Z37xxx Series USB EHCI (rev 0c)
00:1f.0 ISA bridge: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Power Control Unit (rev 0c)
00:1f.3 SMBus: Intel Corporation Device 0f12 (rev 0c)
02:00.0 Network controller: Broadcom Corporation BCM43142 802.11b/g/n (rev 01)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5286 (rev 01)
03:00.2 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 06)

```

---

### Post by varunendra on 2014-08-26
> **varunendra said:**
> While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

Did you read the above part of my post?

---

### Post by rene14 on 2014-08-26
Sorry, I didn't... I corrected my post.

---

### Post by praseodym on 2014-08-26
Please show
```

usb-devices
```without filter. Did you check the BIOS settings for Bluetooth?

---

### Post by rene14 on 2014-08-28
Of course I checked the BIOS, everything is OK there. As I said in my original post, under Windows bluetooth works all right.

```

rene@notebook:~$ usb-devices 


T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.13
S:  Manufacturer=Linux 3.13.0-34-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 4
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=07e6 Rev=00.12
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=01 Lev=02 Prnt=02 Port=01 Cnt=01 Dev#=  7 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1c05 Rev=01.02
S:  Manufacturer=HUAWEI
S:  Product=HUAWEI Mobile
C:  #Ifs= 5 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 3 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 4 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage


T:  Bus=01 Lev=02 Prnt=02 Port=03 Cnt=02 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=04f2 ProdID=b404 Rev=69.63
S:  Manufacturer=Chicony Electronics Co.,Ltd.
S:  Product=USB2.0 HD UVC WebCam
S:  SerialNumber=0x0001
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo

```

---

### Post by varunendra on 2014-08-29
Your bluetooth device is detected by the system, and lists it in 'lsusb' -
```
Bus 001 Device 007: ID 04ca:2006 Lite-On Technology Corp.
```

But evidently, it doesn't seem to recognize it as a bluetooth device, as it is not listed in 'usb-devices'. It is a bit odd though, it should have been there even if not recognized for its kind.

Can you please confirm that running lsusb, and usb-devices immediately after 'lsusb', produces the same results as you posted above? That is, one lists the 'Lite On' device, and the other doesn't? I wonder if it would have disappeared from lsusb too when it doesn't show up in usb-devices. In which case, it could be blamed to a buggy USB bus/driver.

Please also post the output of -
```
lsmod
```

---

### Post by rene14 on 2014-09-04
```

rene@notebook:~$ lsmod
Module                  Size  Used by
ppp_deflate            12950  0 
bsd_comp               12921  0 
ppp_async              17413  1 
crc_ccitt              12707  1 ppp_async
option                 46608  2 
usb_wwan               20429  1 option
usbserial              45014  7 option,usb_wwan
pci_stub               12622  1 
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             27613  0 
vboxdrv               409768  3 vboxnetadp,vboxnetflt,vboxpci
bnep                   19624  2 
rfcomm                 69160  4 
bluetooth             391196  10 bnep,rfcomm
binfmt_misc            17468  1 
snd_hda_codec_hdmi     46254  1 
snd_hda_codec_realtek    61438  1 
usb_storage            62209  0 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
asus_nb_wmi            16990  0 
asus_wmi               24191  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
snd_hda_intel          52355  3 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
intel_rapl             18773  0 
coretemp               13435  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
lib80211_crypt_tkip    17619  0 
kvm_intel             143060  0 
kvm                   451511  1 kvm_intel
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
cryptd                 20359  1 ghash_clmulni_intel
snd_timer              29482  2 snd_pcm,snd_seq
wl                   4207846  0 
joydev                 17381  0 
lib80211               14381  2 wl,lib80211_crypt_tkip
serio_raw              13462  0 
i915                  783805  3 
snd                    69238  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
cfg80211              484040  1 wl
drm_kms_helper         53081  1 i915
drm                   303102  4 i915,drm_kms_helper
i2c_algo_bit           13413  1 i915
soundcore              12680  1 snd
wmi                    19177  1 asus_wmi
video                  19476  2 i915,asus_wmi
mac_hid                13205  0 
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
psmouse               106678  0 
r8169                  67581  0 
ahci                   25819  3 
mii                    13934  1 r8169
libahci                32560  1 ahci



```

---

