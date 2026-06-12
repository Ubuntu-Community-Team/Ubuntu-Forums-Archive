---
title: "Slow wifi start-up"
date: 2013-12-21
forum: Networking &amp; Wireless
---

### Post by Hodevah on 2013-12-21
Hi. I have done a search throughout the forum down to about 15 or so pages. None of the info that I have read pertains to my current situation. Have been using Ubuntu for about 6-7 months so far along with a few other distros that I have installed on HDD. I had the same slow wifi start-up problem with Antergos which was happily resolved. 

However, due to the nature of the various distros having different command structures in using Terminal has me looking into different filesystem folders. Not all of which are the same from one distro to another. 

Current configuration, which includes 13.10 Ubuntu - 64 bit, is as follows. 

> /dev/sda1: OpenSUSE 13.1 (x86_64):SuSE:linux
/dev/sda5::Arch:linux
/dev/sda6:Manjaro Linux (0.8.8):ManjaroLinux:linux
/dev/sda7:Linux Mint 15 Olivia (15):LinuxMint:linux

**PROBLEM:**

Wifi is slow to start. Nothing else starts up at boot other than ufw. 
It can take approx 2 minuites or so for it to start and connect to the network. 
This never happened before. Connection at boot was instantaneous about 1-2 weeks ago. 

```
frankenstein@frankenstein-desktop:~$ cat /etc/os-release
NAME="Ubuntu"
VERSION="13.10, Saucy Salamander"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 13.10"

```

```
frankenstein@frankenstein-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:22:4d:82:e5:5d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:eff00000-eff20000 

eth1      Link encap:Ethernet  HWaddr 00:22:4d:82:e5:6c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Memory:efd20000-efd40000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:897 errors:0 dropped:0 overruns:0 frame:0
          TX packets:897 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:78015 (78.0 KB)  TX bytes:78015 (78.0 KB)

wlan0     Link encap:Ethernet  HWaddr 94:db:c9:50:d4:94  
          inet addr:192.168.1.68  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::96db:c9ff:fe50:d494/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17480 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13011 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13768661 (13.7 MB)  TX bytes:2052690 (2.0 MB)

frankenstein@frankenstein-desktop:~$ 

```

```
frankenstein@frankenstein-desktop:~$ iwconfig
wlan0     IEEE 802.11bgn  ESSID:"TELUS4045"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: FC:F5:28:AD:BF:05   
          Bit Rate=52 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=49/70  Signal level=-61 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2090  Invalid misc:47   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

```

```
frankenstein@frankenstein-desktop:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0  [TELUS4045] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800usb
  State:             connected
  Default:           yes
  HW Address:        94:DB:C9:50:D4:94

  Capabilities:
    Speed:           43 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Elysian Airport: Infra, 88:1F:A1:33:C0:D8, Freq 2437 MHz, Rate 54 Mb/s, Strength 89 WPA2
    *TELUS4045:      Infra, FC:F5:28:AD:BF:05, Freq 2437 MHz, Rate 54 Mb/s, Strength 63 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.68
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254


- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        00:22:4D:82:E5:6C

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        00:22:4D:82:E5:5D

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

```

