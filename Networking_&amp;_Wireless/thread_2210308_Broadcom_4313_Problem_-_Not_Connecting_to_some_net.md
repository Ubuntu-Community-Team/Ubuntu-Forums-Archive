---
title: "Broadcom 4313 Problem - Not Connecting to some network"
date: 2014-03-10
forum: Networking &amp; Wireless
---

### Post by MD_Azhar on 2014-03-10
Hi, 
I'm running Ubunto 13.10 and have a broadcom 4313 wifi card. Now the problem is the I installed the driver which came in the install media. It is bcmwl-kernal-source 6.30.223.141 .
Now the issue I'm facing is that I can see all the networks around me however I can ONLY connect to the ones which does not require a security key. For example, when I try to connect to my Universitie's internet, it shows the user/pass prompt (even though I set it up before). Even after entering the correct credentials, the prompt comes back again and again and it doesn't connect.

Please help me solve this issue.

Also, please note that my ubunto laptop no internet connectivity (even ethernet LAN).. however i do have another laptop(this one) which I can use to download files and transfer through USB.

Here are the results of the following terminals commands:
```
[COLOR=#000000][FONT=Ubuntu Mono]lspci -nnk | grep -iA2 net
[/FONT][/COLOR]iwconfig
rfkill list 
lsmod
```

