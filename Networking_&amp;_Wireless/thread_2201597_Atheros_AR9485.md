---
title: "Atheros AR9485"
date: 2014-01-25
forum: Networking &amp; Wireless
---

### Post by ethan6 on 2014-01-25
hi guys, i have a asus k450j. hope someone can assist me in solving my wireless problem.
more info: i am on dual boot, windows8 and ubuntu 13.1. wireless on my windows partition is working perfectly fine


uname -mr
lspci -nnk | grep -A2 0280
```


ubuntu:~$ uname -mr
3.11.0-12-generic x86_64

ubuntu:~$ lspci -nnk | grep -A2 0280
03:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: AzureWave Device [1a3b:2c97]
    Kernel driver in use: ath9k

```



then i downloaded the script and run it on terminal

```



*************** info trace ***************

***** uname -a *****

Linux yk-ubuntu 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy

***** lspci *****

03:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: AzureWave Device [1a3b:2c97]
    Kernel driver in use: ath9k
04:00.0 Ethernet controller [0200]: Qualcomm Atheros QCA8171 Gigabit Ethernet [1969:10a1] (rev 10)
    Subsystem: Qualcomm Atheros Device [1969:1091]
    Kernel driver in use: alx

***** lsusb *****

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 13d3:5188 IMC Networks 
Bus 003 Device 002: ID 1532:0012 Razer USA, Ltd 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

***** rfkill *****

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

***** lsmod *****

ath9k                 151173  0 
ath9k_common           13859  1 ath9k
ath9k_hw              444645  2 ath9k_common,ath9k
ath                    23827  3 ath9k_common,ath9k,ath9k_hw
mac80211              596969  1 ath9k
cfg80211              479757  3 ath,ath9k,mac80211

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            alx
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 



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


***** resolv.conf *****

nameserver 127.0.1.1

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

filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     3C8D10ED309094E2B73D591
alias:          platform:qca955x_wmac
alias:          platform:ar934x_wmac
alias:          platform:ar933x_wmac
alias:          platform:ath9k
alias:          pci:v0000168Cd00000036sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000037sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv000010CFsd00001783bc*sc*i*
alias:          pci:v0000168Cd00000034sv000014CDsd00000064bc*sc*i*
alias:          pci:v0000168Cd00000034sv000014CDsd00000063bc*sc*i*
alias:          pci:v0000168Cd00000034sv0000103Csd00001864bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006641bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006631bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001043sd0000850Ebc*sc*i*
alias:          pci:v0000168Cd00000034sv00001A3Bsd00002110bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001969sd00000091bc*sc*i*
alias:          pci:v0000168Cd00000034sv000017AAsd00003214bc*sc*i*
alias:          pci:v0000168Cd00000034sv0000168Csd00003117bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006661bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001A3Bsd00002116bc*sc*i*
alias:          pci:v0000168Cd00000033sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000105Bsd0000E075bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002152bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002126bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001237bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002086bc*sc*i*
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
vermagic:       3.11.0-12-generic SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           enable_diversity:Enable Antenna diversity for AR9565 (int)

filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     2DB88A2876852DC1D8C5A1D
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.11.0-12-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     57A1E15BE088B8A5C4BE74F
depends:        ath
intree:         Y
vermagic:       3.11.0-12-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     A890CDBC88E6EF28CD751DD
depends:        cfg80211
intree:         Y
vermagic:       3.11.0-12-generic SMP mod_unload modversions 


***** udev rules *****

# PCI device 0x1969:0x10a1 (alx)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC  address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1",  KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:0x0032 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC  address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1",  KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[   11.324998] ath9k 0000:03:00.0: enabling device (0000 -> 0002)
[   11.332194] ath: EEPROM regdomain: 0x60
[   11.332195] ath: EEPROM indicates we should expect a direct regpair map
[   11.332197] ath: Country alpha2 being used: 00
[   11.332197] ath: Regpair used: 0x60
[   12.278138] psmouse serio1: elantech: assuming hardware version 4 (with firmware version 0x361f01)
[   16.913460] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.928052] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   41.853096] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   45.795894] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   63.653253] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   64.418526] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   65.256455] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   66.326561] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   76.102882] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   77.263445] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  212.591895] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  598.112039] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  769.915873] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  848.710583] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  877.968781] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  878.180955] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  888.664060] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1285.811393] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1293.693552] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1506.448896] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

****************** done ******************




```

---

