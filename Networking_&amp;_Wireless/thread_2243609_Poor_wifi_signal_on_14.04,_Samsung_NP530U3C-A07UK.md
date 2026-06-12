---
title: "Poor wifi signal on 14.04, Samsung NP530U3C-A07UK"
date: 2014-09-10
forum: Networking &amp; Wireless
---

### Post by jftsang on 2014-09-10
Hello,

After reinstalling 14.04 a couple of weeks ago, I've begun to notice that my laptop perceives a very poor wifi signal for my home network. Sometimes, the network can't be seen, and when it can be, often the attempts to connect to it are in vain. I'm able to connect to my college and work neworks. Perhaps it's because those networks don't have WPA, but turning off WPA for my home network didn't seem to help. Or perhaps it's because those networks are stronger, though my other devices at home don't seem to have a problem.

I've tried the usual tricks, including
```
# service network-manager restart
```
to no avail. 

/etc/modprobe.d/iwlwifi.comf:
```
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
```

lsmod:
```
$ lsmod
Module                  Size  Used by
rndis_wlan             50281  0 
rndis_host             14503  1 rndis_wlan
cdc_ether              14351  1 rndis_host
usbnet                 43913  3 rndis_host,rndis_wlan,cdc_ether
pci_stub               12622  1 
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             27613  0 
vboxdrv               339502  3 vboxnetadp,vboxnetflt,vboxpci
snd_hda_codec_hdmi     46368  1 
snd_hda_codec_realtek    65580  1 
btusb                  32412  0 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
joydev                 17381  0 
intel_rapl             18773  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
cdc_acm                28803  0 
kvm_intel             143060  0 
kvm                   451511  1 kvm_intel
wl                   4207846  0 
arc4                   12608  2 
bnep                   19624  2 
snd_hda_intel          56451  7 
iwldvm                232285  0 
crct10dif_pclmul       14289  0 
rfcomm                 69160  12 
crc32_pclmul           13113  0 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
ghash_clmulni_intel    13216  0 
bluetooth             391136  22 bnep,btusb,rfcomm
mac80211              630653  1 iwldvm
snd_hwdep              13602  1 snd_hda_codec
cryptd                 20359  1 ghash_clmulni_intel
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
lib80211               14381  1 wl
iwlwifi               169932  1 iwldvm
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
cfg80211              484040  5 wl,iwlwifi,mac80211,rndis_wlan,iwldvm
i915                  783805  2 
snd_rawmidi            30144  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
drm_kms_helper         53081  1 i915
drm                   303102  3 i915,drm_kms_helper
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
i2c_algo_bit           13413  1 i915
snd                    69322  25 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
binfmt_misc            17468  1 
soundcore              12680  1 snd
mei_me                 18627  0 
mei                    82276  1 mei_me
wmi                    19177  0 
lpc_ich                21080  0 
video                  19476  1 i915
mac_hid                13205  0 
serio_raw              13462  0 
nls_iso8859_1          12713  1 
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
ahci                   25819  6 
psmouse               106678  0 
libahci                32716  1 ahci
r8169                  67581  0 
mii                    13934  2 r8169,usbnet
```

iwconfig:
```
$ iwconfig 
usb0      no wireless extensions.

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

Running 'iwlist wlan0 scanning' does see the network right now:
```
          Cell 02 - Address: 9C:97:26:9C:43:97
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"15SpringfieldRoad"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000087f83418a
                    Extra: Last beacon: 20612ms ago
                    IE: Unknown: 00113135537072696E676669656C64526F6164
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A1C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080400000000000000000000000000000000000000
                    IE: Unknown: DD180050F204104A00011010440001021049000600372A000120
                    IE: Unknown: DD090010180201000C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00

```

lspci:
```

$ lspci
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 Network controller: Intel Corporation Centrino Advanced-N 6235 (rev 24)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)

```

Kernel version:
```
$ uname -r
3.13.0-35-generic

```
I've tried installing past 'linux-headers' and 'linux-image' packages and booting with those, but that didn't help, though I haven't tried this systematically. 

Any tips?

---

### Post by jftsang on 2014-09-10
Just now, I was able to connect when I was less than a metre away from the router. The reported signal strength has fallen now that I've moved a couple of metres away, but I'm still connected. When I was in another room, I couldn't connect at all.

---

