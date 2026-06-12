---
title: "Inconsistent wifi connection 12.04LT Samsung n130 Ubuntu Realtek 8192E BT home hub"
date: 2014-02-02
forum: Networking &amp; Wireless
---

### Post by js12 on 2014-02-02
I've tried a search for different terms but can't find any messages that seem to have this problem. Excuse slightly long post but it will take a while to explain the exact problem.

Basic setup that is causing the problem: Samsung n130, Ubuntu 12.04LTS,  Realtek 8192E network card, BT home hub 3.0

I've installed Ubuntu 12.04 LTS as a dual boot with Windows 7 Starter. Everything works fine apart from the wireless. I realise this is a common problem, but what's odd is that it is only** one** particular wireless network I have a problem with. 

I can connect without any problems to 3 different public networks where I have to login with a username/password through a webpage. I can also connect fine to a different home network (using a Belkin router - can't remember which one exactly [I think it's G] as I'm not there at the moment) by simply entering the WPA/WPA2 password in network manager with no other settings needing changing. 

However I cannot connect to a second home network. This is using a BT Home Hub 3.0. The computer connects to the network with the WPA/WPA2 password set in network manager, and will sometimes allows me about 30 seconds of internet connection before not loading any more pages. If it's of any help when using Chromium the message at the bottom says 'resolving host' and gets no further. However, when this happens the network still shows as connected in network manager. What is odd is that when I boot into windows 7 (as I am at the moment so that I can send this message!) I can connect fine. Secondly, another laptop running Ubuntu 10.04 can connect to the problematic network without any problems. I've checke the settings on that laptop and it just has the WPA/WPA2 password, everything else is left blank, so I wasn't able to copy the setting from the working laptop. 

One thing I have noticed is that in Windows 7 (via Wireless Network Properties -> security ->encryption type) the password encryption has to be set to TKIP - if I change it to AES it won't connect. This caused me some problems when I first got this laptop as it wouldn't connect to the internet with Win 7 until I figured it out one day by chance. However, I can't see an option anywhere to choose TKIP or AES in Ubuntu. Perhaps it is available via the terminal, but I'm new to all this so a bit stuck.

I can only conclude that there is a problem specific to a combination of the BT home hub and Ubuntu 12.04, but after about two hours of googling I haven't found anything that addresses this specific problem. I tried entering the ip/gateway/dns server manually as suggested in other posts but that didn't solve the problem.

Edited to add: I've tried connecting via ethernet but it won't connect that way.

If anybody could offer any help that would be much appreciated. Happy to post any info needed from the terminal.

Thankyou.

---

### Post by praseodym on 2014-02-02
Please show the terminal outputs of:
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
iwlist chan
sudo iwlist scan
```
Does the HUB use its own current source? Does LAN work?

---

### Post by js12 on 2014-02-02
Hello - thanks for your reply. 
[B]
>Does the HUB use its own current source? [/B]

Yes, it its own mains electrical supply.

**>Does LAN work?**

No, I plugged in an ethernet cable directly from the modem and it wouldn't connect at all. The network manager icon was flashing continually as if it was trying to make a connection, but it didn't finish. I tired switching off wireless while it was connected to LAN but that didn't make any difference. 

Here are the results from the terminal commands you asked for:

**js@ubuntu:~$ uname -a**
 ```
