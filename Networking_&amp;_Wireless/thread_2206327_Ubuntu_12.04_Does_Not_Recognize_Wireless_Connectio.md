---
title: "Ubuntu 12.04 Does Not Recognize Wireless Connections"
date: 2014-02-18
forum: Networking &amp; Wireless
---

### Post by javier11 on 2014-02-18
Hello everyone,

This is my first posting on here so I'm very grateful for any help you can provide.  I've been using Ubuntu 12.04 for some 6 months now and I really enjoy it.

Sometimes I find that I lose access to my wireless connections on the system though, but usually this resolves itself after I reboot the machine.  However, this time the lapse has been a sustained one....

So looking at some of the posts on the subject as well as the basic Ubuntu troubleshooting tips regarding wireless connectivity issues, I have come up with the following results:

```
> javier@javier-HP-Mini-311-1000:~$ nm-tool
 
 
NetworkManager Tool
 
 
State: disconnected
 
 
- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             unavailable
  Default:           no
  HW Address:        C8:0A:A9:32:6A:AE
 
 
  Capabilities:
    Carrier Detect:  yes
 
 
  Wired Properties
    Carrier:         off
 
> cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.3 LTS"
Linux javier-HP-Mini-311-1000 3.5.0-43-generic #66~precise1-Ubuntu SMP Thu Oct 24 14:55:08 UTC 2013 i686 i686 i386 GNU/Linux
> javier@javier-HP-Mini-311-1000:~$ lspci -nnk | grep -iA2 net
00:0a.0 Ethernet controller [0200]: NVIDIA Corporation MCP79 Ethernet [10de:0ab0] (rev b1)
            Subsystem: Hewlett-Packard Company Device [103c:3651]
            Kernel driver in use: forcedeth
--
03:00.0 Network controller [0280]: Broadcom Corporation BCM43224 802.11a/b/g/n [14e4:4353] (rev 01)
            Subsystem: Hewlett-Packard Company WMIB-275N Half-size Mini PCIe Card [103c:1509]
            Kernel modules: bcma
> javier@javier-HP-Mini-311-1000:~$ lsusb
Bus 001 Device 007: ID 03f0:201d Hewlett-Packard un2400 Gobi Wireless Modem (QDL mode)
Bus 002 Device 002: ID 090c:637b Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.)
Bus 003 Device 004: ID 03f0:231d Hewlett-Packard
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
> javier@javier-HP-Mini-311-1000:~$ iwconfig
lo        no wireless extensions.
 
eth0      no wireless extensions.
 
javier@javier-HP-Mini-311-1000:~$ rfkill list all
1: hp-wifi: Wireless LAN
            Soft blocked: no
            Hard blocked: no
2: hp-bluetooth: Bluetooth
            Soft blocked: no
            Hard blocked: no
3: hp-wwan: Wireless WAN
            Soft blocked: no
            Hard blocked: no
5: hci0: Bluetooth
            Soft blocked: no
            Hard blocked: no
> javier@javier-HP-Mini-311-1000:~$ lsmod
Module                  Size  Used by
dm_crypt               22572  1
snd_hda_codec_hdmi     31825  1
snd_hda_codec_idt      60238  1
joydev                 17394  0
coretemp               13362  0
hp_wmi                 13653  0
sparse_keymap          13659  1 hp_wmi
snd_hda_intel          32983  3
snd_hda_codec         116477  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13277  1 snd_hda_codec
snd_pcm                81124  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13133  0
snd_rawmidi            25426  1 snd_seq_midi
snd_seq_midi_event     14476  1 snd_seq_midi
snd_seq                51594  2 snd_seq_midi,snd_seq_midi_event
microcode              18396  0
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               72249  0
snd                    62675  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videobuf2_core         32212  1 uvcvideo
videodev              100265  2 uvcvideo,videobuf2_core
qcserial               12663  0
psmouse                91408  0
soundcore              14636  1 snd
usb_wwan               19532  1 qcserial
videobuf2_vmalloc      12757  1 uvcvideo
serio_raw              13032  0
usbserial              36910  2 qcserial,usb_wwan
snd_page_alloc         14109  2 snd_hda_intel,snd_pcm
videobuf2_memops       13213  1 videobuf2_vmalloc
shpchp                 32326  0
btusb                  17952  0
rfcomm                 38104  12
bnep                   17791  2
parport_pc             32115  0
bluetooth             189742  24 btusb,rfcomm,bnep
ppdev                  12850  0
mac_hid                13078  0
binfmt_misc            17293  1
i2c_nforce2            12907  0
lp                     17456  0
parport                40931  3 parport_pc,ppdev,lp
nouveau               855013  3
ttm                    76326  1 nouveau
drm_kms_helper         47459  1 nouveau
drm                   240443  5 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13317  1 nouveau
mxm_wmi                12894  1 nouveau
ahci                   25621  2
libahci                26166  1 ahci
forcedeth              58371  0
video                  19117  1 nouveau
wmi                    18745  3 hp_wmi,nouveau,mxm_wmi
```