```
01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8161 Gigabit Ethernet [1969:1091] (rev 08)	Subsystem: Lenovo Device [17aa:3979]
	Kernel driver in use: alx
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
	Subsystem: Broadcom Corporation Device [14e4:0587]
	Kernel driver in use: wl






eth0      no wireless extensions.


eth1      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.






0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy1: Wireless LAN
	Soft blocked: no
	Hard blocked: no
4: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no








Module                  Size  Used by
lib80211_crypt_tkip    17619  0 
wl                   4207474  0 
lib80211               14352  2 wl,lib80211_crypt_tkip
nls_iso8859_1          12713  1 
usb_storage            62062  1 
parport_pc             32701  0 
ppdev                  17671  0 
rfcomm                 69070  0 
bnep                   19564  2 
bluetooth             371874  8 bnep,rfcomm
arc4                   12608  0 
cordic                 12574  0 
snd_hda_codec_hdmi     41276  1 
snd_hda_codec_realtek    51465  1 
brcmutil               15618  0 
mac80211              596969  0 
cfg80211              479757  2 wl,mac80211
x86_pkg_temp_thermal    14162  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm                   431315  0 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20329  3 ghash_clmulni_intel,aesni_intel,ablk_helper
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40469  1 uvcvideo
videodev              133390  2 uvcvideo,videobuf2_core
joydev                 17377  0 
snd_hda_intel          48171  6 
snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30095  1 snd_seq_midi
microcode              23518  0 
i915                  655752  3 
psmouse                97626  0 
serio_raw              13413  0 
drm_kms_helper         52651  1 i915
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
drm                   296739  4 i915,drm_kms_helper
jmb38x_ms              18670  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
memstick               16760  1 jmb38x_ms
snd_timer              29433  2 snd_pcm,snd_seq
mei_me                 18421  0 
snd                    69141  23 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
i2c_algo_bit           13413  1 i915
lpc_ich                21080  0 
mei                    77692  1 mei_me
soundcore              12680  1 snd
ideapad_laptop         18342  0 
sparse_keymap          13948  1 ideapad_laptop
video                  19318  1 i915
mac_hid                13205  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 53014  0 
hid                   101512  2 hid_generic,usbhid
alx                    32255  0 
sdhci_pci              18985  0 
ahci                   25819  3 
sdhci                  42630  1 sdhci_pci
mdio                   13807  1 alx
libahci                31898  1 ahci

```
[COLOR=#222222][FONT=Verdana]


[/FONT][/COLOR]

---

### Post by varunendra on 2014-03-10
Welcome to the forums MD_Azhar!

You are currently using the proprietary "sta" driver which usually does not work nicely with this card. Please purge it to try the native one instead -
```
sudo apt-get purge bcmwl-kernel-source
```
Reboot and try to connect. Any better?

---

### Post by MD_Azhar on 2014-03-10
Hi, yeah I actually purged the driver. I have been going through almost all the threads... but no use.... regarding the native, for some reason I'm not able to see my networks... although it detects my card... so I'm forced to install the sta drivers.

---

### Post by MD_Azhar on 2014-03-10
Also, another interesting thing to note is that I gave a try with anotherr usb based wifi card (Linksys WUSB54GC) ...and I'm getting the same problem with it... I can only connect to networks which are free OR have simple secuirty code.... but if I try to connect my university network which is using a PEAP security , it fails to connect/

---

### Post by varunendra on 2014-03-10
With the sta driver purged as suggested in my previous post, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

---

### Post by MD_Azhar on 2014-03-10
```


*************** info trace ***************


***** uname -a *****


Linux azhar-Lenovo-IdeaPad-Y580 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


***** lsb_release *****


Distributor ID:	Ubuntu
Description:	Ubuntu 13.10
Release:	13.10
Codename:	saucy


***** lspci *****


01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8161 Gigabit Ethernet [1969:1091] (rev 08)
	Subsystem: Lenovo Device [17aa:3979]
	Kernel driver in use: alx
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
	Subsystem: Broadcom Corporation Device [14e4:0587]
	Kernel driver in use: bcma-pci-bridge


***** lsusb *****


Bus 002 Device 003: ID 04f2:b2f1 Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID e0ff:0005  
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 13b1:0020 Linksys WUSB54GC v1 802.11g Adapter [Ralink RT73]
Bus 003 Device 003: ID 1516:1226 CompUSA 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


***** PCMCIA Card Info *****




***** iwconfig *****


wlan1     IEEE 802.11bg  ESSID:"universe"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC address removed>   
          Bit Rate=36 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:16   Missed beacon:0


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


***** rfkill *****


0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: phy1: Wireless LAN
	Soft blocked: no
	Hard blocked: no


***** iw reg get *****


country US:
	(2402 - 2472 @ 40), (3, 27)
	(5170 - 5250 @ 40), (3, 17)
	(5250 - 5330 @ 40), (3, 20), DFS
	(5490 - 5600 @ 40), (3, 20), DFS
	(5650 - 5710 @ 40), (3, 20), DFS
	(5735 - 5835 @ 40), (3, 30)
	(57240 - 63720 @ 2160), (N/A, 40)


***** route -n *****


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.137.1   0.0.0.0         UG    0      0        0 wlan1
192.168.137.0   0.0.0.0         255.255.255.0   U     9      0        0 wlan1


***** lsmod *****


rt73usb                31467  0 
rt2x00usb              20713  1 rt73usb
rt2x00lib              55238  2 rt73usb,rt2x00usb
crc_itu_t              12707  1 rt73usb
brcmsmac              562767  0 
cordic                 12574  1 brcmsmac
brcmutil               15618  1 brcmsmac
b43                   387185  0 
mac80211              596969  4 b43,brcmsmac,rt2x00lib,rt2x00usb
cfg80211              479757  4 b43,brcmsmac,mac80211,rt2x00lib
ssb                    57932  1 b43
bcma                   46670  3 b43,brcmsmac


***** nm-tool *****


NetworkManager Tool


State: connected (global)


- Device: wlan1  [universe 1] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt73usb
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           36 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    iium-community:  Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 57 WPA WPA2 Enterprise
    iium-community:  Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2 Enterprise
    IIUM-Community!: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WPA2 Enterprise
    iium-community:  Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2 Enterprise
    iium-community:  Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2 Enterprise
    IIUM-Guest!:     Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 54
    IIUM-Registration: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 54
    IIUM-Guest!:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47
    IIUM-Registration: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47
    IIUM-Registration: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30
    iium-community:  Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2 Enterprise
    IIUM-Community!: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA2 Enterprise
    IIUM-Guest!:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 50
    IIUM-Registration: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47
    IIUM-Guest!:     Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 47
    IIUM-Registration: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 40
    *universe:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 66 WPA2
    IIUM-Community!: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 57 WPA2 Enterprise
    IIUM-Community!: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA2 Enterprise
    IIUM-Registration: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44
    IIUM-Guest!:     Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 40
    IIUM-Community!: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 50 WPA2 Enterprise
    iium-community:  Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2 Enterprise
    IIUM-Community!: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 40 WPA2 Enterprise
    IIUM-Registration: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 47
    IIUM-Community!: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 50 WPA2 Enterprise
    iium-community:  Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2 Enterprise
    IIUM-Guest!:     Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 47
    IIUM-Registration: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 47
    IIUM-Guest!:     Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27


  IPv4 Settings:
    Address:         192.168.137.23
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.137.1


    DNS:             192.168.137.1




- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 
    universe:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 45 WPA2




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            alx
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off






***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


***** NetworkManager.conf *****


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


***** interfaces *****




***** iwlist *****


wlan1     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"universe"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000013ff2874
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 0008756E697665727365
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A2C0103FF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001300000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101810003A4000027A4000042435E0062322F00
                    IE: Unknown: DD7E0050F204104A0001101044000102103B000100104700104962029777994EFCA7025E52027D9EE8102100094D6963726F736F66741023000757696E646F777310240008362E322E3932303010420001301054000800010050F20000001011000E53616D73756E67204154495620531008000201081049000600372A000120
                    IE: Unknown: DD080050F21102000000
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:off
                    ESSID:"IIUM-Guest!"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000027cbfd1db
                    Extra: Last beacon: 25808ms ago
                    IE: Unknown: 000B4949554D2D477565737421
                    IE: Unknown: 010882840B160C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD07000B8601040816
          Cell 03 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"IIUM-Community!"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000027cc443d9
                    Extra: Last beacon: 23728ms ago
                    IE: Unknown: 000F4949554D2D436F6D6D756E69747921
                    IE: Unknown: 010882840B0C12161824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 04 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"iium-community"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000027cbfd9f3
                    Extra: Last beacon: 25808ms ago
                    IE: Unknown: 000E6969756D2D636F6D6D756E697479
                    IE: Unknown: 010882840B160C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD07000B8601040816
          Cell 05 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:off
                    ESSID:"IIUM-Registration"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000027cbfe2fc
                    Extra: Last beacon: 23728ms ago
                    IE: Unknown: 00114949554D2D526567697374726174696F6E
                    IE: Unknown: 010882840B0C12161824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
          Cell 06 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"IIUM-Community!"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000270c63525
                    Extra: Last beacon: 560ms ago
                    IE: Unknown: 000F4949554D2D436F6D6D756E69747921
                    IE: Unknown: 010882840B160C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD07000B8601040816
          Cell 07 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:off
                    ESSID:"IIUM-Guest!"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000014e67d181
                    Extra: Last beacon: 25064ms ago
                    IE: Unknown: 000B4949554D2D477565737421
                    IE: Unknown: 010882840B160C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD07000B8601040816
          Cell 08 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"IIUM-Community!"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000071452b525
                    Extra: Last beacon: 24684ms ago
                    IE: Unknown: 000F4949554D2D436F6D6D756E69747921
                    IE: Unknown: 010882840B160C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD07000B8601040816
          Cell 09 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"iium-community"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000714544999
                    Extra: Last beacon: 24580ms ago
                    IE: Unknown: 000E6969756D2D636F6D6D756E697479
                    IE: Unknown: 010882840B160C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD07000B8601040816
          Cell 10 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:off
                    ESSID:"IIUM-Registration"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000270c63ec5
                    Extra: Last beacon: 556ms ago
                    IE: Unknown: 00114949554D2D526567697374726174696F6E
                    IE: Unknown: 010882840B160C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD07000B8601040816
          Cell 11 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:off
                    ESSID:"IIUM-Guest!"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000013ca76554
                    Extra: Last beacon: 23728ms ago
                    IE: Unknown: 000B4949554D2D477565737421
                    IE: Unknown: 010882840B0C12161824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
          Cell 12 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:off
                    ESSID:"IIUM-Guest!"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000003483eedd4
                    Extra: Last beacon: 23728ms ago
                    IE: Unknown: 000B4949554D2D477565737421
                    IE: Unknown: 010882840B0C12161824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
          Cell 13 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"iium-community"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000003483efbe3
                    Extra: Last beacon: 23728ms ago
                    IE: Unknown: 000E6969756D2D636F6D6D756E697479
                    IE: Unknown: 010882840B0C12161824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
          Cell 14 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:off
                    ESSID:"IIUM-Registration"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000003483f01df
                    Extra: Last beacon: 23728ms ago
                    IE: Unknown: 00114949554D2D526567697374726174696F6E
                    IE: Unknown: 010882840B0C12161824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
          Cell 15 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"IIUM-Community!"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000003483f2525
                    Extra: Last beacon: 23756ms ago
                    IE: Unknown: 000F4949554D2D436F6D6D756E69747921
                    IE: Unknown: 010882840B160C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD07000B8601040816
          Cell 16 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"IIUM-Community!"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000014fd3e525
                    Extra: Last beacon: 1216ms ago
                    IE: Unknown: 000F4949554D2D436F6D6D756E69747921
                    IE: Unknown: 010882840B160C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD07000B8601040816
          Cell 17 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:off
                    ESSID:"IIUM-Guest!"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000715b884ff
                    Extra: Last beacon: 1248ms ago
                    IE: Unknown: 000B4949554D2D477565737421
                    IE: Unknown: 010882840B160C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD07000B8601040816
          Cell 18 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:off
                    ESSID:"IIUM-Guest!"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000270cb099d
                    Extra: Last beacon: 244ms ago
                    IE: Unknown: 000B4949554D2D477565737421
                    IE: Unknown: 010882840B160C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD07000B8601040816
          Cell 19 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"iium-community"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000270c63999
                    Extra: Last beacon: 560ms ago
                    IE: Unknown: 000E6969756D2D636F6D6D756E697479
                    IE: Unknown: 010882840B160C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD07000B8601040816
          Cell 20 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:off
                    ESSID:"IIUM-Registration"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000014fd5df8e
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 00114949554D2D526567697374726174696F6E
                    IE: Unknown: 010882840B0C12161824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
          Cell 21 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:off
                    ESSID:"IIUM-Registration"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000715c1eec5
                    Extra: Last beacon: 636ms ago
                    IE: Unknown: 00114949554D2D526567697374726174696F6E
                    IE: Unknown: 010882840B160C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD07000B8601040816
          Cell 22 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:off
                    ESSID:"IIUM-Registration"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000013e11165c
                    Extra: Last beacon: 92ms ago
                    IE: Unknown: 00114949554D2D526567697374726174696F6E
                    IE: Unknown: 010882840B160C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD07000B8601040816


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"universe"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000012b61aaa
                    Extra: Last beacon: 21912ms ago
                    IE: Unknown: 0008756E697665727365
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A2C0103FF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001300000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101810003A4000027A4000042435E0062322F00
                    IE: Unknown: DD7E0050F204104A0001101044000102103B000100104700104962029777994EFCA7025E52027D9EE8102100094D6963726F736F66741023000757696E646F777310240008362E322E3932303010420001301054000800010050F20000001011000E53616D73756E67204154495620531008000201081049000600372A000120
                    IE: Unknown: DD080050F21102000000




***** resolv.conf *****


nameserver 127.0.1.1
search mshome.net


***** blacklist *****


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


***** modinfo *****


filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/rt2x00/rt73usb.ko
license:        GPL
firmware:       rt73.bin
description:    Ralink RT73 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     79088AB6F8FA9AA591F582B
alias:          usb:v0586p3415d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CDEp001Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7167p3840d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB50d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB01d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0471p200Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v6933p5001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0769p31F3d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p9712d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p90ACd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p002Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0027d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0024d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p7100d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04E8p4471d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v18E8p6238d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v18E8p6229d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v18E8p6196d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0812p3101d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp2671d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp2573d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp093Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B75p7318d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0pA874d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0pA861d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p6874d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p6877d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p4600d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13B1p0028d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13B1p0023d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13B1p0020d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v06F8pE020d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v06F8pE010d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v06F8pE002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1472p0009d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1044p800Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1044p8008d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v15A9p0004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p3701d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p7618d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p7318d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C07d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C06d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C04d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C03d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07AAp002Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C22d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1371p9032d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1371p9022d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v178Dp02BEd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p0137d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p0119d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p0116d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p00F4d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p00E6d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p00D9d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p00D8d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v08DDp0120d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1631pC019d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp905Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp905Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp705Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp7050d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1724d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1723d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1690p0722d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v18C5p0002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0EB0p9021d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp9021d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C10d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8pB21Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8pB21Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8pB21Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8pB21Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8pB21Bd*dc*dsc*dp*ic*isc*ip*in*
depends:        rt2x00lib,rt2x00usb,crc-itu-t
intree:         Y
vermagic:       3.11.0-12-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)


filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
license:        GPL
description:    rt2x00 usb library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     5CFE65EA16A08E63C627D96
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.11.0-12-generic SMP mod_unload modversions 


filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     8AE9D454A710B1C25F9F518
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.11.0-12-generic SMP mod_unload modversions 


filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fw
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     DB4E5CDF31AA9B12B2BA2C0
alias:          bcma:m04BFid0812rev18cl*
alias:          bcma:m04BFid0812rev17cl*
alias:          bcma:m04BFid0812rev11cl*
depends:        mac80211,bcma,brcmutil,cfg80211,cordic
intree:         Y
vermagic:       3.11.0-12-generic SMP mod_unload modversions 


filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     E81EE4CBB6A7A689150D93D
depends:        
intree:         Y
vermagic:       3.11.0-12-generic SMP mod_unload modversions 


filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
license:        GPL
author:         Rafa&#322; Mi&#322;ecki
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     9B797CFD1C70935B62C35EE
alias:          bcma:m04BFid0812rev1Dcl*
alias:          bcma:m04BFid0812rev18cl*
alias:          bcma:m04BFid0812rev17cl*
alias:          bcma:m04BFid0812rev11cl*
alias:          ssb:v4243id0812rev10*
alias:          ssb:v4243id0812rev0F*
alias:          ssb:v4243id0812rev0D*
alias:          ssb:v4243id0812rev0C*
alias:          ssb:v4243id0812rev0B*
alias:          ssb:v4243id0812rev0A*
alias:          ssb:v4243id0812rev09*
alias:          ssb:v4243id0812rev07*
alias:          ssb:v4243id0812rev06*
alias:          ssb:v4243id0812rev05*
depends:        ssb,bcma,mac80211,cfg80211
intree:         Y
vermagic:       3.11.0-12-generic SMP mod_unload modversions 
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)


filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     78379A0109AF2689B4F6028
alias:          pci:v000014E4d00004350sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Csv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Bsv*sd*bc*sc*i*
alias:          pci:v000014E4d00004329sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004328sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004325sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004324sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A8D6sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004322sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004321sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004320sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004319sv*sd*bc*sc*i*
alias:          pci:v000014A4d00004318sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004318sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004315sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004312sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004311sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004307sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004306sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004301sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.11.0-12-generic SMP mod_unload modversions 


filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     67ADEA6E309FDB9FC19CBCF
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004365sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004359sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004358sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004331sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A8D8sv*sd*bc*sc*i*
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.11.0-12-generic SMP mod_unload modversions 




***** udev rules *****


# PCI device 0x1969:0x1091 (alx)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x14e4:0x4727 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# PCI device 0x14e4:0x4727 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


# USB device 0x:0x (rt73usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


***** dmesg *****


[   12.823911] bcma: bus0: Found chip with id 0x4313, rev 0x01 and package 0x08
[   12.823943] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x24, class 0x0)
[   12.823969] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x18, class 0x0)
[   12.824023] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x11, class 0x0)
[   12.836605] bcma: bus0: Bus registered
[   13.636159] Support for cores revisions 0x17 and 0x18 disabled by module param allhwsupport=0. Try b43.allhwsupport=1
[   13.636205] b43: probe of bcma0:0 failed with error -524
[   13.939077] brcmsmac bcma0:0: mfg 4bf core 812 rev 24 class 0 irq 17
[   13.955227] ieee80211 phy0: registered radio enabled led device: brcmsmac-phy0:radio gpio: 243
[   17.123011] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   17.123020] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[   17.123630] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.123823] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   36.022426] ieee80211 phy1: rt2x00_set_chip: Info - Chipset detected - rt: 2573, rf: 0002, rev: 000a
[   36.039632] ieee80211 phy1: rt2x00lib_request_firmware: Info - Loading firmware file 'rt73.bin'
[   36.051047] ieee80211 phy1: rt2x00lib_request_firmware: Info - Firmware detected - version: 1.7
[   36.110154] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   36.110448] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   72.367779] wlan1: authenticate with <MAC address removed>
[   72.404711] wlan1: send auth to <MAC address removed> (try 1/3)
[   72.419965] wlan1: authenticated
[   72.423045] wlan1: associate with <MAC address removed> (try 1/3)
[   72.443572] wlan1: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=7)
[   72.452078] wlan1: associated
[   72.452130] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[   74.673339] wlan0: authenticate with <MAC address removed>
[   74.677382] wlan0: send auth to <MAC address removed> (try 1/3)
[   74.681117] wlan0: authenticated
[   74.684986] wlan0: associate with <MAC address removed> (try 1/3)
[   74.739186] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=8)
[   74.739597] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[   74.739600] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[   74.739608] wlan0: associated
[   74.739615] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   82.203560] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[   82.203573] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   82.920640] wlan0: authenticate with <MAC address removed>
[   82.922337] wlan0: send auth to <MAC address removed> (try 1/3)
[   82.928284] wlan0: authenticated
[   82.931982] wlan0: associate with <MAC address removed> (try 1/3)
[   82.975097] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=1 aid=0)
[   82.975106] wlan0: <MAC address removed> denied association (code=1)
[   83.051479] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   95.288386] wlan0: authenticate with <MAC address removed>
[   95.289966] wlan0: send auth to <MAC address removed> (try 1/3)
[   95.294720] wlan0: authenticated
[   95.295612] wlan0: associate with <MAC address removed> (try 1/3)
[   95.339875] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[   95.340568] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[   95.340575] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[   95.340589] wlan0: associated
[  100.302683] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[  100.302698] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  101.020169] wlan0: authenticate with <MAC address removed>
[  101.021779] wlan0: send auth to <MAC address removed> (try 1/3)
[  101.025918] wlan0: authenticated
[  101.027371] wlan0: associate with <MAC address removed> (try 1/3)
[  101.071789] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=1 aid=0)
[  101.071798] wlan0: <MAC address removed> denied association (code=1)
[  101.137459] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  101.857235] wlan0: authenticate with <MAC address removed>
[  101.858815] wlan0: send auth to <MAC address removed> (try 1/3)
[  101.862676] wlan0: authenticated
[  101.864570] wlan0: associate with <MAC address removed> (try 1/3)
[  101.922871] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=5)
[  101.923415] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[  101.923422] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[  101.923438] wlan0: associated
[  104.223930] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[  104.223944] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  108.798617] wlan0: authenticate with <MAC address removed>
[  108.800315] wlan0: send auth to <MAC address removed> (try 1/3)
[  108.804246] wlan0: authenticated
[  108.805913] wlan0: associate with <MAC address removed> (try 1/3)
[  108.863563] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=1 aid=0)
[  108.863572] wlan0: <MAC address removed> denied association (code=1)
[  108.930035] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  109.647772] wlan0: authenticate with <MAC address removed>
[  109.649340] wlan0: send auth to <MAC address removed> (try 1/3)
[  109.653132] wlan0: authenticated
[  109.655049] wlan0: associate with <MAC address removed> (try 1/3)
[  109.677038] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=9)
[  109.677445] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[  109.677451] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[  109.677466] wlan0: associated
[  113.452506] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  114.217563] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[  114.217577] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)


****************** done ******************



```

---

### Post by MD_Azhar on 2014-03-10
I took the above log using another wifi connection (to which I could connect) using the 2nd wifi adapter I mentioned above (Linksys wusb56gc)

---

### Post by varunendra on 2014-03-10
> **MD_Azhar said:**
> ```
***** lsmod *****

....
**b43**                   387185  0 
mac80211              596969  4 **[COLOR="#FF0000"]b43[/COLOR]**,brcmsmac,rt2x00lib,rt2x00usb
cfg80211              479757  4 **[COLOR="#FF0000"]b43[/COLOR]**,brcmsmac,mac80211,rt2x00lib
ssb                    57932  1 **b43**
bcma                   46670  3 **[COLOR="#FF0000"]b43[/COLOR]**,brcmsmac

```
Hmm.. how did b43 got up there? Have you added it manually somewhere to 'Force' load it?

Please show -
```
egrep -v '^#|^$' /etc/modules
egrep -v '^#|^$' /etc/rc.local
```

We need to stop it from loading, to avoid conflict with brcmsmac over resources.

---

### Post by MD_Azhar on 2014-03-10
No i don't remeber adding it manually...

I did what you said.

It gave me a 'exit 0' after the second satetement

---

### Post by varunendra on 2014-03-10
Can I see the outputs? The b43 module shouldn't load by itself.

Please try -
```
echo -e "blacklist b43\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
This will blacklist b43 and ssb drivers so that they don't not load at startup. But this trick will fail if any of the above files are force loading it.

Please post the outputs to confirm, and after a reboot, please check -
```
lsmod | egrep 'b43|brcm'
```
You should only see brcmsmac in the output, not b43. If true, you should get a better working wifi.

---

### Post by MD_Azhar on 2014-03-10
Are you asking for the output for the below statements ? 

```
[COLOR=#000000][FONT=Ubuntu Mono]egrep -v '^#|^$' /etc/modules
[/FONT][/COLOR]egrep -v '^#|^$' /etc/rc.local
```

because terminal just executed these statements without giving any output.. only after the second statement i got a exit 0 .. thats it.... sorry i'm quite new to ubuntu

---

### Post by varunendra on 2014-03-10
The output for the second one being "exit 0" is normal, but there should have been a couple of lines for the first one.

These commands are actually just reading two different files, only while 'filtering out' the non interesting parts. It is good if they don't contain any reference to b43, I just need to confirm, because b43 driver should not load automatically for the card you have.

You can manually browse to these files - **/etc/modules** and **/etc/rc.local** (that is - "modules" and "rc.local" files inside **/etc** directory (click "filesystem" in the File browser > locate "etc")) - and post their contents here so that I can be sure these are not loading it.

And have you tried the command I suggested earlier? Run it and reboot, then check the "lsmod" command I suggested. If b43 is not loading after that, your wifi should work better.

---

### Post by wildmanne39 on 2014-03-10
Hi Varun, I think this is important to the files accuracy that he posted. > I took the above log using another wifi connection (to which I could connect) using the 2nd wifi adapter I mentioned above (Linksys wusb56gc) 

---

### Post by MD_Azhar on 2014-03-10
The content of the /modules and /rc.local are :
```
# /etc/modules: kernel modules to load at boot time.#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
# Parameters can be specified after the module name.


lp
rtc






#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.


exit 0

```


The output of the statement : [COLOR=#000000][FONT=Ubuntu Mono]echo -e "blacklist b43\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist.conf  is

```
[/FONT][/COLOR]blacklist b43
blacklist ssb
[COLOR=#000000][FONT=Ubuntu Mono]
```


The output of the statement : [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]lsmod | egrep 'b43|brcm' is

```
[/FONT][/COLOR]brcmsmac              562767  0 
cordic                 12574  1 brcmsmac
brcmutil               15618  1 brcmsmac
mac80211              596969  1 brcmsmac
cfg80211              479757  2 brcmsmac,mac80211
bcma                   46670  2 brcmsmac


[COLOR=#000000][FONT=Ubuntu Mono]
```


I would like to point out that after doing all the above procedure, my wifi adapter is not able to detect any network let alone connect to it... :([/FONT][/COLOR]

---

### Post by varunendra on 2014-03-10
> **MD_Azhar said:**
> I would like to point out that after doing all the above procedure, my wifi adapter is not able to detect any network let alone connect to it... :(

Hmm.. the sta works, and brcmsmac is not even able to scan the networks with BCM4313 - that would be surprise of the year for me.

Without the cable plugged, and without the USB adapter plugged in, could you please run the script again? The script would already be present in you Home directory, use the "No Internet" (offline) method to run it, and post back the fresh report.

And since I am always ready for surprises, lets see the version of sta you would be using _IF_ you install it again -
```
apt-cache show bcmwl-kernel-source | grep Version
```

---

### Post by MD_Azhar on 2014-03-10
Ok, here is the wirelss script as asked by you in the manner described. No cable, no 2nd wifi, pure offline method. 

```

*************** info trace ***************

***** uname -a *****

Linux azhar-Lenovo-IdeaPad-Y580 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy

***** lspci *****

01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8161 Gigabit Ethernet [1969:1091] (rev 08)
    Subsystem: Lenovo Device [17aa:3979]
    Kernel driver in use: alx
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:0587]
    Kernel driver in use: bcma-pci-bridge

***** lsusb *****

Bus 002 Device 003: ID 04f2:b2f1 Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

***** rfkill *****

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** iw reg get *****

country US:
    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5600 @ 40), (3, 20), DFS
    (5650 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)
    (57240 - 63720 @ 2160), (N/A, 40)

***** route -n *****

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

***** lsmod *****

brcmsmac              562767  0 
cordic                 12574  1 brcmsmac
brcmutil               15618  1 brcmsmac
mac80211              596969  1 brcmsmac
cfg80211              479757  2 brcmsmac,mac80211
bcma                   46670  2 brcmsmac

***** nm-tool *****

NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    IIUM-Guest!:     Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34
    Ez WiFi 3:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            alx
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off



***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****


***** iwlist *****

No way to aquire root rights found.

***** resolv.conf *****


***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
blacklist b43
blacklist ssb

***** modinfo *****

filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fw
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     DB4E5CDF31AA9B12B2BA2C0
alias:          bcma:m04BFid0812rev18cl*
alias:          bcma:m04BFid0812rev17cl*
alias:          bcma:m04BFid0812rev11cl*
depends:        mac80211,bcma,brcmutil,cfg80211,cordic
intree:         Y
vermagic:       3.11.0-12-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     E81EE4CBB6A7A689150D93D
depends:        
intree:         Y
vermagic:       3.11.0-12-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     67ADEA6E309FDB9FC19CBCF
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004365sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004359sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004358sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004331sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A8D8sv*sd*bc*sc*i*
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.11.0-12-generic SMP mod_unload modversions 


***** udev rules *****

# PCI device 0x1969:0x1091 (alx)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4727 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x14e4:0x4727 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# USB device 0x:0x (rt73usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

***** dmesg *****

[   12.948518] bcma: bus0: Found chip with id 0x4313, rev 0x01 and package 0x08
[   12.948553] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x24, class 0x0)
[   12.948579] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x18, class 0x0)
[   12.948633] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x11, class 0x0)
[   12.960315] bcma: bus0: Bus registered
[   13.603826] brcmsmac bcma0:0: mfg 4bf core 812 rev 24 class 0 irq 17
[   13.742597] ieee80211 phy0: registered radio enabled led device: brcmsmac-phy0:radio gpio: 243
[   17.393538] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   17.393547] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[   17.394191] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.394412] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   73.858217] brcmsmac bcma0:0: phyerr 0x20, rate 0xa
[  108.277155] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  108.277170] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[  108.277798] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

