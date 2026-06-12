---
title: "After 14.04.1 update; Intel wireless STILL totally hosed"
date: 2014-07-26
forum: Networking &amp; Wireless
---

### Post by CaptSaltyJack on 2014-07-26
I'm about to sell this ThinkPad and get a Dell XPS Developer Edition. Ubuntu just does not play nice with the ThinkPad S431's wifi. Look at this terrible speed (typical):

[img]http://www.speedtest.net/result/3649973914.png[/img]

Yet I do a speed test from my phone and get 45-50Mbps!

It's sporadic. Sometimes I do a test and get a result like this:

[img]http://www.speedtest.net/result/3649984041.png[/img]

Still, 32/10 is slow compared to what my phone gets (57/38).

Here's my lsmod output:

```

Module                  Size  Used by
acpi_call              12714  0 
ctr                    13049  3 
ccm                    17773  3 
btusb                  32412  0 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
snd_hda_codec_hdmi     46254  1 
snd_hda_codec_realtek    61438  1 
intel_rapl             18773  0 
x86_pkg_temp_thermal    14205  0 
snd_hda_intel          52355  3 
intel_powerclamp       14705  0 
arc4                   12608  2 
coretemp               13435  0 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
kvm_intel             143060  0 
snd_hwdep              13602  1 snd_hda_codec
iwldvm                232285  0 
kvm                   451511  1 kvm_intel
mac80211              630653  1 iwldvm
iwlwifi               169932  1 iwldvm
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
joydev                 17381  0 
mei_me                 18627  0 
serio_raw              13462  0 
rtsx_pci_ms            18151  0 
cfg80211              484040  3 iwlwifi,mac80211,iwldvm
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
memstick               16966  1 rtsx_pci_ms
mei                    82276  1 mei_me
lpc_ich                21080  0 
rfcomm                 69160  8 
bnep                   19624  2 
bluetooth             391196  22 bnep,btusb,rfcomm
thinkpad_acpi          81013  1 
nvram                  14411  1 thinkpad_acpi
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
snd                    69238  18 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,thinkpad_acpi,snd_seq_device,snd_seq_midi
soundcore              12680  1 snd
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
mac_hid                13205  0 
parport                42348  3 lp,ppdev,parport_pc
nls_iso8859_1          12713  1 
dm_crypt               23177  1 
rtsx_pci_sdmmc         23274  0 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
aesni_intel            55624  8 
aes_x86_64             17131  1 aesni_intel
i915                  783805  3 
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  4 ghash_clmulni_intel,aesni_intel,ablk_helper
i2c_algo_bit           13413  1 i915
psmouse               106678  0 
drm_kms_helper         53081  1 i915
ahci                   25819  3 
libahci                32560  1 ahci
drm                   303102  4 i915,drm_kms_helper
r8169                  67581  0 
rtsx_pci               45956  2 rtsx_pci_ms,rtsx_pci_sdmmc
mii                    13934  1 r8169
wmi                    19177  0 
video                  19476  1 i915

```

Wireless device is:
03:00.0 Network controller: Intel Corporation Centrino Wireless-N 2230 (rev c4)

Is there something I can do? Is there an updated driver I should be using?

---

### Post by CaptSaltyJack on 2014-07-27
I have a USB wifi adapter (Atheros chipset, a TP-Link TL-WN722N). Atheros AR9271.

When I do a speed test with the built-in Intel:

[img]http://www.speedtest.net/result/3650479849.png[/img]

When I plug in the Atheros USB wifi and run a test:

[img]http://www.speedtest.net/result/3650483978.png[/img]

---

### Post by varunendra on 2014-07-27
If you have already decided, and are about to sell this one, why bother with wifi troubleshooting?

But if you are just 'thinking', not decided, or if wish to troubleshoot it anyway, a technical detail about the wifi may be helpful. Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

Unplug the USB dongle and reboot before running the script, so that we have a clean report containing the details of the internal card only.

---