### Post by varunendra on 2014-01-25
> **ethan6 said:**
> hi guys, i have a asus k450j.
Asus ? Are you sure? Because the kernel thinks you have an acer -
```

***** rfkill *****

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: **[COLOR="#FF0000"]acer-wireless[/COLOR]**: Wireless LAN
    **Soft blocked: [COLOR="#FF0000"]yes[/COLOR]**
    Hard blocked: no

```

Please post back the full output of -
```
lsmod
```
If the output includes "acer_wmi", try this -
```
echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
..then reboot and check -
```
rfkill list
lsmod | grep acer
```
The first one's output should show no hard or soft blocks. If so, can you now scan networks and connect to them?
If not, run the second command and make sure 'acer_wmi' is not there.

Of course this workaround applies only if the module "acer_wmi" is loaded, while the laptop is Asus, not Acer.

Post back whatever happens, and we may try something else as and if required.

---

### Post by ethan6 on 2014-01-25
[SIZE=4]**Thank Varunendra, i can connect to wireless after following your instructions.**[/SIZE]

haha, yes, it is a asus laptop. but i really got no idea why there are acer being detected.
> **varunendra said:**
> Asus ? Are you sure? Because the kernel thinks you have an acer -
```

***** rfkill *****

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: **[COLOR=#FF0000]acer-wireless[/COLOR]**: Wireless LAN
    **Soft blocked: [COLOR=#FF0000]yes[/COLOR]**
    Hard blocked: no

```



Full output of the command 'lsmod' before blacklisting 
```

yk@yk-ubuntu:~$ lsmod
Module                  Size  Used by
nvram                  14362  0 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
parport_pc             32701  0 
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40499  1 uvcvideo
videodev              133509  2 uvcvideo,videobuf2_core
ppdev                  17671  0 
bnep                   19704  2 
rfcomm                 69130  12 
x86_pkg_temp_thermal    14162  0 
coretemp               13435  0 
kvm_intel             138567  0 
kvm                   431720  1 kvm_intel
nls_iso8859_1          12713  2 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
snd_hda_codec_hdmi     41117  1 
snd_hda_codec_realtek    55704  1 
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
joydev                 17377  0 
acer_wmi               32522  0 
asus_nb_wmi            16990  0 
asus_wmi               24191  1 asus_nb_wmi
sparse_keymap          13948  2 acer_wmi,asus_wmi
ath3k                  13318  0 
btusb                  28267  0 
bluetooth             372041  23 bnep,ath3k,btusb,rfcomm
arc4                   12608  2 
ath9k                 155779  0 
snd_hda_intel          48171  5 
snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
ath9k_common           13859  1 ath9k
ath9k_hw              444732  2 ath9k_common,ath9k
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
nouveau               943717  0 
ath                    23827  3 ath9k_common,ath9k,ath9k_hw
mac80211              597268  1 ath9k
i915                  661261  5 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
cfg80211              480503  3 ath,ath9k,mac80211
mxm_wmi                13021  1 nouveau
snd_rawmidi            30095  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
ttm                    84169  1 nouveau
mei_me                 18421  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
mei                    77782  1 mei_me
drm_kms_helper         52710  2 i915,nouveau
drm                   297056  6 ttm,i915,drm_kms_helper,nouveau
snd                    69141  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
psmouse                97655  0 
soundcore              12680  1 snd
i2c_algo_bit           13413  2 i915,nouveau
lpc_ich                21080  0 
mac_hid                13205  0 
serio_raw              13413  0 
wmi                    19070  4 acer_wmi,mxm_wmi,nouveau,asus_wmi
video                  19318  4 i915,acer_wmi,nouveau,asus_wmi
microcode              23576  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
usb_storage            62062  1 
hid_generic            12548  0 
usbhid                 53014  0 
hid                   105858  2 hid_generic,usbhid
alx                    32452  0 
ahci                   25819  4 
libahci                31928  1 ahci
mdio                   13807  1 alx

```



"acer_wmi" exist, so i  tried  the following and acer-wireless is not there anymore when i run the command 'rfkill list' :
> 
If the output includes "acer_wmi", try this -
```
echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
..then reboot and check -
```
rfkill list
lsmod | grep acer
```


---

### Post by varunendra on 2014-01-25
Glad you sorted it out, and I forgot something more important earlier -

**[FONT=Comic Sans MS][COLOR="#800000"]Welcome to Ubuntu Forums !![/COLOR][/FONT]** :P

---

