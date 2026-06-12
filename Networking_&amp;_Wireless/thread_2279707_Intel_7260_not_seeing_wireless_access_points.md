---
title: "Intel 7260 not seeing wireless access points"
date: 2015-05-25
forum: Networking &amp; Wireless
---

### Post by ivan-fernandez on 2015-05-25
I recently installed an Intel 7260 Mini PCI Express wireless card. The card gets detected, the modules get loaded, but the card fails to see any network access points. All my other devices detect plenty of them, and I've tried to set up a hotspot right next to the computer, so it does not seem to be a range issue. I'm not sure how to diagnose the problem. Here's the output from some commands:

```
iwconfig wlan1
wlan1     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

```
iwlist wlan1 scanning
wlan1     No scan results
```

Any help would be very appreciated, thanks.

--
Ivan

---

### Post by chili555 on 2015-05-25
Let's see some further diagnostics:```
rfkill list all
dmesg | grep -e wlan -e iwl
```Thanks.

---

### Post by ivan-fernandez on 2015-05-25
There

```
rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

```
dmesg | grep -e wlan -e iwl
[    4.023109] iwlwifi 0000:03:00.0: loaded firmware version 25.17.12.0 op_mode iwlmvm
[    4.174264] iwlwifi 0000:03:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[    4.176111] iwlwifi 0000:03:00.0: L1 Disabled - LTR Disabled
[    4.176355] iwlwifi 0000:03:00.0: L1 Disabled - LTR Disabled
[    4.414486] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    4.422668] iwlwifi 0000:03:00.0 wlan1: renamed from wlan0
[    6.634014] iwlwifi 0000:03:00.0: L1 Disabled - LTR Disabled
[    6.634264] iwlwifi 0000:03:00.0: L1 Disabled - LTR Disabled
```

---

### Post by chili555 on 2015-05-25
I just love problems where everything looks just perfect but it just doesn’t work! I wonder why this is wlan[COLOR="#FF0000"]1[/COLOR] and not wlan0. Is there another existing and probably conflicting wireless device? May we see:```
lsmod
dmesg | grep 03:00
cat /etc/network/interfaces
```

---

### Post by ivan-fernandez on 2015-05-25
It's great that some people like these kind of problems ;) I usually make do with google and forums search for my computer problems, but this one's got me stumped...