### Post by CaptSaltyJack on 2014-07-29
```


########## wireless info START ##########

##### release #####

Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty

##### kernel #####

Linux obsidian 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

##### lspci #####

03:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 2230 [8086:0888] (rev c4)
	Subsystem: Intel Corporation Centrino Wireless-N 2230 BGN [8086:4262]
	Kernel driver in use: iwlwifi
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
	Subsystem: Lenovo Device [17aa:5010]
	Kernel driver in use: r8169

##### lsusb #####

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 8087:07da Intel Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 0bda:5720 Realtek Semiconductor Corp. 
Bus 003 Device 003: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 102 Flash Drive / HEMA Flash Drive 2 GB / PNY Attache 4GB Stick
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA Card Info #####

##### rfkill #####

0: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

##### lsmod #####

iwldvm                232285  0 
mac80211              630653  1 iwldvm
iwlwifi               169932  1 iwldvm
cfg80211              484040  3 iwlwifi,mac80211,iwldvm

##### iw reg get #####

country US:
	(2402 - 2472 @ 40), (3, 27)
	(5170 - 5250 @ 40), (3, 17)
	(5250 - 5330 @ 40), (3, 20), DFS
	(5490 - 5600 @ 40), (3, 20), DFS
	(5650 - 5710 @ 40), (3, 20), DFS
	(5735 - 5835 @ 40), (3, 30)
	(57240 - 63720 @ 2160), (N/A, 40)

##### interfaces #####

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

##### iwconfig #####

wlan0     IEEE 802.11bgn  ESSID:"S is for Studio"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC address removed>   
          Bit Rate=130 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-33 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:152   Missed beacon:0

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.11.1    0.0.0.0         UG    0      0        0 wlan0
192.168.11.0    0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #####

nameserver 127.0.1.1

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: wlan0  [S is for Studio] ---------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           65 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Guesty McGuesterson: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2
    *S is for Studio:Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 86 WPA2
    red dragon:      Infra, <MAC address removed>, Freq 2422 MHz, Rate 54 Mb/s, Strength 50 WPA2
    DIRECT-roku-823-5AA25E: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 45 WPA2
    belkin54g:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    Jameron:         Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    magalicious:     Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA
    freydapotato:    Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA2
    HDN:             Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 42

  IPv4 Settings:
    Address:         192.168.11.108
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.11.1

    DNS:             192.168.11.1

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### iwlist #####

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-35 dBm  
                    Encryption key:on
                    ESSID:"S is for Studio"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002fc1d1f130
                    Extra: Last beacon: 216ms ago
                    IE: Unknown: 000F5320697320666F722053747564696F
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 200100
                    IE: Unknown: 23021900
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AAD1917FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081500000000000000000000000000000000000000
                    IE: Unknown: 7F080000000000000040
                    IE: Unknown: DD0B0017F20100010100000007
                    IE: Unknown: DD0700039301780320
                    IE: Unknown: DD0E0017F20700010106907240245079
                    IE: Unknown: DD090010180204001C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 46050200010000
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"belkin54g"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000024f082cc8
                    Extra: Last beacon: 16ms ago
                    IE: Unknown: 000962656C6B696E353467
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD970050F204104A0001101044000102103B00010210470010E7FE1B918CD5031098DD00173FEF286A1021000642656C6B696E1023000F463544373233302D342D763830303010240007575053303030311042000E32303734373732333030313737351054000800060050F204000110110020463544373233302D340000000000000000000000000000000000000000000000100800020084
                    IE: Unknown: DD090010180201F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:on
                    ESSID:"Guesty McGuesterson"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002fc2b0c3a1
                    Extra: Last beacon: 16ms ago
                    IE: Unknown: 0013477565737479204D6347756573746572736F6E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 200100
                    IE: Unknown: 23021900
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AAD1917FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081500000000000000000000000000000000000000
                    IE: Unknown: 7F080000000000000040
                    IE: Unknown: DD0700039301780208
                    IE: Unknown: DD0E0017F20700010106907240245079
                    IE: Unknown: DD090010180200001C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 46050200010000
          Cell 04 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"magalicious"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000007e93c67
                    Extra: Last beacon: 14492ms ago
                    IE: Unknown: 000B6D6167616C6963696F7573
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030106
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 3204B048606C
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4C101BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406001B00000000000000000000000000000000000000
                    IE: Unknown: 3D1606001B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD9E0050F204104A0001101044000102103B00010310470010000000000000100000001CAFF7CFE78510210006442D4C696E6B1023000D442D4C696E6B20526F75746572102400074449522D363031104200046E6F6E651054000800060050F204000110110016442D4C696E6B2053797374656D73204449522D363031100800020086103C000103104900140024E26002000101600000020001600100020001
          Cell 05 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:off
                    ESSID:"HDN"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000118db3e4181
                    Extra: Last beacon: 92ms ago
                    IE: Unknown: 000348444E
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: Unknown: DD180050F202010100000394000027A400004243000062320000
          Cell 06 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000118da61f5b6
                    Extra: Last beacon: 14528ms ago
                    IE: Unknown: 00080000000000000000
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F202010100000394000027A400004243000062320000

##### iwlist channel #####

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
          Current Frequency:2.437 GHz (Channel 6)

##### modinfo #####

##### modules #####

lp
rtc

##### blacklist #####

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

[/etc/modprobe.d/fbdev-blacklist.conf]
blacklist arkfb
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist gx1fb
blacklist gxfb
blacklist kyrofb
blacklist matroxfb_base
blacklist mb862xxfb
blacklist neofb
blacklist nvidiafb
blacklist pm2fb
blacklist pm3fb
blacklist s3fb
blacklist savagefb
blacklist sisfb
blacklist tdfxfb
blacklist tridentfb
blacklist viafb
blacklist vt8623fb

##### udev rules #####

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x0888 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# USB device 0x:0x (ath9k_htc)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #####

[    9.371895] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   23.090557] iwlwifi 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[   23.090689] iwlwifi 0000:03:00.0: irq 46 for MSI/MSI-X
[   23.095943] iwlwifi 0000:03:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
[   23.120016] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   23.120020] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   23.120022] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   23.120026] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Wireless-N 2230 BGN, REV=0xC8
[   23.120571] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   23.146436] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   23.582883] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   23.591146] iwlwifi 0000:03:00.0: Radio type=0x2-0x0-0x0
[   23.834360] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   23.841990] iwlwifi 0000:03:00.0: Radio type=0x2-0x0-0x0
[   23.910630] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.910995] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.536931] wlan0: authenticate with <MAC address removed>
[   24.542548] wlan0: send auth to <MAC address removed> (try 1/3)
[   24.550306] wlan0: authenticated
[   24.551622] wlan0: associate with <MAC address removed> (try 1/3)
[   24.555561] wlan0: RX AssocResp from <MAC address removed> (capab=0x1411 status=0 aid=4)
[   24.574990] wlan0: associated
[   24.575021] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   24.651538] wlan0: Limiting TX power to 30 (30 - 0) dBm as advertised by <MAC address removed>

########## wireless info END ############

```

