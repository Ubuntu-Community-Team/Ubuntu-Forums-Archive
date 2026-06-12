---
title: "Unable to enable WiFi connection after installing Ubuntu 14.10 on my laptop."
date: 2015-04-04
forum: Networking &amp; Wireless
---

### Post by Perqin on 2015-04-04
Hi. Last night I have installed Ubuntu 14.10 on my laptop using a U disk. During installation the wireless connection worked correctly and I skipped the download of language pack because it spent too much time. However, after installation I boot Ubuntu from my laptop and found that the WiFi connection didn't work. It reads "Wifi is disabled by hardware switch". I am completely confused, because it worked well during installation. It shouldn't be the problem of my hardware, should it? I am able to connect to WiFi on Windows 7.
I have already tried pressing Fn+F3, which seems to be the wireless switch of my laptop, but it doesn't work:(

---

### Post by praseodym on 2015-04-05
Hi,

please run the wireles-script from the sticky thread and show the outputs. What kind of laptop is it?

---

### Post by Perqin on 2015-04-05
I tried to download the script but failed. Maybe Dropbox is blocked in my country. Could you send the script to my email address : [email]perqinxie@gmail.com[/email]? Very thanks.

---

### Post by praseodym on 2015-04-05
Please find it attached. Save it in your /home folder and run:

```
mv wireless_script.txt wireless_script && chmod +x wireless_script && ./wireless_script
```

---

### Post by Perqin on 2015-04-05
My laptop is Acer V3-572G-59GB, and here's the content of wireless_info.txt:
```

########## wireless info START ##########

Report from: 05 Apr 2015 23:41 CST +0800

Booted last: 05 Apr 2015 20:19 CST +0800

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.10
Release:    14.10
Codename:    utopic

##### kernel ############################

Linux 3.16.0-33-generic #44-Ubuntu SMP Thu Mar 12 12:19:35 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
    Subsystem: Acer Incorporated [ALI] Device [1025:0866]
    Kernel driver in use: r8169

02:00.0 Network controller [0280]: Qualcomm Atheros AR9462 Wireless Network Adapter [168c:0034] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e052]
    Kernel driver in use: ath9k

##### lsusb #############################

Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 04f2:b469 Chicony Electronics Co., Ltd 
Bus 002 Device 006: ID 0489:e04e Foxconn / Hon Hai 
Bus 002 Device 003: ID 0c45:7603 Microdia 
Bus 002 Device 002: ID 046d:c247 Logitech, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

##### lsmod #############################

ath9k                 136984  0 
ath9k_common           25638  1 ath9k
ath9k_hw              446568  2 ath9k_common,ath9k
ath                    29052  3 ath9k_common,ath9k,ath9k_hw
mac80211              660592  1 ath9k
cfg80211              510218  4 ath,ath9k_common,ath9k,mac80211
ath3k                  13331  0 
bluetooth             446190  23 bnep,ath3k,btusb,rfcomm

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.199.196  Bcast:192.168.199.255  Mask:255.255.255.0
          inet6 addr: fe80::faa9:63ff:fe71:577e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4941 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3144 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2392468 (2.3 MB)  TX bytes:444932 (444.9 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.199.1   0.0.0.0         UG    0      0        0 eth0
192.168.199.0   0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search lan

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.199.196
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.199.1

    DNS:             192.168.199.1

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Ninest520Studio_5G]] (600 root)
[connection] id=Ninest520Studio_5G | type=802-11-wireless
[802-11-wireless] ssid=Ninest520Studio_5G | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Asia/Shanghai (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), NO-IR
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, NO-IR
    (5170 - 5250 @ 40), (3, 20), NO-IR
    (5735 - 5835 @ 40), (3, 20), NO-IR

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     32 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

lo        Interface doesn't support scanning.

##### module infos ######################

[ath9k]
filename:       /lib/modules/3.16.0-33-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     5C1878F185424DB0329389D
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.16.0-33-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        27:43:73:00:F8:EE:18:3C:88:11:43:4F:EB:7F:D9:5F:C6:87:82:EC
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)

[ath9k_common]
filename:       /lib/modules/3.16.0-33-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     265A5990B1258ECC29235FC
depends:        cfg80211,ath9k_hw,ath
intree:         Y
vermagic:       3.16.0-33-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        27:43:73:00:F8:EE:18:3C:88:11:43:4F:EB:7F:D9:5F:C6:87:82:EC
sig_hashalgo:   sha512

[ath9k_hw]
filename:       /lib/modules/3.16.0-33-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     0D1161FC3B202FBE214F25D
depends:        ath
intree:         Y
vermagic:       3.16.0-33-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        27:43:73:00:F8:EE:18:3C:88:11:43:4F:EB:7F:D9:5F:C6:87:82:EC
sig_hashalgo:   sha512

[ath]
filename:       /lib/modules/3.16.0-33-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     165C1DF76AF8C8B6A45DA4F
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-33-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        27:43:73:00:F8:EE:18:3C:88:11:43:4F:EB:7F:D9:5F:C6:87:82:EC
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.16.0-33-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     5410C94462FA26A0A3F256C
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-33-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        27:43:73:00:F8:EE:18:3C:88:11:43:4F:EB:7F:D9:5F:C6:87:82:EC
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.16.0-33-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     4A525D9D32B0C6D120CA547
depends:        
intree:         Y
vermagic:       3.16.0-33-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        27:43:73:00:F8:EE:18:3C:88:11:43:4F:EB:7F:D9:5F:C6:87:82:EC
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ath3k]
filename:       /lib/modules/3.16.0-33-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     CD45B9D14D1C139B22425B7
depends:        bluetooth
intree:         Y
vermagic:       3.16.0-33-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        27:43:73:00:F8:EE:18:3C:88:11:43:4F:EB:7F:D9:5F:C6:87:82:EC
sig_hashalgo:   sha512

##### module parameters #################

[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
nohwcrypt: 0
ps_enable: 0
use_chanctx: 0

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

##### modprobe options ##################

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

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x0034 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[    8.668627] ath9k 0000:02:00.0: found PCI INT A -> IRQ 10
[    8.782715] ath: phy0: ASPM enabled: 0x42
[    8.782719] ath: EEPROM regdomain: 0x6c
[    8.782720] ath: EEPROM indicates we should expect a direct regpair map
[    8.782721] ath: Country alpha2 being used: 00
[    8.782723] ath: Regpair used: 0x6c

########## wireless info END ############


```

