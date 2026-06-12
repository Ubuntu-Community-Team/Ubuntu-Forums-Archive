---
title: "[UNSOLVED] Slow speeds just on Ubuntu (Asus PCIE N10)"
date: 2013-10-18
forum: Networking &amp; Wireless
---

### Post by Cracky7 on 2013-10-18
I finished building my computer a day ago, and now I'm facing with this problem. I have a wireless card (Asus PCIE N10) installed, and I'm getting speeds of 0.77Mbps on speedtest.net. When I try the same test on either my laptop or Windows 8, I get around x10 that speed (6-7Mbps).

After googling a bit, I logged into the router and tried to change the channel to 11, it didn't work. So I'll trust you guys with this one. Thanks! I'm using latest Ubuntu 13.10

iwconfig:
```
eth0      no wireless extensions.

lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"DARP"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 02:1E:58:41:EE:47   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=44/70  Signal level=-66 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:3035   Missed beacon:0
```

I tried to install the drivers that came with the card, but they can't be installed in Ubuntu versions older than 10.10.

---

### Post by praseodym on 2013-10-18
Please show:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
cat /etc/resolv.conf
iwlist chan
sudo iwlist scan
```

---

### Post by Cracky7 on 2013-10-18
lspci -nnk | grep -iA2 net
```
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
	Subsystem: ASUSTeK Computer Inc. Device [1043:84b5]
	Kernel driver in use: rtl8192ce
--
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
	Subsystem: Micro-Star International Co., Ltd. Device [1462:7693]
	Kernel driver in use: r8169



```

lsusb
```
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 011 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 010 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 003: ID 045e:0737 Microsoft Corp. Compact Optical Mouse 500
Bus 009 Device 002: ID 046d:c31c Logitech, Inc. Keyboard K120 for Business
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 1130:1620 Tenx Technology, Inc. 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
lsmod
```
Module                  Size  Used by
nls_iso8859_1          12713  0 
usb_storage            62062  0 
parport_pc             32701  0 
ppdev                  17671  0 
bnep                   19564  2 
rfcomm                 69070  0 
bluetooth             371874  10 bnep,rfcomm
joydev                 17377  0 
binfmt_misc            17468  1 
hid_generic            12548  0 
usbhid                 53014  0 
snd_usb_audio         149162  1 
hid                   101512  2 hid_generic,usbhid
snd_usbmidi_lib        25070  1 snd_usb_audio
arc4                   12608  2 
radeon               1402449  4 
rtl8192ce              53550  0 
snd_hda_codec_hdmi     41276  1 
rtl_pci                26641  1 rtl8192ce
rtlwifi                63229  2 rtl_pci,rtl8192ce
snd_hda_codec_realtek    51465  1 
snd_hda_intel          48171  5 
snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
rtl8192c_common        48877  1 rtl8192ce
mxm_wmi                13021  0 
mac80211              596969  3 rtl_pci,rtlwifi,rtl8192ce
kvm_amd                59958  0 
kvm                   431315  1 kvm_amd
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ttm                    83995  1 radeon
ablk_helper            13597  1 aesni_intel
snd_hwdep              13602  2 snd_usb_audio,snd_hda_codec
snd_pcm               102033  4 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
cfg80211              479757  2 mac80211,rtlwifi
cryptd                 20329  3 ghash_clmulni_intel,aesni_intel,ablk_helper
psmouse                97626  0 
snd_seq_midi           13324  0 
drm_kms_helper         52651  1 radeon
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30095  2 snd_usbmidi_lib,snd_seq_midi
microcode              23518  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
edac_core              62312  0 
snd_timer              29433  2 snd_pcm,snd_seq
snd                    69141  25 snd_hda_codec_realtek,snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
wmi                    19070  1 mxm_wmi
soundcore              12680  1 snd
drm                   296739  6 ttm,drm_kms_helper,radeon
ohci_pci               13561  0 
serio_raw              13413  0 
edac_mce_amd           22617  0 
k10temp                13126  0 
fam15h_power           13119  0 
sp5100_tco             13979  0 
i2c_algo_bit           13413  1 radeon
i2c_piix4              22106  0 
mac_hid                13205  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
pata_acpi              13038  0 
r8169                  67341  0 
pata_atiixp            13242  0 
mii                    13934  1 r8169
ahci                   25819  2 
libahci                31898  1 ahci

```

cat /etc/resolv.conf
```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1

```

iwlist chan
```
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
          Current Frequency:2.462 GHz (Channel 11)



```

sudo iwlist scan
```
eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: 02:1E:58:41:EE:47
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"DARP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000039c32aea8
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 000444415250
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180201F4
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

```

---

### Post by Cracky7 on 2013-10-19
Bump

---