****************** done ******************


```


Now something interesting, I found out that after purging the sta driver, I mentioned that I could not even detect networks right? Well, actually what I noticed was that few netwroks would get detected but EXTREMELY weak signal. I was reading from another thread which  had a very similar problem to mine. It asked to execute the below two statement:

```
sudo apt-get install linux-headers-generic 
sudo apt-get install bcmwl-kernel-source
```

Now I did the above but the issue did not go so I decided to purge the driver again by runnign the below command :
```
sudo apt-get purge bcmwl-kernel-source
```

But, when I run the below command to confirm the purge, it still shows that I have the driver installed....
```
apt-cache show bcmwl-kernel-source | grep Version
```
output:
```
Version: 6.30.223.141+bdcom-0ubuntu1
```

What's going on? I thought I purged it right? Why is it showing again?

Anyways, moving ahead, what next steps should I take to fix my wifi?

---

### Post by Hadaka on 2014-03-10
Hi, you did purge the file from your modules file that loads
the info to the wireless card. but the file is still avaiabe to load 
in the event you had or changed to a wireless card that required it.
so...it did exactly what you requested and all is well.
when you inserted the usb wifi that had effect on the numbering
and wlan/eth label. Please make sure you leave that usb wifi unplugged
while we try to sort this out.. also..let's run a command to clean a file
it may have interacted with when you tested it eairler. please do.
```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```
also..re-reading your entiere post..it looks like you have been able
to connect to wireless, just NOT some of your university hot spots..
IS THIS CORRECT??

thanks.

---

### Post by MD_Azhar on 2014-03-10
Yes, you are absolutely right. Basically let me summarize for others :

Broadcom 4313 + STA drivers :
- Can detect networks
- Can connect to "some" wifi (without security) + some other with simple security
- CANNOT at all connect to univeeristy hotspot which is secures with PEAP

USB wifi (Linksys WUSB54GC):
-Exactly the same as above surprisngly

Broadcom 4313 + native drivers (after purge) :
- Network detection is extremely WEAK
- Can connect to normal wifi (I guess, didn't try)
- CANNOT connect to uni hotspot which is behind PEAP

Ethernet LAN based :
- Can connect normally

---

### Post by Hadaka on 2014-03-10
Thank YOU..atleast now Im not as confused...well...
were you getting a cant connect because of certs error
message when you attempted the peap school wifi?
+ CA_Certificate..might have had this verbage?

---

### Post by varunendra on 2014-03-11
> **MD_Azhar said:**
> ```