Any recommendations on how to proceed?  Again, I am most grateful.

Regards

---

### Post by varunendra on 2014-02-19
Welcome to Ubuntu Forums javier11 !

Please try this -
```
sudo modprobe -v brcmsmac
```
Does it bring up the wireless?

If not, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by javier11 on 2014-02-19
Yes, it most certainly did!  Many thanks Varun :)

---

### Post by javier11 on 2014-02-19
Hello again Varun,

Thank you kindly for your help.  It seems that the solution you first provided works but must be input into the terminal each time I boot the computer up newly.  So given that reality, I chose to run the wireless script as you requested, in the hopes that you could analyze it and suggest a more permanent fix.  Here are the results:



```
*************** info trace ***************


***** uname -a *****


Linux javier-HP-Mini-311-1000 3.5.0-43-generic #66~precise1-Ubuntu SMP Thu Oct 24 14:55:08 UTC 2013 i686 i686 i386 GNU/Linux


***** lsb_release *****


Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.3 LTS
Release:	12.04
Codename:	precise


***** lspci *****


00:0a.0 Ethernet controller [0200]: NVIDIA Corporation MCP79 Ethernet [10de:0ab0] (rev b1)
	Subsystem: Hewlett-Packard Company Device [103c:3651]
	Kernel driver in use: forcedeth
--
03:00.0 Network controller [0280]: Broadcom Corporation BCM43224 802.11a/b/g/n [14e4:4353] (rev 01)
	Subsystem: Hewlett-Packard Company WMIB-275N Half-size Mini PCIe Card [103c:1509]
	Kernel driver in use: bcma-pci-bridge


***** lsusb *****


Bus 001 Device 004: ID 03f0:201d Hewlett-Packard un2400 Gobi Wireless Modem (QDL mode)
Bus 002 Device 002: ID 090c:637b Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) 
Bus 003 Device 002: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 003 Device 003: ID 03f0:231d Hewlett-Packard 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


***** PCMCIA Card Info *****




***** iwconfig *****


wlan0     IEEE 802.11abgn  ESSID:"guest-net"  
          Mode:Managed  Frequency:5.22 GHz  Access Point: <MAC address removed>   
          Bit Rate=54 Mb/s   Tx-Power=17 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=52/70  Signal level=-58 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:8  Invalid misc:0   Missed beacon:0




***** rfkill *****


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hp-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: hp-wwan: Wireless WAN
	Soft blocked: no
	Hard blocked: no
4: phy0: Wireless LAN
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


***** lsmod *****


brcmsmac              512643  0 
mac80211              475546  1 brcmsmac
bcma                   34573  1 brcmsmac
brcmutil               14356  1 brcmsmac
cfg80211              181041  2 brcmsmac,mac80211
cordic                 12519  1 brcmsmac


***** nm-tool *****


NetworkManager Tool


State: connected (global)


- Device: wlan0  [guest-net] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           54 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    voice:           Infra, <MAC address removed>, Freq 5220 MHz, Rate 54 Mb/s, Strength 65 WPA2 Enterprise
    paris:           Infra, <MAC address removed>, Freq 5220 MHz, Rate 54 Mb/s, Strength 64 WPA Enterprise
    priv-psk:        Infra, <MAC address removed>, Freq 5220 MHz, Rate 54 Mb/s, Strength 64 WPA
    athens:          Infra, <MAC address removed>, Freq 5220 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2 Enterprise
    priv-psk:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 60 WPA
    athens:          Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 59 WPA WPA2 Enterprise
    paris:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 59 WPA Enterprise
    priv-psk:        Infra, <MAC address removed>, Freq 5300 MHz, Rate 54 Mb/s, Strength 45 WPA
    athens:          Infra, <MAC address removed>, Freq 5300 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2 Enterprise
    paris:           Infra, <MAC address removed>, Freq 5300 MHz, Rate 54 Mb/s, Strength 45 WPA Enterprise
    athens:          Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2 Enterprise
    paris:           Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA Enterprise
    voice:           Infra, <MAC address removed>, Freq 5300 MHz, Rate 54 Mb/s, Strength 44 WPA2 Enterprise
    priv-psk:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WPA
    paris:           Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA Enterprise
    athens:          Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2 Enterprise
    voice:           Infra, <MAC address removed>, Freq 5785 MHz, Rate 54 Mb/s, Strength 35 WPA2 Enterprise
    athens:          Infra, <MAC address removed>, Freq 5785 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2 Enterprise
    priv-psk:        Infra, <MAC address removed>, Freq 5785 MHz, Rate 54 Mb/s, Strength 34 WPA
    paris:           Infra, <MAC address removed>, Freq 5785 MHz, Rate 54 Mb/s, Strength 34 WPA Enterprise
    paris:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA Enterprise
    priv-psk:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA
    athens:          Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2 Enterprise
    athens:          Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2 Enterprise
    paris:           Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA Enterprise
    priv-psk:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA
    paris:           Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA Enterprise
    Genephianess:    Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 12 WPA2
    Bizarro:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WEP
    guest-net:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 60
    guest-net:       Infra, <MAC address removed>, Freq 5300 MHz, Rate 54 Mb/s, Strength 45
    guest-net:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44
    guest-net:       Infra, <MAC address removed>, Freq 5785 MHz, Rate 54 Mb/s, Strength 34
    guest-net:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29
    HP-Print-3F-Officejet 4630: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 29
    guest-net:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27
    guest-net:       Infra, <MAC address removed>, Freq 5765 MHz, Rate 54 Mb/s, Strength 25
    guest-net:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 35
    priv-psk:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WPA
    guest-net:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20
    *guest-net:      Infra, <MAC address removed>, Freq 5220 MHz, Rate 54 Mb/s, Strength 60
    guest-net:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 19
    athens:          Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2 Enterprise
    guest-net:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 19
    priv-psk:        Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 24 WPA
    athens:          Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2 Enterprise


  IPv4 Settings:
    Address:         10.124.43.110
    Prefix:          23 (255.255.254.0)
    Gateway:         10.124.42.1


    DNS:             156.111.60.150
    DNS:             156.111.70.150




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
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
plugins=ifupdown,keyfile
dns=dnsmasq


[ifupdown]
managed=false


***** interfaces *****


auto lo
iface lo inet loopback




***** iwlist *****


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:44
                    Frequency:5.22 GHz (Channel 44)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:off
                    ESSID:"guest-net"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=00000044fe5ef4d6
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 000967756573742D6E6574
                    IE: Unknown: 01069824B048606C
                    IE: Unknown: 071255532024041134041864051884031895041E
                    IE: Unknown: 0B050100008D5B
                    IE: Unknown: 851E03008F000F00FF03590062646830382D6170303900000000000001000026
                    IE: Unknown: 9606004096000200
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301003401
                    IE: Unknown: DD050040961404
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"athens"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000044ff3d10ef
                    Extra: Last beacon: 4556ms ago
                    IE: Unknown: 0006617468656E73
                    IE: Unknown: 01088B0C129618243048
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B0502001E8D5B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 3202606C
                    IE: Unknown: 9606004096000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301003401
                    IE: Unknown: DD050040961405
          Cell 03 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"T-Mobile Broadband16"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000575a35180
                    Extra: Last beacon: 4552ms ago
                    IE: Unknown: 0014542D4D6F62696C652042726F616462616E643136
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 050401050000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A2C0000FF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601000100000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD080050F21100000002
          Cell 04 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"Belkin.3923"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001f2fe7b167
                    Extra: Last beacon: 4544ms ago
                    IE: Unknown: 000B42656C6B696E2E33393233
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6E1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601000500000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0502004C127A
                    IE: Unknown: DD1E00904C336E1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3401000500000000000000000000000000000000000000
                    IE: Unknown: DD07000C4304000000
          Cell 05 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"priv-psk"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000044febd1e9a
                    Extra: Last beacon: 4532ms ago
                    IE: Unknown: 0008707269762D70736B
                    IE: Unknown: 01088B0C129618243048
                    IE: Unknown: 030101
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B050100108D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 3202606C
                    IE: Unknown: 851E04008F000F00FF03590062646830382D6170303800000000000001000027
                    IE: Unknown: 9606004096000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301003401
                    IE: Unknown: DD050040961404
          Cell 06 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"athens"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000044febcf18b
                    Extra: Last beacon: 4528ms ago
                    IE: Unknown: 0006617468656E73
                    IE: Unknown: 01088B0C129618243048
                    IE: Unknown: 030101
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B050100108D5B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 3202606C
                    IE: Unknown: 9606004096000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301003401
                    IE: Unknown: DD050040961405
          Cell 07 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:off
                    ESSID:"guest-net"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000044febda8eb
                    Extra: Last beacon: 4532ms ago
                    IE: Unknown: 000967756573742D6E6574
                    IE: Unknown: 01088B0C129618243048
                    IE: Unknown: 030101
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B050100108D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 3202606C
                    IE: Unknown: 851E04008F000F00FF03590062646830382D6170303800000000000001000027
                    IE: Unknown: 9606004096000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301003401
                    IE: Unknown: DD050040961404
          Cell 08 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"paris"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000044febe0bca
                    Extra: Last beacon: 4532ms ago
                    IE: Unknown: 00057061726973
                    IE: Unknown: 01088B0C129618243048
                    IE: Unknown: 030101
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B050100108D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 3202606C
                    IE: Unknown: 9606004096000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301003401
                    IE: Unknown: DD050040961404
          Cell 09 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"priv-psk"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000044fe4331de
                    Extra: Last beacon: 4244ms ago
                    IE: Unknown: 0008707269762D70736B
                    IE: Unknown: 01088B0C129618243048
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B050100178D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 3202606C
                    IE: Unknown: 851E02008F000F00FF03590062646830382D6170303900000000000001000027
                    IE: Unknown: 9606004096000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301003401
                    IE: Unknown: DD050040961404
          Cell 10 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"athens"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000044fe4310ee
                    Extra: Last beacon: 4240ms ago
                    IE: Unknown: 0006617468656E73
                    IE: Unknown: 01088B0C129618243048
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B050100178D5B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 3202606C
                    IE: Unknown: 9606004096000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301003401
                    IE: Unknown: DD050040961405
          Cell 11 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"athens"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000044ff107c67
                    Extra: Last beacon: 4252ms ago
                    IE: Unknown: 0006617468656E73
                    IE: Unknown: 01088B0C129618243048
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B050400118D5B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 3202606C
                    IE: Unknown: 9606004096000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301003401
                    IE: Unknown: DD050040961405
          Cell 12 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:off
                    ESSID:"guest-net"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000044ff114220
                    Extra: Last beacon: 4252ms ago
                    IE: Unknown: 000967756573742D6E6574
                    IE: Unknown: 01088B0C129618243048
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B050400118D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 3202606C
                    IE: Unknown: 851E06008F000F00FF03590062646830392D6170313000000000000004000027
                    IE: Unknown: 9606004096000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301003401
                    IE: Unknown: DD050040961404
          Cell 13 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:off
                    ESSID:"guest-net"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000044fe43b5c0
                    Extra: Last beacon: 4248ms ago
                    IE: Unknown: 000967756573742D6E6574
                    IE: Unknown: 01088B0C129618243048
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B050100178D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 3202606C
                    IE: Unknown: 851E02008F000F00FF03590062646830382D6170303900000000000001000027
                    IE: Unknown: 9606004096000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301003401
                    IE: Unknown: DD050040961404
          Cell 14 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"priv-psk"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000044ff10be33
                    Extra: Last beacon: 4248ms ago
                    IE: Unknown: 0008707269762D70736B
                    IE: Unknown: 01088B0C129618243048
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B050400118D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 3202606C
                    IE: Unknown: 851E06008F000F00FF03590062646830392D6170313000000000000004000027
                    IE: Unknown: 9606004096000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301003401
                    IE: Unknown: DD050040961404
          Cell 15 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"paris"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000044fe441f17
                    Extra: Last beacon: 4248ms ago
                    IE: Unknown: 00057061726973
                    IE: Unknown: 01088B0C129618243048
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B050100178D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 3202606C
                    IE: Unknown: 9606004096000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301003401
                    IE: Unknown: DD050040961404
          Cell 16 - Address: <MAC address removed>
                    Channel:44
                    Frequency:5.22 GHz (Channel 44)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"paris"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=00000044fe5f56aa
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 00057061726973
                    IE: Unknown: 01069824B048606C
                    IE: Unknown: 071255532024041134041864051884031895041E
                    IE: Unknown: 0B050100008D5B
                    IE: Unknown: 9606004096000200
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301003401
                    IE: Unknown: DD050040961404
          Cell 17 - Address: <MAC address removed>
                    Channel:44
                    Frequency:5.22 GHz (Channel 44)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"voice"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=00000044fe5e95ba
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 0005766F696365
                    IE: Unknown: 01069824B048606C
                    IE: Unknown: 071255532024041134041864051884031895041E
                    IE: Unknown: 0B050100008D5B
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (2) : 802.1x Proprietary
                    IE: Unknown: 851E03008F000F00FF03590062646830382D6170303900000000000001000026
                    IE: Unknown: 9606004096000200
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301003401
                    IE: Unknown: DD050040961405
          Cell 18 - Address: <MAC address removed>
                    Channel:44
                    Frequency:5.22 GHz (Channel 44)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"priv-psk"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=00000044fe5e6786
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 0008707269762D70736B
                    IE: Unknown: 01069824B048606C
                    IE: Unknown: 071255532024041134041864051884031895041E
                    IE: Unknown: 0B050100008D5B
                    IE: Unknown: 851E03008F000F00FF03590062646830382D6170303900000000000001000026
                    IE: Unknown: 9606004096000200
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301003401
                    IE: Unknown: DD050040961404
          Cell 19 - Address: <MAC address removed>
                    Channel:44
                    Frequency:5.22 GHz (Channel 44)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"athens"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=00000044fe5e33e1
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 0006617468656E73
                    IE: Unknown: 01069824B048606C
                    IE: Unknown: 071255532024041134041864051884031895041E
                    IE: Unknown: 0B050100008D5B
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 9606004096000200
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301003401
                    IE: Unknown: DD050040961405
          Cell 20 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"athens"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000044fe8960ee
                    Extra: Last beacon: 3732ms ago
                    IE: Unknown: 0006617468656E73
                    IE: Unknown: 01088B0C129618243048
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B050100108D5B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 3202606C
                    IE: Unknown: 9606004096000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301003401
                    IE: Unknown: DD050040961405
          Cell 21 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"paris"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000044fe8a55c5
                    Extra: Last beacon: 3744ms ago
                    IE: Unknown: 00057061726973
                    IE: Unknown: 01088B0C129618243048
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B050100108D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 3202606C
                    IE: Unknown: 9606004096000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301003401
                    IE: Unknown: DD050040961404
          Cell 22 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"priv-psk"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000044fe896ebd
                    Extra: Last beacon: 3744ms ago
                    IE: Unknown: 0008707269762D70736B
                    IE: Unknown: 01088B0C129618243048
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B050100108D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 3202606C
                    IE: Unknown: 851E04008F000F00FF03590062646830382D6170313000000000000001000027
                    IE: Unknown: 9606004096000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301003401
                    IE: Unknown: DD050040961404
          Cell 23 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"athens"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000014c47179226
                    Extra: Last beacon: 3732ms ago
                    IE: Unknown: 0006617468656E73
                    IE: Unknown: 01088B0C129618243048
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B0502001D8D5B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 3202606C
                    IE: Unknown: 9606004096000200
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301003401
                    IE: Unknown: DD050040961405
          Cell 24 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:off
                    ESSID:"guest-net"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000014c47182e5f
                    Extra: Last beacon: 3740ms ago
                    IE: Unknown: 000967756573742D6E6574
                    IE: Unknown: 01088B0C129618243048
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B0502001D8D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 3202606C
                    IE: Unknown: 851E01008F000F00FF03590062646830372D6170303900000000000002000027
                    IE: Unknown: 9606004096000200
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301003401
                    IE: Unknown: DD050040961404
          Cell 25 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"paris"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000014c4718940c
                    Extra: Last beacon: 3740ms ago
                    IE: Unknown: 00057061726973
                    IE: Unknown: 01088B0C129618243048
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B0502001D8D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 3202606C
                    IE: Unknown: 9606004096000200
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301003401
                    IE: Unknown: DD050040961404
          Cell 26 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"priv-psk"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000014c4717aad3
                    Extra: Last beacon: 3736ms ago
                    IE: Unknown: 0008707269762D70736B
                    IE: Unknown: 01088B0C129618243048
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B0502001D8D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 3202606C
                    IE: Unknown: 851E01008F000F00FF03590062646830372D6170303900000000000002000027
                    IE: Unknown: 9606004096000200
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301003401
                    IE: Unknown: DD050040961404
          Cell 27 - Address: <MAC address removed>
                    Channel:60
                    Frequency:5.3 GHz (Channel 60)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:off
                    ESSID:"guest-net"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=00000044feabc036
                    Extra: Last beacon: 2572ms ago
                    IE: Unknown: 000967756573742D6E6574
                    IE: Unknown: 01069824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071255532024041134041864051884031895041E
                    IE: Unknown: 0B0502000B8D5B
                    IE: Unknown: 851E04008F000F00FF03590062646830382D6170313000000000000002000026
                    IE: Unknown: 9606004096001100
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301003401
                    IE: Unknown: DD050040961404
          Cell 28 - Address: <MAC address removed>
                    Channel:60
                    Frequency:5.3 GHz (Channel 60)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"voice"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=00000044feaa3034
                    Extra: Last beacon: 2652ms ago
                    IE: Unknown: 0005766F696365
                    IE: Unknown: 01069824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071255532024041134041864051884031895041E
                    IE: Unknown: 0B0502000B8D5B
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (2) : 802.1x Proprietary
                    IE: Unknown: 851E04008F000F00FF03590062646830382D6170313000000000000002000026
                    IE: Unknown: 9606004096001100
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301003401
                    IE: Unknown: DD050040961405
          Cell 29 - Address: <MAC address removed>
                    Channel:60
                    Frequency:5.3 GHz (Channel 60)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"priv-psk"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=00000044feaa3036
                    Extra: Last beacon: 2640ms ago
                    IE: Unknown: 0008707269762D70736B
                    IE: Unknown: 01069824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071255532024041134041864051884031895041E
                    IE: Unknown: 0B0502000B8D5B
                    IE: Unknown: 851E04008F000F00FF03590062646830382D6170313000000000000002000026
                    IE: Unknown: 9606004096001100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301003401
                    IE: Unknown: DD050040961404
          Cell 30 - Address: <MAC address removed>
                    Channel:60
                    Frequency:5.3 GHz (Channel 60)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"athens"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=00000044feaa3034
                    Extra: Last beacon: 2624ms ago
                    IE: Unknown: 0006617468656E73
                    IE: Unknown: 01069824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071255532024041134041864051884031895041E
                    IE: Unknown: 0B0502000B8D5B
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 9606004096001100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301003401
                    IE: Unknown: DD050040961405
          Cell 31 - Address: <MAC address removed>
                    Channel:60
                    Frequency:5.3 GHz (Channel 60)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"paris"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=00000044feabc034
                    Extra: Last beacon: 2596ms ago
                    IE: Unknown: 00057061726973
                    IE: Unknown: 01069824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 071255532024041134041864051884031895041E
                    IE: Unknown: 0B0502000B8D5B
                    IE: Unknown: 9606004096001100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301003401
                    IE: Unknown: DD050040961404
          Cell 32 - Address: <MAC address removed>
                    Channel:157
                    Frequency:5.785 GHz (Channel 157)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"priv-psk"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=000000022e15082c
                    Extra: Last beacon: 548ms ago
                    IE: Unknown: 0008707269762D70736B
                    IE: Unknown: 01069824B048606C
                    IE: Unknown: 071255532024041134041864051884031895041E
                    IE: Unknown: 0B050100038D5B
                    IE: Unknown: 851E02008F000F00FF03590062646830382D6170303800000000000001000026
                    IE: Unknown: 9606004096000200
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301003401
                    IE: Unknown: DD050040961404
          Cell 33 - Address: <MAC address removed>
                    Channel:157
                    Frequency:5.785 GHz (Channel 157)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"athens"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=000000022e14d43f
                    Extra: Last beacon: 548ms ago
                    IE: Unknown: 0006617468656E73
                    IE: Unknown: 01069824B048606C
                    IE: Unknown: 071255532024041134041864051884031895041E
                    IE: Unknown: 0B050100038D5B
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 9606004096000200
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301003401
                    IE: Unknown: DD050040961405
          Cell 34 - Address: <MAC address removed>
                    Channel:157
                    Frequency:5.785 GHz (Channel 157)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:off
                    ESSID:"guest-net"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=000000022e15953d
                    Extra: Last beacon: 548ms ago
                    IE: Unknown: 000967756573742D6E6574
                    IE: Unknown: 01069824B048606C
                    IE: Unknown: 071255532024041134041864051884031895041E
                    IE: Unknown: 0B050100038D5B
                    IE: Unknown: 851E02008F000F00FF03590062646830382D6170303800000000000001000026
                    IE: Unknown: 9606004096000200
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301003401
                    IE: Unknown: DD050040961404
          Cell 35 - Address: <MAC address removed>
                    Channel:157
                    Frequency:5.785 GHz (Channel 157)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"voice"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=000000022e15362a
                    Extra: Last beacon: 548ms ago
                    IE: Unknown: 0005766F696365
                    IE: Unknown: 01069824B048606C
                    IE: Unknown: 071255532024041134041864051884031895041E
                    IE: Unknown: 0B050100038D5B
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (2) : 802.1x Proprietary
                    IE: Unknown: 851E02008F000F00FF03590062646830382D6170303800000000000001000026
                    IE: Unknown: 9606004096000200
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301003401
                    IE: Unknown: DD050040961405
          Cell 36 - Address: <MAC address removed>
                    Channel:157
                    Frequency:5.785 GHz (Channel 157)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"paris"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=000000022e165034
                    Extra: Last beacon: 524ms ago
                    IE: Unknown: 00057061726973
                    IE: Unknown: 01069824B048606C
                    IE: Unknown: 071255532024041134041864051884031895041E
                    IE: Unknown: 0B050100038D5B
                    IE: Unknown: 9606004096000200
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301003401
                    IE: Unknown: DD050040961404




***** resolv.conf *****


nameserver 127.0.0.1
search cpmc.columbia.edu


***** blacklist *****


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma


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


filename:       /lib/modules/3.5.0-43-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     746A0009D00AA48FECEA1EA
alias:          bcma:m04BFid0812rev18cl*
alias:          bcma:m04BFid0812rev17cl*
depends:        mac80211,bcma,brcmutil,cfg80211,cordic
intree:         Y
vermagic:       3.5.0-43-generic SMP mod_unload modversions 686 


filename:       /lib/modules/3.5.0-43-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     2C92CCB735C6654CB7E788B
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004331sv*sd*bc*sc*i*
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.5.0-43-generic SMP mod_unload modversions 686 


filename:       /lib/modules/3.5.0-43-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     0BDD8C54E0A4ECD78D4B6FC
depends:        
intree:         Y
vermagic:       3.5.0-43-generic SMP mod_unload modversions 686 




***** udev rules *****


# PCI device 0x10de:/sys/devices/pci0000:00/0000:00:0a.0 (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:15.0/0000:03:00.0/bcma0:0 (bcma-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:15.0/0000:03:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:15.0/0000:03:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"


***** dmesg *****


[  149.200127] bcma: Found chip with id 0xA8D8, rev 0x01 and package 0x0A
[  149.200167] bcma: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x22, class 0x0)
[  149.200199] bcma: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x17, class 0x0)
[  149.200257] bcma: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x0F, class 0x0)
[  149.235908] bcma: Bus registered
[  149.369945] brcmsmac bcma0:0: mfg 4bf core 812 rev 23 class 0 irq 16
[  149.589263] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  149.589290] ieee80211 phy0: brcms_ops_config: change power-save mode: false (implement)
[  149.591972] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  149.605229] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  158.504630] wlan0: authenticate with <MAC address removed>
[  158.556748] wlan0: send auth to <MAC address removed> (try 1/3)
[  158.559508] wlan0: authenticated
[  158.579769] wlan0: associate with <MAC address removed> (try 1/3)
[  158.581813] wlan0: RX AssocResp from <MAC address removed> (capab=0x1 status=0 aid=1)
[  158.582605] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: associated
[  158.582621] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[  158.582631] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[  158.582658] wlan0: associated
[  158.583222] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  162.866364] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)


****************** done ******************

```
I appreciate your help greatly!

