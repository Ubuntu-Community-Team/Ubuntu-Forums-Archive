---
title: "300Mbps High Gain Wireless USB Adapter TL-WN822N on Ubuntu 14.10"
date: 2014-11-24
forum: Networking &amp; Wireless
---

### Post by torajeshr on 2014-11-24
I'm using TP-LINK wireless adapter model # TL-WN822N on 14.10. During the Live Media Boot, my wife Access Point was automatically detected by the Wireless Adapter all the upgrades went through just fine. After booting up to the installed 14.10, I'm able to access apt-get repositories, thunderbird e-mail client, software update etc. without an issue. The Internet access is seamless in all such situations. But when I pull up a browser, both firefox and Chromium, try to access a webpage, the Internet stops working immediately. A disconnect and connect lets me access Internet for all purposes like repository updates, e-mail client etc., but the moment I pull up a browser again and try to access a URL, internet stops working!! 

I've tried changing the proxy setting on the browser to 'No Proxy', but to no avail. My Netgear router IP is 10.0.0.1. When I connect to the WIFI AP by using the TL-WN822N adapter, it gets an IP, say 10.0.0.5, I'm able to ping 10.0.0.1 as well as use the other utilities like nslookup, traceroute etc. But immediately after I try accessing the Internet using a browser, none of above utilities work and I lose ping access to 10.0.0.1. That leads me to believe that it cannot be a configuration issue with my router. 

Request help.

Rajesh

---

### Post by praseodym on 2014-11-25
Please open a terminal with CTRL+ALT+T and show the outputs of these commands:
```

lsusb
lsmod
iwconfig
rfkill list
iwlist chan
sudo iwlist scan
```

---

### Post by torajeshr on 2014-11-28
Hello,

Thank you for attending to this. As advised, please find the output of all the commands mentioned in the post:

--snip--

Welcome to Ubuntu 14.10 (GNU/Linux 3.16.0-25-generic x86_64)
root@home313:/mystorage/rajeshr# **lsusb**
Bus 002 Device 002: ID 8087:8001 Intel Corp.
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8009 Intel Corp.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 002: ID 0bda:8178 Realtek Semiconductor Corp. RTL8192CU 802.11n WLAN Adapter
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
root@home313:/mystorage/rajeshr#** lsmod**
Module                  Size  Used by
arc4                   12608  2
rtl8192cu              67670  0
rtl_usb                18448  1 rtl8192cu
rtlwifi                64237  2 rtl_usb,rtl8192cu
rtl8192c_common        53170  1 rtl8192cu
mac80211              660592  3 rtl_usb,rtlwifi,rtl8192cu
cfg80211              510218  2 mac80211,rtlwifi
joydev                 17344  0
hid_logitech_dj        18469  0
usbhid                 52574  0
rfcomm                 69509  0
bnep                   19543  2
bluetooth             446190  10 bnep,rfcomm
6lowpan_iphc           18702  1 bluetooth
binfmt_misc            17468  1
snd_hda_codec_realtek    76887  1
snd_hda_codec_generic    68914  1 snd_hda_codec_realtek
snd_hda_codec_hdmi     47547  1
eeepc_wmi              13151  0
asus_wmi               24094  1 eeepc_wmi
sparse_keymap          13948  1 asus_wmi
mxm_wmi                13021  0
intel_rapl             18783  0
x86_pkg_temp_thermal    14205  0
intel_powerclamp       18786  0
nls_iso8859_1          12713  1
coretemp               13441  0
kvm                   459835  0
crct10dif_pclmul       14307  0
crc32_pclmul           13133  0
ghash_clmulni_intel    13230  0
aesni_intel           152552  0
aes_x86_64             17131  1 aesni_intel
lrw                    13287  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13944  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20360  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_soc_rt5640         93042  0
snd_soc_rl6231         13037  1 snd_soc_rt5640
snd_soc_core          200108  1 snd_soc_rt5640
snd_hda_intel          30379  5
serio_raw              13434  0
snd_hda_controller     35152  1 snd_hda_intel
snd_hda_codec         139675  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_compress           19200  1 snd_soc_core
snd_hwdep              17698  1 snd_hda_codec
snd_pcm_dmaengine      15172  1 snd_soc_core
i915                  917658  5
snd_pcm               104102  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
drm_kms_helper         61627  1 i915
drm                   310919  4 i915,drm_kms_helper
mei_me                 19742  0
mei                    87931  1 mei_me
shpchp                 37040  0
i2c_algo_bit           13406  1 i915
snd_seq_midi           13564  0
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30876  1 snd_seq_midi
snd_seq                67224  2 snd_seq_midi_event,snd_seq_midi
tpm_infineon           17131  0
video                  20128  2 i915,asus_wmi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
dw_dmac                12835  0
snd_timer              29513  2 snd_pcm,snd_seq
wmi                    19193  2 mxm_wmi,asus_wmi
snd_soc_sst_acpi       13007  0
parport_pc             32741  0
snd                    87611  23 snd_hda_codec_realtek,snd_soc_core,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_compress
i2c_hid                18719  0
hid                   110426  4 i2c_hid,usbhid,hid_logitech_dj
soundcore              15052  2 snd,snd_hda_codec
8250_dw                13551  0
ppdev                  17671  0
i2c_designware_platform    12979  0
i2c_designware_core    14768  1 i2c_designware_platform
dw_dmac_core           24298  1 dw_dmac
spi_pxa2xx_platform    23079  0
lp                     17759  0
acpi_pad               17942  0
mac_hid                13227  0
parport                42299  3 lp,ppdev,parport_pc
psmouse               106548  0
ahci                   34062  4
r8169                  71471  0
libahci                32424  1 ahci
mii                    13934  1 r8169
sdhci_acpi             13351  0
sdhci                  43448  1 sdhci_acpi
root@home313:/mystorage/rajeshr# **iwconfig**
eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"RAJR_IN"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 20:4E:7F:15:D0:9A
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=69/70  Signal level=-41 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lo        no wireless extensions.