```
frankenstein@frankenstein-desktop:~$ lsmod
Module                  Size  Used by
parport_pc             31981  0 
ppdev                  17391  0 
bnep                   18893  2 
rfcomm                 53664  12 
binfmt_misc            13140  1 
x86_pkg_temp_thermal    13810  0 
intel_powerclamp       14239  0 
coretemp               13195  0 
arc4                   12536  2 
kvm_intel             128218  0 
ip6t_REJECT            12826  1 
xt_hl                  12465  6 
ip6t_rt                13259  3 
nf_conntrack_ipv6      18450  7 
snd_hda_codec_hdmi     40373  1 
kvm                   364766  1 kvm_intel
nf_defrag_ipv6         26064  1 nf_conntrack_ipv6
ipt_REJECT             12485  1 
xt_LOG                 17446  10 
crc32_pclmul           12967  0 
aesni_intel            18156  1 
aes_i586               16995  1 aesni_intel
xt_limit               12541  13 
rt2800usb              22485  0 
xt_tcpudp              12756  18 
xt_addrtype            12563  4 
rt2x00usb              20041  1 rt2800usb
xts                    12749  1 aesni_intel
rt2800lib              70115  1 rt2800usb
rt2x00lib              48854  3 rt2x00usb,rt2800lib,rt2800usb
nf_conntrack_ipv4      14492  7 
lrw                    13057  1 aesni_intel
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
xt_conntrack           12664  14 
gf128mul               14503  2 lrw,xts
mac80211              513247  3 rt2x00lib,rt2x00usb,rt2800lib
mxm_wmi                12893  0 
ablk_helper            13357  1 aesni_intel
cryptd                 15577  1 ablk_helper
ip6table_filter        12711  1 
ip6_tables             17819  1 ip6table_filter
cfg80211              401436  2 mac80211,rt2x00lib
nf_conntrack_netbios_ns    12585  0 
nf_conntrack_broadcast    12541  1 nf_conntrack_netbios_ns
nf_nat_ftp             12645  0 
nf_nat                 25588  1 nf_nat_ftp
nf_conntrack_ftp       14056  1 nf_nat_ftp
crc_ccitt              12627  1 rt2800lib
nf_conntrack           82912  8 nf_nat_ftp,nf_conntrack_netbios_ns,nf_nat,xt_conntrack,nf_conntrack_broadcast,nf_conntrack_ftp,nf_conntrack_ipv4,nf_conntrack_ipv6
joydev                 17097  0 
iptable_filter         12706  1 
ip_tables              17987  1 iptable_filter
x_tables               22067  13 ip6table_filter,xt_hl,ip_tables,xt_tcpudp,xt_limit,xt_conntrack,xt_LOG,iptable_filter,ip6t_rt,ipt_REJECT,ip6_tables,xt_addrtype,ip6t_REJECT
snd_hda_codec_realtek    45592  1 
radeon               1307301  3 
btusb                  23443  0 
bluetooth             323622  22 bnep,btusb,rfcomm
ttm                    71886  1 radeon
snd_hda_intel          42658  7 
drm_kms_helper         46867  1 radeon
snd_hda_codec         164003  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
drm                   242354  5 ttm,drm_kms_helper,radeon
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                89488  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
i2c_algo_bit           13197  1 radeon
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25094  1 snd_seq_midi
microcode              18830  0 
psmouse                90642  0 
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
serio_raw              13189  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24447  2 snd_pcm,snd_seq
mei_me                 13933  0 
lpc_ich                16864  0 
wmi                    18590  1 mxm_wmi
snd                    60790  24 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
mei                    66411  1 mei_me
video                  18777  0 
soundcore              12600  1 snd
mac_hid                13037  0 
lp                     13299  0 
parport                40795  3 lp,ppdev,parport_pc
hid_generic            12492  0 
usbhid                 47361  0 
hid                    87370  2 hid_generic,usbhid
usb_storage            48294  2 
firewire_ohci          35257  0 
firewire_core          57656  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
ahci                   25579  1 
libahci                26554  1 ahci
e1000e                222921  0 
ptp                    18156  1 e1000e
pps_core               18546  1 ptp

```

```
frankenstein@frankenstein-desktop:~$ lspci -nnk | grep -iA2 net 
00:19.0 Ethernet controller [0200]: Intel Corporation 82579V Gigabit Network Connection [8086:1503] (rev 04)
    Subsystem: Intel Corporation Device [8086:2037]
    Kernel driver in use: e1000e
--
03:00.0 Ethernet controller [0200]: Intel Corporation 82574L Gigabit Network Connection [8086:10d3]
    Subsystem: Intel Corporation Device [8086:2037]
    Kernel driver in use: e1000e

```

```
frankenstein@frankenstein-desktop:~$ lsusb
Bus 002 Device 004: ID 0db0:a871 Micro Star International 
Bus 002 Device 003: ID 0db0:3871 Micro Star International 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 05e3:0612 Genesys Logic, Inc. 
Bus 004 Device 002: ID 05e3:0612 Genesys Logic, Inc. 
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 003 Device 003: ID 4971:ce07 SimpleTech 
Bus 003 Device 006: ID 046d:c317 Logitech, Inc. Wave Corded Keyboard
Bus 003 Device 008: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 003 Device 007: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 003 Device 005: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 003 Device 002: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

If any other information needed, please let me know. 

EDIT: Had a look at some of the output. In particular this:

> Capabilities:
    Speed:           43 Mb/s

It's quite high isn't it? Would that be part and parcel of the problem of the slow wifi-start-up.

EDIT: The following:
> Wireless Access Points (* = current AP)     Elysian Airport
belongs to my neighbor. The connection point I am using is the other one listed.

---

### Post by varunendra on 2013-12-22
Have you tried disabling "Connect Automatically" option in the Network Manager settings for the connection? Try that first.

And the encryption type WPA/WPA2 mixed mode is not good for Linux drivers -
```

  Wireless Access Points (* = current AP)
    Elysian Airport: Infra, 88:1F:A1:33:C0:D8, Freq 2437 MHz, Rate 54 Mb/s, Strength 89 WPA2
    *TELUS4045:      Infra, FC:F5:28:AD:BF:05, Freq 2437 MHz, Rate 54 Mb/s, Strength 63 **[COLOR="#FF0000"]WPA WPA2[/COLOR]**

