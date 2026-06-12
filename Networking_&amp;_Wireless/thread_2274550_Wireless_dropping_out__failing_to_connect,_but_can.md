---
title: "Wireless dropping out / failing to connect, but can see networks"
date: 2015-04-20
forum: Networking &amp; Wireless
---

### Post by Ratscallion on 2015-04-20
I have a Toshiba Satellite computer (C55-A-1RD), and am having WiFi issues. 
[LIST=1]
[*]Cannot connect to wireless networks - wired is and always has been fine.
[*]Often dropping connection to networks, but reconnection will solve this
[*]Does only occasionally restart working after a restart of network-manager service
[*]If 3 does not work, a reboot will not work
[*]If the computer is off for >10 minutes and then boots, that generally solves the problem
[/LIST]

Obviously, losing 15+ minutes isn't ideal. Mostly, this issue occurs after waking from sleep, but not always. Sometimes it can be random, or after a network-manager restart. There are always wifi networks available to view, but connecting to them fails. Bluetooth always works.

Running elementary Freya, based on Ubuntu 14.04, and the issue was also apparent in Ubuntu 14.04.

Restarting the Wireless Router doesn't do anything, since I can see and refresh wireless connections available, but not connect to them. The same connection on my Android phone works fine during the period in which I can't connect on my computer. The mobile hotspot on my phone works when I can connect to other connections on my computer, but I cannot connect to that, either, when I can't connect to anything else. 

**Wireless Script Results**
```


########## wireless info START ##########

Report from: 20 Apr 2015 19:15 BST +0100

Booted last: 20 Apr 2015 11:37 BST +0100

Script from: 06 Apr 2015 17:23 UTC +0000

##### release ###########################

Distributor ID:    elementary OS
Description:    elementary OS Freya
Release:    0.3
Codename:    freya

##### kernel ############################

Linux 3.16.0-34-generic #47~14.04.1-Ubuntu SMP Fri Apr 10 17:49:16 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Pantheon

##### lspci #############################

01:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
    Subsystem: Lite-On Communications Inc Device [11ad:0612]
    Kernel driver in use: ath9k

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 064e:e374 Suyin Corp. 
Bus 001 Device 009: ID 0930:0220 Toshiba Corp. 
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 003: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 001 Device 002: ID 062a:4101 Creative Labs 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ath3k                  13331  0 
bluetooth             446409  23 bnep,ath3k,btusb,rfcomm
wl                   6367833  0 
ath9k                 137283  0 
ath9k_common           25638  1 ath9k
ath9k_hw              446521  2 ath9k_common,ath9k
ath                    29006  3 ath9k_common,ath9k,ath9k_hw
mac80211              652718  1 ath9k
cfg80211              494362  5 wl,ath,ath9k_common,ath9k,mac80211
snd_soc_rt5640         93042  0 
snd_soc_rl6231         13037  1 snd_soc_rt5640
snd_soc_core          200204  1 snd_soc_rt5640
snd_pcm               104112  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
wmi                    19193  1 toshiba_acpi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2ae3:47ff:fefb:61d3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:279320 errors:0 dropped:0 overruns:0 frame:0
          TX packets:164571 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:359297752 (359.2 MB)  TX bytes:20611757 (20.6 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Beryl 2.4"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: <MAC 'Beryl 2.4' [AC1]>   
          Bit Rate=57.8 Mb/s   Tx-Power=16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=42/70  Signal level=-68 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:408   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: wlan0  [Beryl 2.4] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           57 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    TARDIS:          Infra, <MAC 'TARDIS' [AC2]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
    VM392640-2G:     Infra, <MAC 'VM392640-2G' [AC3]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    virginmedia6759608: Infra, <MAC 'virginmedia6759608' [AC4]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    *Beryl 2.4:      Infra, <MAC 'Beryl 2.4' [AC1]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 51 WPA WPA2

  IPv4 Settings:
    Address:         192.168.0.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1

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

[[/etc/NetworkManager/system-connections/Beryl 2.4]] (600 root)
[connection] id=Beryl 2.4 | type=802-11-wireless
[802-11-wireless] ssid=Beryl 2.4 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/TARDIS-40]] (600 root)
[connection] id=TARDIS-40 | type=802-11-wireless
[802-11-wireless] ssid=TARDIS-40 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/London (based on set time zone)

country GB:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5490 - 5710 @ 40), (N/A, 27), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR

##### iwlist channels ###################

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
          Current Frequency:2.417 GHz (Channel 2)

##### iwlist scan #######################

Channel occupancy:

      2   APs on   Frequency:2.417 GHz (Channel 2)
      2   APs on   Frequency:2.462 GHz (Channel 11)

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Beryl 2.4' [AC1]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"Beryl 2.4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000019a1fb4959
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'TARDIS' [AC2]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"TARDIS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000019a21c01fd
                    Extra: Last beacon: 216ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'VM392640-2G' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=lo        Interface doesn't support scanning.

38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"VM392640-2G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000028fa4e45a7
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'virginmedia6759608' [AC4]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"virginmedia6759608"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000016da03f630
                    Extra: Last beacon: 17212ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[ath3k]
filename:       /lib/modules/3.16.0-34-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     8449188E53D477A663A0DBF
depends:        bluetooth
intree:         Y
vermagic:       3.16.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        80:21:14:84:DC:DA:08:06:05:39:31:B7:EE:AA:DE:22:EA:7E:C2:62
sig_hashalgo:   sha512

[wl]
filename:       /lib/modules/3.16.0-34-generic/extra/wl.ko
license:        MIXED/Proprietary
srcversion:     9A49255BA90267D99664757
depends:        cfg80211
vermagic:       3.16.0-34-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[ath9k]
filename:       /lib/modules/3.16.0-34-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     5C1878F185424DB0329389D
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.16.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        80:21:14:84:DC:DA:08:06:05:39:31:B7:EE:AA:DE:22:EA:7E:C2:62
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)

[ath9k_common]
filename:       /lib/modules/3.16.0-34-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     265A5990B1258ECC29235FC
depends:        cfg80211,ath9k_hw,ath
intree:         Y
vermagic:       3.16.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        80:21:14:84:DC:DA:08:06:05:39:31:B7:EE:AA:DE:22:EA:7E:C2:62
sig_hashalgo:   sha512

[ath9k_hw]
filename:       /lib/modules/3.16.0-34-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     0D1161FC3B202FBE214F25D
depends:        ath
intree:         Y
vermagic:       3.16.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        80:21:14:84:DC:DA:08:06:05:39:31:B7:EE:AA:DE:22:EA:7E:C2:62
sig_hashalgo:   sha512

[ath]
filename:       /lib/modules/3.16.0-34-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     165C1DF76AF8C8B6A45DA4F
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        80:21:14:84:DC:DA:08:06:05:39:31:B7:EE:AA:DE:22:EA:7E:C2:62
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.16.0-34-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     5410C94462FA26A0A3F256C
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        80:21:14:84:DC:DA:08:06:05:39:31:B7:EE:AA:DE:22:EA:7E:C2:62
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.16.0-34-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     4A525D9D32B0C6D120CA547
depends:        
intree:         Y
vermagic:       3.16.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        80:21:14:84:DC:DA:08:06:05:39:31:B7:EE:AA:DE:22:EA:7E:C2:62
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

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

lp
rtc

##### modprobe options ##################

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
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x0036 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

########## wireless info END ############



```

