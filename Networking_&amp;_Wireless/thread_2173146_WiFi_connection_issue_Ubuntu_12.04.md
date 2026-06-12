---
title: "WiFi connection issue Ubuntu 12.04"
date: 2013-09-08
forum: Networking &amp; Wireless
---

### Post by luchfilip on 2013-09-08
I get connected to wifi network but i don't have internet, even thought there is, checked from phone. Any help would be greatly appreciated.

lspci
```

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:01.1 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:01.2 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b5)
00:1c.7 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 8 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Whistler [AMD Radeon HD 6600M Series] (rev ff)
09:00.0 Network controller: Intel Corporation Centrino Advanced-N 6230 (rev 34)
0a:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)
10:00.0 Ethernet controller: Atheros Communications Inc. AR8151 v2.0 Gigabit Ethernet (rev c0)
11:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
```

iwconfig
```
wlan0     IEEE 802.11abgn  ESSID:"Luch"            Mode:Managed  Frequency:2.412 GHz  Access Point: 54:E6:FC:B8:22:AF   
          Bit Rate=216 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=63/70  Signal level=-47 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:11  Invalid misc:27   Missed beacon:0


lo        no wireless extensions.


eth0      no wireless extensions.
```

lsmod
```
Module                  Size  Used byrndis_wlan             28551  0 
rndis_host             13568  1 rndis_wlan
cdc_ether              13320  1 rndis_host
usbnet                 25247  3 rndis_wlan,rndis_host,cdc_ether
usb_storage            39720  0 
pci_stub               12551  1 
vboxpci                22911  0 
vboxnetadp             13329  0 
vboxnetflt             27241  0 
vboxdrv               252211  3 vboxpci,vboxnetadp,vboxnetflt
snd_hda_codec_hdmi     31778  1 
snd_hda_codec_idt      60238  1 
bnep                   17791  2 
rfcomm                 38104  12 
parport_pc             32115  0 
ppdev                  12850  0 
binfmt_misc            17293  1 
arc4                   12474  2 
iwlwifi               364652  0 
snd_usb_audio         106661  1 
uvcvideo               72249  0 
videobuf2_core         32212  1 uvcvideo
snd_hda_intel          32983  3 
snd_usbmidi_lib        24590  1 snd_usb_audio
radeon                837142  0 
i915                  479235  3 
snd_hda_codec         116477  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13277  2 snd_usb_audio,snd_hda_codec
snd_pcm                81124  5 snd_hda_codec_hdmi,snd_usb_audio,snd_hda_intel,snd_hda_codec
videodev              100265  2 uvcvideo,videobuf2_core
coretemp               13362  0 
kvm_intel             127736  0 
kvm                   365588  1 kvm_intel
aesni_intel            17979  3 
cryptd                 19822  1 aesni_intel
aes_i586               16996  1 aesni_intel
videobuf2_vmalloc      12757  1 uvcvideo
snd_seq_midi           13133  0 
hp_accel               25729  0 
lis3lv02d              19270  1 hp_accel
videobuf2_memops       13213  1 videobuf2_vmalloc
hp_wmi                 13653  0 
mei                    36404  0 
snd_rawmidi            25426  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14476  1 snd_seq_midi
snd_seq                51594  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
lpc_ich                16993  0 
sparse_keymap          13659  1 hp_wmi
rtsx_pci_ms            13013  0 
mac80211              475546  1 iwlwifi
cfg80211              181041  3 rndis_wlan,iwlwifi,mac80211
psmouse                91408  0 
joydev                 17394  0 
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
btusb                  17952  0 
bluetooth             189625  24 bnep,rfcomm,btusb
snd                    62675  19 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_usb_audio,snd_hda_intel,snd_usbmidi_lib,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14636  1 snd
ttm                    76326  1 radeon
drm_kms_helper         47459  2 radeon,i915
drm                   240443  6 radeon,i915,ttm,drm_kms_helper
i2c_algo_bit           13317  2 radeon,i915
input_polldev          13649  1 lis3lv02d
snd_page_alloc         14109  2 snd_hda_intel,snd_pcm
microcode              18396  0 
serio_raw              13032  0 
wmi                    18745  1 hp_wmi
memstick               15886  1 rtsx_pci_ms
mac_hid                13078  0 
video                  19117  1 i915
lp                     17456  0 
parport                40931  3 parport_pc,ppdev,lp
hid_generic            12485  0 
usbhid                 46054  0 
hid                    82511  2 hid_generic,usbhid
rtsx_pci_sdmmc         17545  0 
rtsx_pci               32871  2 rtsx_pci_ms,rtsx_pci_sdmmc
atl1c                  36969  0 
ahci                   25621  5 
libahci                26166  1 ahci
```

sudo lshw -C network
```
*-network                      description: Wireless interface
       product: Centrino Advanced-N 6230
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: wlan0
       version: 34
       serial: 88:53:2e:7d:85:25
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.5.0-39-generic firmware=18.168.6.1 ip=192.168.1.4 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:55 memory:c2600000-c2601fff
  *-network
       description: Ethernet interface
       product: AR8151 v2.0 Gigabit Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: eth0
       version: c0
       serial: e4:11:5b:3b:e3:4e
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI latency=0 link=no multicast=yes port=twisted pair
       resources: irq:58 memory:c1500000-c153ffff ioport:2000(size=128)
```

iwlist scan
```
wlan0     Scan completed :          Cell 01 - Address: 54:E6:FC:B8:22:AF
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:"Luch"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000b7e847d80
                    Extra: Last beacon: 51628ms ago
                    IE: Unknown: 00044C756368
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101850003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34010D0A00000000000000000000000000000000000000
                    IE: Unknown: 3D16010D0A00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010006004000


lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.
```

Does anyone know what could be the issue? 
Thank you in advance.

---

### Post by wildmanne39 on 2013-09-08
Looks like you are using tethering you will have to disconnect that device and possibly reboot to clear it out, then do:
```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```
Thanks

---