***** iwlist *****

[COLOR="#FF0000"]No way to aquire root rights found.[/COLOR]

```
The above quoted part is not anything wrong with your setup, but it indicates that you probably didn't supply your password when asked by the script, hence it could not scan the available networks. That information may help, so please separately provide that -
```
sudo iwlist scan
```

> **MD_Azhar said:**
> What's going on? I thought I purged it right? Why is it showing again?
The apt-cache command shows ALL the package versions that are AVAILABLE to your system 'In the Repositories'. It may not necessarily installed in the system. So in your case, that version is what you would get IF you installed it again, it is NOT already in your system.

As of now, please post the above "iwlist scan" results, plus, the result of the following -
```
sudo cat /etc/NetworkManager/system-connections/[COLOR="#0000CD"]*<connection name of your University's network>[/COLOR]*
```
..where [COLOR="#0000CD"]*<connection name of your University's network>[/COLOR]* is the name by which you have saved your University's connection. If it contains spaces, enclose the name within double-quotes.

**[COLOR="#FF0000"]CAUTION![/COLOR]** The above output will also contain the **[COLOR="#FF0000"]SECURITY KEY[/COLOR]** that you have saved for the connection. _DELETE or OBSCURE IT BEFORE POSTING THE OUTPUT HERE_.

While I have full faith on brcmsmac, I am not totally rejecting the possibility that it may not always be the best for that card. But I'd like to do some tinkering, even try a later version of it before reverting to the STA.

---

### Post by MD_Azhar on 2014-03-11
Alright guys, I managed to solve this problem. It seems the problem was not with the driver, but rather the PEAP security of my University. 

So this is what I did to solve it :

- In order to get over with the weak network detection caused by the native drivers, I had no choice but to go back to the sta drivers which atleast showed networks. 
- Then I went to th /etc/NetworkManager/system-connections/ directory and opened the profile file of my university's hotspot,
- I deleted the following line :
```
system-ca-cert=true
```

And voila! It connected without any issue. 

I would like to thank all the people involved in this thread especially **varunendra** and **Hadaka** . I learnt a lot of new things thorugh you guys! Keep up the amazing work. 

CHEERS!

---

### Post by varunendra on 2014-03-11
Glad to see you went one step ahead and fixed it yourself. :)

Sometimes, the line comes back after a reboot or a disconnect --> reconnect cycle. If that happens, try changing its value to "false" instead of deleting it altogether.

Hope it remains stable though.

---

### Post by Hadaka on 2014-03-11
fantastic ! aws you can see from my last post, this was
the direction i was headed next , I am seriously pleased
you put the added effort in and went forward to a fix !
I agree with Varun,better to "#" comment out that line or
change it to FALSE. also...which driver did you end up using?
thanks again for takeing the responsibility for your own computer !!

---

### Post by MD_Azhar on 2014-03-11
Alrighty! I'll remember to do that :D

Thanks for those closing tips though ;)

---