Linux ubuntu 3.8.0-35-generic #50~precise1-Ubuntu SMP Wed Dec 4 17:28:45 UTC 2013 i686 i686 i386 GNU/Linux
```
 **js@ubuntu:~$ lspci -nnk | grep -iA2 net**
```
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192E/RTL8192SE Wireless LAN Controller [10ec:8192] (rev 01)
     Subsystem: Askey Computer Corp. Device [144f:7160]
     Kernel driver in use: rtl819xE
 --
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
Subsystem: Samsung Electronics Co Ltd Device [144d:c04d]
Kernel driver in use: r8169
```
 **js@ubuntu:~$ lsusb**
```
Bus 001 Device 002: ID 0ac8:c33f Z-Star Microelectronics Corp. Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```
 **js@ubuntu:~$ lsmod**
```
Module                  Size  Used by
michael_mic            12540  4  
arc4                   12509  2  
rtllib_crypt_tkip      17096  4294967295  
rtllib_crypt_ccmp      12725  4294967295  
bnep                   17919  2  
rfcomm                 38400  0  
bluetooth             211586  10 bnep,rfcomm
parport_pc             27612  0  
ppdev                  12849  0  
snd_hda_codec_realtek    65042  1  
r8192e_pci            209766  0  
uvcvideo               72250  0  
rtllib                137277  1 r8192e_pci
snd_hda_intel          38819  3  
coretemp               13324  0  
snd_hda_codec         118650  2 snd_hda_codec_realtek,snd_hda_intel
videobuf2_core         39385  1 uvcvideo
joydev                 17329  0  
videodev               96131  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12920  1 uvcvideo
lib80211               14040  3 rtllib_crypt_tkip,rtllib_crypt_ccmp,rtllib
videobuf2_memops       13042  1 videobuf2_vmalloc
snd_hwdep              13276  1 snd_hda_codec
rtl8192se              63787  0  
snd_pcm                85934  2 snd_hda_intel,snd_hda_codec
i915                  554735  3  
rtlwifi                70322  1 rtl8192se
snd_seq_midi           13132  0  
snd_rawmidi            25157  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51593  2 snd_seq_midi,snd_seq_midi_event
psmouse                82769  0  
drm_kms_helper         47749  1 i915
microcode              18433  0  
serio_raw              13031  0  
snd_timer              28931  2 snd_pcm,snd_seq
samsung_laptop         18195  0  
drm                   233935  4 i915,drm_kms_helper
mac80211              546065  2 rtl8192se,rtlwifi
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
lpc_ich                17048  0  
snd                    57014  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              454468  2 rtlwifi,mac80211
soundcore              12600  1 snd
i2c_algo_bit           13316  1 i915
snd_page_alloc         18398  2 snd_hda_intel,snd_pcm
video                  19116  2 i915,samsung_laptop
mac_hid                13077  0  
lp                     17455  0  
parport                40930  3 parport_pc,ppdev,lp
r8169                  62613  0  
```
 **js@ubuntu:~$ iwconfig**
```

wlan0     802.11bgn  ESSID:"BTHub3-C2JZ"  Nickname:"rtl8192E"
Mode:Managed  Frequency=2.412 GHz  Access Point: 34:6B3:90:AC:37    
Bit Rate=65 Mb/s    
Retry min limit:7   RTS thr:ff   Fragment thr:ff
Power Management period:0us  mode:All packets received
Link Quality=93/100  Signal level=-52 dBm  Noise level=-116 dBm
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.
```
**js@ubuntu:~$ iwlist chan**
```
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

Current Frequency=2.412 GHz (Channel 1)

lo        no frequency information.

eth0      no frequency information.
```
**js@ubuntu:~$ sudo iwlist scan**      [B][#I have highlighted the router I'm trying to connect to in bold]
[/B][sudo] password for js:  

```
wlan0     Scan completed :
           Cell 01 - Address: 02:FE:F4:28:DB:A0
 ESSID:"BTWiFi"
Protocol:IEEE802.11N-24G
Mode:Master
Channel:1
Encryption key ff
Bit Rates:144.5 Mb/s
Extra: Rates (Mb/s): 1 2 5.5 11 6 9 12 18 24 36 48 54  
Quality=84/100  Signal level=-61 dBm  Noise level=-112 dBm
Extra: Last beacon: 166ms ago
Cell 02 - Address: 00:26:447:3C:7D
ESSID:"melchiorson"
Protocol:IEEE802.11bg
Mode:Master
                     Channel:1
                      Encryption key n
 Bit Rates:54 Mb/s
Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54  
Quality=72/100  Signal level=-61 dBm  Noise level=-106 dBm
Extra: Last beacon: 158ms ago
           Cell 03 - Address: 00:FE:F4:28 B:A0
 ESSID:"BTHub3-FN5Z"
