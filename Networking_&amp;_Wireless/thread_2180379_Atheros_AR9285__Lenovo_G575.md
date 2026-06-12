---
title: "Atheros AR9285 / Lenovo G575"
date: 2013-10-12
forum: Networking &amp; Wireless
---

### Post by XtbA3cC on 2013-10-12
I know there is many theards in the same title, but i think my problem can be so complicated.

I got Lenovo G575, and I've installed ubuntu one week ago. Until that my wifi doesn't work. I was searching on google some solves, and I use it, and now i think that was bad idea. So, on my laptop wifi is disconnecting, but on my tablet got nice 2 wifis signals. 

```
hogan@hogan:~$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
hogan@hogan:~$ lsmod
Module                  Size  Used by
rfcomm                 47864  0 
bnep                   18258  2 
snd_hda_codec_conexant    62464  1 
joydev                 17613  0 
bluetooth             247024  10 rfcomm,bnep
uvcvideo               82214  0 
parport_pc             28284  0 
ppdev                  17113  0 
videobuf2_core         40785  1 uvcvideo
videodev              130053  2 uvcvideo,videobuf2_core
snd_hda_intel          44339  3 
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
snd_hda_codec         141716  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm               102477  2 snd_hda_intel,snd_hda_codec
radeon                960918  3 
arc4                   12573  2 
snd_seq_midi           13324  0 
snd_rawmidi            30417  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
ath9k                 151796  0 
snd_seq                61930  2 snd_seq_midi,snd_seq_midi_event
mac80211              630977  1 ath9k
snd_timer              29989  2 snd_pcm,snd_seq
ttm                    84051  1 radeon
kvm_amd                60205  0 
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
kvm                   455932  1 kvm_amd
drm_kms_helper         49597  1 radeon
snd                    69533  15 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ath9k_common           14053  1 ath9k
ideapad_laptop         18596  0 
ath9k_hw              422432  2 ath9k,ath9k_common
drm                   287564  5 radeon,ttm,drm_kms_helper
soundcore              12680  1 snd
k10temp                13173  0 
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13564  1 radeon
ath                    24123  3 ath9k,ath9k_common,ath9k_hw
sp5100_tco             13870  0 
psmouse                97873  0 
i2c_piix4              13459  0 
sparse_keymap          13890  1 ideapad_laptop
serio_raw              13215  0 
microcode              23017  0 
mac_hid                13253  0 
video                  19652  0 
cfg80211              525244  3 ath9k,mac80211,ath
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
hid_generic            12540  0 
usbhid                 47346  0 
hid                   105549  2 hid_generic,usbhid
atl1c                  41885  0 
ahci                   25879  2 
libahci                31606  1 ahci
hogan@hogan:~$ clear


hogan@hogan:~$ sudo lshw -C network
[sudo] password for hogan: 
  *-network               
       description: Ethernet interface
       product: AR8152 v2.0 Fast Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: c1
       serial: dc:0e:a1:7b:52:ac
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.1-NAPI latency=0 link=no multicast=yes port=twisted pair
       resources: irq:41 memory:f0100000-f013ffff ioport:2000(size=128)
  *-network
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 9c:b7:0d:1d:ed:45
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.8.0-29-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f0000000-f000ffff
hogan@hogan:~$ dmesg | grep iwl
hogan@hogan:~$ rfkill list all
0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
hogan@hogan:~$ dmesg | grep iwl
hogan@hogan:~$ lspci -nn | grep 0280
03:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
hogan@hogan:~$ lspci -nn | grep 0280
03:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
hogan@hogan:~$ sudo modprobe ath9k
[sudo] password for hogan: 
WARNING: /etc/modprobe.d/ath9k.conf line 1: ignoring bad line starting with 'option'
hogan@hogan:~$ dmesg | grep ath
[    1.890997] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 38550890b1fce75cc801d8fb942703db919b9386'
[   11.643925] ath: phy0: ASPM enabled: 0x42
[   11.643935] ath: EEPROM regdomain: 0x65
[   11.643938] ath: EEPROM indicates we should expect a direct regpair map
[   11.643944] ath: Country alpha2 being used: 00
[   11.643946] ath: Regpair used: 0x65
[   18.100178] type=1400 audit(1381604378.695:22): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=939 comm="apparmor_parser"
[   18.100963] type=1400 audit(1381604378.695:23): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=939 comm="apparmor_parser"
[   59.861751] type=1400 audit(1381604420.467:31): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=1817 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[   67.837547] ath9k 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   67.837553] ath9k 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   72.374591] ath9k 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   72.374603] ath9k 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 1165.667257] ath9k 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 1165.667268] ath9k 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 1187.684328] ath9k 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 1187.684346] ath9k 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 1195.676763] ath9k 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 1195.676770] ath9k 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 1258.042246] ath9k 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 1258.042252] ath9k 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 1338.697893] ath9k 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 1338.697904] ath9k 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 1787.612807] ath9k 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 1787.612814] ath9k 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 1932.275646] ath9k 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 1932.275665] ath9k 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 1935.687139] ath9k 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 1935.687157] ath9k 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 2023.901818] ath: phy0: ASPM enabled: 0x42
[ 2350.583960] ath9k 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 2350.583967] ath9k 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
hogan@hogan:~$ clear


hogan@hogan:~$ lspci -nn | grep 0280
03:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
hogan@hogan:~$ dmesg | grep iwl
hogan@hogan:~$ rfkill list all
0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
hogan@hogan:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: AR8152 v2.0 Fast Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: c1
       serial: dc:0e:a1:7b:52:ac
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.1-NAPI latency=0 link=no multicast=yes port=twisted pair
       resources: irq:41 memory:f0100000-f013ffff ioport:2000(size=128)
  *-network
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 9c:b7:0d:1d:ed:45
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.8.0-29-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f0000000-f000ffff
```