---

### Post by jeremy31 on 2015-04-21
I would change encryption settings on the wifi router to WPA2-AES or WPA2 only as you have TKIP enabled and Linux struggles with TKIP and it is less secure

Also try ```
echo "options ath9k btcoex_enable=1" | sudo tee /etc/modprobe.d/ath9k.conf
```

Reboot

You also have Broadcom modules installed but no sign of a Broadcom wifi card, to remove ```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-dkms
```

---

### Post by Ratscallion on 2015-04-21
I updated the router settings - it was previously on WPA Auto and is now WPA2-PSK[AES].
The first code may not have worked, as it printed "options [etc]" and the sudo tee command didn't visibly do anything.
The Broadcom packages have been removed.
We'll see what happens and I'll update accordingly - thanks for your help.

---

### Post by Ratscallion on 2015-04-24
This is still a thing. Primarily when waking after sleep, now.

---

### Post by kurt18947 on 2015-04-24
> **Ratscallion said:**
> This is still a thing. Primarily when waking after sleep, now.

There was a problem with some adapters years ago that would exhibit problems with working after a suspend/resume cycle. The cause was the wifi device's module not removing itself cleanly. When the machine tried to resume, it tried to reload the module but couldn't do so cleanly due to remnants from the previous session. I haven't seen this problem for quite some time, I assume it was fixed. I wonder if it would be worth trying something like this:

```

sudo modprobe -r ath9k (should remove ath9k modules)
sudo modprobe ath9k (should reload ath9k modules)

```
You could check that all ath9k entries are removed by running "lsmod" in a terminal before running the second line.

I would think though that a power cycle would clear any residual driver problems.

---

### Post by Ratscallion on 2015-04-24
> **kurt18947 said:**
> 

I would think though that a power cycle would clear any residual driver problems.

This is true - powering off for a few minutes and then rebooting makes things work again. A straight reboot does not. I'll give the code a go on the next occasion and report back. Thanks :)

---