---

### Post by praseodym on 2015-04-05
Please show the outputs of

```
lsmod

```
completely

---

### Post by Arjun_Govindjee on 2015-04-05
```
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
```

I'm no expert, but the hard block seems like a problem to me, do you have a WiFi switch on your device? Or on some laptops WiFi is disabled when Ethernet/power/other things are attached, so try removing any of those?

---

### Post by praseodym on 2015-04-05
Is it a BIOS? If yes, reset it to default

---

### Post by Perqin on 2015-04-06
Here's the output of the command:
```

Module                  Size  Used by
intel_rapl             18783  0 
x86_pkg_temp_thermal    14205  0 
bnep                   19543  2 
intel_powerclamp       18786  0 
arc4                   12608  2 
coretemp               13441  0 
ath9k                 136984  0 
kvm_intel             143592  0 
ath9k_common           25638  1 ath9k
kvm                   459835  1 kvm_intel
ath9k_hw              446568  2 ath9k_common,ath9k
ath                    29052  3 ath9k_common,ath9k,ath9k_hw
crct10dif_pclmul       14307  0 
mac80211              660592  1 ath9k
crc32_pclmul           13133  0 
ghash_clmulni_intel    13230  0 
aesni_intel           152552  1 
aes_x86_64             17131  1 aesni_intel
lrw                    13287  1 aesni_intel
rfcomm                 69509  8 
gf128mul               14951  1 lrw
glue_helper            13944  1 aesni_intel
cfg80211              510218  4 ath,ath9k_common,ath9k,mac80211
ablk_helper            13597  1 aesni_intel
cryptd                 20360  3 ghash_clmulni_intel,aesni_intel,ablk_helper
uvcvideo               81065  0 
snd_hda_codec_hdmi     47547  1 
ttm                    97680  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         59104  1 uvcvideo
serio_raw              13434  0 
v4l2_common            15682  1 videobuf2_core
videodev              149725  3 uvcvideo,v4l2_common,videobuf2_core
media                  21963  2 uvcvideo,videodev
i915                  917748  6 
joydev                 17344  0 
snd_hda_codec_realtek    77467  1 
snd_hda_codec_generic    68914  1 snd_hda_codec_realtek
lpc_ich                21093  0 
snd_hda_intel          30420  5 
mac_hid                13227  0 
snd_hda_controller     35152  1 snd_hda_intel
snd_hda_codec         139675  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              17698  1 snd_hda_codec
rtsx_pci_ms            18168  0 
memstick               16966  1 rtsx_pci_ms
video                  20128  1 i915
ath3k                  13331  0 
snd_pcm               104102  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
btusb                  32448  0 
drm_kms_helper         61627  1 i915
drm                   310919  6 ttm,i915,drm_kms_helper
snd_seq_midi           13564  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30876  1 snd_seq_midi
snd_seq                67224  2 snd_seq_midi_event,snd_seq_midi
bluetooth             446190  23 bnep,ath3k,btusb,rfcomm
6lowpan_iphc           18702  1 bluetooth
mei_me                 19742  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29513  2 snd_pcm,snd_seq
i2c_algo_bit           13406  1 i915
shpchp                 37040  0 
snd                    87611  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
mei                    87931  1 mei_me
soundcore              15052  2 snd,snd_hda_codec
binfmt_misc            17468  1 
parport_pc             32741  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
hid_generic            12559  0 
usbhid                 52566  0 
hid                   110426  2 hid_generic,usbhid
rtsx_pci_sdmmc         23043  0 
psmouse               106593  0 
ahci                   34062  4 
libahci                32424  1 ahci
r8169                  71471  0 
mii                    13934  1 r8169
rtsx_pci               46301  2 rtsx_pci_ms,rtsx_pci_sdmmc

```

---

### Post by Perqin on 2015-04-06
I've tried Fn+F3 but it didn't work. I didn't change any settings for I just installed Ubuntu days ago.

---

### Post by praseodym on 2015-04-06
Lets try
```

sudo modprobe -rfv ath9k
sudo rfkill unblock all
sudo modprobe -v ath9k
rfkill list
```

---

### Post by marga2 on 2015-04-06
##

---

### Post by Perqin on 2015-04-07
Sadly, it doesn't work. The Wireless LAN is still hard blocked:(

---

