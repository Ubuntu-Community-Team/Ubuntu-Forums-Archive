---
title: "Wireless Connectivity Problem"
date: 2013-09-06
forum: Networking &amp; Wireless
---

### Post by steven5 on 2013-09-06
I installed ubuntu 12.04 LTS and have a problem with my wifi connection.  My router allows home network and a separate guest access for the internet.  I can not establish a connection to the home network but have no problem accessing the guest internet access.  I have doublechecked my security settings on the router and I an using WPA/WPA2 personal security. I do not want to change to WEP but don't know how else to keep a secure network.  I have also changed the passphrase but to no avail.  Any suggestions?

---

### Post by praseodym on 2013-09-07
Hi,

please open a terminal with CTRL+ALT+T and show
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
sudo iwlist scan
```
I recommend using WPA2-AES only, a fixed channel and setting the bandwidth to 20 MHz instead of 20/40 MHz.

---

### Post by steven5 on 2013-09-07
Looked at my router and disabled the iPv6   changed the iPv4 to b/g only and set the channel to 11  Selected WPA2 Personal but there was no option between AES and TKIP available so I don't know which one it is using   I still can not connect using the home network SSID.  I can only connect to the Guest access.

---

### Post by praseodym on 2013-09-07
Is there a MAC address filter active in your router? If yes, deactivate it.

---

### Post by steven5 on 2013-09-07
There is no active MAC address filter.

---

### Post by steven5 on 2013-09-07
> **praseodym said:**
> Hi,

please open a terminal with CTRL+ALT+T and show
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
sudo iwlist scan
```
I recommend using WPA2-AES only, a fixed channel and setting the bandwidth to 20 MHz instead of 20/40 MHz.

I am getting this...

steven@ubuntu:~$ lspci -nnk | grep -iA2 net
01:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0a)
    Subsystem: Hewlett-Packard Company Device [103c:18a4]
    Kernel driver in use: r8169
--
02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 2230 [8086:0887] (rev c4)
    Subsystem: Intel Corporation Centrino Wireless-N 2230 BGN [8086:4062]
    Kernel driver in use: iwlwifi

steven@ubuntu:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 0461:4d0f Primax Electronics, Ltd 
Bus 003 Device 003: ID 138a:0018 Validity Sensors, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 064e:c336 Suyin Corp. 
Bus 001 Device 004: ID 8087:07da Intel Corp.


steven@ubuntu:~$ lsmod
Module                  Size  Used by
snd_hda_codec_hdmi     37407  1 
snd_hda_codec_idt      71153  1 
coretemp               13596  0 
arc4                   12573  2 
snd_hda_intel          44339  3 
snd_hda_codec         141761  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
iwldvm                249093  0 
kvm                   455932  0 
bnep                   18258  2 
uvcvideo               82214  0 
snd_hwdep              13668  1 snd_hda_codec
mac80211              630977  1 iwldvm
rfcomm                 47864  12 
snd_pcm               102477  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
ghash_clmulni_intel    13259  0 
snd_seq_midi           13324  0 
videobuf2_core         40785  1 uvcvideo
aesni_intel            55495  0 
snd_rawmidi            30417  1 snd_seq_midi
videodev              130053  2 uvcvideo,videobuf2_core
ablk_helper            13597  1 aesni_intel
i915                  620419  3 
snd_seq_midi_event     14899  1 snd_seq_midi
cryptd                 20501  3 ghash_clmulni_intel,aesni_intel,ablk_helper
videobuf2_vmalloc      13056  1 uvcvideo
snd_seq                61930  2 snd_seq_midi,snd_seq_midi_event
lrw                    13294  1 aesni_intel
videobuf2_memops       13202  1 videobuf2_vmalloc
snd_timer              29989  2 snd_pcm,snd_seq
aes_x86_64             17255  1 aesni_intel
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
iwlwifi               183603  1 iwldvm
xts                    12922  1 aesni_intel
gf128mul               14951  2 lrw,xts
drm_kms_helper         49597  1 i915
snd                    69533  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   287564  4 i915,drm_kms_helper
joydev                 17613  0 
soundcore              12680  1 snd
btusb                  22431  0 
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
cfg80211              525244  3 iwldvm,mac80211,iwlwifi
parport_pc             28284  0 
bluetooth             247024  24 bnep,rfcomm,btusb
ppdev                  17113  0 
i2c_algo_bit           13564  1 i915
hp_accel               26012  0 
psmouse                97873  0 
mei                    41820  0 
rtsx_pci_ms            13180  0 
lis3lv02d              20200  1 hp_accel
hp_wmi                 18092  0 
mac_hid                13253  0 
microcode              23017  0 
lpc_ich                17144  0 
sparse_keymap          13890  1 hp_wmi
memstick               16605  1 rtsx_pci_ms
serio_raw              13215  0 
wmi                    19256  1 hp_wmi
video                  19652  1 i915
input_polldev          13896  1 lis3lv02d
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
hid_generic            12540  0 
usbhid                 47346  0 
hid                   105549  2 hid_generic,usbhid
rtsx_pci_sdmmc         17800  0 
r8169                  68716  0 
rtsx_pci               34214  2 rtsx_pci_ms,rtsx_pci_sdmmc
ahci                   25879  1 
libahci                31606  1 ahci


steven@ubuntu:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"You Shall Not Pass-guest"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 48:F8:B3:12:1D:36   
          Bit Rate=54 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-36 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:112   Missed beacon:0

steven@ubuntu:~$ sudo iwlist scan
[sudo] password for steven: 
eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 48:F8:B3:12:1D:36
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-27 dBm  
                    Encryption key:off
                    ESSID:"You Shall Not Pass-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000003d6b89ae
                    Extra: Last beacon: 68ms ago
                    IE: Unknown: 0018596F75205368616C6C204E6F7420506173732D6775657374
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180206F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: 48:F8:B3:12:1D:34
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-27 dBm  
                    Encryption key:on
                    ESSID:"You Shall Not Pass"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000003d6b8313
                    Extra: Last beacon: 68ms ago
                    IE: Unknown: 0012596F75205368616C6C204E6F742050617373
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180206F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00


And as a non-hacker, I have no idea how to interpret this.

---

### Post by praseodym on 2013-09-07
Deactivate the N-mode of the driver (bug):
```

echo "options iwlwifi 11n_disable=1" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```

---