```
Read this post (only the answer to point "**2)**" in the post, and the linked post in it) to understand why : [http://ubuntuforums.org/showthread.php?p=12880174](http://ubuntuforums.org/showthread.php?p=12880174)

> **Hodevah said:**
> 
```
Capabilities:
Speed: 43 Mb/s
```
It's quite high isn't it?
No it isn't. The small 'b' in "Mbps" stands for "bit". Divide it with '8' to get its value in "Bytes". So,
43 M**[COLOR="#FF0000"]b[/COLOR]**/s = 43/8 M**[COLOR="#006400"]B[/COLOR]**/s = 5.4 M**B**/s approx., which isn't very high for a local network. :)

---

### Post by Hodevah on 2013-12-23
Hi and thanks for responding. :p
ok. I can give it a try to connect when the network is available but I don't see how this would increase the speed of network connectivity to the network. What I get upon logging into Ubuntu is the '*Network Disconnected you are now offline" *icon and message upon login the operating system. Personnally, I can't see this method of increasing the connection of wifi but I will give it a go for a short while. 


Also, I have the contents of the script as made available by yourself. Please find the contents of that script here:

```

*************** info trace ***************

***** uname -a *****

Linux frankenstein-desktop 3.11.0-14-generic #21-Ubuntu SMP Tue Nov 12 17:07:40 UTC 2013 i686 i686 i686 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy

***** lspci *****

00:19.0 Ethernet controller [0200]: Intel Corporation 82579V Gigabit Network Connection [8086:1503] (rev 04)
    Subsystem: Intel Corporation Device [8086:2037]
    Kernel driver in use: e1000e
--
03:00.0 Ethernet controller [0200]: Intel Corporation 82574L Gigabit Network Connection [8086:10d3]
    Subsystem: Intel Corporation Device [8086:2037]
    Kernel driver in use: e1000e

***** lsusb *****

Bus 002 Device 004: ID 0db0:a871 Micro Star International 
Bus 002 Device 003: ID 0db0:3871 Micro Star International 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 05e3:0612 Genesys Logic, Inc. 
Bus 004 Device 002: ID 05e3:0612 Genesys Logic, Inc. 
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 003 Device 003: ID 4971:ce07 SimpleTech 
Bus 003 Device 006: ID 046d:c317 Logitech, Inc. Wave Corded Keyboard
Bus 003 Device 008: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 003 Device 007: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 003 Device 005: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 003 Device 002: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11bgn  ESSID:"TELUS4045"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC address removed>   
          Bit Rate=57.8 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=55/70  Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:400  Invalid misc:48   Missed beacon:0


***** rfkill *****

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** lsmod *****

rt2800usb              22485  0 
rt2x00usb              20041  1 rt2800usb
rt2800lib              70115  1 rt2800usb
rt2x00lib              48854  3 rt2x00usb,rt2800lib,rt2800usb
mac80211              513247  3 rt2x00lib,rt2x00usb,rt2800lib
cfg80211              401436  2 mac80211,rt2x00lib
crc_ccitt              12627  1 rt2800lib

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: wlan0  [TELUS4045] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800usb
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           57 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Elysian Airport: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 95 WPA2
    *TELUS4045:      Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 63 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.68
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254


- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
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

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

***** iwlist *****

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"TELUS4045"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000f54ce68efa
                    Extra: Last beacon: 196ms ago
                    IE: Unknown: 000954454C555334303435
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001500000000000000000000000000000000000000
                    IE: Unknown: DD780050F204104A00011010440001021041000100103B00010310470010198F745AE6F086D3D4760420D78E63B6102100055A7958454C1023000756534731343332102400075653473134333210420007393633363847571054000800060050F20400011011000756534731343332100800020084103C000101
                    IE: Unknown: DD090010180202F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:on
                    ESSID:"Elysian Airport"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000132d163be80
                    Extra: Last beacon: 0ms ago
                    IE: Unknown: 000F456C797369616E20416972706F7274
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
                    IE: Unknown: 3D1606001700000000000000000000000000000000000000
                    IE: Unknown: 7F080000000000000040
                    IE: Unknown: DD0B0017F20100010100000007
                    IE: Unknown: DD0700039301770320
                    IE: Unknown: DD0E0017F20700010106881FA133C0D9
                    IE: Unknown: DD090010180203001C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 46050200010000


***** resolv.conf *****

nameserver 127.0.1.1
search Home

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

