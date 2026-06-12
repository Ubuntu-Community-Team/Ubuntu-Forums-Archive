---
title: "RTL8192E Wireless Card - Samsung R580 Laptop"
date: 2014-04-15
forum: Networking &amp; Wireless
---

### Post by mamen on 2014-04-15
Hi,

I need a help with this wireless card. i tried everything i know, and i cant still put this card working correctly. 
Now i am running with ndiswrapper, and have a lot of bugs and errors :(
The default module that came with ubuntu was also a problem, was always disconnecting, and most of the times cant even connect to a wireless network..


Can please someone help me setting this right please? I am doing a fresh ubuntu install to do a fresh, and i am open to all your ideas.

---

### Post by praseodym on 2014-04-15
Hi,

please show the outputs of:
```

lspci -nnk | grep -iA2 net
lsmod
iwconfig
rfkill list
sudo iwlist scan
cat /etc/resolv.conf
dmesg | grep ndis
```

---

### Post by mamen on 2014-04-15
I have lan cable connected to the laptop.


lspci -nnk | grep -iA2 net
```

03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192E/RTL8192SE Wireless LAN Controller [10ec:8192] (rev 01)
	Subsystem: Askey Computer Corp. Device [144f:7160]
	Kernel driver in use: rtl819xE
07:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Yukon Optima 88E8059 [PCIe Gigabit Ethernet Controller with AVB] [11ab:4381] (rev 11)
	Subsystem: Samsung Electronics Co Ltd Device [144d:c06a]
	Kernel driver in use: sky2

```

lsmod
```
Module                  Size  Used by
parport_pc             32701  0 
ppdev                  17671  0 
bnep                   19704  2 
rfcomm                 69130  12 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm_intel             138567  0 
joydev                 17377  0 
kvm                   431754  1 kvm_intel
snd_hda_codec_hdmi     41154  4 
r8192e_pci            201415  0 
samsung_laptop         14486  0 
uvcvideo               80885  0 
rtllib                155790  1 r8192e_pci
lib80211               14381  1 rtllib
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40499  1 uvcvideo
videodev              133509  2 uvcvideo,videobuf2_core
nouveau               943749  3 
snd_hda_codec_realtek    56475  1 
snd_hda_intel          52267  5 
snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
rtl8192se              63196  0 
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
mxm_wmi                13021  1 nouveau
rtl_pci                26641  1 rtl8192se
wmi                    19070  2 mxm_wmi,nouveau
ttm                    84169  1 nouveau
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30095  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
drm_kms_helper         52710  1 nouveau
microcode              23656  0 
drm                   297056  5 ttm,drm_kms_helper,nouveau
rtlwifi                63229  2 rtl_pci,rtl8192se
i2c_algo_bit           13413  1 nouveau
btusb                  28267  0 
snd                    69141  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
mac80211              597268  3 rtl_pci,rtlwifi,rtl8192se
soundcore              12680  1 snd
cfg80211              480503  2 mac80211,rtlwifi
bluetooth             372041  22 bnep,btusb,rfcomm
psmouse                97655  0 
serio_raw              13413  0 
lpc_ich                21080  0 
mac_hid                13205  0 
intel_ips              18470  0 
video                  19318  2 samsung_laptop,nouveau
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
ahci                   25819  3 
libahci                32009  1 ahci
sky2                   58191  0 


```


iwconfig

```

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     802.11bgn  ESSID:"Ricardo"  Nickname:"rtl8192E"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:05:CA:63:FE:E8   
          Bit Rate=1 Mb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

rfkill list

```
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: samsung-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

sudo iwlist scan
```

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:05:CA:63:FE:E9
                    ESSID:"FON_ZON_FREE_INTERNET"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:1
                    Encryption key:off
                    Bit Rates:270 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 11 9 12 18 24 36 48 54 
                    Quality=65/100  Signal level=-55 dBm  Noise level=-102 dBm
                    Extra: Last beacon: 93ms ago
          Cell 02 - Address: 00:05:CA:63:FE:E8
                    ESSID:"Ricardo"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:270 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 11 9 12 18 24 36 48 54 
                    Quality=65/100  Signal level=-55 dBm  Noise level=-102 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD270050F204104A000110104400010210470010BC329E001DD811B286010005CA63FEE8103C000101
                    Extra: Last beacon: 93ms ago
          Cell 03 - Address: 00:24:B2:2D:38:5A
                    ESSID:"ZON-Santos"
                    Protocol:IEEE802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=60/100  Signal level=-54 dBm  Noise level=-100 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 148ms ago
          Cell 04 - Address: BC:14:01:9D:F3:48
                    ESSID:"ZON-F340"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:12
                    Encryption key:on
                    Bit Rates:130 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 11 9 12 18 24 36 48 54 
                    Quality=69/100  Signal level=-56 dBm  Noise level=-104 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD270050F204104A0001101044000102104700102880288028801880A880BC14019DF348103C000101
                    Extra: Last beacon: 10ms ago
          Cell 05 - Address: BC:14:01:9D:F3:49
                    ESSID:"FON_ZON_FREE_INTERNET"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:12
                    Encryption key:off
                    Bit Rates:130 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 11 9 12 18 24 36 48 54 
                    Quality=71/100  Signal level=-57 dBm  Noise level=-105 dBm
                    Extra: Last beacon: 10ms ago
          Cell 06 - Address: 00:05:CA:72:4E:A8
                    ESSID:"Sandra zon"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:130 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 11 9 12 18 24 36 48 54 
                    Quality=60/100  Signal level=-56 dBm  Noise level=-100 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD270050F204104A000110104400010210470010BC329E001DD811B286010005CA724EA8103C000101
                    Extra: Last beacon: 64ms ago
          Cell 07 - Address: 00:05:CA:72:4E:A9
                    ESSID:"FON_ZON_FREE_INTERNET"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:11
                    Encryption key:off
                    Bit Rates:130 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 11 9 12 18 24 36 48 54 
                    Quality=62/100  Signal level=-56 dBm  Noise level=-101 dBm
                    Extra: Last beacon: 63ms ago
          Cell 08 - Address: 1E:3E:84:08:89:21
                    ESSID:"DIRECT-Vj-BRAVIA"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:144.5 Mb/s
                    Extra: Rates (Mb/s): 6 9 12 18 24 36 48 54 
                    Quality=100/100  Signal level=-55 dBm  Noise level=-120 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD3A0050F204104A00011010440001021049000600372A00012010110012425241564941204B444C2D343257363531411054000800070050F2040001
                    Extra: Last beacon: 214ms ago
          Cell 09 - Address: 00:3A:99:8A:22:30
                    ESSID:"<hidden>\x00"
                    Protocol:IEEE802.11bg
                    Mode:Master
                    Channel:8
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=62/100  Signal level=-55 dBm  Noise level=-101 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 106ms ago


```

cat /etc/resolv.conf
```

# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search home


```

dmesg | grep ndis

```
Nothing came up
```

---

### Post by mamen on 2014-04-15
After a fresh install wireless doesnt even conect to a network, just keeps asking the wifi password..

---

### Post by praseodym on 2014-04-15
Which Ubuntu version is it? Please show also
[B]
uname -a[/B]

---

### Post by mamen on 2014-04-15
i am running Ubuntu 13.10

uname -a
```

Linux LaptopLinux 3.11.0-19-generic #33-Ubuntu SMP Tue Mar 11 18:48:34 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by praseodym on 2014-04-15
Try this driver:
```

sudo apt-get install --reinstall linux-headers-generic linux-headers-$(uname -r) build-essential dkms git
git clone https://github.com/FreedomBen/rtl8188ce-linux-driver
cd rtl8188ce-linux-driver
make
sudo make install
sudo cp -r firmware/* /lib/firmware
echo "blacklist r8192e_pci\nblacklist rtl8192se" | sudo tee /etc/modprobe.d/blacklist-realtek.conf
```
Reboot.

---

### Post by mamen on 2014-04-15
still doesnt connect.. :(

---

### Post by praseodym on 2014-04-15
Ok, lets check now:
```

lsmod
iwconfig
dmesg | grep rtl
sudo iwlist scan
cat /etc/resolv.conf
iwlist chan
rfkill list
```

---

### Post by mamen on 2014-04-15
lsmod
```
Module                  Size  Used by
michael_mic            12612  0 
arc4                   12608  0 
rtllib_crypt_tkip      17179  -1 
rtllib_crypt_ccmp      12829  -1 
parport_pc             32701  0 
ppdev                  17671  0 
rfcomm                 69130  12 
bnep                   19704  2 
snd_hda_codec_hdmi     41154  4 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm_intel             138567  0 
kvm                   431754  1 kvm_intel
joydev                 17377  0 
samsung_laptop         14486  0 
binfmt_misc            17468  1 
uvcvideo               80885  0 
snd_hda_codec_realtek    56475  1 
snd_hda_intel          52267  5 
snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
r8192e_pci            201415  0 
rtllib                155790  1 r8192e_pci
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40499  1 uvcvideo
lib80211               14381  3 rtllib,rtllib_crypt_ccmp,rtllib_crypt_tkip
videodev              133509  2 uvcvideo,videobuf2_core
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
nouveau               943749  3 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
rtl8192se              94062  0 
mxm_wmi                13021  1 nouveau
rtlwifi               110108  1 rtl8192se
psmouse                97655  0 
snd_rawmidi            30095  1 snd_seq_midi
wmi                    19070  2 mxm_wmi,nouveau
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
ttm                    84169  1 nouveau
drm_kms_helper         52710  1 nouveau
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
drm                   297056  5 ttm,drm_kms_helper,nouveau
serio_raw              13413  0 
i2c_algo_bit           13413  1 nouveau
btusb                  28267  0 
snd                    69141  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
bluetooth             372041  22 bnep,btusb,rfcomm
soundcore              12680  1 snd
mac80211              597268  2 rtlwifi,rtl8192se
microcode              23656  0 
cfg80211              480503  2 mac80211,rtlwifi
mac_hid                13205  0 
lpc_ich                21080  0 
intel_ips              18470  0 
video                  19318  2 samsung_laptop,nouveau
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
ahci                   25819  3 
libahci                32009  1 ahci
sky2                   58191  0 
```

iwconfig
```
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     802.11bgn  ESSID:"Ricardo"  Nickname:"rtl8192E"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:05:CA:63:FE:E8   
          Bit Rate=1 Mb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

dmesg | grep rtl
```
[    9.155774] rtlwifi: module verification failed: signature and/or required key missing - tainting kernel
[    9.708406] rtllib: module is from the staging directory, the quality is unknown, you have been warned.
[    9.762545] rtl819xE:EEPROM ID is invalid:4a4, 8129
[   64.251126] rtllib_crypt_ccmp: module is from the staging directory, the quality is unknown, you have been warned.
[   64.255183] rtllib_crypt_tkip: module is from the staging directory, the quality is unknown, you have been warned.
[   83.793047] rtl819x_TxCheckStuck: QueueID=6 tcb_desc->nStuckCount=2
[   85.797436] rtl819x_TxCheckStuck: QueueID=6 tcb_desc->nStuckCount=3
[   87.801933] rtl819x_TxCheckStuck: QueueID=6 tcb_desc->nStuckCount=4
[   89.806333] rtl819x_TxCheckStuck: QueueID=6 tcb_desc->nStuckCount=5
[   91.810810] rtl819x_TxCheckStuck: QueueID=6 tcb_desc->nStuckCount=6
[   93.814413] rtl819x_TxCheckStuck: QueueID=6 tcb_desc->nStuckCount=7
[   95.817922] rtl819x_TxCheckStuck: QueueID=6 tcb_desc->nStuckCount=8
[   95.817932] rtl819x_ifcheck_resetornot(): TxResetType is 2, RxResetType is 0
[  130.884094] rtl819x_TxCheckStuck: QueueID=6 tcb_desc->nStuckCount=2
[  130.884103] rtl819x_ifcheck_resetornot(): TxResetType is 2, RxResetType is 0
[  139.905271] rtl819x_TxCheckStuck: QueueID=6 tcb_desc->nStuckCount=2
[  139.905281] rtl819x_ifcheck_resetornot(): TxResetType is 2, RxResetType is 0
[  140.237155] rtl819xE:rtl8192_phy_SwChnl(): ERR !! driver is not up
[  140.237160] rtl819xE:rtl8192_SetBWModeWorkItem(): ERR!! driver is not up
[  140.930383] rtllib: received DELBA while QOS or HT is not supported(0, 1)
[  140.930729] rtllib: received DELBA while QOS or HT is not supported(0, 1)
[  140.931208] rtllib: received DELBA while QOS or HT is not supported(0, 1)
[  148.927235] rtl819x_TxCheckStuck: QueueID=6 tcb_desc->nStuckCount=2
[  150.930547] rtl819x_TxCheckStuck: QueueID=6 tcb_desc->nStuckCount=3
[  152.933860] rtl819x_TxCheckStuck: QueueID=6 tcb_desc->nStuckCount=4
[  154.937296] rtl819x_TxCheckStuck: QueueID=6 tcb_desc->nStuckCount=5
[  156.940854] rtl819x_TxCheckStuck: QueueID=6 tcb_desc->nStuckCount=6
[  158.944250] rtl819x_TxCheckStuck: QueueID=6 tcb_desc->nStuckCount=7
[  158.944261] rtl819x_ifcheck_resetornot(): TxResetType is 2, RxResetType is 0
[  184.625345] rtl819xE:No more TX desc@6, ring->idx = 29, idx = 45, skblen = 0x32 queuelen=16
[  184.625354] rtl819xE:No more TX desc@6, ring->idx = 29, idx = 45, skblen = 0x32 queuelen=16
[  185.997727] rtl819x_TxCheckStuck: QueueID=6 tcb_desc->nStuckCount=2
[  188.002018] rtl819x_TxCheckStuck: QueueID=6 tcb_desc->nStuckCount=3
[  188.002029] rtl819x_ifcheck_resetornot(): TxResetType is 2, RxResetType is 0
[  201.037041] rtl819x_TxCheckStuck: QueueID=6 tcb_desc->nStuckCount=2
[  203.041379] rtl819x_TxCheckStuck: QueueID=6 tcb_desc->nStuckCount=3
[  203.041390] rtl819x_ifcheck_resetornot(): TxResetType is 2, RxResetType is 0
[  203.405381] rtl819xE:rtl8192_phy_SwChnl(): ERR !! driver is not up
[  210.254922] rtllib: can't get TS for TXTS in rtllib_rx_DELBA()
[  212.067809] rtl819x_TxCheckStuck: QueueID=6 tcb_desc->nStuckCount=2
[  214.072259] rtl819x_TxCheckStuck: QueueID=6 tcb_desc->nStuckCount=3
[  216.076625] rtl819x_TxCheckStuck: QueueID=6 tcb_desc->nStuckCount=4
[  224.094377] rtl819x_TxCheckStuck: QueueID=6 tcb_desc->nStuckCount=5
[  226.098834] rtl819x_TxCheckStuck: QueueID=6 tcb_desc->nStuckCount=6
[  228.103021] rtl819x_TxCheckStuck: QueueID=6 tcb_desc->nStuckCount=7
[  230.107713] rtl819x_TxCheckStuck: QueueID=6 tcb_desc->nStuckCount=8
[  230.107723] rtl819x_ifcheck_resetornot(): TxResetType is 2, RxResetType is 0
```

sudo iwlist scan
```
eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:05:CA:63:FE:E8
                    ESSID:"Ricardo"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:270 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 11 9 12 18 24 36 48 54 
                    Quality=66/100  Signal level=-57 dBm  Noise level=-103 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD270050F204104A000110104400010210470010BC329E001DD811B286010005CA63FEE8103C000101
                    Extra: Last beacon: 0ms ago
          Cell 02 - Address: 00:05:CA:63:FE:E9
                    ESSID:"FON_ZON_FREE_INTERNET"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:1
                    Encryption key:off
                    Bit Rates:270 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 11 9 12 18 24 36 48 54 
                    Quality=94/100  Signal level=-57 dBm  Noise level=-117 dBm
                    Extra: Last beacon: 0ms ago
          Cell 03 - Address: 1E:3E:84:08:89:21
                    ESSID:"DIRECT-Vj-BRAVIA"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:144.5 Mb/s
                    Extra: Rates (Mb/s): 6 9 12 18 24 36 48 54 
                    Quality=94/100  Signal level=-57 dBm  Noise level=-117 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD3A0050F204104A00011010440001021049000600372A00012010110012425241564941204B444C2D343257363531411054000800070050F2040001
                    Extra: Last beacon: 11ms ago
          Cell 04 - Address: BC:14:01:9D:F3:48
                    ESSID:"ZON-F340"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:12
                    Encryption key:on
                    Bit Rates:130 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 11 9 12 18 24 36 48 54 
                    Quality=95/100  Signal level=-58 dBm  Noise level=-117 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD270050F204104A0001101044000102104700102880288028801880A880BC14019DF348103C000101
                    Extra: Last beacon: 24ms ago
          Cell 05 - Address: 00:3A:99:8A:22:30
                    ESSID:"<hidden>\x00"
                    Protocol:IEEE802.11bg
                    Mode:Master
                    Channel:8
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=65/100  Signal level=-59 dBm  Noise level=-102 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 107ms ago
          Cell 06 - Address: BC:14:01:9D:F3:49
                    ESSID:"FON_ZON_FREE_INTERNET"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:12
                    Encryption key:off
                    Bit Rates:130 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 11 9 12 18 24 36 48 54 
                    Quality=95/100  Signal level=-57 dBm  Noise level=-117 dBm
                    Extra: Last beacon: 24ms ago
          Cell 07 - Address: 00:05:CA:72:4E:A8
                    ESSID:"Sandra zon"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:130 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 11 9 12 18 24 36 48 54 
                    Quality=95/100  Signal level=-58 dBm  Noise level=-117 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD270050F204104A000110104400010210470010BC329E001DD811B286010005CA724EA8103C000101
                    Extra: Last beacon: 65ms ago
          Cell 08 - Address: 00:05:CA:72:4E:A9
                    ESSID:"FON_ZON_FREE_INTERNET"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:11
                    Encryption key:off
                    Bit Rates:130 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 11 9 12 18 24 36 48 54 
                    Quality=94/100  Signal level=-58 dBm  Noise level=-117 dBm
                    Extra: Last beacon: 65ms ago
          Cell 09 - Address: 00:24:B2:2D:38:5A
                    ESSID:"ZON-Santos"
                    Protocol:IEEE802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=95/100  Signal level=-59 dBm  Noise level=-117 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 143ms ago


```

cat /etc/resolv.conf
```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search home


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
          Current Frequency:2.412 GHz (Channel 1)

```

rfkill list
```
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: samsung-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no


```

---

### Post by praseodym on 2014-04-15
The wrong drivers are still loaded:
```

sudo modprobe -rfv r8192e_pci
sudo modprobe -rfv rtl8192se
sudo depmod -a
sudo update-initramfs -u
sudo modprobe -v rtl8192ce
```

---

### Post by mamen on 2014-04-15
Sorry, but nothing yet mate. The networkmanager just keeps loading but just dont connect :(

---

### Post by praseodym on 2014-04-15
Ok, once again:
```
lsmod
ifconfig -a
egrep 'r8|rtl8' /etc/modprobe.d/*
cat /etc/modules
modinfo rtl8192ce
locate rtl8192ce.ko | grep lib
```
Change the encryption mode to pure WPA2-AES (CCMP) and a fixed channel.

---

### Post by mamen on 2014-04-15
Change the encrpition on my network? i dont think thats the problem, i tried with several wifi networks and didnt even asked for password..

lsmod
```
Module                  Size  Used by
hid_generic            12548  0 
usbhid                 53014  0 
hid                   101762  2 hid_generic,usbhid
michael_mic            12612  0 
arc4                   12608  0 
rtllib_crypt_tkip      17179  -1 
rtllib_crypt_ccmp      12829  -1 
parport_pc             32701  0 
ppdev                  17671  0 
bnep                   19704  2 
rfcomm                 69130  12 
binfmt_misc            17468  1 
snd_hda_codec_hdmi     41154  4 
joydev                 17377  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm_intel             138567  0 
kvm                   431754  1 kvm_intel
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40499  1 uvcvideo
videodev              133509  2 uvcvideo,videobuf2_core
samsung_laptop         14486  0 
snd_hda_codec_realtek    56475  1 
snd_hda_intel          52267  5 
snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
microcode              23656  0 
r8192e_pci            201415  0 
rtllib                155790  1 r8192e_pci
lib80211               14381  3 rtllib,rtllib_crypt_ccmp,rtllib_crypt_tkip
rtl8192se              94062  0 
rtlwifi               110108  1 rtl8192se
snd_rawmidi            30095  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
psmouse                97655  0 
mac80211              597268  2 rtlwifi,rtl8192se
serio_raw              13413  0 
intel_ips              18470  0 
lpc_ich                21080  0 
nouveau               943749  3 
btusb                  28267  0 
bluetooth             372041  22 bnep,btusb,rfcomm
cfg80211              480503  2 mac80211,rtlwifi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
mxm_wmi                13021  1 nouveau
snd_timer              29433  2 snd_pcm,snd_seq
wmi                    19070  2 mxm_wmi,nouveau
ttm                    84169  1 nouveau
drm_kms_helper         52710  1 nouveau
drm                   297056  5 ttm,drm_kms_helper,nouveau
snd                    69141  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
i2c_algo_bit           13413  1 nouveau
soundcore              12680  1 snd
video                  19318  2 samsung_laptop,nouveau
mac_hid                13205  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
ahci                   25819  3 
sky2                   58191  0 
libahci                32009  1 ahci


```


ifconfig -a
```
eth0      Link encap:Ethernet  Endereço de HW 00:24:54:5d:0a:ca  
          inet end.: 192.168.1.6  Bcast:192.168.1.255  Masc:255.255.255.0
          endereço inet6: fe80::224:54ff:fe5d:aca/64 Escopo:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1
          pacotes RX:3154 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:3130 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000 
          RX bytes:2610961 (2.6 MB) TX bytes:563107 (563.1 KB)
          IRQ:19 

lo        Link encap:Loopback Local  
          inet end.: 127.0.0.1  Masc:255.0.0.0
          endereço inet6: ::1/128 Escopo:Máquina
          UP LOOPBACK RUNNING  MTU:65536  Métrica:1
          pacotes RX:1045 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:1045 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:0 
          RX bytes:95132 (95.1 KB) TX bytes:95132 (95.1 KB)

wlan0     Link encap:Ethernet  Endereço de HW 00:e0:4c:00:00:01  
          endereço inet6: fe80::2e0:4cff:fe00:1/64 Escopo:Link
          UP BROADCAST MULTICAST  MTU:1500  Métrica:1
          pacotes RX:166 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:347 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000 
          RX bytes:82174 (82.1 KB) TX bytes:63943 (63.9 KB)
          IRQ:16 Memória:ffffc90000678000-ffffc90000678100 


```

egrep 'r8|rtl8' /etc/modprobe.d/*
```
/etc/modprobe.d/blacklist-realtek.conf:blacklist r8192e_pci\nblacklist rtl8192se
/etc/modprobe.d/modprobe.conf:options rtl8192ce ips=0
/etc/modprobe.d/modprobe.conf:options rtl8192ce fwlps=0

```

cat /etc/modules
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
# Parameters can be specified after the module name.

lp
rtc

```

modinfo rtl8192ce
```
filename:       /lib/modules/3.11.0-19-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Benjamin Porter	<BenjaminPorter86@gmail.com>
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     7B1C05B089A32851C837B52
alias:          pci:v000010ECd00008176sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008177sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008178sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008191sv*sd*bc*sc*i*
depends:        rtlwifi,mac80211
vermagic:       3.11.0-19-generic SMP mod_unload modversions 
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 0 is off)
 (bool)
parm:           fwlps:using no linked fw control power save (default 0 is off)
 (bool)

```

locate rtl8192ce.ko | grep lib
```
/lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko


```

---

### Post by praseodym on 2014-04-15
> /etc/modprobe.d/blacklist-realtek.conf:blacklist r8192e_pci\nblacklist rtl8192se
Sorry, typo:


```
echo [COLOR="#FF0000"]-e[/COLOR] "blacklist r8192e_pci\nblacklist rtl8192se" | sudo tee /etc/modprobe.d/blacklist-realtek.conf
```
Reboot and check again:
```

modinfo rtl8192ce
lsmod
iwconfig
dmesg | grep rtl
```

---

### Post by mamen on 2014-04-15
Now the wireless card doesnt show on the network config.. :(

modinfo rtl8192ce
```
filename:       /lib/modules/3.11.0-19-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Benjamin Porter    <BenjaminPorter86@gmail.com>
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     7B1C05B089A32851C837B52
alias:          pci:v000010ECd00008176sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008177sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008178sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008191sv*sd*bc*sc*i*
depends:        rtlwifi,mac80211
vermagic:       3.11.0-19-generic SMP mod_unload modversions 
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 0 is off)
 (bool)
parm:           fwlps:using no linked fw control power save (default 0 is off)
 (bool)
```

lsmod
```
Module                  Size  Used by
parport_pc             32701  0 
ppdev                  17671  0 
rfcomm                 69130  12 
bnep                   19704  2 
snd_hda_codec_hdmi     41154  4 
binfmt_misc            17468  1 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm_intel             138567  0 
kvm                   431754  1 kvm_intel
samsung_laptop         14486  0 
joydev                 17377  0 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40499  1 uvcvideo
videodev              133509  2 uvcvideo,videobuf2_core
snd_hda_codec_realtek    56475  1 
snd_hda_intel          52267  5 
snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
microcode              23656  0 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30095  1 snd_seq_midi
nouveau               943749  3 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
psmouse                97655  0 
serio_raw              13413  0 
mxm_wmi                13021  1 nouveau
wmi                    19070  2 mxm_wmi,nouveau
ttm                    84169  1 nouveau
drm_kms_helper         52710  1 nouveau
intel_ips              18470  0 
btusb                  28267  0 
bluetooth             372041  22 bnep,btusb,rfcomm
lpc_ich                21080  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
snd                    69141  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
drm                   297056  5 ttm,drm_kms_helper,nouveau
soundcore              12680  1 snd
i2c_algo_bit           13413  1 nouveau
video                  19318  2 samsung_laptop,nouveau
mac_hid                13205  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 53014  0 
hid                   101762  2 hid_generic,usbhid
ahci                   25819  3 
libahci                32009  1 ahci
sky2                   58191  0 

```

iwconfig
```
eth0      no wireless extensions.

lo        no wireless extensions.

```

dmesg | grep rtl
```
Nothing appeared
```

---

### Post by praseodym on 2014-04-15
Ok, setup a new blacklist:
```

sudo rm /etc/modprobe.d/blacklist-realtek.conf
echo "blacklist r8192e_pci" | sudo tee -a /etc/modprobe.d/blacklist-realtek.conf
```
Reload the updated driver:
```

sudo modprobe -v rtl8192se
```

---

### Post by mamen on 2014-04-15
Still no wireless card ..

---

### Post by praseodym on 2014-04-15
Strange:
```

dmesg | egrep 'error|fail|bug|rtl8|r8|wlan'
iwconfig
lsmod
locate rtl8192cfw.bin | grep lib
sudo iwlist scan
rfkill list
cat /etc/resolv.conf
route -n
cat /etc/network/interfaces
```

---

### Post by mamen on 2014-04-15
dmesg | egrep 'error|fail|bug|rtl8|r8|wlan'
```
[    0.000000] PERCPU: Embedded 29 pages/cpu @ffff880137c00000 s86720 r8192 d23872 u524288
[    0.000000] pcpu-alloc: s86720 r8192 d23872 u524288 alloc=1*2097152
[    0.280065] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.288054] acpi PNP0A08:00: ACPI _OSC support notification failed, disabling PCIe ASPM
[    0.302853] acpi PNP0A03:00: ACPI _OSC support notification failed, disabling PCIe ASPM
[    0.657727] ehci-pci 0000:00:1a.0: debug port 2
[    0.673234] ehci-pci 0000:00:1d.0: debug port 2
[   10.838890] rtlwifi: module verification failed: signature and/or required key missing - tainting kernel
[   10.871880] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled until i915 loads
[   12.553123] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[   13.334792] init: failsafe main process (599) killed by TERM signal

```

iwconfig
```

eth0      no wireless extensions.

lo        no wireless extensions.
```

lsmod
```
Module                  Size  Used by
parport_pc             32701  0 
ppdev                  17671  0 
rfcomm                 69130  12 
bnep                   19704  2 
binfmt_misc            17468  1 
snd_hda_codec_hdmi     41154  4 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm_intel             138567  0 
kvm                   431754  1 kvm_intel
samsung_laptop         14486  0 
uvcvideo               80885  0 
joydev                 17377  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40499  1 uvcvideo
videodev              133509  2 uvcvideo,videobuf2_core
microcode              23656  0 
psmouse                97655  0 
serio_raw              13413  0 
snd_hda_codec_realtek    56475  1 
intel_ips              18470  0 
rtl8192se              94062  0 
rtlwifi               110108  1 rtl8192se
snd_hda_intel          52267  5 
mac80211              597268  2 rtlwifi,rtl8192se
snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
nouveau               943749  3 
btusb                  28267  0 
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
bluetooth             372041  22 bnep,btusb,rfcomm
cfg80211              480503  2 mac80211,rtlwifi
snd_seq_midi           13324  0 
mxm_wmi                13021  1 nouveau
snd_seq_midi_event     14899  1 snd_seq_midi
wmi                    19070  2 mxm_wmi,nouveau
ttm                    84169  1 nouveau
snd_rawmidi            30095  1 snd_seq_midi
drm_kms_helper         52710  1 nouveau
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
drm                   297056  5 ttm,drm_kms_helper,nouveau
lpc_ich                21080  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
i2c_algo_bit           13413  1 nouveau
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
snd                    69141  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12680  1 snd
video                  19318  2 samsung_laptop,nouveau
mac_hid                13205  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 53014  0 
hid                   101762  2 hid_generic,usbhid
ahci                   25819  3 
sky2                   58191  0 
libahci                32009  1 ahci

```

locate rtl8192cfw.bin | grep lib
```
locate rtl8192cfw.bin | grep lib
```



sudo iwlist scan
```
eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.


```


rfkill list
```
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: samsung-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```


cat /etc/resolv.conf
```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search home


```


route -n
```
Tabela de Roteamento IP do Kernel
Destino         Roteador        MáscaraGen.    Opções Métrica Ref   Uso Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0


```

cat /etc/network/interfaces
```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


```

Ty for your help :D

---

### Post by praseodym on 2014-04-16
Obviously, the device ID is not part of the module. Try
```

echo 'install rtl8192se modprobe --ignore-install rtl8192se ; /bin/echo "10ec 8192" > [COLOR="#FF0000"]/sys/bus/pci/drivers/rtl8192se/new_id[/COLOR]' | sudo tee /etc/modprobe.d/rtl8192se.conf
```
Please check first if the red path is valid

---

### Post by mamen on 2014-04-16
The path is valid. A executed the command but still no wireless card :(

---

### Post by praseodym on 2014-04-16
Now reload the driver:
```

sudo modprobe -rfv rtl8192se
sudo modprobe -v rtl8192se
dmesg | egrep 'firm|rtl|r8'
iwconfig
```

---

### Post by mamen on 2014-04-16
Executing one of the commands gave me error..

sudo modprobe -rfv rtl8192se
```
rmmod rtl8192sermmod rtlwifi
rmmod mac80211
rmmod cfg80211



```




sudo modprobe -v rtl8192se
```
insmod /lib/modules/3.11.0-19-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.11.0-19-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.11.0-19-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko 
install modprobe --ignore-install rtl8192se ; /bin/echo "10ec 8192" > /sys/bus/pci/drivers/rtl8192se/new_id 
insmod /lib/modules/3.11.0-19-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.ko 
/bin/echo: erro de escrita: Argumento inválido
libkmod: ERROR ../libkmod/libkmod-module.c:925 command_do: Error running install command for rtl8192se
ERROR: could not insert 'rtl8192se': Operation not permitted
```

---

### Post by praseodym on 2014-04-16
Please show the other outputs, too.

---

### Post by mamen on 2014-04-16
dmesg | egrep 'firm|rtl|r8'
```
[    0.000000] PERCPU: Embedded 29 pages/cpu @ffff880137c00000 s86720 r8192 d23872 u524288
[    0.000000] pcpu-alloc: s86720 r8192 d23872 u524288 alloc=1*2097152
[   10.555930] rtlwifi: module verification failed: signature and/or required key missing - tainting kernel
```



iwconfig
```
eth0      no wireless extensions.


lo        no wireless extensions.
```

---

### Post by praseodym on 2014-04-16
Try to update that driver:
```

sudo apt-get install build-essential linux-headers-$(uname -r) linux-headers-generic
wget https://www.kernel.org/pub/linux/kernel/projects/backports/2014/02/21/backports-20140221.tar.gz    
tar -xvf backports-20140221.tar.gz     
cd backports-20140221
make defconfig-rtlwifi
make
sudo make install 
```
Reboot and check the outputs again.

---

### Post by mamen on 2014-04-16
Still no wireless card :(

---

### Post by jadon2 on 2014-04-16
Hey, I have a RealTek USB wireless adapter, not sure what model. I have tried to use it on Raspbian, on my Raspberry Pi. In the kernel it shows no errors,and acts like the adapter is registered, but on wifi config it doesnt find it. What should i do???

---

### Post by praseodym on 2014-04-16
So, I'm running out of ideas. Lets try this driver:

```
sudo apt-get install --reinstall linux-headers-generic build-essential dkms
wget http://media.cdn.ubuntu-de.org/forum/attachments/02/01/3137672-rtl8192e_linux_2.6.0015.1013.2010.tar.gz
tar xvf 3137672-rtl8192e_linux_2.6.0015.1013.2010.tar.gz
cd rtl8192e_linux_2.6.0015.1013.2010
make
sudo make install
```

The module name is r8192e_pci again. Clean up:
```

sudo rm /etc/modprobe.d/blacklist-realtek.conf
echo "blacklist rtl8192se" | sudo tee /etc/modprobe.d/blacklist-realtek.conf
```
Reboot and check:
```

modinfo r8192e_pci
lsmod
iwconfig
sudo iwlist scan
dmesg | grep r8
```

---

### Post by mamen on 2014-04-16
Executing make I get the errors:


```

make[1]: Entrando no diretório `/usr/src/linux-headers-3.11.0-19-generic'
gcc: error: /lib/modules/3.11.0-19-generic/build/include/linux/autoconf.h: Ficheiro ou directoria inexistente
gcc: fatal error: no input files
compilation terminated.
scripts/Makefile.build:49: *** CFLAGS was changed in "/home/ricardo/rtl8192e_linux_2.6.0015.1013.2010/HAL/rtl8192/Makefile". Fix it to use ccflags-y.  Pare.
make[1]: ** [_module_/home/ricardo/rtl8192e_linux_2.6.0015.1013.2010/HAL/rtl8192] Erro 2
make[1]: Saindo do diretório `/usr/src/linux-headers-3.11.0-19-generic'
make: ** [all] Erro 2

```


and sudo make install :
```

make[1]: Entrando no diretório `/usr/src/linux-headers-3.11.0-19-generic'
gcc: error: /lib/modules/3.11.0-19-generic/build/include/linux/autoconf.h: Ficheiro ou directoria inexistente
gcc: fatal error: no input files
compilation terminated.
scripts/Makefile.build:49: *** CFLAGS was changed in "/home/ricardo/rtl8192e_linux_2.6.0015.1013.2010/HAL/rtl8192/Makefile". Fix it to use ccflags-y.  Pare.
make[1]: ** [_module_/home/ricardo/rtl8192e_linux_2.6.0015.1013.2010/HAL/rtl8192] Erro 2
make[1]: Saindo do diretório `/usr/src/linux-headers-3.11.0-19-generic'
make: ** [all] Erro 2

```

---

### Post by praseodym on 2014-04-16
[http://ubuntuforums.org/showthread.php?t=2144845&page=4&p=12654945#post12654945](http://ubuntuforums.org/showthread.php?t=2144845&page=4&p=12654945#post12654945)

Same as here, try the fixes. I strongly recommend buying a new card/stick which is supported ootb. This one is too old and there is no new driver available.

---

