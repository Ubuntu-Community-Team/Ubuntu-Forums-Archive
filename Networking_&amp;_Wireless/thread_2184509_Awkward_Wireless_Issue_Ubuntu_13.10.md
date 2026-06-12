---
title: "Awkward Wireless Issue Ubuntu 13.10"
date: 2013-10-29
forum: Networking &amp; Wireless
---

### Post by ddomin4360 on 2013-10-29
I have a kind of weird issue with my laptop's wireless connection.

At home my wifi works perfect when I boot the laptop into windows but is terrible on Ubuntu. It works briefly after I connect and it will still show a strong signal, but it won't work anymore. If I want to keep going on the internet I have to disconnect and reconnect the wifi, but even that is a temporary fix.

This was a problem with my current and past router.

Now why is it weird? When I connect via Ethernet at home it works just fine, and when I am at school on their wifi it also has no problems. Just on ubuntu wifi, and only at home. Seems very strange.

My wireless card: Intel Centrino N-2230
Laptop: [SIZE=2][COLOR=#333333][FONT=Arial]Dell Inspiron i15R-2105sLV[/FONT][/COLOR][/SIZE]

---

### Post by praseodym on 2013-10-29
Hi,

please open a terminal with CTRL+ALT+T and show the outputs of:
```

lspci -nnk | grep -iA2 net
lsmod
iwconfig
sudo iwlist scan
```

---

### Post by ddomin4360 on 2013-11-06
Ok sorry this took me so long, very busy week.

For [COLOR=#000000][FONT=Ubuntu Mono]lspci -nnk | grep -iA2 net:
```
[/FONT][/COLOR]danny@danny-Inspiron-5520:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Realtek SemiconductorCo., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136](rev 05)
            Subsystem:Dell Device [1028:0569]
            Kerneldriver in use: r8169
02:00.0 Network controller [0280]: Intel Corporation CentrinoWireless-N 2230 [8086:0887] (rev c4)
            Subsystem:Intel Corporation Centrino Wireless-N 2230 BGN [8086:4462]


            Kerneldriver in use: iwlwifi[COLOR=#000000][FONT=Ubuntu Mono]
```

For [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]lsmod:
```
[/FONT][/COLOR]danny@danny-Inspiron-5520:~$ lsmod
Module                 Size  Used by
usb_storage            62062 0
joydev                17377  0
parport_pc            32701  0
ppdev                 17671  0
bnep                  19564  2
rfcomm                69070  12
snd_hda_codec_hdmi    41276  1
snd_hda_codec_conexant   56945  1
btusb                 28267  0
bluetooth            371874  22 bnep,btusb,rfcomm
x86_pkg_temp_thermal   14162  0
intel_powerclamp      14705  0
coretemp              13435  0
kvm_intel            138538  0
kvm                  431315  1 kvm_intel
crct10dif_pclmul      14289  0
crc32_pclmul          13113  0
ghash_clmulni_intel   13259  0
aesni_intel           55624  1
aes_x86_64            17131  1 aesni_intel
lrw                   13257  1 aesni_intel
gf128mul              14951  1 lrw
glue_helper           13990  1 aesni_intel
ablk_helper           13597  1 aesni_intel
cryptd                20329  3ghash_clmulni_intel,aesni_intel,ablk_helper
uvcvideo              80885  0
videobuf2_vmalloc     13216  1 uvcvideo
videobuf2_memops      13362  1 videobuf2_vmalloc
videobuf2_core        40469  1 uvcvideo
videodev             133390  2 uvcvideo,videobuf2_core
dell_wmi              12761  0
sparse_keymap         13948  1 dell_wmi
dell_laptop           17369  0
dcdbas                 14847  1 dell_laptop
arc4                  12608  2
iwldvm               237440  0
mac80211             596969  1 iwldvm
snd_hda_intel         48171  3
snd_hda_codec        188738  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep             13602  1 snd_hda_codec
snd_pcm              102033  3snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
microcode             23518  0
iwlwifi              165398  1 iwldvm
psmouse               97626  0
snd_page_alloc        18710  2 snd_pcm,snd_hda_intel
serio_raw             13413  0
cfg80211             479757  3 iwlwifi,mac80211,iwldvm
snd_seq_midi          13324  0
snd_seq_midi_event    14899  1 snd_seq_midi
snd_rawmidi           30095  1 snd_seq_midi
snd_seq               61560  2snd_seq_midi_event,snd_seq_midi
lpc_ich               21080  0
rts5139              331166  0
snd_seq_device        14497  3snd_seq,snd_rawmidi,snd_seq_midi
snd_timer             29433  2 snd_pcm,snd_seq
snd                   69141  17snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
i915                 655752  3
wmi                   19070  1 dell_wmi
video                 19318  1 i915
drm_kms_helper        52651  1 i915
drm                  296739  4 i915,drm_kms_helper
mei_me                 18421 0
lp                    17759  0
parport               42299  3 lp,ppdev,parport_pc
mac_hid               13205  0
mei                   77692  1 mei_me
i2c_algo_bit          13413  1 i915
soundcore             12680  1 snd
r8169                 67341  0
ahci                  25819  2
libahci               31898  1 ahci


mii                   13934  1 r8169[COLOR=#000000][FONT=Ubuntu Mono]
```

For iwconfig:
```
[/FONT][/COLOR]danny@danny-Inspiron-5520:~$ iwconfig
eth0      no wirelessextensions.
 
lo        no wirelessextensions.
 
wlan0     IEEE802.11bgn  ESSID:"Danny'sNetwork"  
         Mode:Managed  Frequency:2.437GHz  Access Point: 98:FC:11:EF:01:F5   
          Bit Rate=150Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7  RTS thr:off   Fragment thr:off
          PowerManagement:on
          LinkQuality=70/70  Signal level=-27 dBm  
          Rx invalidnwid:0  Rx invalid crypt:0  Rx invalid frag:0


          Tx excessiveretries:7  Invalid misc:86   Missed beacon:0[COLOR=#000000][FONT=Ubuntu Mono]
```

For sudo iwlist scan:
```
[/FONT][/COLOR]danny@danny-Inspiron-5520:~$ sudo iwlist scan
[sudo] password for danny:
eth0      Interfacedoesn't support scanning.
 
lo        Interface doesn'tsupport scanning.
 
wlan0     Scancompleted :
          Cell 01 -Address: 98:FC:11:EF:01:F5
                   Channel:6
                   Frequency:2.437 GHz (Channel 6)
                   Quality=42/70  Signal level=-68dBm  
                   Encryption key:on
                   ESSID:"Danny's Network"
                    BitRates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                             24 Mb/s; 36 Mb/s; 54 Mb/s
                    BitRates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                   Extra:tsf=0000006ee0d54fb8
                   Extra: Last beacon: 32ms ago
                    IE:Unknown: 000F44616E6E792773204E6574776F726B
                    IE:Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE:Unknown: 2A0100
                    IE:Unknown: 2F0100
                    IE:IEEE 802.11i/WPA2 Version 1
                       Group Cipher : TKIP
                       Pairwise Ciphers (2) : CCMP TKIP
                       Authentication Suites (1) : PSK
                    IE:Unknown: 32040C121860
                    IE:Unknown: 0B050100270000
                    IE:Unknown: 2D1A6E1817FFFF000000000000000000000000000000000000000000
                    IE: Unknown:3D16060F0000000000000000000000000000000000000000
                    IE:Unknown: 4A0E14000A002C01C800140005001900
                    IE:Unknown: 7F080100080000000040
                    IE:Unknown: DD950050F204104A0001101044000102103B00010310470010893E503D606A4EDE0AC0DA1766A2BDFC1021000B4C696E6B737973204C4C431023000E4C696E6B73797320454136323030102400064541363230301042000832303133303132351054000800060050F20400011011001244616E6E792773204E6574776F726B20415010080002200C103C0001031049000600372A000120
                    IE:Unknown: DD090010180201000C0000
                    IE:WPA Version 1
                       Group Cipher : TKIP
                       Pairwise Ciphers (2) : CCMP TKIP
                       Authentication Suites (1) : PSK
                    IE:Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 -Address: C8:3A:35:37:78:E0
                   Channel:6
                   Frequency:2.437 GHz (Channel 6)
                   Quality=39/70  Signal level=-71dBm  
                   Encryption key:on
                   ESSID:"Tenda_3778E0"
                    BitRates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                             24 Mb/s; 36 Mb/s; 54 Mb/s
                    BitRates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                   Mode:Master
                    Extra:tsf=0000003f58a18e56
                   Extra: Last beacon: 32ms ago
                    IE:Unknown: 000C54656E64615F333737384530
                    IE:Unknown: 010882840B162430486C
                    IE:Unknown: 030106
                    IE:Unknown: 2A0100
                    IE:Unknown: 2F0100
                    IE:Unknown: 32040C121860
                    IE:Unknown: 2D1A7E181BFF00000000000000000000000000000000000000000000
                    IE:Unknown: 3D16060F0400000000000000000000000000000000000000
                    IE:Unknown: DD090010180202F02C0000
                    IE:WPA Version 1
                       Group Cipher : CCMP
                       Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE:Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 03 -Address: 9A:FC:11:EF:01:F6
                   Channel:6
                   Frequency:2.437 GHz (Channel 6)
                   Quality=68/70  Signal level=-42dBm  
                   Encryption key:off
                   ESSID:"Danny's Network-guest"
                    BitRates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                             24 Mb/s; 36 Mb/s; 54 Mb/s
                    BitRates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                   Mode:Master
                   Extra:tsf=0000006ee0d23d02
                   Extra: Last beacon: 32ms ago
                    IE:Unknown: 001544616E6E792773204E6574776F726B2D6775657374
                    IE:Unknown: 010882848B962430486C
                    IE:Unknown: 030106
                    IE:Unknown: 2A0100
                    IE:Unknown: 2F0100
                    IE:Unknown: 32040C121860
                    IE:Unknown: 0B0500001C0000
                    IE:Unknown: 2D1A6E1817FFFF000000000000000000000000000000000000000000
                    IE:Unknown: 3D16060F0000000000000000000000000000000000000000
                    IE: Unknown:4A0E14000A002C01C800140005001900
                    IE:Unknown: 7F080100080000000040
                    IE:Unknown: DD090010180200000C0000
                    IE:Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
 


danny@danny-Inspiron-5520:~$[COLOR=#000000][FONT=Ubuntu Mono]
```

Hope that helps. Thank you[/FONT][/COLOR]

---

### Post by praseodym on 2013-11-06
Deactivate the N-mode of the driver (bug) and the power management:
```

echo "options iwlwifi 11n_disable=1" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
sudo iwconfig wlan0 power off
```
I recommend changing the channel to fixed "13" and to pure WPA2-AES (CCMP) encryption.

Check after that:
```

dmesg | grep iwl
iwconfig
iwlist chan
```

---

### Post by ddomin4360 on 2013-11-06
> **praseodym said:**
> Deactivate the N-mode of the driver (bug) and the power management:
```

echo "options iwlwifi 11n_disable=1" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
sudo iwconfig wlan0 power off
```
I recommend changing the channel to fixed "13" and to pure WPA2-AES (CCMP) encryption.

Check after that:
```

dmesg | grep iwl
iwconfig
iwlist chan
```

How do I change the channel to fixed 13?

Also thank you, here's what was produced:

```
danny@danny-Inspiron-5520:~$ echo "options iwlwifi 11n_disable=1" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
[sudo] password for danny: 
options iwlwifi 11n_disable=1
danny@danny-Inspiron-5520:~$ sudo -rfv iwlwifi
sudo: iwlwifi: command not found
danny@danny-Inspiron-5520:~$ sudo modprobe -rfv iwlwifi
FATAL: Module iwlwifi is in use.
danny@danny-Inspiron-5520:~$ sudo modprobe -v iwlwifi
danny@danny-Inspiron-5520:~$ sudo iwconfig wlan0 power off
danny@danny-Inspiron-5520:~$ 
danny@danny-Inspiron-5520:~$ dmesg | grep iwl
[    2.031388] iwlwifi 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[    2.031520] iwlwifi 0000:02:00.0: irq 45 for MSI/MSI-X
[    2.049498] iwlwifi 0000:02:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
[    2.068264] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUG disabled
[    2.068268] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[    2.068270] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[    2.068272] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_P2P disabled
[    2.068275] iwlwifi 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N 2230 BGN, REV=0xC8
[    2.068389] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[    2.098942] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[    3.303484] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[    3.311226] iwlwifi 0000:02:00.0: Radio type=0x2-0x0-0x0
[    3.553769] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[    3.561543] iwlwifi 0000:02:00.0: Radio type=0x2-0x0-0x0
[ 8789.237981] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[ 8789.245760] iwlwifi 0000:02:00.0: Radio type=0x2-0x0-0x0
[11152.837434] iwlwifi 0000:02:00.0: fail to flush all tx fifo queues Q 2
[11152.837443] iwlwifi 0000:02:00.0: Current SW read_ptr 61 write_ptr 62
[11152.837493] iwl data: 00000000: 00 00 00 00 00 00 00 00 00 00 00 20 00 00 00 00  ........... ....
[11152.837509] iwlwifi 0000:02:00.0: FH TRBs(0) = 0x00000000
[11152.837524] iwlwifi 0000:02:00.0: FH TRBs(1) = 0xc010b056
[11152.837539] iwlwifi 0000:02:00.0: FH TRBs(2) = 0x00000000
[11152.837554] iwlwifi 0000:02:00.0: FH TRBs(3) = 0x80300041
[11152.837568] iwlwifi 0000:02:00.0: FH TRBs(4) = 0x00000000
[11152.837598] iwlwifi 0000:02:00.0: FH TRBs(5) = 0x00000000
[11152.837636] iwlwifi 0000:02:00.0: FH TRBs(6) = 0x00000000
[11152.837651] iwlwifi 0000:02:00.0: FH TRBs(7) = 0x00709079
[11152.837710] iwlwifi 0000:02:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [66,66]
[11152.837769] iwlwifi 0000:02:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[11152.837831] iwlwifi 0000:02:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [61,62]
[11152.837914] iwlwifi 0000:02:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[11152.837999] iwlwifi 0000:02:00.0: Q 4 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[11152.838081] iwlwifi 0000:02:00.0: Q 5 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[11152.838163] iwlwifi 0000:02:00.0: Q 6 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[11152.838243] iwlwifi 0000:02:00.0: Q 7 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[11152.838300] iwlwifi 0000:02:00.0: Q 8 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[11152.838357] iwlwifi 0000:02:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [122,122]
[11152.838414] iwlwifi 0000:02:00.0: Q 10 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[11152.838471] iwlwifi 0000:02:00.0: Q 11 is active and mapped to fifo 1 ra_tid 0x0000 [82,87]
[11152.838529] iwlwifi 0000:02:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[11152.838585] iwlwifi 0000:02:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[11152.838643] iwlwifi 0000:02:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[11152.838699] iwlwifi 0000:02:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[11152.838756] iwlwifi 0000:02:00.0: Q 16 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[11152.838813] iwlwifi 0000:02:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[11152.838869] iwlwifi 0000:02:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[11152.838926] iwlwifi 0000:02:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[11180.921519] iwlwifi 0000:02:00.0: fail to flush all tx fifo queues Q 2
[11180.921536] iwlwifi 0000:02:00.0: Current SW read_ptr 84 write_ptr 91
[11180.921590] iwl data: 00000000: 00 00 f0 07 00 00 00 00 00 00 00 00 00 00 00 00  ................
[11180.921628] iwlwifi 0000:02:00.0: FH TRBs(0) = 0x00000000
[11180.921644] iwlwifi 0000:02:00.0: FH TRBs(1) = 0xc010b075
[11180.921659] iwlwifi 0000:02:00.0: FH TRBs(2) = 0x00000000
[11180.921674] iwlwifi 0000:02:00.0: FH TRBs(3) = 0x80300042
[11180.921688] iwlwifi 0000:02:00.0: FH TRBs(4) = 0x00000000
[11180.921703] iwlwifi 0000:02:00.0: FH TRBs(5) = 0x00000000
[11180.921718] iwlwifi 0000:02:00.0: FH TRBs(6) = 0x00000000
[11180.921732] iwlwifi 0000:02:00.0: FH TRBs(7) = 0x00709086
[11180.921792] iwlwifi 0000:02:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [67,67]
[11180.921849] iwlwifi 0000:02:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[11180.921905] iwlwifi 0000:02:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [84,91]
[11180.921962] iwlwifi 0000:02:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[11180.922019] iwlwifi 0000:02:00.0: Q 4 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[11180.922076] iwlwifi 0000:02:00.0: Q 5 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[11180.922132] iwlwifi 0000:02:00.0: Q 6 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[11180.922190] iwlwifi 0000:02:00.0: Q 7 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[11180.922246] iwlwifi 0000:02:00.0: Q 8 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[11180.922303] iwlwifi 0000:02:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [135,135]
[11180.922359] iwlwifi 0000:02:00.0: Q 10 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[11180.922417] iwlwifi 0000:02:00.0: Q 11 is active and mapped to fifo 1 ra_tid 0x0000 [111,118]
[11180.922473] iwlwifi 0000:02:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[11180.922530] iwlwifi 0000:02:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[11180.922586] iwlwifi 0000:02:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[11180.922642] iwlwifi 0000:02:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[11180.922700] iwlwifi 0000:02:00.0: Q 16 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[11180.922757] iwlwifi 0000:02:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[11180.922814] iwlwifi 0000:02:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[11180.922871] iwlwifi 0000:02:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[11182.931801] iwlwifi 0000:02:00.0: fail to flush all tx fifo queues Q 2
[11182.931811] iwlwifi 0000:02:00.0: Current SW read_ptr 86 write_ptr 93
[11182.931861] iwl data: 00000000: 00 00 c0 1f 00 00 00 00 00 00 00 00 00 00 00 00  ................
[11182.931876] iwlwifi 0000:02:00.0: FH TRBs(0) = 0x00000000
[11182.931891] iwlwifi 0000:02:00.0: FH TRBs(1) = 0xc010b078
[11182.931906] iwlwifi 0000:02:00.0: FH TRBs(2) = 0x00000000
[11182.931921] iwlwifi 0000:02:00.0: FH TRBs(3) = 0x80300043
[11182.931936] iwlwifi 0000:02:00.0: FH TRBs(4) = 0x00000000
[11182.931951] iwlwifi 0000:02:00.0: FH TRBs(5) = 0x00000000
[11182.931965] iwlwifi 0000:02:00.0: FH TRBs(6) = 0x00000000
[11182.931980] iwlwifi 0000:02:00.0: FH TRBs(7) = 0x00709086
[11182.932037] iwlwifi 0000:02:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [68,68]
[11182.932095] iwlwifi 0000:02:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[11182.932151] iwlwifi 0000:02:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [86,93]
[11182.932209] iwlwifi 0000:02:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[11182.932265] iwlwifi 0000:02:00.0: Q 4 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[11182.932323] iwlwifi 0000:02:00.0: Q 5 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[11182.932379] iwlwifi 0000:02:00.0: Q 6 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[11182.932436] iwlwifi 0000:02:00.0: Q 7 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[11182.932492] iwlwifi 0000:02:00.0: Q 8 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[11182.932549] iwlwifi 0000:02:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [135,135]
[11182.932607] iwlwifi 0000:02:00.0: Q 10 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[11182.932663] iwlwifi 0000:02:00.0: Q 11 is active and mapped to fifo 1 ra_tid 0x0000 [112,121]
[11182.932720] iwlwifi 0000:02:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[11182.932777] iwlwifi 0000:02:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[11182.932834] iwlwifi 0000:02:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[11182.932890] iwlwifi 0000:02:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[11182.932947] iwlwifi 0000:02:00.0: Q 16 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[11182.933004] iwlwifi 0000:02:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[11182.933061] iwlwifi 0000:02:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[11182.933118] iwlwifi 0000:02:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[11822.633380] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[11822.641177] iwlwifi 0000:02:00.0: Radio type=0x2-0x0-0x0
[12027.248103] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[12027.255929] iwlwifi 0000:02:00.0: Radio type=0x2-0x0-0x0
danny@danny-Inspiron-5520:~$ 
danny@danny-Inspiron-5520:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Danny's Network"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 98:FC:11:EF:01:F5   
          Bit Rate=65 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-23 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:63   Missed beacon:0

danny@danny-Inspiron-5520:~$ 
danny@danny-Inspiron-5520:~$ iwlist chan
eth0      no frequency information.

lo        no frequency information.

wlan0     13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Current Frequency:2.412 GHz (Channel 1)

danny@danny-Inspiron-5520:~$ 


```

---

### Post by praseodym on 2013-11-07
Enter the router settings, check the manual

---

### Post by easytvshop.art on 2013-11-08
Thanks for post this issue i have done it and fix my problem. i am do for [easytvshop.com]("http://www.easytvshop.com")

---