Protocol:IEEE802.11N-24G
Mode:Master
Channel:1
Encryption key n
Bit Rates:144.5 Mb/s
Extra: Rates (Mb/s): 1 2 5.5 11 6 9 12 18 24 36 48 54  
Quality=76/100  Signal level=-62 dBm  Noise level=-108 dBm
IE: WPA Version 1
                         Group Cipher : TKIP
 Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: Unknown: DD2C0050F204104A0001101044000102105700010010470010565AA94967C14C0EAA8FF349E6F59311103C000101
Extra: Last beacon: 157ms ago
           Cell 04 - Address: 12:FE:F4:28 B:A0
 ESSID:"BTWiFi-with-FON"
Protocol:IEEE802.11N-24G
Mode:Master
Channel:1
Encryption key ff
Bit Rates:144.5 Mb/s
Extra: Rates (Mb/s): 1 2 5.5 11 6 9 12 18 24 36 48 54  
Quality=84/100  Signal level=-62 dBm  Noise level=-112 dBm
Extra: Last beacon: 163ms ago

          Cell 05 - Address: 02:01:3B:99:7A:8A
 ESSID:"BTWiFi"
Protocol:IEEE802.11N-24G
Mode:Master
Channel:1
Encryption key:off
Bit Rates:144.5 Mb/s
Extra: Rates (Mb/s): 1 2 5.5 11 6 9 12 18 24 36 48 54  
Quality=65/100  Signal level=-60 dBm  Noise level=-102 dBm
Extra: Last beacon: 183ms ago

           Cell 06 - Address: A0:21:B7 6:86:76
 ESSID:"virginmedia6482790"
Protocol:IEEE802.11N-24G
Mode:Master
Channel:1
Encryption key n
Bit Rates:144.5 Mb/s
Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54  
Quality=74/100  Signal level=-62 dBm  Noise level=-107 dBm

IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIPAuthentication Suites (1) : PSK
                     IE: IEEE 802.11i/WPA2 Version 1
 Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: Unknown: DD180050F204104A00011010440001021049000600372A000120
Extra: Last beacon: 165ms ago

**          Cell 07 - Address: **34:6B:D3:90:AC:37
[B]ESSID:"BTHub3-C2JZ"
[/B]
[B]Protocol:IEEE802.11N-24G
Mode:Master
[/B]
[B]Channel:1
Encryption key on
[/B]
[B]Bit Rates:144.5 Mb/s
[/B]
[B]Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54  
[/B]
[B]Quality=90/100  Signal level=-62 dBm  Noise level=-115 dBm
[/B]
[B]IE: WPA Version 1
[/B]
[B]Group Cipher : TKIP
[/B]
[B]Pairwise Ciphers (2) : CCMP TKIP
[/B]
[B]Authentication Suites (1) : PSK
[/B]
[B]IE: IEEE 802.11i/WPA2 Version 1
[/B]
[B]Group Cipher : TKIP
[/B]
[B]Pairwise Ciphers (2) : CCMP TKIP
[/B]
[B]Authentication Suites (1) : PSK
[/B]
[B]IE: Unknown: DD0E0050F204104A0001101044000102
[/B]
**Extra: Last beacon: 158ms ago**

           Cell 08 - Address: 28:10:7B:F5:FE:66
 ESSID:"dlink"