filename:       /lib/modules/3.11.0-14-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
license:        GPL
firmware:       rt2870.bin
description:    Ralink RT2800 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     8D972A7DDE6652BA484C8AE
alias:          usb:vF201p5370d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v177Fp0254d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApF511d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApD522d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApC522d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApA512d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p006Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0069d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0053d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p004Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p004Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p003Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v08B9p1197d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v18E8p6259d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB24d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1D4Dp0010d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05A6p0101d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v100Dp9032d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0789p0169d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0789p0168d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p0615d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p0605d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp094Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148FpF101d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v06F8pE036d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1044p800Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v15A9p0010d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p0602d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p0600d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v203Dp14A1d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C0Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v18C5p0008d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07AAp0042d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07AAp0041d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p0150d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p0148d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p012Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp1003d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3401d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3400d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3399d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3340d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3322d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3284d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3262d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p17A7d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1790d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1761d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1760d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p166Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E0Bp9041d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E0Bp9031d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C11d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C08d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p3074d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p3073d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp5572d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v043Ep7A13d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3C1Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v057Cp8501d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v043Ep7A32d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp5372d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp5370d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0471p2182d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0471p2181d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0471p2180d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0471p2126d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0471p2104d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04DAp23F6d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04DAp1800d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04DAp1801d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v043Ep7A42d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v043Ep7A22d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3C1Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3C1Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3C1Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3C19d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3C15d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3365d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3329d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v043Ep7A32d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v043Ep7A12d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5A57p0284d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0930p0A07d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0068d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0066d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0065d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0062d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0041d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp3572d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1737p0079d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13B1p002Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp0944d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9801d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v167Bp4001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p179Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1690p0764d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1690p0761d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1690p0744d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v8516p3572d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v177Fp0165d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v177Fp0163d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0050d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp8070d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp3370d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0471p20DDd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApB511d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3C17d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp945Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0586p343Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0586p341Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0586p341Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0586p3418d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0586p3416d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5A57p5257d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5A57p0283d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5A57p0280d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CDEp0025d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CDEp0022d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v157Ep3013d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v157Ep300Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v177Fp0324d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v177Fp0323d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v177Fp0313d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v177Fp0302d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v177Fp0164d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v177Fp0153d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v15A9p0006d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApB522d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApA703d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApA702d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApA701d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApA618d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083Ap8522d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083Ap7522d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083Ap7512d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083Ap7511d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083Ap6618d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0060d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p005Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0051d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0048d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0047d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0042d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0040d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p003Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p003Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p003Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p003Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0039d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p002Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p002Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p002Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0017d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v129Bp1828d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04E8p2018d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp3072d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp3071d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp2870d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp2770d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp2070d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1A32p0304d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pED06d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB25d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019p5201d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0471p200Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1D4Dp0011d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1D4Dp000Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1D4Dp000Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1D4Dp0002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v20B8p8888d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B75p3072d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B75p3071d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p899Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p871Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p871Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p871Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p870Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p822Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p822Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p822Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p821Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p6899d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p3871d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p3870d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p3822d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p3821d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p3820d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v100Dp9031d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0789p0166d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0789p0164d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0789p0163d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0789p0162d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1737p0078d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1737p0077d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1737p0071d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1737p0070d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13B1p0031d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp0948d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp0947d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp0945d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0018d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0017d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0013d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p000Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0009d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0003d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1044p800Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1044p800Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v15A9p0012d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9709d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9708d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9707d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9706d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9705d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9703d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9702d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9701d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v203Dp14A9d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v203Dp1480d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p7722d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p7718d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p7717d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p7711d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p4085d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0FE9pB307d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07FAp7712d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3C1Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C17d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C16d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C15d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C13d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C11d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C0Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C0Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C0Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C0Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C09d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v18C5p0012d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07AAp003Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07AAp003Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07AAp002Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p01EEd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p01A2d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p016Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p015Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p0158d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p00E8d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp935Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp935Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp825Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp825Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp805Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp8053d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3321d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3307d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3305d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3273d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3247d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1761p0B05d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1784d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1742d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1732d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1731d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1690p0740d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v15C5p0008d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C2Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C28d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C27d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C25d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C23d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C12d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C09d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C07d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C06d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v8516p3072d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v8516p3071d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v8516p3070d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v8516p2870d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v8516p2770d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v8516p2070d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1EDAp2310d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1EDAp2210d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1EDAp2012d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1482p3C09d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p3072d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p3071d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p2770d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p2870d*dc*dsc*dp*ic*isc*ip*in*
depends:        rt2x00lib,rt2800lib,rt2x00usb
intree:         Y
vermagic:       3.11.0-14-generic SMP mod_unload modversions 686 
parm:           nohwcrypt:Disable hardware encryption. (bool)

filename:       /lib/modules/3.11.0-14-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
license:        GPL
description:    rt2x00 usb library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     5CFE65EA16A08E63C627D96
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.11.0-14-generic SMP mod_unload modversions 686 

filename:       /lib/modules/3.11.0-14-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     26219235502295A1CDE028F
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       3.11.0-14-generic SMP mod_unload modversions 686 