---

### Post by XtbA3cC on 2013-10-13
anybody could help me? today i saw that i cannot disabled my wifi by FN + F5

---

### Post by wildmanne39 on 2013-10-13
Hi, please copy the contents of:
```
gksudo gedit /etc/modprobe.d/ath9k.conf
```
and paste it here.

Also in your router enable ```
HT as WMM/QoS is not supported by the AP
VHT as WMM/QoS is not supported by the AP
```
Thanks

---

### Post by XtbA3cC on 2013-10-13
options ath9k nohwcrypt=1

---

### Post by wildmanne39 on 2013-10-13
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by XtbA3cC on 2013-10-14
```
*************** info trace ***************

***** uname -a *****

Linux hogan 3.8.0-29-generic #42~precise1-Ubuntu SMP Wed Aug 14 16:19:23 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise

***** lspci *****

02:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
    Subsystem: Lenovo Device [17aa:397b]
    Kernel driver in use: atl1c
--
03:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: Lenovo Device [17aa:30a1]
    Kernel driver in use: ath9k

***** lsusb *****

Bus 001 Device 003: ID 5986:0292 Acer, Inc 
Bus 003 Device 002: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11bgn  ESSID:"noclegikrakow0"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: <MAC address removed>   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=55/70  Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:36  Invalid misc:2   Missed beacon:0


***** rfkill *****

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** lsmod *****

ath9k                 151796  0 
mac80211              630977  1 ath9k
ath9k_common           14053  1 ath9k
ath9k_hw              422432  2 ath9k,ath9k_common
ath                    24123  3 ath9k,ath9k_common,ath9k_hw
cfg80211              525244  3 ath9k,mac80211,ath

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: wlan0  [noclegikrakow0] ----------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
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
    noclegikrakow:   Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    *noclegikrakow0: Infra, <MAC address removed>, Freq 2442 MHz, Rate 54 Mb/s, Strength 68 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.104
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1
    DNS:             192.204.152.34


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
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

no-auto-default=<MAC address removed>,

[ifupdown]
managed=false

***** interfaces *****

auto lo
iface lo inet loopback


***** iwlist *****

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:on
                    ESSID:"noclegikrakow0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000a6e3bb181
                    Extra: Last beacon: 1448ms ago
                    IE: Unknown: 000E6E6F636C6567696B72616B6F7730
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030107
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"noclegikrakow"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000009aeef0072
                    Extra: Last beacon: 36ms ago
                    IE: Unknown: 000D6E6F636C6567696B72616B6F77
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD0900037F01010008FF7F
                    IE: Unknown: DD1A00037F03010000000023CDCE4EA30623CDCE4EA364002C010808


***** resolv.conf *****

nameserver 127.0.0.1

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

filename:       /lib/modules/3.8.0-29-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     74064173F9189761845D970
alias:          platform:qca955x_wmac
alias:          platform:ar934x_wmac
alias:          platform:ar933x_wmac
alias:          platform:ath9k
alias:          pci:v0000168Cd00000036sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000037sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000033sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000030sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Esv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
depends:        ath9k_hw,ath9k_common,mac80211,ath,cfg80211
intree:         Y
vermagic:       3.8.0-29-generic SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           enable_diversity:Enable Antenna diversity for AR9565 (int)

filename:       /lib/modules/3.8.0-29-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     3D03F9DDA976A5AB5EAA737
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.8.0-29-generic SMP mod_unload modversions 

filename:       /lib/modules/3.8.0-29-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     083DD7A079F4041AE50FFC4
depends:        ath
intree:         Y
vermagic:       3.8.0-29-generic SMP mod_unload modversions 

filename:       /lib/modules/3.8.0-29-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     5627B8DA4AC105006A960BE
depends:        cfg80211
intree:         Y
vermagic:       3.8.0-29-generic SMP mod_unload modversions 


***** udev rules *****

# PCI device 0x1969:/sys/devices/pci0000:00/0000:00:15.0/0000:02:00.0 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:15.1/0000:03:00.0 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[   12.018219] ath: phy0: ASPM enabled: 0x42
[   12.018230] ath: EEPROM regdomain: 0x65
[   12.018233] ath: EEPROM indicates we should expect a direct regpair map
[   12.018239] ath: Country alpha2 being used: 00
[   12.018241] ath: Regpair used: 0x65
[   18.724089] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.726496] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  162.665807] wlan0: authenticate with <MAC address removed>
[  162.677866] wlan0: direct probe to <MAC address removed> (try 1/3)
[  162.880257] wlan0: send auth to <MAC address removed> (try 2/3)
[  163.084138] wlan0: send auth to <MAC address removed> (try 3/3)
[  163.091424] wlan0: authenticated
[  163.091876] ath9k 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  163.091888] ath9k 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  163.092828] wlan0: associate with <MAC address removed> (try 1/3)
[  163.098269] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=11)
[  163.098889] wlan0: associated
[  163.099200] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  166.928118] wlan0: authenticate with <MAC address removed>
[  166.934294] wlan0: send auth to <MAC address removed> (try 1/3)
[  166.943626] wlan0: authenticated
[  166.944237] ath9k 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  166.944248] ath9k 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  166.947874] wlan0: associate with <MAC address removed> (try 1/3)
[  167.151137] wlan0: associate with <MAC address removed> (try 2/3)
[  167.158733] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=12)
[  167.159394] wlan0: associated
[  170.923406] wlan0: authenticate with <MAC address removed>
[  170.930100] wlan0: send auth to <MAC address removed> (try 1/3)
[  171.134115] wlan0: send auth to <MAC address removed> (try 2/3)
[  171.338078] wlan0: send auth to <MAC address removed> (try 3/3)
[  171.542000] wlan0: authentication with <MAC address removed> timed out
[  182.352097] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  189.354647] wlan0: authenticate with <MAC address removed>
[  189.360503] wlan0: send auth to <MAC address removed> (try 1/3)
[  189.561375] wlan0: send auth to <MAC address removed> (try 2/3)
[  189.765358] wlan0: send auth to <MAC address removed> (try 3/3)
[  189.969267] wlan0: authentication with <MAC address removed> timed out
[  365.133877] wlan0: authenticate with <MAC address removed>
[  365.139572] wlan0: send auth to <MAC address removed> (try 1/3)
[  365.145718] wlan0: authenticated
[  365.146049] ath9k 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  365.146055] ath9k 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  365.148051] wlan0: associate with <MAC address removed> (try 1/3)
[  365.155793] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=12)
[  365.156166] wlan0: associated
[  365.156447] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1101.349388] wlan0: authenticate with <MAC address removed>
[ 1101.353014] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1101.553822] wlan0: send auth to <MAC address removed> (try 2/3)
[ 1101.757769] wlan0: send auth to <MAC address removed> (try 3/3)
[ 1101.765709] wlan0: authenticated
[ 1101.766327] ath9k 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 1101.766341] ath9k 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 1101.769829] wlan0: associate with <MAC address removed> (try 1/3)
[ 1101.973790] wlan0: associate with <MAC address removed> (try 2/3)
[ 1102.177725] wlan0: associate with <MAC address removed> (try 3/3)
[ 1102.181602] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=14)
[ 1102.182415] wlan0: associated
[ 1984.533809] wlan0: authenticate with <MAC address removed>
[ 1984.534900] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1984.738146] wlan0: send auth to <MAC address removed> (try 2/3)
[ 1984.942111] wlan0: send auth to <MAC address removed> (try 3/3)
[ 1985.146161] wlan0: authentication with <MAC address removed> timed out
[ 1999.507207] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2002.816668] wlan0: authenticate with <MAC address removed>
[ 2002.825647] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2002.829633] wlan0: authenticated
[ 2002.829964] ath9k 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 2002.829970] ath9k 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 2002.833607] wlan0: associate with <MAC address removed> (try 1/3)
[ 2002.836335] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=14)
[ 2002.836664] wlan0: associated
[ 2002.836724] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2013.120119] wlan0: authenticate with <MAC address removed>
[ 2013.126092] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2013.326856] wlan0: send auth to <MAC address removed> (try 2/3)
[ 2013.530710] wlan0: send auth to <MAC address removed> (try 3/3)
[ 2013.734666] wlan0: authentication with <MAC address removed> timed out
[ 2019.620952] wlan0: authenticate with <MAC address removed>
[ 2019.626869] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2019.827833] wlan0: send auth to <MAC address removed> (try 2/3)
[ 2019.832157] wlan0: authenticated
[ 2019.832640] ath9k 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 2019.832651] ath9k 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 2019.835990] wlan0: associate with <MAC address removed> (try 1/3)
[ 2019.838822] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=14)
[ 2019.839457] wlan0: associated
[ 2028.121437] wlan0: authenticate with <MAC address removed>
[ 2028.124904] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2028.127574] wlan0: authenticated
[ 2028.127848] ath9k 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 2028.127854] ath9k 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 2028.130289] wlan0: associate with <MAC address removed> (try 1/3)
[ 2028.145357] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=14)
[ 2028.146333] wlan0: associated
[ 2050.105166] wlan0: authenticate with <MAC address removed>
[ 2050.111366] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2050.118078] wlan0: authenticated
[ 2050.119037] ath9k 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 2050.119112] ath9k 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 2050.123157] wlan0: associate with <MAC address removed> (try 1/3)
[ 2050.132655] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=14)
[ 2050.133325] wlan0: associated
[ 2052.100619] wlan0: authenticate with <MAC address removed>
[ 2052.106901] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2052.307629] wlan0: send auth to <MAC address removed> (try 2/3)
[ 2052.511664] wlan0: send auth to <MAC address removed> (try 3/3)
[ 2052.715791] wlan0: authentication with <MAC address removed> timed out
[ 2064.506295] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2076.269009] wlan0: authenticate with <MAC address removed>
[ 2076.269155] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2076.469516] wlan0: send auth to <MAC address removed> (try 2/3)
[ 2076.473667] wlan0: authenticated
[ 2076.474166] ath9k 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 2076.474178] ath9k 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 2076.477783] wlan0: associate with <MAC address removed> (try 1/3)
[ 2076.485268] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=14)
[ 2076.485945] wlan0: associated
[ 2076.486047] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2088.117602] wlan0: authenticate with <MAC address removed>
[ 2088.123454] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2088.324416] wlan0: send auth to <MAC address removed> (try 2/3)
[ 2088.528386] wlan0: send auth to <MAC address removed> (try 3/3)
[ 2088.732556] wlan0: authentication with <MAC address removed> timed out
[ 2102.518555] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2114.267899] wlan0: authenticate with <MAC address removed>
[ 2114.275404] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2114.280385] wlan0: authenticated
[ 2114.280853] ath9k 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 2114.280864] ath9k 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 2114.284418] wlan0: associate with <MAC address removed> (try 1/3)
[ 2114.290714] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=14)
[ 2114.291045] wlan0: associated
[ 2114.291103] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2268.130651] wlan0: authenticate with <MAC address removed>
[ 2268.134090] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2268.136316] wlan0: authenticated
[ 2268.137158] ath9k 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 2268.137176] ath9k 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 2268.139199] wlan0: associate with <MAC address removed> (try 1/3)
[ 2268.142160] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=14)
[ 2268.143776] wlan0: associated

****************** done ******************
```