Protocol:IEEE802.11N-24G
Mode:Master
Channel:6Encryption key n
Bit Rates:300 Mb/s
Extra: Rates (Mb/s): 1 2 5.5 6 11 9 12 18 24 36 48 54  
Quality=65/100  Signal level=-63 dBm  Noise level=-102 dBm
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: Unknown: DD130050F204104A00011010440001021041000100
Extra: Last beacon: 82ms ago

           Cell 09 - Address: A0:21:B7:58:C1:25
 ESSID:"virginmedia2215215"
                     Protocol:IEEE802.11N-24G
                    Mode:Master
 Channel:6
Encryption key n
Bit Rates:144.5 Mb/s
Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54  
Quality=65/100  Signal level=-64 dBm  Noise level=-102 dBm
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: Unknown: DD180050F204104A00011010440001021049000600372A000120
Extra: Last beacon: 81ms ago

           Cell 10 - Address: C4:3D:C7:3D:29:83
ESSID:"virginmedia62035491"
Protocol:IEEE802.11N-24G
Mode:Master
Channel:6
Encryption key n
Bit Rates:144.5 Mb/s
Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54  
Quality=72/100  Signal level=-63 dBm  Noise level=-106 dBm
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: Unknown: DD180050F204104A00011010440001021049000600372A000120
Extra: Last beacon: 97ms ago

           Cell 11 - Address: 88:03:55:9B:ED:EF
 ESSID:"EE-BrightBox-wy33n2"
Protocol:IEEE802.11N-24G
Mode:Master
Channel:6
Encryption key n
Bit Rates:144.5 Mb/sExtra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54  
Quality=68/100  Signal level=-63 dBm  Noise level=-104 dBm
IE: WPA Version 1
Group Cipher : TKIPPairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
Extra: Last beacon: 86ms ago

           Cell 12 - Address: 64:70:02:47:0B 4
                      ESSID:"TP-LINK_470BD4"
                    Protocol:IEEE802.11N-24G
 Mode:Master
Channel:6
Encryption key n
Bit Rates:300 Mb/s
Extra: Rates (Mb/s): 1 2 5.5 6 11 9 12 18 24 36 48 54  
Quality=63/100  Signal level=-63 dBm  Noise level=-101 dBm
IE: IEEE 802.11i/WPA2 Version 1Group Cipher : CCMP
                         Pairwise Ciphers (1) : CCMP
 Authentication Suites (1) : PSK
IE: Unknown: DD270050F204104A000100104400010210470010BC329E001DD811B28601647002470BD4103C000101
Extra: Last beacon: 89ms ago

           Cell 13 - Address: 00:8E:F2 C:21:1C
 ESSID:"virginmedia3870065"
Protocol:IEEE802.11N-24G
Mode:Master
Channel:6
Encryption key n
Bit Rates:144.5 Mb/s
Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54  
Quality=65/100  Signal level=-62 dBm  Noise level=-102 dBm
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: Unknown: DD180050F204104A00011010440001021049000600372A000120
Extra: Last beacon: 127ms ago

           Cell 14 - Address: 00:01:3B:99:7A:8A
 ESSID:"BTHub3-QRRQ"
Protocol:IEEE802.11N-24G
Mode:Master
Channel:1
Encryption key n
Bit Rates:144.5 Mb/s
                     Extra: Rates (Mb/s): 1 2 5.5 11 6 9 12 18 24 36 48 54  
 Quality=65/100  Signal level=-61 dBm  Noise level=-102 dBm
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: Unknown: DD2C0050F204104A0001101044000102105700010010470010565AA94967C14C0EAA8FF349E6F59311103C000101
Extra: Last beacon: 173ms ago

           Cell 15 - Address: 12:01:3B:A2:58:B2
 ESSID:"BTWiFi-with-FON"
Protocol:IEEE802.11N-24G
Mode:Master
Channel:1Encryption key ff
Bit Rates:144.5 Mb/s
Extra: Rates (Mb/s): 1 2 5.5 11 6 9 12 18 24 36 48 54  
Quality=65/100  Signal level=-60 dBm  Noise level=-102 dBm
Extra: Last beacon: 188ms ago

           Cell 16 - Address: 02:818:74:EE:CA
 ESSID:"BTWiFi"