filename:       /lib/modules/3.11.0-14-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     8AE9D454A710B1C25F9F518
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.11.0-14-generic SMP mod_unload modversions 686 


***** udev rules *****

# PCI device 0x8086:0x10d3 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x8086:0x1503 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

***** dmesg *****

[    1.322633] e1000e 0000:03:00.0 eth1: registered PHC clock
[    1.322635] e1000e 0000:03:00.0 eth1: (PCI Express:2.5GT/s:Width x1) <MAC address removed>
[    1.322636] e1000e 0000:03:00.0 eth1: Intel(R) PRO/1000 Network Connection
[    1.322653] e1000e 0000:03:00.0 eth1: MAC: 3, PHY: 8, PBA No: FFFFFF-0FF
[   13.067662] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   13.752161] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[   13.780511] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 0005 detected
[   19.393762] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   19.393967] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   19.395007] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[   19.408748] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[   19.857106] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.857405] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   45.829333] wlan0: authenticate with <MAC address removed>
[   45.896249] wlan0: send auth to <MAC address removed> (try 1/3)
[   45.897859] wlan0: authenticated
[   45.900517] wlan0: associate with <MAC address removed> (try 1/3)
[   45.908901] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[   45.915727] wlan0: associated
[   45.915764] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   49.963879] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:f5:28:ad:bf:04:08:00 SRC=41.215.180.61 DST=192.168.1.68 LEN=48 TOS=0x00 PREC=0x00 TTL=108 ID=9505 PROTO=UDP SPT=63293 DPT=6881 LEN=28 
[   50.381406] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:f5:28:ad:bf:04:08:00 SRC=87.119.177.107 DST=192.168.1.68 LEN=58 TOS=0x00 PREC=0x00 TTL=117 ID=21524 PROTO=UDP SPT=32314 DPT=6881 LEN=38 
[   53.339448] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:f5:28:ad:bf:04:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[   53.549647] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:f5:28:ad:bf:04:08:00 SRC=72.27.42.148 DST=192.168.1.68 LEN=58 TOS=0x00 PREC=0x00 TTL=51 ID=41209 PROTO=UDP SPT=37959 DPT=6881 LEN=38 
[   53.632024] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:f5:28:ad:bf:04:08:00 SRC=87.119.177.107 DST=192.168.1.68 LEN=58 TOS=0x00 PREC=0x00 TTL=117 ID=22436 PROTO=UDP SPT=32314 DPT=6881 LEN=38 
[   54.981324] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:f5:28:ad:bf:04:08:00 SRC=41.215.180.61 DST=192.168.1.68 LEN=48 TOS=0x00 PREC=0x00 TTL=108 ID=11333 PROTO=UDP SPT=63293 DPT=6881 LEN=28 
[   56.720014] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:f5:28:ad:bf:04:08:00 SRC=72.27.42.148 DST=192.168.1.68 LEN=58 TOS=0x00 PREC=0x00 TTL=51 ID=61837 PROTO=UDP SPT=37959 DPT=6881 LEN=38 
[   56.916779] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:f5:28:ad:bf:04:08:00 SRC=14.201.43.117 DST=192.168.1.68 LEN=48 TOS=0x00 PREC=0x00 TTL=114 ID=15832 PROTO=UDP SPT=17342 DPT=6881 LEN=28 
[   58.889704] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:f5:28:ad:bf:04:08:00 SRC=178.85.81.197 DST=192.168.1.68 LEN=58 TOS=0x00 PREC=0x00 TTL=118 ID=881 PROTO=UDP SPT=51000 DPT=6881 LEN=38 
[   59.781413] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:f5:28:ad:bf:04:08:00 SRC=87.119.177.107 DST=192.168.1.68 LEN=58 TOS=0x00 PREC=0x00 TTL=117 ID=23114 PROTO=UDP SPT=32314 DPT=6881 LEN=38 
[   70.750822] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:f5:28:ad:bf:04:08:00 SRC=14.207.150.80 DST=192.168.1.68 LEN=48 TOS=0x00 PREC=0x00 TTL=118 ID=18008 PROTO=UDP SPT=54434 DPT=6881 LEN=28 
[   92.257505] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:f5:28:ad:bf:04:08:00 SRC=100.0.208.14 DST=192.168.1.68 LEN=58 TOS=0x00 PREC=0x00 TTL=115 ID=10480 PROTO=UDP SPT=20312 DPT=6881 LEN=38 
[  113.659673] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:f5:28:ad:bf:04:08:00 SRC=14.201.43.117 DST=192.168.1.68 LEN=48 TOS=0x00 PREC=0x00 TTL=114 ID=9411 PROTO=UDP SPT=17342 DPT=6881 LEN=28 
[  133.316718] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:f5:28:ad:bf:04:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[  150.681502] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:f5:28:ad:bf:04:08:00 SRC=37.142.206.90 DST=192.168.1.68 LEN=58 TOS=0x00 PREC=0x00 TTL=50 ID=53915 PROTO=UDP SPT=26910 DPT=6881 LEN=38 
[  170.595463] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:f5:28:ad:bf:04:08:00 SRC=14.201.43.117 DST=192.168.1.68 LEN=48 TOS=0x00 PREC=0x00 TTL=114 ID=5046 PROTO=UDP SPT=17342 DPT=6881 LEN=28 
[  191.591696] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:f5:28:ad:bf:04:08:00 SRC=201.50.105.96 DST=192.168.1.68 LEN=58 TOS=0x00 PREC=0x00 TTL=116 ID=11761 PROTO=UDP SPT=30707 DPT=6881 LEN=38 
[  213.394501] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:f5:28:ad:bf:04:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[  231.905741] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:f5:28:ad:bf:04:08:00 SRC=87.119.177.107 DST=192.168.1.68 LEN=58 TOS=0x00 PREC=0x00 TTL=117 ID=1482 PROTO=UDP SPT=32314 DPT=6881 LEN=38 
[  252.517415] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:f5:28:ad:bf:04:08:00 SRC=14.201.43.117 DST=192.168.1.68 LEN=48 TOS=0x00 PREC=0x00 TTL=114 ID=13502 PROTO=UDP SPT=17342 DPT=6881 LEN=28 
[  271.357922] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:f5:28:ad:bf:04:08:00 SRC=80.244.72.152 DST=192.168.1.68 LEN=58 TOS=0x00 PREC=0x00 TTL=114 ID=1216 PROTO=UDP SPT=44116 DPT=6881 LEN=38 
[  293.473389] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:f5:28:ad:bf:04:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[  311.604126] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:f5:28:ad:bf:04:08:00 SRC=37.142.206.90 DST=192.168.1.68 LEN=58 TOS=0x00 PREC=0x00 TTL=50 ID=44420 PROTO=UDP SPT=26910 DPT=6881 LEN=38 
[  330.544895] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:f5:28:ad:bf:04:08:00 SRC=72.27.42.148 DST=192.168.1.68 LEN=58 TOS=0x00 PREC=0x00 TTL=51 ID=8702 PROTO=UDP SPT=37959 DPT=6881 LEN=38 
[  350.205626] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:f5:28:ad:bf:04:08:00 SRC=100.0.208.14 DST=192.168.1.68 LEN=58 TOS=0x00 PREC=0x00 TTL=115 ID=29285 PROTO=UDP SPT=20312 DPT=6881 LEN=38 
[  370.158356] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:f5:28:ad:bf:04:08:00 SRC=14.201.43.117 DST=192.168.1.68 LEN=48 TOS=0x00 PREC=0x00 TTL=114 ID=2091 PROTO=UDP SPT=17342 DPT=6881 LEN=28 
[  396.901618] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:f5:28:ad:bf:04:08:00 SRC=86.185.99.38 DST=192.168.1.68 LEN=52 TOS=0x00 PREC=0x00 TTL=113 ID=20019 DF PROTO=TCP SPT=54759 DPT=51413 WINDOW=8192 RES=0x00 SYN URGP=0 
[  411.956498] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:f5:28:ad:bf:04:08:00 SRC=108.197.157.211 DST=192.168.1.68 LEN=58 TOS=0x00 PREC=0x00 TTL=118 ID=1327 PROTO=UDP SPT=41902 DPT=6881 LEN=38 
[  453.628701] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:f5:28:ad:bf:04:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[  477.285886] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:f5:28:ad:bf:04:08:00 SRC=86.185.99.38 DST=192.168.1.68 LEN=52 TOS=0x00 PREC=0x00 TTL=113 ID=26787 DF PROTO=TCP SPT=55091 DPT=51413 WINDOW=8192 RES=0x00 SYN URGP=0 
[  480.356703] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:f5:28:ad:bf:04:08:00 SRC=86.185.99.38 DST=192.168.1.68 LEN=52 TOS=0x00 PREC=0x00 TTL=113 ID=27031 DF PROTO=TCP SPT=55091 DPT=51413 WINDOW=8192 RES=0x00 SYN URGP=0 
[  492.479007] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:f5:28:ad:bf:04:08:00 SRC=108.197.157.211 DST=192.168.1.68 LEN=58 TOS=0x00 PREC=0x00 TTL=118 ID=3837 PROTO=UDP SPT=41902 DPT=6881 LEN=38 
[  513.741695] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:f5:28:ad:bf:04:08:00 SRC=14.201.43.117 DST=192.168.1.68 LEN=48 TOS=0x00 PREC=0x00 TTL=114 ID=3284 PROTO=UDP SPT=17342 DPT=6881 LEN=28 
[  533.608847] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:f5:28:ad:bf:04:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[  555.725960] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:f5:28:ad:bf:04:08:00 SRC=80.244.72.152 DST=192.168.1.68 LEN=58 TOS=0x00 PREC=0x00 TTL=114 ID=17264 PROTO=UDP SPT=44116 DPT=6881 LEN=38 
[  573.643046] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:f5:28:ad:bf:04:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[  613.682000] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:f5:28:ad:bf:04:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[  626.768307] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:f5:28:ad:bf:04:08:00 SRC=203.190.77.8 DST=192.168.1.68 LEN=58 TOS=0x00 PREC=0x40 TTL=115 ID=87 PROTO=UDP SPT=28377 DPT=6881 LEN=38 
[  630.070402] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:f5:28:ad:bf:04:08:00 SRC=203.190.77.8 DST=192.168.1.68 LEN=58 TOS=0x00 PREC=0x40 TTL=116 ID=2990 PROTO=UDP SPT=28377 DPT=6881 LEN=38 
[  650.122550] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:f5:28:ad:bf:04:08:00 SRC=108.197.157.211 DST=192.168.1.68 LEN=58 TOS=0x00 PREC=0x00 TTL=118 ID=7402 PROTO=UDP SPT=41902 DPT=6881 LEN=38 
[  693.760255] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:f5:28:ad:bf:04:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[  727.658532] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:f5:28:ad:bf:04:08:00 SRC=86.185.99.38 DST=192.168.1.68 LEN=52 TOS=0x00 PREC=0x00 TTL=113 ID=21173 DF PROTO=TCP SPT=57203 DPT=51413 WINDOW=8192 RES=0x00 SYN URGP=0 
[  733.696848] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:f5:28:ad:bf:04:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[  736.678225] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:f5:28:ad:bf:04:08:00 SRC=86.185.99.38 DST=192.168.1.68 LEN=48 TOS=0x00 PREC=0x00 TTL=113 ID=21908 DF PROTO=TCP SPT=57203 DPT=51413 WINDOW=8192 RES=0x00 SYN URGP=0 
[  773.737160] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:f5:28:ad:bf:04:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[  804.870861] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:f5:28:ad:bf:04:08:00 SRC=203.190.77.8 DST=192.168.1.68 LEN=58 TOS=0x00 PREC=0x40 TTL=115 ID=15064 PROTO=UDP SPT=28377 DPT=6881 LEN=38 
[  808.144890] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:f5:28:ad:bf:04:08:00 SRC=203.190.77.8 DST=192.168.1.68 LEN=58 TOS=0x00 PREC=0x40 TTL=116 ID=17304 PROTO=UDP SPT=28377 DPT=6881 LEN=38 
[  813.775997] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:f5:28:ad:bf:04:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[  853.815320] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:f5:28:ad:bf:04:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[  893.855272] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:f5:28:ad:bf:04:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[  903.284791] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:f5:28:ad:bf:04:08:00 SRC=86.185.99.38 DST=192.168.1.68 LEN=52 TOS=0x00 PREC=0x00 TTL=113 ID=11151 DF PROTO=TCP SPT=59100 DPT=51413 WINDOW=8192 RES=0x00 SYN URGP=0 
[  906.249318] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:f5:28:ad:bf:04:08:00 SRC=86.185.99.38 DST=192.168.1.68 LEN=52 TOS=0x00 PREC=0x00 TTL=113 ID=11574 DF PROTO=TCP SPT=59100 DPT=51413 WINDOW=8192 RES=0x00 SYN URGP=0 
[  921.813192] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:f5:28:ad:bf:04:08:00 SRC=203.190.77.8 DST=192.168.1.68 LEN=58 TOS=0x00 PREC=0x40 TTL=115 ID=11433 PROTO=UDP SPT=28377 DPT=6881 LEN=38 
[  931.336257] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:f5:28:ad:bf:04:08:00 SRC=203.190.77.8 DST=192.168.1.68 LEN=58 TOS=0x00 PREC=0x40 TTL=116 ID=19488 PROTO=UDP SPT=28377 DPT=6881 LEN=38 
[  973.834924] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:f5:28:ad:bf:04:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[  989.476241] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:f5:28:ad:bf:04:08:00 SRC=86.185.99.38 DST=192.168.1.68 LEN=52 TOS=0x00 PREC=0x00 TTL=113 ID=21813 DF PROTO=TCP SPT=59553 DPT=51413 WINDOW=8192 RES=0x00 SYN URGP=0 

