---
title: "bluetooth not working?"
date: 2014-07-30
forum: Networking &amp; Wireless
---

### Post by gandhi2 on 2014-07-30
hey there brilliant people!

i recently got a usb bluetooth adapter for my computer, so i can play music though my bluetooth speakers BUT xubuntu doesn't detect my device?

any help would be greatly appreciated 

big love

Gandhi

---

### Post by praseodym on 2014-07-30
Please show the terminal outputs of:

```
lsusb
hciconfig --all
lsmod
dmesg | grep blue
```
Did you install the packages

```
sudo apt-get install bluez-utils libopenobex1 blueman
sudo service bluetooth restart 
```

---

### Post by gandhi2 on 2014-07-31
yeah i've installed that, here is the info you asked for:

Module                  Size  Used by
rndis_host             14087  0 
cdc_ether              13967  1 rndis_host
usbnet                 37865  2 rndis_host,cdc_ether
btusb                  27580  0 
bnep                   18895  2 
rfcomm                 53664  4 
bluetooth             342206  12 bnep,btusb,rfcomm
binfmt_misc            13140  1 
arc4                   12536  0 
joydev                 17101  0 
hid_generic            12492  0 
rt2500usb              30861  0 
rt2x00usb              20041  1 rt2500usb
rt2x00lib              48886  2 rt2x00usb,rt2500usb
mac80211              546051  2 rt2x00lib,rt2x00usb
cfg80211              409394  2 mac80211,rt2x00lib
usbhid                 46997  0 
snd_atiixp             19305  4 
hid                    87604  2 hid_generic,usbhid
usblp                  18277  0 
snd_ac97_codec        105709  1 snd_atiixp
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                85501  2 snd_ac97_codec,snd_atiixp
snd_page_alloc         14230  2 snd_pcm,snd_atiixp
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25135  1 snd_seq_midi
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28584  2 snd_pcm,snd_seq
snd                    60871  16 snd_ac97_codec,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_seq_device,snd_atiixp,snd_seq_midi
radeon               1420526  3 
serio_raw              13230  0 
soundcore              12600  1 snd
ttm                    72698  1 radeon
drm_kms_helper         47182  1 radeon
i2c_piix4              17723  0 
drm                   244037  5 ttm,drm_kms_helper,radeon
i2c_algo_bit           13197  1 radeon
shpchp                 32128  0 
ati_agp                13177  0 
parport_pc             31981  1 
ppdev                  17391  0 
mac_hid                13037  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
usb_storage            48417  0 
pata_acpi              12886  0 
firewire_ohci          35529  0 
psmouse                91329  0 
firewire_core          61867  1 firewire_ohci
8139too                32571  0 
8139cp                 27171  0 
crc_itu_t              12627  1 firewire_core
mii                    13654  3 usbnet,8139cp,8139too
floppy                 55416  0 
sata_sil               13256  2 
pata_atiixp            13058  0 


thank you again for your help

Gandhi

---

### Post by gandhi2 on 2014-07-31
and this:

Bus 001 Device 006: ID 0424:2228 Standard Microsystems Corp. 9-in-2 Card Reader
Bus 001 Device 009: ID 19d2:1365 ZTE WCDMA Technologies MSM 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 045e:0029 Microsoft Corp. IntelliMouse Optical
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1c4f:0002 SiGma Micro Keyboard TRACER Gamma Ivory
Bus 002 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
gandhi@gandhi-ATI-Xpress200:~$ hciconfig --all
hci0:    Type: BR/EDR  Bus: USB
    BD Address: 00:1B:10:00:2A:EC  ACL MTU: 1017:8  SCO MTU: 64:0
    DOWN 
    RX bytes:474 acl:0 sco:0 events:18 errors:0
    TX bytes:74 acl:0 sco:0 commands:18 errors:0
    Features: 0xff 0xff 0x8d 0xfe 0x8f 0xf9 0x00 0x80
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
    Link policy: 
    Link mode: SLAVE ACCEPT

---

### Post by praseodym on 2014-08-01
Can you start it via terminal?
```

sudo service bluetooth restart
rfkill list
```

---

### Post by jeremy31 on 2014-08-01
Looks like a fun one with all the bug reports but they might have it fixed
[https://launchpad.net/~inaddy/+archive/ubuntu/sf00069767](https://launchpad.net/~inaddy/+archive/ubuntu/sf00069767)

---

### Post by gandhi2 on 2014-08-01
blueman is running...... but my device doesn't appear?

---