Protocol:IEEE802.11N-24G
Mode:Master
Channel:11
Encryption keyff
Bit Rates:144.5 Mb/s
Extra: Rates (Mb/s): 1 2 5.5 11 6 9 12 18 24 36 48 54  
Quality=81/100  Signal level=-67 dBm  Noise level=-110 dBm
Extra: Last beacon: 3ms ago

           Cell 17 - Address: 00:818:74:EE:CA
 ESSID:"BTHub3-FFKH"
Protocol:IEEE802.11N-24G
Mode:Master
Channel:11
Encryption keyn
Bit Rates:144.5 Mb/s
Extra: Rates (Mb/s): 1 2 5.5 11 6 9 12 18 24 36 48 54  
Quality=79/100  Signal level=-68 dBm  Noise level=-109 dBmIE: WPA Version 1
                         Group Cipher : TKIP
 Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: Unknown: DD2C0050F204104A0001101044000102105700010010470010565AA94967C14C0EAA8FF349E6F59311103C000101
Extra: Last beacon: 13ms ago

           Cell 18 - Address: 12:818:74:EE:CA
 ESSID:"BTWiFi-with-FON"
Protocol:IEEE802.11N-24GMode:Master
Channel:11
Encryption keyff
Bit Rates:144.5 Mb/s
Extra: Rates (Mb/s): 1 2 5.5 11 6 9 12 18 24 36 48 54  
Quality=84/100  Signal level=-68 dBm  Noise level=-112 dBm
Extra: Last beacon: 7ms ago
Cell 19 - Address: 40:CB:A8:56:FE:C4
ESSID:"TALKTALK-56FEBC"
Protocol:IEEE802.11N-24G
Mode:Master
Channel:11
Encryption keyn
Bit Rates:270 Mb/s
Extra: Rates (Mb/s): 1 2 5.5 6 11 9 12 18 24 36 48 54  
Quality=71/100  Signal level=-67 dBm  Noise level=-105 dBm
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : PSK
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : PSK
IE: Unknown: DD270050F204104A0001101044000102104700102880288028801880A88040CBA856FEC4103C000101
Extra: Last beacon: 3ms ago

           Cell 20 - Address: 00:14:A5:54:31 4
 ESSID:"belkin54g"
Protocol:IEEE802.11bg
Mode:Master
Channel:11
Encryption key n
Bit Rates:54 Mb/s
Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54  
Quality=62/100  Signal level=-66 dBm  Noise level=-101 dBm
Extra: Last beacon: 36ms ago
Cell 21 - Address: 42:534:B7:70:9C
ESSID:"BTWiFi-with-FON"
Protocol:IEEE802.11N-24G
Mode:MasterChannel:11
                     Encryption keyff
 Bit Rates:144.5 Mb/s
Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54  
Quality=63/100  Signal level=-65 dBm  Noise level=-101 dBm
Extra: Last beacon: 40ms ago

           Cell 22 - Address: 42:53:D4:B7:70:9B
 ESSID:"BTWiFi"
Protocol:IEEE802.11N-24G
Mode:Master
Channel:11
Encryption keyff
Bit Rates:144.5 Mb/s
Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54  
Quality=63/100  Signal level=-65 dBm  Noise level=-101 dBm
Extra: Last beacon: 40ms ago

           Cell 23 - Address: 02:01:3B:A2:58:B2
 ESSID:"BTWiFi"
Protocol:IEEE802.11N-24G
Mode:Master
Channel:1
Encryption keyf
Bit Rates:144.5 Mb/s
Extra: Rates (Mb/s): 1 2 5.5 11 6 9 12 18 24 36 48 54  
Quality=63/100  Signal level=-61 dBm  Noise level=-101 dBm
Extra: Last beacon: 165ms ago

           Cell 24 - Address: 00:01:3B:A2:58:B2
 ESSID:"BTHub3-H6G9"
