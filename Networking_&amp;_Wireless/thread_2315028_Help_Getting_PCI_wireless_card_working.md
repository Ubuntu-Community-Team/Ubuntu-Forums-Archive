---
title: "Help Getting PCI wireless card working"
date: 2016-02-25
forum: Networking &amp; Wireless
---

### Post by zach45 on 2016-02-25
Hello, I am having a difficult time getting my encore PCI wireless card to work. When i attempt to use ndisgtk, i run into issues. I select the appropriate driver, then i get the message " modprobe: FATAL: Module ndiswrapper not found." I select ok and it brings mo to the main screen, where its says "Hardware not present". i find the second message strange as the card shows up in the bios and in the operating system. In regards to the first message, in the software center, it shows both add ons as present and installed.[ATTACH=CONFIG]267494[/ATTACH][ATTACH=CONFIG]267495[/ATTACH]

---

### Post by weatherman2 on 2016-02-25
ndiswrapper - using the Windows driver in Linux - should be a last resort.  A native driver for the wireless card is going to be much more robust overall.

Ask for this thread to be moved to the "Networking & Wireless" forum to get better response on how to proceed.

---

### Post by zach45 on 2016-02-27
bump

---

### Post by praseodym on 2016-02-27
Please show the outputs of these commands:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
rfkill list
```
Does LAN work?

---

### Post by zach45 on 2016-02-27
> **praseodym said:**
> Please show the outputs of these commands:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
rfkill list
```
Does LAN work?

```

lspci -nnk | grep -iA2 net

02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5787 Gigabit Ethernet PCI Express [14e4:169b] (rev 02)

            Subsystem: Dell Device [1028:0220]

            Kernel driver in use: tg3

03:01.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless [11ab:1faa] (rev 03)

            Subsystem: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless [11ab:1faa]

 
lsusb
Bus 001 Device 007: ID 0781:5576 SanDisk Corp.

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Bus 005 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 002 Device 002: ID 413c:2107 Dell Computer Corp.

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 
 
lsmod

Module                  Size  Used by

nls_iso8859_1          16384  1

uas                    24576  0

usb_storage            69632  2 uas

bnep                   20480  2

rfcomm                 69632  0

bluetooth             512000  10 bnep,rfcomm

snd_hda_codec_analog    16384  1

snd_hda_codec_generic    73728  1 snd_hda_codec_analog

snd_hda_intel          36864  5

snd_hda_codec         135168  3 snd_hda_codec_generic,snd_hda_intel,snd_hda_codec_analog

snd_hda_core           65536  4 snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_hda_codec_analog

snd_hwdep              16384  1 snd_hda_codec

i915                 1126400  4

snd_pcm               102400  4 snd_hda_codec,snd_hda_intel,snd_hda_core

snd_seq_midi           16384  0

joydev                 20480  0

snd_seq_midi_event     16384  1 snd_seq_midi

input_leds             16384  0

snd_rawmidi            32768  1 snd_seq_midi

snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi

snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi

snd_timer              32768  2 snd_pcm,snd_seq

gpio_ich               16384  0

video                  40960  1 i915

drm_kms_helper        126976  1 i915

snd                    81920  19 snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_hda_codec_analog

coretemp               16384  0

drm                   360448  6 i915,drm_kms_helper

dcdbas                 16384  0

soundcore              16384  1 snd

serio_raw              16384  0

lpc_ich                24576  0

i2c_algo_bit           16384  1 i915

shpchp                 36864  0

8250_fintek            16384  0

ppdev                  20480  0

parport_pc             32768  1

lp                     20480  0

mac_hid                16384  0

parport                49152  3 lp,ppdev,parport_pc

hid_generic            16384  0

usbhid                 49152  0

hid                   118784  3 hid_generic,usbhid

psmouse               126976  0

tg3                   163840  0

ahci                   36864  2

libahci                32768  1 ahci

pata_acpi              16384  0

ptp                    20480  1 tg3

pps_core               20480  1 ptp

```

Yes, LAN does work, but it is impractical to run a Ethernet cable to the router.

---

### Post by zach45 on 2016-03-19
bump

---

### Post by jeremy31 on 2016-03-19
Download from [http://driverzone.com/%7B14ce7f97-734f-44ab-bce6-4399b1c4d270%7D?id=2219768](http://driverzone.com/%7B14ce7f97-734f-44ab-bce6-4399b1c4d270%7D?id=2219768)
Right click, extract here
Then use ndiswrapper to navigate to where you extracted the drivers and use the Windows XP WG311v3.INF file

---

### Post by zach45 on 2016-04-22
I have completed the steps you gave, but there still is a slight problem. The error message "[COLOR=#000000]modprobe: FATAL: Module ndiswrapper not found" still appears. However progress has been made as the ndisgtk program now recognizes the hardware is present. What steps should i take from here?[/COLOR]

---

### Post by jeremy31 on 2016-04-22
Lets see if everything needed for ndiswrapper is present ```
dpkg -l | grep -i ndis
```

---

