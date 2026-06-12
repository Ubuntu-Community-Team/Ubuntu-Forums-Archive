---
title: "TP-Link TL-WN723N works in 3.8.0.27, not 3.8.0.29 or .30"
date: 2013-09-08
forum: Networking &amp; Wireless
---

### Post by prich-earthling on 2013-09-08
I have a TL-WN723N which was originally purchased to be used on a Raspberry Pi.  I was never able to get it to run on the Pi.  Some weeks ago I decided to try the device on a laptop running Ubuntu (Gnome).  To my complete surprise, it worked straight up.  However, with the update to 3.8.0.29 (from 27) it stopped working.  After the update to 3.8.0.30 the situation remains the same.  If I revert to 3.8.0.27 the device works.

I am a long term user of Ubuntu but am certainly NOT an expert.  I have checked which USB devices are recognised at startup and which modules are loaded - these, as far as I can tell, are identical accross all 3 kernel versions.

Any suggestions regarding a fix for this problem would be appreciated.

Peter

---

### Post by varunendra on 2013-09-09
> **prich-earthling said:**
> I have a TL-WN723N which was originally purchased to be used on a Raspberry Pi.  I was never able to get it to run on the Pi.  Some weeks ago I decided to try the device on a laptop running Ubuntu (Gnome).  To my complete surprise, it worked straight up.  However, with the update to 3.8.0.29 (from 27) it stopped working.  After the update to 3.8.0.30 the situation remains the same.  If I revert to 3.8.0.27 the device works.

I am a long term user of Ubuntu but am certainly NOT an expert.  I have checked which USB devices are recognised at startup and which modules are loaded - these, as far as I can tell, are identical accross all 3 kernel versions.

Any suggestions regarding a fix for this problem would be appreciated.

Peter

Welcome to the forums prich-earthling !

While the USB adapter is plugged, please run the following and post back their outputs :
```
uname -mr
lsb_release -cd
lsusb
nm-tool
lsmod
rfkill list all
```
Please use 'Code' tags to post these outputs (Follow the "Using Code tags" link in my sig to see how).

---

### Post by Bucky Ball on 2013-09-09
*Post moved to own thread in **Networking & Wireless**.*

---

### Post by prich-earthling on 2013-09-11
varunendra, 

The info you requested is set out below.

The second set of data is using the laptop internal wifi  (802.11g).  As far as I know the internal wifi has been disabled but it does get switched on at boot.

From my inexperienced and simplistic point of view it appears that the TL WN723N is not 'switched on' at boot.  Additionally, this dongle is Version 3 - I think this unit differs from previous versions in that the chipset is not identified in lsusb.

All of the PRMR SSIDs are mine - PRMR4 is the only one set to allow 802.11g (all the others are n only).  PRMR3 is located in the same room as the problem laptop

Thanks in advance for your assistance