Protocol:IEEE802.11N-24G
Mode:Master
Channel:1
Encryption keyn
Bit Rates:144.5 Mb/s
Extra: Rates (Mb/s): 1 2 5.5 11 6 9 12 18 24 36 48 54  
Quality=65/100  Signal level=-61 dBm  Noise level=-102 dBm
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: Unknown: DD2C0050F204104A0001101044000102105700010010470010565AA94967C14C0EAA8FF349E6F59311103C000101
Extra: Last beacon: 181ms ago

           Cell 25 - Address: 00:01:3B:B9:CA:22
 ESSID:"BTHub3-NX97"
Protocol:IEEE802.11N-24G
Mode:Master
Channel:11
Encryption keyn
Bit Rates:144.5 Mb/s
Extra: Rates (Mb/s): 1 2 5.5 11 6 9 12 18 24 36 48 54  
Quality=62/100  Signal level=-65 dBm  Noise level=-101 dBm
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: Unknown: DD2C0050F204104A0001101044000102105700010010470010565AA94967C14C0EAA8FF349E6F59311103C000101
Extra: Last beacon: 41ms ago

lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.
```
Thanks for your help, I hope all that makes some sense!

---

### Post by praseodym on 2014-02-02
```
IE: [COLOR="#FF0000"]WPA[/COLOR] Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: IEEE 802.11i/[COLOR="#FF0000"]WPA2[/COLOR] Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK

```
Midex mode WPA/WPA2. Try to change the encryption mode to pure WPA2-AES (CCMP), check the router manual. 

Additionally there are 2 drivers loaded:

```

r8192e_pci 209766 0
...
rtl8192se 63787 0

```
Check:```

sudo modprobe -rfv rtl8192se r8192e_pci
sudo modprobe -v r8192e_pci
iwconfig
```

---

### Post by js12 on 2014-02-02
[SIZE=2][FONT=arial]Hello - thanks for that. I've chnaged the router setting to WP2 and entered the commands you suggested. Here are the results:

js@ubuntu:~$ sudo modprobe -rfv rtl8192se r8192e_pci

```


rmmod /lib/modules/3.8.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.ko

rmmod /lib/modules/3.8.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko

rmmod /lib/modules/3.8.0-35-generic/kernel/net/mac80211/mac80211.ko

rmmod /lib/modules/3.8.0-35-generic/kernel/net/wireless/cfg80211.ko

rmmod /lib/modules/3.8.0-35-generic/kernel/drivers/staging/rtl8192e/rtl8192e/r8192e_pci.ko

rmmod /lib/modules/3.8.0-35-generic/kernel/drivers/staging/rtl8192e/rtllib.ko


```

js@ubuntu:~$ sudo modprobe -v r8192e_pci

```
insmod /lib/modules/3.8.0-35-generic/kernel/drivers/staging/rtl8192e/rtllib.ko 

insmod /lib/modules/3.8.0-35-generic/kernel/drivers/staging/rtl8192e/rtl8192e/r8192e_pci.ko 

```[/FONT][/SIZE][SIZE=2][FONT=arial]

[/FONT][/SIZE][SIZE=2][FONT=arial]js@ubuntu:~$ iwconfig

```
wlan0     802.11bgn  ESSID:"BTHub3-C2JZ"  Nickname:"rtl8192E"

          Mode:Managed  Frequency=2.412 GHz  Access Point: 34:6B:D3:90:AC:37   

          Bit Rate=65 Mb/s   

          Retry min limit:7   RTS thr: off   Fragment thr: off

          Power Management: off

          Link Quality=87/100  Signal level=-51 dBm  Noise level=-113 dBm

          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


lo        no wireless extensions.


eth0      no wireless extensions.


js@ubuntu:~$ 