****************** done ******************

```

PS. I did go to _both_ of the links you supplied and as you were mentioning about understanding why it is not a good idea to have both wpa and wpa2 at the same time, I did not find any posts that described the reason why. 
I went all the way down to post #24 at this link: [http://ubuntuforums.org/showthread.php?t=2082305](http://ubuntuforums.org/showthread.php?t=2082305)  however, sorry but I did not see an explanation as to why.

PS. At post #6,  at this link:    [http://ubuntuforums.org/showthread.php?t=2193725&p=12878387#post12878387](http://ubuntuforums.org/showthread.php?t=2193725&p=12878387#post12878387)
I did see you post a reason why explaining:

> **2)** Many of these APs are using the dreaded WPA/WPA2 mixed mode  encryption. It is HIGHLY recommended to change the encryption type in  the router to pure WPA2-PSK (AES/CCMP) only. No mixed mode, no TKIP.  Even if this alone can't help, leave it like this.
***[COLOR=#800000]EDIT:[/COLOR]*** Just noticed you  mentioned your AP isn't even mentioned in the report. Is is set to use  correct frequencies/channel as permitted by your country's "Regulatory  Settings"? Is it detected by other devices there?

Unfortunately, I do not have direct access to the router. My landlord and I both share the same network and hence am unable to directly affect any settings to the router. Unless you think that accessing it via web access might help. 

Thank you in advance for your continuing help. ;)

**EDIT:** Ok. So I can access the router via web access; however, I would please request some help from you on which security settings would be optimal regarding my network. 
What I see available via web access for wifi settings are the following as you do make suggestion of having no tkip. Why no tkip,if I may ask?

> SECURITY MODE:
mixed wpa2-psk/wpa-psk;
wpa-psk;
wpa2-psk;
no security ( I will _no_t enable this)

On Encryption there is the following:

> ENCRYPTION:

tkip-aes;
aes

---

### Post by varunendra on 2013-12-24
Optimal Encryption is -
```
WPA2-PSK
```
..and corresponding encryption algorithm is -
```
AES
```

PS:
There seem to be too many blocks in UFW. Are you sure it has been configured correctly and the blocked traffic is intentionally blocked?

---

### Post by Hodevah on 2013-12-24
Hi again, Varun.  So I have set up the wifi for the router as per your suggestions and am going to enable the wifi to start up on boot up again.   I have tested the start up of wifi upon boot twice now and I must say that the wifi starts up much quicker. Thank your for the information. With respect to the ufw,


```
frankenstein@frankenstein-desktop:~$ sudo netstat -ntulp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.1.1:53            0.0.0.0:*               LISTEN      1691/dnsmasq    
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      3077/cupsd      
tcp6       0      0 ::1:631                 :::*                    LISTEN      3077/cupsd      
udp        0      0 127.0.1.1:53            0.0.0.0:*                           1691/dnsmasq    
udp        0      0 0.0.0.0:68              0.0.0.0:*                           1662/dhclient   
udp        0      0 0.0.0.0:631             0.0.0.0:*                           999/cups-browsed
udp        0      0 0.0.0.0:52410           0.0.0.0:*                           1662/dhclient   
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           899/avahi-daemon: r
udp        0      0 0.0.0.0:47919           0.0.0.0:*                           899/avahi-daemon: r
udp6       0      0 :::5353                 :::*                                899/avahi-daemon: r
udp6       0      0 :::44887                :::*                                899/avahi-daemon: r
udp6       0      0 :::13683                :::*                                1662/dhclient   
frankenstein@frankenstein-desktop:~$ 

```

or for a better idea of what I have regarding ufw...

```
frankenstein@frankenstein-desktop:~$ sudo ufw status numbered
Status: active

     To                         Action      From
     --                         ------      ----
[ 1] 53,137,138/udp             ALLOW OUT   Anywhere (out)
[ 2] 20,21,22,25,80,139,443,5900,8001/tcp ALLOW OUT   Anywhere (out)
[ 3] 6881:6999/tcp              ALLOW IN    Anywhere
[ 4] 22                         ALLOW IN    Anywhere
[ 5] Anywhere                   DENY IN     207.46.232.182
[ 6] Anywhere                   DENY IN     207.46.0.0/16
[ 7] Anywhere                   DENY IN     69.172.201.20
[ 8] Anywhere                   DENY IN     76.74.24.200
[ 9] 53,137,138/udp             ALLOW OUT   Anywhere (v6) (out)
[10] 20,21,22,25,80,139,443,5900,8001/tcp ALLOW OUT   Anywhere (v6) (out)
[11] 6881:6999/tcp              ALLOW IN    Anywhere (v6)
[12] 22                         ALLOW IN    Anywhere (v6)

```

---