---

### Post by XtbA3cC on 2013-10-14
Sorry for pasting it here, but i cannnot attach this file, and I was scared of my Internet connection down

---

### Post by wildmanne39 on 2013-10-14
Did you enable this in your router? ```
HT as WMM/QoS is not supported by the AP
```

Also set encryption to just wpa2 AES if you have that option in your router.

Make your wireless settings in network manager match the screenshots especially ipv6.
Thanks

---

### Post by wildmanne39 on 2013-10-14
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by XtbA3cC on 2013-10-15
It doesn't work :/ I cannot change configuration on router, because it's not mine. What I can do? Maybe I change something in configs, and it crash? Is it better when I reinstall Ubuntu?

---

### Post by wildmanne39 on 2013-10-15
Are you saying you try to change the configuration of ubuntu and it does crash or it just might crash?

Did you do this? > Make your wireless settings in network manager match the screenshots especially ipv6.
Thanks

---

### Post by XtbA3cC on 2013-10-15
it just night. wifi stopped Work since I just install ubuntu. i've change ipv6 config

---

### Post by wildmanne39 on 2013-10-15
Post a new wireless file so we can see if the changes you made were saved.
Thanks

---

### Post by XtbA3cC on 2013-10-15
i've made changes before i wrote on this forum

---

### Post by wildmanne39 on 2013-10-15
Please attach screenshots of your wireless network settings in network manager like I did in post 8 and please run the script again and post the  new wireless information file.
Thanks

---

