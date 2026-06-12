---
title: "Wireless problem on Acer aspire one D270"
date: 2014-01-31
forum: Networking &amp; Wireless
---

### Post by Gneykan_ on 2014-01-31
Hi everybody,
I've got an Acer Aspire D270 minibook and I installed Ubuntu 13.10 on that.Installation went no problem but after installing Ubuntu there is a problem with my wireless connection.Wireless device is recognized but it cannot connect to ethernet.There is no problem with wired conneciton.I've been searching everywhere to fix that problem but I couldn't find any solution.Is there any solution or suggestion?

Thanks

---

### Post by praseodym on 2014-01-31
Please show the terminal outputs of
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
```

---

### Post by Gneykan_ on 2014-02-01
guney@guney-AOD270:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Acer Incorporated [ALI] Device [1025:061f]
    Kernel driver in use: r8169
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e042]
    Kernel driver in use: wl
guney@guney-AOD270:~$ lsusb
Bus 001 Device 002: ID 064e:d250 Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
guney@guney-AOD270:~$ lsmod
Module                  Size  Used by
michael_mic            12540  4 
arc4                   12536  2 
parport_pc             31981  0 
ppdev                  17391  0 
vesafb                 13500  0 
rfcomm                 53664  0 
bnep                   18959  2 
bluetooth             323656  10 bnep,rfcomm
coretemp               13195  0 
joydev                 17097  0 
snd_hda_codec_realtek    45592  1 
snd_hda_codec_hdmi     40373  1 
acer_wmi               31735  0 
sparse_keymap          13708  1 acer_wmi
uvcvideo               71309  0 
videobuf2_vmalloc      13048  1 uvcvideo
videobuf2_memops       13170  1 videobuf2_vmalloc
videobuf2_core         39125  1 uvcvideo
videodev              107508  2 uvcvideo,videobuf2_core
snd_hda_intel          42658  3 
snd_hda_codec         164003  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                89488  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25094  1 snd_seq_midi
microcode              18830  0 
lib80211_crypt_tkip    17456  0 
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
psmouse                90642  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
serio_raw              13189  0 
snd_timer              24447  2 snd_pcm,snd_seq
wl                   3999620  0 
gma500_gfx            173701  2 
lib80211               14040  2 wl,lib80211_crypt_tkip
lpc_ich                16864  0 
cfg80211              401762  1 wl
rtsx_pci_ms            17807  0 
drm_kms_helper         46867  1 gma500_gfx
memstick               16008  1 rtsx_pci_ms
drm                   242400  3 drm_kms_helper,gma500_gfx
snd                    60790  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
i2c_algo_bit           13197  1 gma500_gfx
soundcore              12600  1 snd
wmi                    18590  1 acer_wmi
video                  18777  2 acer_wmi,gma500_gfx
mac_hid                13037  0 
lp                     13299  0 
parport                40795  3 lp,ppdev,parport_pc
rtsx_pci_sdmmc         22898  0 
ahci                   25579  2 
r8169                  61562  0 
libahci                26554  1 ahci
rtsx_pci               43458  2 rtsx_pci_ms,rtsx_pci_sdmmc
mii                    13654  1 r8169
guney@guney-AOD270:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

---

### Post by praseodym on 2014-02-01
Try the native driver, same as here:

[http://ubuntuforums.org/showthread.php?t=2202899&p=12916344#post12916344](http://ubuntuforums.org/showthread.php?t=2202899&p=12916344#post12916344)

---

### Post by Gneykan_ on 2014-02-01
thanks but it doesn't work for me(no direction or directory error ). I  executed first code and removed the package but &#305; couldn't execute the other ones. 
.

---

### Post by praseodym on 2014-02-01
If there are errors in the "rm" or "sed"-lines, its Ok. Install the firmware and reboot.

---