```

***********************************************************************************************************
Kernel 3.8.0.27
***********************************************************************************************************

peter@ASUSF5RL:~$ uname -mr
3.8.0-27-generic i686


peter@ASUSF5RL:~$ lsb_release -cd
Description:    Ubuntu 13.04
Codename:    raring


peter@ASUSF5RL:~$ lsusb
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 003: ID 0bda:0116 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 004: ID 064e:a111 Suyin Corp. 
Bus 005 Device 002: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 0bda:8179 Realtek Semiconductor Corp. 
Bus 001 Device 007: ID 05e3:0723 Genesys Logic, Inc. GL827L SD/MMC/MS Flash Card Reader


peter@ASUSF5RL:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan2  [Auto PRMR3] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8188eu
  State:             connected
  Default:           no
  HW Address:        A0:F3:C1:26:D2:32

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    PRMR2:           Infra, F4:EC:38:FB:C7:E1, Freq 2427 MHz, Rate 44 Mb/s, Strength 47 WPA2
    PRMR4:           Infra, 78:A0:51:01:01:82, Freq 2452 MHz, Rate 44 Mb/s, Strength 45 WPA WPA2
    PRMR:            Infra, 94:0C:6D:E6:A8:20, Freq 2452 MHz, Rate 44 Mb/s, Strength 44 WPA2
    BigPond187B:     Infra, 20:E5:2A:FD:92:40, Freq 2437 MHz, Rate 16 Mb/s, Strength 23 WPA WPA2
    iWireless:       Infra, 00:1B:2F:E4:22:8E, Freq 2427 MHz, Rate 14 Mb/s, Strength 27 WPA WPA2
    *PRMR3:          Infra, 14:CF:92:6D:8E:7A, Freq 2462 MHz, Rate 63 Mb/s, Strength 100 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.102
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             208.67.222.222
    DNS:             208.67.220.220


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl2
  State:             unavailable
  Default:           no
  HW Address:        00:22:15:F0:3B:62

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [PRMR4 1] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             connected
  Default:           yes
  HW Address:        00:22:43:03:27:50

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    PRMR3:           Infra, 14:CF:92:6D:8E:7A, Freq 2462 MHz, Rate 63 Mb/s, Strength 100 WPA WPA2
    PRMR2:           Infra, F4:EC:38:FB:C7:E1, Freq 2427 MHz, Rate 54 Mb/s, Strength 62 WPA2
    PRMR:            Infra, 94:0C:6D:E6:A8:20, Freq 2452 MHz, Rate 54 Mb/s, Strength 52 WPA2
    BigPond187B:     Infra, 20:E5:2A:FD:92:40, Freq 2437 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    iWireless:       Infra, 00:1B:2F:E4:22:8E, Freq 2427 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    NetComm Wireless:Infra, 00:60:64:83:47:86, Freq 2412 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    *PRMR4:          Infra, 78:A0:51:01:01:82, Freq 2452 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    Herbert:         Infra, 00:04:ED:D3:28:BA, Freq 2412 MHz, Rate 54 Mb/s, Strength 15 WPA2

  IPv4 Settings:
    Address:         192.168.1.104
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             208.67.222.222
    DNS:             208.67.220.220


peter@ASUSF5RL:~$ lsmod
Module                  Size  Used by
parport_pc             27504  0 
ppdev                  12817  0 
bnep                   17669  2 
rfcomm                 37420  0 
bluetooth             202109  10 bnep,rfcomm
arc4                   12543  2 
coretemp               13131  0 
uvcvideo               71279  0 
videobuf2_vmalloc      12920  1 uvcvideo
videobuf2_memops       13042  1 videobuf2_vmalloc
videobuf2_core         39161  1 uvcvideo
8188eu                728041  0 
videodev               95806  2 uvcvideo,videobuf2_core
snd_hda_codec_si3054    12864  1 
snd_hda_codec_realtek    63791  1 
joydev                 17097  0 
snd_hda_intel          38307  3 
snd_hda_codec         117580  3 snd_hda_codec_realtek,snd_hda_codec_si3054,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
microcode              18286  0 
snd_pcm                80890  3 snd_hda_codec_si3054,snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
ath5k                 134997  0 
snd_seq_midi_event     14475  1 snd_seq_midi
ath                    19187  1 ath5k
snd_rawmidi            25114  1 snd_seq_midi
mac80211              526519  1 ath5k
asus_laptop            23874  0 
video                  18894  0 
sparse_keymap          13658  1 asus_laptop
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
radeon                875105  3 
input_polldev          13648  1 asus_laptop
cfg80211              436177  3 ath,ath5k,mac80211
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24411  2 snd_pcm,snd_seq
ttm                    71289  1 radeon
drm_kms_helper         47545  1 radeon
drm                   228489  5 ttm,drm_kms_helper,radeon
snd                    56485  16 snd_hda_codec_realtek,snd_hda_codec_si3054,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
psmouse                81038  0 
i2c_algo_bit           13197  1 radeon
mac_hid                13037  0 
serio_raw              13031  0 
soundcore              12600  1 snd
sp5100_tco             13447  0 
shpchp                 32129  0 
ati_agp                13177  0 
i2c_piix4              13066  0 
lp                     13299  0 
parport                40753  3 lp,ppdev,parport_pc
hid_generic            12484  0 
usbhid                 41805  0 
hid                    82666  2 hid_generic,usbhid
pata_acpi              12886  0 
usb_storage            47684  0 
pata_atiixp            13058  0 
ahci                   25507  2 
libahci                26108  1 ahci
atl2                   27628  0 


peter@ASUSF5RL:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

******************************************************************************************************************
Kernel  3.8.0.30
******************************************************************************************************************

peter@ASUSF5RL:~$ uname -mr
3.8.0-30-generic i686

peter@ASUSF5RL:~$ lsb_release -cd
Description:    Ubuntu 13.04
Codename:    raring

peter@ASUSF5RL:~$ lsusb
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 003: ID 0bda:0116 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 004: ID 064e:a111 Suyin Corp. 
Bus 005 Device 002: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 0bda:8179 Realtek Semiconductor Corp. 
Bus 001 Device 007: ID 05e3:0723 Genesys Logic, Inc. GL827L SD/MMC/MS Flash Card Reader


peter@ASUSF5RL:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl2
  State:             unavailable
  Default:           no
  HW Address:        00:22:15:F0:3B:62

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [PRMR4 1] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             connected
  Default:           yes
  HW Address:        00:22:43:03:27:50

  Capabilities:
    Speed:           1 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    PRMR2:           Infra, F4:EC:38:FB:C7:E1, Freq 2427 MHz, Rate 54 Mb/s, Strength 69 WPA2
    PRMR3:           Infra, 14:CF:92:6D:8E:7A, Freq 2462 MHz, Rate 63 Mb/s, Strength 55 WPA WPA2
    PRMR:            Infra, 94:0C:6D:E6:A8:20, Freq 2452 MHz, Rate 54 Mb/s, Strength 57 WPA2
    BigPond187B:     Infra, 20:E5:2A:FD:92:40, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    iWireless:       Infra, 00:1B:2F:E4:22:8E, Freq 2427 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    NetComm Wireless:Infra, 00:60:64:83:47:86, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    Herbert:         Infra, 00:04:ED:D3:28:BA, Freq 2412 MHz, Rate 54 Mb/s, Strength 5 WPA2
    *PRMR4:          Infra, 78:A0:51:01:01:82, Freq 2452 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    B&T CO:          Infra, 00:60:64:76:E8:A6, Freq 2437 MHz, Rate 54 Mb/s, Strength 5 WPA WPA2
    phils home comp: Infra, A0:21:B7:5E:4E:A9, Freq 2462 MHz, Rate 54 Mb/s, Strength 0 WPA2

  IPv4 Settings:
    Address:         192.168.1.104
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             208.67.222.222
    DNS:             208.67.220.220


peter@ASUSF5RL:~$ lsmod
Module                  Size  Used by
parport_pc             27504  0 
ppdev                  12817  0 
rfcomm                 37420  0 
bnep                   17669  2 
bluetooth             202109  10 bnep,rfcomm
arc4                   12543  2 
snd_hda_codec_si3054    12864  1 
snd_hda_codec_realtek    63791  1 
snd_hda_intel          38307  3 
snd_hda_codec         117617  3 snd_hda_codec_realtek,snd_hda_codec_si3054,snd_hda_intel
radeon                875105  3 
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80890  3 snd_hda_codec_si3054,snd_hda_codec,snd_hda_intel
ath5k                 134997  0 
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
uvcvideo               71279  0 
ttm                    71289  1 radeon
snd_rawmidi            25114  1 snd_seq_midi
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
ath                    19187  1 ath5k
drm_kms_helper         47545  1 radeon
drm                   228489  5 ttm,drm_kms_helper,radeon
mac80211              526519  1 ath5k
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
videobuf2_vmalloc      12920  1 uvcvideo
snd_timer              24411  2 snd_pcm,snd_seq
i2c_algo_bit           13197  1 radeon
videobuf2_memops       13042  1 videobuf2_vmalloc
videobuf2_core         39161  1 uvcvideo
asus_laptop            23874  0 
snd                    56485  16 snd_hda_codec_realtek,snd_hda_codec_si3054,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
videodev               95806  2 uvcvideo,videobuf2_core
soundcore              12600  1 snd
sp5100_tco             13447  0 
coretemp               13131  0 
cfg80211              436177  3 ath,ath5k,mac80211
ati_agp                13177  0 
i2c_piix4              13066  0 
shpchp                 32129  0 
psmouse                81065  0 
joydev                 17097  0 
microcode              18286  0 
sparse_keymap          13658  1 asus_laptop
mac_hid                13037  0 
serio_raw              13031  0 
lp                     13299  0 
video                  18894  0 
parport                40753  3 lp,ppdev,parport_pc
input_polldev          13648  1 asus_laptop
hid_generic            12484  0 
usbhid                 41805  0 
hid                    82666  2 hid_generic,usbhid
usb_storage            47684  0 
pata_acpi              12886  0 
pata_atiixp            13058  0 
ahci                   25507  2 
atl2                   27628  0 
libahci                26108  1 ahci


peter@ASUSF5RL:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no




```

---

