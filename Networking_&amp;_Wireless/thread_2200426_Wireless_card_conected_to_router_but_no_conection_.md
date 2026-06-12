---
title: "Wireless card conected to router but no conection to internet."
date: 2014-01-19
forum: Networking &amp; Wireless
---

### Post by dave.etaj on 2014-01-19
Very new user to Unbuntu.

Have Unbunto 13.04 installed and have been using the internet wired to router.
Now trying to go wireless.

Installed wireless card and was able to connect to my router but when I try firefox it doesn't connect. 

Using Century Link internet service and wireless router suplied by Century Link.

Any ideas?

---

### Post by praseodym on 2014-01-19
Hi,

please show the outputs of:
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
iwlist chan
sudo iwlist scan
```
Support for 13.04 ends at the end of January!

---

### Post by dave.etaj on 2014-01-19
Thank you for your response. I think this is the information your looking for.

dave@dave-KJ382AA-ABA-m9250f:~$ uname -a
Linux dave-KJ382AA-ABA-m9250f 3.11.0-15-generic #23-Ubuntu SMP Mon Dec 9 18:17:04 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
dave@dave-KJ382AA-ABA-m9250f:~$ lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
    Kernel driver in use: r8169
04:02.0 Network controller [0280]: Qualcomm Atheros AR9227 Wireless Network Adapter [168c:002d] (rev 01)
    Subsystem: Qualcomm Atheros Device [168c:0300]
    Kernel driver in use: ath9k
dave@dave-KJ382AA-ABA-m9250f:~$ lsusb
Bus 002 Device 003: ID 046d:c51b Logitech, Inc. V220 Cordless Optical Mouse for Notebooks
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
dave@dave-KJ382AA-ABA-m9250f:~$ lsmod
Module                  Size  Used by
mt2131                 13341  1 
s5h1409                18550  1 
rfcomm                 69130  0 
bnep                   19704  2 
bluetooth             372041  10 bnep,rfcomm
tda8290                22428  1 
tuner                  27308  1 
x86_pkg_temp_thermal    14162  0 
cx25840               102511  1 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm                   431720  0 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
cryptd                 20359  1 ghash_clmulni_intel
ppdev                  17671  0 
arc4                   12608  2 
cx23885               166107  1 
btcx_risc              13640  1 cx23885
altera_ci              19500  1 cx23885
videobuf_dvb           14092  1 cx23885
tda18271               41831  2 cx23885
snd_hda_codec_realtek    55704  1 
altera_stapl           34428  1 cx23885
tveeprom               21216  1 cx23885
cx2341x                28230  1 cx23885
videobuf_dma_sg        19262  1 cx23885
dvb_core              117465  3 cx23885,altera_ci,videobuf_dvb
rc_core                27718  1 cx23885
v4l2_common            20585  4 cx2341x,cx23885,cx25840,tuner
videobuf_core          26022  3 videobuf_dma_sg,cx23885,videobuf_dvb
videodev              133509  5 cx2341x,cx23885,cx25840,tuner,v4l2_common
snd_hda_intel          48171  3 
snd_hda_codec         188738  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102033  3 cx23885,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30095  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
ath9k                 155779  0 
ath9k_common           13859  1 ath9k
microcode              23576  0 
ath9k_hw              444732  2 ath9k_common,ath9k
snd                    69141  19 snd_hda_codec_realtek,cx23885,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
ath                    23827  3 ath9k_common,ath9k,ath9k_hw
serio_raw              13413  0 
mac80211              597268  1 ath9k
nouveau               943717  3 
mxm_wmi                13021  1 nouveau
wmi                    19070  2 mxm_wmi,nouveau
ttm                    84169  1 nouveau
cfg80211              480503  3 ath,ath9k,mac80211
drm_kms_helper         52710  1 nouveau
lpc_ich                21080  0 
mei_me                 18421  0 
drm                   297056  5 ttm,drm_kms_helper,nouveau
i2c_algo_bit           13413  1 nouveau
soundcore              12680  1 snd
mei                    77782  1 mei_me
video                  19318  1 nouveau
parport_pc             32701  1 
mac_hid                13205  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 53014  0 
hid                   105858  2 hid_generic,usbhid
r8169                  67581  0 
mii                    13934  1 r8169
dave@dave-KJ382AA-ABA-m9250f:~$ iwconfig
wlan1     IEEE 802.11bgn  ESSID:"myqwest0276"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 40:4A:03:DE:F3:F2   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=52/70  Signal level=-58 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:222   Missed beacon:0

eth1      no wireless extensions.

lo        no wireless extensions.

dave@dave-KJ382AA-ABA-m9250f:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
dave@dave-KJ382AA-ABA-m9250f:~$ iwlist chan
wlan1     13 channels in total; available frequencies :
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

eth1      no frequency information.

lo        no frequency information.

dave@dave-KJ382AA-ABA-m9250f:~$ sudo iwlist scan
[sudo] password for dave: 
wlan1     Scan completed :
          Cell 01 - Address: 40:4A:03:DE:F3:F2
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"myqwest0276"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001e05cde6f61
                    Extra: Last beacon: 52ms ago
                    IE: Unknown: 000B6D79717765737430323736
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD7A0050F204104A0001101044000102103B00010310470010555555550000C0A80001404A03DEF3F2102100055A7958454C1023000F5A7958454C2057464144657669636510240007504B353030305A1042000830303030303030311054000800060050F20400011011000A504B353030305A20415010080002008C
          Cell 02 - Address: 00:22:3F:33:CD:36
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:off
                    ESSID:"Whiplash"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000a4fe36fe8f4
                    Extra: Last beacon: 52ms ago
                    IE: Unknown: 0008576869706C617368
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0102
                    IE: Unknown: 32041224606C

eth1      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

dave@dave-KJ382AA-ABA-m9250f:~$

---

### Post by dave.etaj on 2014-01-19
Just some more information. I can connect and look at the modem/router status and it says connected to ISP.

---

### Post by praseodym on 2014-01-19
Deactivate the hardware encryption of the driver:

```
echo "options ath9k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
and change the encryption to pure WPA2-AES (CCMP) in the router interface.

---

### Post by dave.etaj on 2014-01-19
That worked, thank you very much. Have a good evening.

---