```[/FONT][/SIZE][SIZE=2][FONT=arial]

And here is the result from [/FONT][/SIZE][SIZE=2][FONT=arial]$ sudo iwlist scan (I've removed all the other results, just showing my connection)
It looks like the router is now only showing WPA2.
[/FONT][/SIZE]
```
[SIZE=2][FONT=arial]lan0     Scan completed :
[/FONT][/SIZE]
[SIZE=2][FONT=arial]

[/FONT][/SIZE]
[SIZE=2][FONT=arial]Cell 05 - Address: 34:6B:D3:90:AC:37
[/FONT][/SIZE]
[SIZE=2][FONT=arial]

[/FONT][/SIZE]
[SIZE=2][FONT=arial]                    ESSID:"BTHub3-C2JZ"[/FONT][/SIZE]
[SIZE=2][FONT=arial]

[/FONT][/SIZE]
[SIZE=2][FONT=arial]                    Protocol:IEEE802.11N-24G[/FONT][/SIZE]
[SIZE=2][FONT=arial]

[/FONT][/SIZE]
[SIZE=2][FONT=arial]                    Mode:Master[/FONT][/SIZE]
[SIZE=2][FONT=arial]

[/FONT][/SIZE]
[SIZE=2][FONT=arial]                    Channel:1[/FONT][/SIZE]
[SIZE=2][FONT=arial]

[/FONT][/SIZE]
[SIZE=2][FONT=arial]                    Encryption key:on[/FONT][/SIZE]
[SIZE=2][FONT=arial]

[/FONT][/SIZE]
[SIZE=2][FONT=arial]                    Bit Rates:144.5 Mb/s[/FONT][/SIZE]
[SIZE=2][FONT=arial]

[/FONT][/SIZE]
[SIZE=2][FONT=arial]                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54  [/FONT][/SIZE]
[SIZE=2][FONT=arial]

[/FONT][/SIZE]
[SIZE=2][FONT=arial]                    Quality=94/100  Signal level=-54 dBm  Noise level=-117 dBm[/FONT][/SIZE]
[SIZE=2][FONT=arial]

[/FONT][/SIZE]
[SIZE=2][FONT=arial]                    IE: IEEE 802.11i/WPA2 Version 1[/FONT][/SIZE]
[SIZE=2][FONT=arial]

[/FONT][/SIZE]
[SIZE=2][FONT=arial]                        Group Cipher : CCMP[/FONT][/SIZE]
[SIZE=2][FONT=arial]

[/FONT][/SIZE]
[SIZE=2][FONT=arial]                        Pairwise Ciphers (1) : CCMP[/FONT][/SIZE]
[SIZE=2][FONT=arial]

[/FONT][/SIZE]
[SIZE=2][FONT=arial]                        Authentication Suites (1) : PSK[/FONT][/SIZE]
[SIZE=2][FONT=arial]

[/FONT][/SIZE]
[SIZE=2][FONT=arial]                    IE: Unknown: DD0E0050F204104A0001101044000102[/FONT][/SIZE]
[SIZE=2][FONT=arial]

[/FONT][/SIZE]
[SIZE=2][FONT=arial]                    Extra: Last beacon: 159ms ago
[/FONT][/SIZE]