---

### Post by varunendra on 2014-02-20
> **javier11 said:**
> It seems that the solution you first provided works but must be input into the terminal each time I boot the computer up newly.
Yup, I knew it would be temporary, it was just a quick test to confirm, and the reason of the problem is a (most probably failed) installation attempt of the sta driver "wl" (package name - "bcmwl-kernel-source"), as evident here -
> **javier11 said:**
> 
```

[**/etc/modprobe.d/blacklist-bcm43.conf**]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
**[COLOR="#FF0000"]blacklist brcmsmac[/COLOR]**
blacklist bcma
....
<snip>
....
***** udev rules *****
....
# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:15.0/0000:03:00.0 (**[COLOR="#FF0000"]wl[/COLOR]**)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="**[COLOR="#FF0000"]eth1[/COLOR]**"


# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:15.0/0000:03:00.0 (**[COLOR="#FF0000"]wl[/COLOR]**)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="**[COLOR="#FF0000"]eth2[/COLOR]**"

```
I appreciate your help greatly!

Fortunately, the fix is quite easy - just 'Purge' the sta driver if it is (or its remnants are) still installed. It seems that its installation probably failed, so we may also have to manually clean the mess it created.

Accordingly, please run the following commands and you should be all set -
```
sudo apt-get purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```
The first command will purge the wrong driver if it is still installed.
The second command will remove the blacklist file that is preventing the correct driver "brcmsmac" from loading automatically.
The last command will delete the udev rules file. It will be automatically regenerated when needed - with only relevant entries this time.

Reboot, and let us have your confirmation please.

---

### Post by javier11 on 2014-02-20
I can confirm that it now appears to be working normally.  Many thanks once again Varun.

---

### Post by varunendra on 2014-02-20
You're welcome! Enjoy Ubuntu and have fun with us here on the forums. :)

---