---

### Post by varunendra on 2014-07-30
> **CaptSaltyJack said:**
> ```
##### iwconfig #####

wlan0     IEEE 802.11bgn  ESSID:"**S is for Studio**"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC address removed>   
          Bit Rate=130 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          **Power Management:[COLOR="#FF0000"]on[/COLOR]**
          Link Quality=70/70  Signal level=-33 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:152   Missed beacon:0

```

Try -
```
sudo iwconfig wlan0 power off
```
Then check -
```
iwconfig
```
Is Power Management "off" now? If yes, wait a couple minutes and test the speed. Is it better? Reboot and check 'iwconfig' again to make sure it remains "off".

If the power management automatically turns "on" again, try disabling the default power management script by creating a blank "wireless" file in **/etc/pm/power.d/** directory -
```
sudo touch /etc/pm/power.d/wireless
```
Usually there's no need to put anything in it or make it executable. But if it fails to keep the power management off, we can put the following contents in it -
```
#!/bin/bash
/sbin/iwconfig wlan0 power off
```
..and make it executable -
```
sudo chmod +x /etc/pm/power.d/wireless
```

By the way, some older drivers and card didn't like blank spaces in an AP's name (SSID). I don't think it should cause speed issues (only connectivity issues), but you may try changing it to something that doesn't contain these - All CAPS, blank spaces, special characters. These should be good - Alphabets (not All CAPS), numbers, hyphen (-) and underscore (_).

Another recommendation is to try channel 1 or 11 instead of current '6'. Sometimes helps improving performance.

You may also try some driver parameters with iwlwifi as suggested here (the part about 'iwlmvm' doesn't apply to your case) : [http://ubuntuforums.org/showpost.php?p=12943350](http://ubuntuforums.org/showpost.php?p=12943350)

---

### Post by connors2647 on 2014-12-08
Thank you. Power Off Helped my performace issues on Lenovo s431, Ubuntu 14.04 LTS

---

### Post by darkshadow on 2014-12-14
I had a problem with my Intel Wireless 5100 with the last couple Ubuntu versions giving me slow wireless speed. But I just found a article online that explained it and fixed it for me. In real numbers my LAN scp transfers went from 3-4 megabytes per second up to 11.5-12 megabytes. After using the following modules options

options iwlwifi 11n_disable=8
options iwlwifi bt_coex_active=0


Full info better explained here.
[http://bernaerts.dyndns.org/linux/74-ubuntu/322-ubuntu-trusty-intel-centrino-6235-slow](http://bernaerts.dyndns.org/linux/74-ubuntu/322-ubuntu-trusty-intel-centrino-6235-slow)

---

### Post by danbebber on 2015-03-29
The Intel Centrino 2230 card has a lot of problems, see this thread [https://communities.intel.com/thread/38676](https://communities.intel.com/thread/38676)
I have seen numerous solutions posted for Linux but the one that worked for me is simply to disable Bluetooth. Slightly annoying but now my wifi is fast again (not as fast as my Macbook Air, but pretty fast)
This is Intel's fault, nothing to do with Linux.

---

### Post by paulgj on 2015-12-04
Thank you for that link! My ThinkPad T500 with Intel 5100 went from 50Mbps to 120Mbps :D

---

### Post by CaptSaltyJack on 2016-03-21
> **paulgj said:**
> Thank you for that link! My ThinkPad T500 with Intel 5100 went from 50Mbps to 120Mbps :D

Which link are you referring to? If it's the forum thread right above, which page did you find the solution on?

---

### Post by jeremy31 on 2016-03-21
I would guess setting the options to 11n_disable=8 and bt_coex_active=0
```
echo "options iwlwifi 11n_disable=8 bt_coex_active=0" | sudo tee /etc/modprobe.d/iwlopt.conf
```

Reboot and test

---