root@home313:/mystorage/rajeshr#** rfkill list**
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
root@home313:/mystorage/rajeshr#** iwlist chan**
eth0      no frequency information.

wlan0     11 channels in total; available frequencies :
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
          Current Frequency:2.462 GHz (Channel 11)

lo        no frequency information.

root@home313:/mystorage/rajeshr# **iwlist scan**
eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 20:4E:7F:15:D0:9A
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=54/70  Signal level=-56 dBm
                    Encryption key:off
                    ESSID:"RAJR_IN"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000047890fbf10
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 000752414A525F494E
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6C181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD7F0050F204104A00011010440001021041000100103B00010310470010E6141C5DDE255811367BE3CF7A0DE51E1021000D4E4554474541522C20496E632E10230009574752363134763130102400095747523631347631301042000538333235381054000800060050F204000110110009574752363134763130100800020084
                    IE: Unknown: DD090010180203F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336C181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B081500000000000000000000000000000000000000
          Cell 02 - Address: AC:F1:DF:E6:F9:AF
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=22/70  Signal level=-88 dBm
                    Encryption key:on
                    ESSID:"Peace"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003a2738617b
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 00055065616365
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6C181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001300000000000000000000000000000000000000
                    IE: Unknown: DD090010180201F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: CC:B2:55:2E:52:99
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=12/70  Signal level=-98 dBm
                    Encryption key:on
                    ESSID:"Ola"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000008cf69f0325
                    Extra: Last beacon: 1708ms ago
                    IE: Unknown: 00034F6C61
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFE181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1601051600000000000000000000000000000000000000
                    IE: Unknown: DD090010180203F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 04 - Address: C8:BE:19:76:B8:C4
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=12/70  Signal level=-98 dBm
                    Encryption key:on
                    ESSID:"Tismo"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000042efa75fe5
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 00055469736D6F
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030102
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1602000000000000000000000000000000000000000000
                    IE: Unknown: DD7B0050F204104A00011010440001011041000100103B000103104700106BC590C97765E4ACB36E5D0C5158F6631021000842726F6164636F6D1023000842726F6164636F6D1024000631323334353610420004313233341054000800060050F20400011011000A42726F6164636F6D4150100800020088103C000101
                    IE: Unknown: DD090010180200F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 05 - Address: 74:44:01:35:5A:FC
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=48/70  Signal level=-62 dBm
                    Encryption key:on
                    ESSID:"Tismo 6"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000001732a6cb
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 00075469736D6F2036
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD7F0050F204104A00011010440001021041000100103B000103104700106897A667F904F10268566BBF5FCC502F1021000D4E4554474541522C20496E632E10230009574752363134763130102400095747523631347631301042000538333235381054000800060050F204000110110009574752363134763130100800020084
                    IE: Unknown: DD090010180200F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 06 - Address: 76:44:01:35:5A:FD
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=48/70  Signal level=-62 dBm
                    Encryption key:on
                    ESSID:"TismoGuest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000001732b22b
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 000A5469736D6F4775657374
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 07 - Address: C4:A8:1D:8D:D3:24
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=36/70  Signal level=-74 dBm
                    Encryption key:on
                    ESSID:"kelshikar"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000044cfd217e
                    Extra: Last beacon: 692ms ago
                    IE: Unknown: 00096B656C7368696B6172
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030108
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6F181FFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1608000000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A00B400C800140005001900
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336F181FFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3408000000000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020160
                    IE: Unknown: DD1D0050F204104A0001101044000102103C0001031049000600372A000120
          Cell 08 - Address: 00:1F:33:BB:46:54
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=12/70  Signal level=-98 dBm
                    Encryption key:on
                    ESSID:"Tismo"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000252bbb0ba22

lo        Interface doesn't support scanning.

--snip--

Kindly let me know if any other information is required around the same.

Thank you,

Rajesh

---

### Post by praseodym on 2014-11-28
Change the driver via:
```

sudo apt-get install --reinstall build-essential dkms git
git clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.9
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf   
```
Reboot. I strongly recommend encrypting the network with WPA2-AES (CCMP), you are online unencrypted!
> ```

Cell 01 - Address: 20:4E:7F:15:D0:9A
Channel:11
Frequency:2.462 GHz (Channel 11)
Quality=54/70 Signal level=-56 dBm
Encryption key:[COLOR="#FF0000"]off[/COLOR]
```

---

### Post by torajeshr on 2014-11-29
Hello,

At the outset, thank you for the fast response. It all worked like a charm. Now I'm able to browse as well. Thank you again!

About the Encryption part of network, I've set the Access Control List on my router to the devices that I own. Do I need to encrypt it as no one else can join the network?

Since the problem with my wifi is solved, marking this thread as solved.

Gratefully yours,

Rajesh

---

### Post by praseodym on 2014-11-30
MAC addresses can be cloned (e.g. from the outputs above!!!). So, encryption is always necessary

---

### Post by Gabriel_Pinho on 2015-03-17
> **praseodym said:**
> Change the driver via:
```

sudo apt-get install --reinstall build-essential dkms git
git clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.9
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf   
```
Reboot. I strongly recommend encrypting the network with WPA2-AES (CCMP), you are online unencrypted!

I had exactly same problem. Same wifi adapter and same ubuntu version. And it's solve my problem too.


Thanks a lot.

---