```[SIZE=2][FONT=arial]

That didn't quite solve the problem although it made it better than it was, so thanks for helping. I could connect but it would drop the connection after loading one or two pages. 

So I followed the advice here which seems to be specific to my router/ISP, but changed the DNS server to google's dns servers (8.8.8.8, 8.8.4.4) as advised on another page.[/FONT][/SIZE][SIZE=2][FONT=arial]
[/FONT][/SIZE]
[SIZE=2][FONT=arial][U][http://askubuntu.com/questions/217678/bt-home-hub-2-0](http://askubuntu.com/questions/217678/bt-home-hub-2-0)

[/U]
I then disabled IVP6 (changed the settings to 'ignore' on the IVP6 tab in network manager->edit connection ->wireless) also advised on another ubuntu forum post found via google.

So far this seems to have **partially** solved the problem: I can connect to the internet for a while - I'm posting this reply from Ubuntu - but it still drops the connection. I can reconnect simply by clicking my network name in network manager, but it's annoying that it still loses the connection. I really don't want to have give up and go back to Windows!

Do you have any other idea that I could try? Or perhaps I should start  new thread as the problem is now slightly different from my original request? [/FONT][/SIZE]Either way, thanks again for your help as it got it working enough for me to make the other changes.

---

### Post by praseodym on 2014-02-02
This device/driver combo is known to be buggy...Do not forget to blacklist the "wrong" driver:
```

echo "blacklist rtl8192se" | sudo tee /etc/modprobe.d/blacklist-rtl8192se.conf
```


Driver version with this kernel is:
```
modinfo r8192e_pci 
filename:       /lib/modules/3.8.0-35-generic/kernel/drivers/staging/rtl8192e/rtl8192e/r8192e_pci.ko
firmware:       RTL8192E/data.img
firmware:       RTL8192E/main.img
firmware:       RTL8192E/boot.img
license:        GPL
version:        [COLOR="#FF0000"]0014.0401.2010[/COLOR]
```
You could try to compile this new(er) version **0015.1013.2010**:
[http://media.cdn.ubuntu-de.org/forum/attachments/02/01/3137672-rtl8192e_linux_2.6.0015.1013.2010.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/02/01/3137672-rtl8192e_linux_2.6.0015.1013.2010.tar.gz)

---

### Post by js12 on 2014-02-02
Thanks, I've blacklisted the 'wrong' driver. 
I downloaded the new version, and unzipped to my downlads directory. When I navigate to it in terminal and try to 'make' I get an error 2. Do you have any ideas what I might be doing wrong?

EDit: just realised it would be helpful to post the error message from the terminal

```

js@ubuntu:~/Downloads/rtl8192e_linux_2.6.0015.1013.2010$ sudo make
[sudo] password for js: 
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-35-generic'
gcc: error: /lib/modules/3.8.0-35-generic/build/include/linux/autoconf.h: No such file or directory
gcc: fatal error: no input files
compilation terminated.
scripts/Makefile.build:49: *** CFLAGS was changed in "/home/js/Downloads/rtl8192e_linux_2.6.0015.1013.2010/HAL/rtl8192/Makefile". Fix it to use ccflags-y. Stop.
make[1]: *** [_module_/home/js/Downloads/rtl8192e_linux_2.6.0015.1013.2010/HAL/rtl8192] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-35-generic'
make: *** [all] Error 2
js@ubuntu:~/Downloads/rtl8192e_linux_2.6.0015.1013.2010$ 

```

---

### Post by praseodym on 2014-02-03
Doesnt compile here, too. Lets check the "wrong" driver:
```

sudo modprobe -rfv rtl8192e_pci
sudo modprobe -v rtl8192se
```

---

### Post by js12 on 2014-02-03
Here are the results:

```

js@ubuntu:~$ sudo modprobe -rfv rtl8192e_pci
[sudo] password for js: 
FATAL: Module rtl8192e_pci not found.

js@ubuntu:~$ sudo modprobe -v rtl8192se
insmod /lib/modules/3.8.0-35-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.8.0-35-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.8.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko 
insmod /lib/modules/3.8.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.ko 

```

Today I used Ubuntu to go online through public wifi and had no problems, and at the moment I'm using a home connection at my family's house and have no problem here with a Belkin G Router. So it looks like there is some specific issue linked to the router setup  I'm having trouble with. This morning the problem returned and I could only get online for 30 seconds and then no more pages would load.

---

### Post by praseodym on 2014-02-03
**sudo modprobe -rfv r8192e_pci**

Typo

---