```
lsmod
Module                  Size  Used by
des3_ede_x86_64        40960  0 
des_generic            24576  1 des3_ede_x86_64
md4                    16384  0 
nls_utf8               16384  4 
cifs                  565248  8 
fscache                65536  1 cifs
binfmt_misc            20480  1 
rfcomm                 69632  8 
bnep                   20480  2 
snd_hda_codec_hdmi     53248  4 
nvidia              11366400  31 
joydev                 20480  0 
arc4                   16384  2 
snd_hda_codec_realtek    86016  1 
snd_hda_codec_generic    69632  1 snd_hda_codec_realtek
hid_generic            16384  0 
snd_hda_intel          32768  3 
gpio_ich               16384  0 
snd_hda_controller     32768  1 snd_hda_intel
snd_hda_codec         143360  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              20480  1 snd_hda_codec
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
iwlmvm                278528  0 
rndis_host             16384  0 
cdc_ether              16384  1 rndis_host
snd_seq_midi           16384  0 
mac80211              724992  1 iwlmvm
usbnet                 45056  2 rndis_host,cdc_ether
usbhid                 53248  0 
snd_seq_midi_event     16384  1 snd_seq_midi
hid                   110592  2 hid_generic,usbhid
serio_raw              16384  0 
snd_rawmidi            32768  1 snd_seq_midi
coretemp               16384  0 
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
iwlwifi               196608  1 iwlmvm
cfg80211              540672  3 iwlwifi,mac80211,iwlmvm
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
drm                   344064  3 nvidia
ir_xmp_decoder         16384  0 
snd_timer              32768  2 snd_pcm,snd_seq
lpc_ich                24576  0 
btusb                  32768  0 
ir_rc5_decoder         16384  0 
ir_sanyo_decoder       16384  0 
ir_sony_decoder        16384  0 
ir_rc6_decoder         16384  0 
bluetooth             491520  22 bnep,btusb,rfcomm
ir_lirc_codec          16384  0 
lirc_dev               20480  1 ir_lirc_codec
ir_mce_kbd_decoder     16384  0 
ir_sharp_decoder       16384  0 
ir_jvc_decoder         16384  0 
ir_nec_decoder         16384  0 
snd                    90112  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              16384  2 snd,snd_hda_codec
shpchp                 40960  0 
rc_rc6_mce             16384  0 
8250_fintek            16384  0 
fintek_cir             20480  0 
rc_core                28672  14 ir_sharp_decoder,ir_xmp_decoder,lirc_dev,ir_lirc_codec,ir_rc5_decoder,ir_nec_decoder,ir_sony_decoder,ir_mce_kbd_decoder,ir_jvc_decoder,fintek_cir,ir_rc6_decoder,ir_sanyo_decoder,rc_rc6_mce
mac_hid                16384  0 
parport_pc             32768  0 
ppdev                  20480  0 
lp                     20480  0 
parport                45056  3 lp,ppdev,parport_pc
autofs4                40960  2 
ums_realtek            20480  0 
uas                    24576  0 
usb_storage            69632  2 uas,ums_realtek
raid10                 49152  0 
raid456                94208  0 
async_raid6_recov      20480  1 raid456
async_memcpy           16384  2 raid456,async_raid6_recov
async_pq               16384  2 raid456,async_raid6_recov
async_xor              16384  3 async_pq,raid456,async_raid6_recov
async_tx               16384  5 async_pq,raid456,async_xor,async_memcpy,async_raid6_recov
xor                    24576  1 async_xor
raid6_pq               98304  2 async_pq,async_raid6_recov
pata_acpi              16384  0 
raid1                  40960  0 
pata_jmicron           16384  0 
ahci                   36864  0 
raid0                  20480  0 
libahci                32768  1 ahci
r8169                  81920  0 
multipath              16384  0 
mii                    16384  2 r8169,usbnet
linear                 16384  0 

```
```
dmesg | grep 03:00
[    0.204179] pci 0000:03:00.0: [8086:08b1] type 00 class 0x028000
[    0.204224] pci 0000:03:00.0: reg 0x10: [mem 0xfeafe000-0xfeafffff 64bit]
[    0.204426] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    4.382534] iwlwifi 0000:03:00.0: loaded firmware version 25.17.12.0 op_mode iwlmvm
[    4.526389] iwlwifi 0000:03:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[    4.526480] iwlwifi 0000:03:00.0: L1 Disabled - LTR Disabled
[    4.526726] iwlwifi 0000:03:00.0: L1 Disabled - LTR Disabled
[    4.811253] iwlwifi 0000:03:00.0 wlan1: renamed from wlan0
[    7.463615] iwlwifi 0000:03:00.0: L1 Disabled - LTR Disabled
[    7.463861] iwlwifi 0000:03:00.0: L1 Disabled - LTR Disabled
```
```
cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
```
Looking in the syslog file, I also found this, not sure if it's relevant:
```
May 25 19:50:55 barataria kernel: [    4.811253] iwlwifi 0000:03:00.0 wlan1: renamed from wlan0
May 25 19:50:55 barataria systemd[1]: Started ifup for wlan1.
May 25 19:50:55 barataria systemd[1]: Starting ifup for wlan1...
May 25 19:50:55 barataria sh[544]: Unknown interface wlan1
```

---

### Post by chili555 on 2015-05-26
> May 25 19:50:55 barataria kernel: [    4.811253] iwlwifi 0000:03:00.0 wlan1: renamed from wlan0
May 25 19:50:55 barataria systemd[1]: Started ifup for wlan1.
May 25 19:50:55 barataria systemd[1]: Starting ifup for wlan1...
May 25 19:50:55 barataria sh[544]: Unknown interface wlan1This just gets weirder!

May we see:```
cat /var/log/syslog | grep -e etwork -e wlan | tail -n20
```If there seem to be few lines, indicating the log filled up, was archived and a new one started, repeat with:```
/cat /var/log/syslog[COLOR="#FF0000"].1[/COLOR] | grep -e etwork -e wlan | tail -n20
```Since the output is lengthy, paste it here and give us the link: [http://paste.ubuntu.com](http://paste.ubuntu.com)

Also, let's look at:```
cat /etc/NetworkManager/NetworkManager.conf
```

---

### Post by lokeey on 2015-06-07
having the same issue. you ever get this resolved?

> [   44.224264] iwlwifi 0000:04:00.0: irq 54 for MSI/MSI-X
[   44.249782] iwlwifi 0000:04:00.0: loaded firmware version 22.24.8.0 op_mode iwlmvm
[   44.285185] iwlwifi 0000:04:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[   44.285239] iwlwifi 0000:04:00.0: L1 Disabled - LTR Disabled
[   44.285468] iwlwifi 0000:04:00.0: L1 Disabled - LTR Disabled
[   44.519456] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   45.054675] iwlwifi 0000:04:00.0: L1 Disabled - LTR Disabled
[   45.054897] iwlwifi 0000:04:00.0: L1 Disabled - LTR Disabled

---

### Post by ivan-fernandez on 2015-06-07
> **lokeey said:**
> having the same issue. you ever get this resolved?

Nope, sorry

---

