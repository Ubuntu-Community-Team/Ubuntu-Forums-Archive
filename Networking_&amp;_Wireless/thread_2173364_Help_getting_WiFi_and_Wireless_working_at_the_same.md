---
title: "Help getting WiFi and Wireless working at the same time"
date: 2013-09-09
forum: Networking &amp; Wireless
---

### Post by corey5 on 2013-09-09
I'm installing Ubuntu for the first time on my old Dell Inspiron 1505 and I was able to get the wireless to work with something I found on these forums, sudo apt-get install firmware-b43-installer b43-fwcutter, but after the restart my laptop won't connect to a wired connection and I'm not sure what to do. Additionally when I turn on WiFi it seems that I have to manually tell it to connect to the network each time even though I checked connect automatically, like if I turn WiFi off and turn it back on no networks are detected until I tell it to connect to a hidden network (but the network isn't hidden). I've tried reading through other threads about the wired connection issue, but I got a bit lost. I didn't see anything about the wireless issue though, maybe I missed something, but thats not a big deal as long as I know about it.

The first thing people seem to check is $ ifconfig. Nothing like eth0 or eth1 shows up just lo and wlan.
After that someone suggested sudo ifconfig eth0 up and I tried through eth4 with no results.
The next thing it seemed that was suggested was lspci -nm, but I have no idea what any of that means.

lspci -nm
00:00.0 "0600" "8086" "27a0" -r03 "1028" "01bd"
00:01.0 "0604" "8086" "27a1" -r03 "" ""
00:1b.0 "0403" "8086" "27d8" -r01 "1028" "01bd"
00:1c.0 "0604" "8086" "27d0" -r01 "" ""
00:1c.3 "0604" "8086" "27d6" -r01 "" ""
00:1d.0 "0c03" "8086" "27c8" -r01 "1028" "01bd"
00:1d.1 "0c03" "8086" "27c9" -r01 "1028" "01bd"
00:1d.2 "0c03" "8086" "27ca" -r01 "1028" "01bd"
00:1d.3 "0c03" "8086" "27cb" -r01 "1028" "01bd"
00:1d.7 "0c03" "8086" "27cc" -r01 -p20 "1028" "01bd"
00:1e.0 "0604" "8086" "2448" -re1 -p01 "" ""
00:1f.0 "0601" "8086" "27b9" -r01 "1028" "01bd"
00:1f.2 "0101" "8086" "27c4" -r01 -p80 "1028" "01bd"
00:1f.3 "0c05" "8086" "27da" -r01 "1028" "01bd"
01:00.0 "0300" "1002" "7145" "1028" "2003"
03:00.0 "0200" "14e4" "170c" -r02 "1028" "01af"
03:01.0 "0c00" "1180" "0832" -p10 "1028" "01bd"
03:01.1 "0805" "1180" "0822" -r19 -p01 "1028" "01bd"
03:01.2 "0880" "1180" "0592" -r0a "1028" "01bd"
03:01.3 "0880" "1180" "0852" -r05 "1028" "01bd"
0b:00.0 "0280" "14e4" "4311" -r01 "1028" "0007"

Please help. Thanks!

---

### Post by varunendra on 2013-09-09
Welcome to the Forums corey5 !
> **corey5 said:**
> 
lspci -nm
....
03:00.0 "0200" "14e4" "170c" -r02 "1028" "01af"
....
0b:00.0 "0280" "14e4" "4311" -r01 "1028" "0007"

The first one above is your ethernet card that uses b44 driver, and the second one is the wireless card that uses b43 driver. The fact that your ethernet is not detected makes me suspect if you also have the proprietary driver "wl" installed for your wireless. It blacklists both b43 and b44 if is installed.

Accordingly, please post the outputs of the following commands :
```
lspci -nnk | grep -iA2 net
lsmod
```

Please use 'Code' tags to post the outputs. Follow the "Using Code tags" link in my signature to see how to use it. Thanks! :)

---

### Post by corey5 on 2013-09-12
```

lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Inspiron 6400 [1028:01af]
    Kernel modules: b44
--
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
    Kernel driver in use: b43-pci-bridge

```

```

lsmod
Module                  Size  Used by
hid_generic            12540  0 
usbhid                 47346  0 
hid                   105549  2 hid_generic,usbhid
nls_utf8               12557  1 
nls_iso8859_1          12713  1 
udf                    94509  1 
bnep                   18258  2 
rfcomm                 47864  0 
bluetooth             247024  10 bnep,rfcomm
parport_pc             28284  0 
ppdev                  17113  0 
radeon                960918  3 
snd_hda_codec_idt      71153  1 
snd_hda_intel          44339  3 
snd_hda_codec         141716  2 snd_hda_codec_idt,snd_hda_intel
coretemp               13596  0 
ttm                    84051  1 radeon
snd_hwdep              13668  1 snd_hda_codec
snd_pcm               102477  2 snd_hda_intel,snd_hda_codec
arc4                   12573  2 
joydev                 17613  0 
gpio_ich               13526  0 
kvm                   455932  0 
drm_kms_helper         49597  1 radeon
snd_seq_midi           13324  0 
snd_rawmidi            30417  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
drm                   287564  5 radeon,ttm,drm_kms_helper
snd_seq                61930  2 snd_seq_midi,snd_seq_midi_event
r852                   18241  0 
snd_timer              29989  2 snd_pcm,snd_seq
sm_common              16860  1 r852
psmouse                97873  0 
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
nand                   59304  2 r852,sm_common
mtd                    45243  2 sm_common,nand
snd                    69533  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nand_ids               12723  1 nand
serio_raw              13215  0 
i2c_algo_bit           13564  1 radeon
dell_wmi               12681  0 
soundcore              12680  1 snd
nand_bch               13147  1 nand
lpc_ich                17144  0 
r592                   18144  0 
microcode              23017  0 
mac_hid                13253  0 
sparse_keymap          13890  1 dell_wmi
ssb_hcd                12909  0 
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
bch                    22063  1 nand_bch
dell_laptop            17425  0 
nand_ecc               13273  1 nand
memstick               16605  1 r592
dcdbas                 14449  1 dell_laptop
b43                   392109  0 
video                  19652  0 
wmi                    19256  1 dell_wmi
mac80211              630977  1 b43
cfg80211              525244  2 b43,mac80211
ssb                    57842  2 ssb_hcd,b43
bcma                   41244  1 b43
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
firewire_ohci          44864  0 
firewire_core          64836  1 firewire_ohci
crc_itu_t              12707  2 udf,firewire_core
sdhci_pci              18721  0 
sdhci                  33141  1 sdhci_pci
usb_storage            61749  1

```

---

### Post by varunendra on 2013-09-12
Hmm.. no b44 in there, that's why ethernet doesn't work.

There used to be a 'Who's first' fight over the ssb module between b43 and b44 ages ago. It seemed to have been fixed long ago, but I suspected the old rivalry has resurrected on your system. There was a simple workaround to make both happy, but let's first make sure it is what I suspect it is.

Please do a fresh reboot (so that we have only fresh messages in dmesg), and post back the output of -
```
dmesg | egrep 'b43|b44|firm|ssb'
```

---

