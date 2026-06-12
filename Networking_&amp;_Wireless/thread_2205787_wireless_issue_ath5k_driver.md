---
title: "wireless issue ath5k driver"
date: 2014-02-15
forum: Networking &amp; Wireless
---

### Post by jmorri36 on 2014-02-15
Hi, I'm having similar issues with my WPA wireless.  I can log onto most WPA networks, but I can't log onto the WPA network in my home.  Here are the details from your script.  

Any help would be greatly appreciated! Thanks!

```


*************** info trace ***************


***** uname -a *****


Linux MiniLinux 3.11.0-15-generic #25~precise1-Ubuntu SMP Thu Jan 30 17:42:40 UTC 2014 i686 i686 i386 GNU/Linux


***** lsb_release *****


Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise


***** lspci *****


02:00.0 Ethernet controller [0200]: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: Askey Computer Corp. Device [144f:7130]
    Kernel driver in use: ath5k
--
03:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 13)
    Subsystem: Samsung Electronics Co Ltd Device [144d:ca00]
    Kernel driver in use: sky2


***** lsusb *****


Bus 001 Device 003: ID 0ac8:c326 Z-Star Microelectronics Corp. Namuga 1.3M Webcam
Bus 003 Device 002: ID 0a5c:2101 Broadcom Corp. Bluetooth Controller
Bus 004 Device 002: ID 04f2:0939 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


***** PCMCIA Card Info *****




***** iwconfig *****


wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


***** rfkill *****


0: samsung-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


***** lsmod *****


ath5k                 141236  0 
ath                    19435  1 ath5k
mac80211              534884  1 ath5k
cfg80211              416271  3 ath5k,ath,mac80211


***** nm-tool *****


NetworkManager Tool


State: connecting


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off




- Device: wlan0  [The Feinberg] ------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             connecting (configuring)
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 
    MyWi Josephs-iPhone: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 59 WPA2
    CS_Wireless2.4:  Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    Jerard:          Infra, <MAC address removed>, Freq 2452 MHz, Rate 54 Mb/s, Strength 20 WPA2
    Jerard Guest:    Infra, <MAC address removed>, Freq 2452 MHz, Rate 54 Mb/s, Strength 20 WPA2
    MADE:            Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA2
    SBG65800A:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 17 WPA2
    TWCWiFi:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 19
    xfinitywifi:     Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 17
    dlink:           Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 19
    HP4DD136:        Ad-Hoc, <MAC address removed>, Freq 2457 MHz, Rate 11 Mb/s, Strength 10
    CableWiFi:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 17
    optimumwifi:     Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 17
    xfinitywifi:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0
    TWCWiFi:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 4
    optimumwifi:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 4
    The Feinberg:    Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 60 WPA2






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




***** iwlist *****




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


***** modinfo *****


filename:       /lib/modules/3.11.0-15-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
license:        Dual BSD/GPL
description:    Support for 5xxx series of Atheros 802.11 wireless LAN cards.
author:         Nick Kossifidis
author:         Jiri Slaby
srcversion:     B7A923930DCF3B82CF57D26
alias:          pci:v0000168Cd0000FF1Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000019sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000018sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000017sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000016sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000015sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000014sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00001014sv*sd*bc*sc*i*
alias:          pci:v000010B7d00000013sv*sd*bc*sc*i*
alias:          pci:v0000A727d00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000012sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000011sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000007sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000207sv*sd*bc*sc*i*
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       3.11.0-15-generic SMP mod_unload modversions 686 
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)


filename:       /lib/modules/3.11.0-15-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     A890CDBC88E6EF28CD751DD
depends:        cfg80211
intree:         Y
vermagic:       3.11.0-15-generic SMP mod_unload modversions 686 




***** udev rules *****


# PCI device 0x11ab:/sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0 (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


***** dmesg *****


[ 2595.334244] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2595.336419] wlan0: authenticated
[ 2595.340119] wlan0: associate with <MAC address removed> (try 1/3)
[ 2595.344130] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=14)
[ 2595.344146] wlan0: <MAC address removed> denied association (code=27)
[ 2595.353674] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2596.113537] wlan0: authenticate with <MAC address removed>
[ 2596.116829] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2596.118738] wlan0: authenticated
[ 2596.128112] wlan0: associate with <MAC address removed> (try 1/3)
[ 2596.130856] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 2596.130872] wlan0: <MAC address removed> denied association (code=27)
[ 2596.144505] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2596.914919] wlan0: authenticate with <MAC address removed>
[ 2596.915273] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2596.917182] wlan0: authenticated
[ 2596.924117] wlan0: associate with <MAC address removed> (try 1/3)
[ 2596.926724] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=128)
[ 2596.926741] wlan0: <MAC address removed> denied association (code=27)
[ 2596.944496] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2597.706673] wlan0: authenticate with <MAC address removed>
[ 2597.711171] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2597.715119] wlan0: authenticated
[ 2597.716482] wlan0: associate with <MAC address removed> (try 1/3)
[ 2597.719083] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=128)
[ 2597.719103] wlan0: <MAC address removed> denied association (code=27)
[ 2597.721309] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2598.481558] wlan0: authenticate with <MAC address removed>
[ 2598.486283] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2598.488736] wlan0: authenticated
[ 2598.492181] wlan0: associate with <MAC address removed> (try 1/3)
[ 2598.494799] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=128)
[ 2598.494814] wlan0: <MAC address removed> denied association (code=27)
[ 2598.504570] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2599.265950] wlan0: authenticate with <MAC address removed>
[ 2599.270447] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2599.272416] wlan0: authenticated
[ 2599.277138] wlan0: associate with <MAC address removed> (try 1/3)
[ 2599.279774] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=3094)
[ 2599.279789] wlan0: <MAC address removed> denied association (code=27)
[ 2599.284581] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2600.045751] wlan0: authenticate with <MAC address removed>
[ 2600.051041] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2600.053278] wlan0: authenticated
[ 2600.060155] wlan0: associate with <MAC address removed> (try 1/3)
[ 2600.062853] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=4650)
[ 2600.062869] wlan0: <MAC address removed> denied association (code=27)
[ 2600.072437] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2600.833760] wlan0: authenticate with <MAC address removed>
[ 2600.837763] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2600.840502] wlan0: authenticated
[ 2600.844165] wlan0: associate with <MAC address removed> (try 1/3)
[ 2600.846792] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 2600.846808] wlan0: <MAC address removed> denied association (code=27)
[ 2600.856627] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2601.617648] wlan0: authenticate with <MAC address removed>
[ 2601.621855] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2601.627340] wlan0: authenticated
[ 2601.628345] wlan0: associate with <MAC address removed> (try 1/3)
[ 2601.630986] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=128)
[ 2601.631007] wlan0: <MAC address removed> denied association (code=27)
[ 2601.641016] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2602.401643] wlan0: authenticate with <MAC address removed>
[ 2602.408990] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2602.414290] wlan0: authenticated
[ 2602.416089] wlan0: associate with <MAC address removed> (try 1/3)
[ 2602.419009] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=3094)
[ 2602.419027] wlan0: <MAC address removed> denied association (code=27)
[ 2602.424993] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2603.185841] wlan0: authenticate with <MAC address removed>
[ 2603.190191] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2603.195740] wlan0: authenticated
[ 2603.200128] wlan0: associate with <MAC address removed> (try 1/3)
[ 2603.202907] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 2603.202923] wlan0: <MAC address removed> denied association (code=27)
[ 2603.220167] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2603.981819] wlan0: authenticate with <MAC address removed>
[ 2603.985865] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2603.988518] wlan0: authenticated
[ 2603.992525] wlan0: associate with <MAC address removed> (try 1/3)
[ 2603.995900] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 2603.995916] wlan0: <MAC address removed> denied association (code=27)
[ 2604.008662] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2604.769945] wlan0: authenticate with <MAC address removed>
[ 2604.774939] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2604.782954] wlan0: authenticated
[ 2604.788435] wlan0: associate with <MAC address removed> (try 1/3)
[ 2604.791376] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=4651)
[ 2604.791398] wlan0: <MAC address removed> denied association (code=27)
[ 2604.804607] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2605.565727] wlan0: authenticate with <MAC address removed>
[ 2605.570017] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2605.571923] wlan0: authenticated
[ 2605.576150] wlan0: associate with <MAC address removed> (try 1/3)
[ 2605.578796] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=3094)
[ 2605.578811] wlan0: <MAC address removed> denied association (code=27)
[ 2605.588980] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2606.350205] wlan0: authenticate with <MAC address removed>
[ 2606.354499] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2606.356460] wlan0: authenticated
[ 2606.360570] wlan0: associate with <MAC address removed> (try 1/3)
[ 2606.363152] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 2606.363168] wlan0: <MAC address removed> denied association (code=27)
[ 2606.368592] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2607.130541] wlan0: authenticate with <MAC address removed>
[ 2607.136717] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2607.244106] wlan0: send auth to <MAC address removed> (try 2/3)
[ 2607.246241] wlan0: authenticated
[ 2607.248104] wlan0: associate with <MAC address removed> (try 1/3)
[ 2607.250715] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=13838)
[ 2607.250732] wlan0: <MAC address removed> denied association (code=27)
[ 2607.268533] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2608.029648] wlan0: authenticate with <MAC address removed>
[ 2608.032812] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2608.035095] wlan0: authenticated
[ 2608.048113] wlan0: associate with <MAC address removed> (try 1/3)
[ 2608.051221] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 2608.051237] wlan0: <MAC address removed> denied association (code=27)
[ 2608.068498] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2608.829642] wlan0: authenticate with <MAC address removed>
[ 2608.834558] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2608.841354] wlan0: authenticated
[ 2608.844488] wlan0: associate with <MAC address removed> (try 1/3)
[ 2608.847298] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 2608.847314] wlan0: <MAC address removed> denied association (code=27)
[ 2608.857721] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2609.617604] wlan0: authenticate with <MAC address removed>
[ 2609.622571] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2609.629968] wlan0: authenticated
[ 2609.632413] wlan0: associate with <MAC address removed> (try 1/3)
[ 2609.635029] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=10523)
[ 2609.635045] wlan0: <MAC address removed> denied association (code=27)
[ 2609.648545] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2610.410585] wlan0: authenticate with <MAC address removed>
[ 2610.419295] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2610.427394] wlan0: authenticated
[ 2610.432250] wlan0: associate with <MAC address removed> (try 1/3)
[ 2610.435004] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=10523)
[ 2610.435019] wlan0: <MAC address removed> denied association (code=27)
[ 2610.449140] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2611.206642] wlan0: authenticate with <MAC address removed>
[ 2611.212884] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2611.222080] wlan0: authenticated
[ 2611.224094] wlan0: associate with <MAC address removed> (try 1/3)
[ 2611.227156] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 2611.227171] wlan0: <MAC address removed> denied association (code=27)
[ 2611.236557] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2611.997685] wlan0: authenticate with <MAC address removed>
[ 2612.001976] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2612.005635] wlan0: authenticated
[ 2612.008189] wlan0: associate with <MAC address removed> (try 1/3)
[ 2612.010818] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=128)
[ 2612.010838] wlan0: <MAC address removed> denied association (code=27)
[ 2612.024641] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2612.785672] wlan0: authenticate with <MAC address removed>
[ 2612.789982] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2612.798233] wlan0: authenticated
[ 2612.800119] wlan0: associate with <MAC address removed> (try 1/3)
[ 2612.802726] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=3094)
[ 2612.802752] wlan0: <MAC address removed> denied association (code=27)
[ 2612.808550] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2613.569913] wlan0: authenticate with <MAC address removed>
[ 2613.574239] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2613.579374] wlan0: authenticated
[ 2613.580489] wlan0: associate with <MAC address removed> (try 1/3)
[ 2613.584710] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 2613.584732] wlan0: <MAC address removed> denied association (code=27)
[ 2613.603734] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2614.368261] wlan0: authenticate with <MAC address removed>
[ 2614.371086] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2614.374815] wlan0: authenticated
[ 2614.376485] wlan0: associate with <MAC address removed> (try 1/3)
[ 2614.379194] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 2614.379210] wlan0: <MAC address removed> denied association (code=27)
[ 2614.416556] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2615.177771] wlan0: authenticate with <MAC address removed>
[ 2615.181748] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2615.185757] wlan0: authenticated
[ 2615.188101] wlan0: associate with <MAC address removed> (try 1/3)
[ 2615.192968] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=12047)
[ 2615.192990] wlan0: <MAC address removed> denied association (code=27)
[ 2615.200585] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2615.961761] wlan0: authenticate with <MAC address removed>
[ 2615.966308] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2615.968448] wlan0: authenticated
[ 2615.972273] wlan0: associate with <MAC address removed> (try 1/3)
[ 2615.974858] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=128)
[ 2615.974874] wlan0: <MAC address removed> denied association (code=27)
[ 2615.984597] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2616.749799] wlan0: authenticate with <MAC address removed>
[ 2616.754601] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2616.762769] wlan0: authenticated
[ 2616.764481] wlan0: associate with <MAC address removed> (try 1/3)
[ 2616.767355] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=4654)
[ 2616.767371] wlan0: <MAC address removed> denied association (code=27)
[ 2616.776560] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2617.537857] wlan0: authenticate with <MAC address removed>
[ 2617.542321] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2617.546048] wlan0: authenticated
[ 2617.548152] wlan0: associate with <MAC address removed> (try 1/3)
[ 2617.550784] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=4654)
[ 2617.550803] wlan0: <MAC address removed> denied association (code=27)
[ 2617.564528] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2618.325706] wlan0: authenticate with <MAC address removed>
[ 2618.329722] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2618.334133] wlan0: authenticated
[ 2618.336243] wlan0: associate with <MAC address removed> (try 1/3)
[ 2618.338882] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 2618.338903] wlan0: <MAC address removed> denied association (code=27)
[ 2618.344613] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2619.105744] wlan0: authenticate with <MAC address removed>
[ 2619.109737] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2619.112083] wlan0: authenticated
[ 2619.116205] wlan0: associate with <MAC address removed> (try 1/3)
[ 2619.119017] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=128)
[ 2619.119032] wlan0: <MAC address removed> denied association (code=27)
[ 2619.152643] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2619.913711] wlan0: authenticate with <MAC address removed>
[ 2619.918312] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2619.922279] wlan0: authenticated
[ 2619.924231] wlan0: associate with <MAC address removed> (try 1/3)
[ 2619.926919] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=4654)
[ 2619.926939] wlan0: <MAC address removed> denied association (code=27)
[ 2619.937016] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2620.697710] wlan0: authenticate with <MAC address removed>
[ 2620.701755] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2620.705109] wlan0: authenticated
[ 2620.708241] wlan0: associate with <MAC address removed> (try 1/3)
[ 2620.710896] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 2620.710912] wlan0: <MAC address removed> denied association (code=27)
[ 2620.716570] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2621.478051] wlan0: authenticate with <MAC address removed>
[ 2621.481083] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2621.483009] wlan0: authenticated
[ 2621.485177] wlan0: associate with <MAC address removed> (try 1/3)
[ 2621.487794] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 2621.487815] wlan0: <MAC address removed> denied association (code=27)
[ 2621.493019] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2622.254030] wlan0: authenticate with <MAC address removed>
[ 2622.258638] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2622.263431] wlan0: authenticated
[ 2622.264700] wlan0: associate with <MAC address removed> (try 1/3)
[ 2622.267331] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=3094)
[ 2622.267353] wlan0: <MAC address removed> denied association (code=27)
[ 2622.272590] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2623.033691] wlan0: authenticate with <MAC address removed>
[ 2623.038497] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2623.040843] wlan0: authenticated
[ 2623.044616] wlan0: associate with <MAC address removed> (try 1/3)
[ 2623.048485] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=4654)
[ 2623.048501] wlan0: <MAC address removed> denied association (code=27)
[ 2623.060571] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2623.821611] wlan0: authenticate with <MAC address removed>
[ 2623.826525] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2623.832225] wlan0: authenticated
[ 2623.836219] wlan0: associate with <MAC address removed> (try 1/3)
[ 2623.839739] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=3094)
[ 2623.839751] wlan0: <MAC address removed> denied association (code=27)
[ 2623.856449] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2624.617781] wlan0: authenticate with <MAC address removed>
[ 2624.621848] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2624.625050] wlan0: authenticated
[ 2624.628159] wlan0: associate with <MAC address removed> (try 1/3)
[ 2624.630797] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=128)
[ 2624.630816] wlan0: <MAC address removed> denied association (code=27)
[ 2624.701212] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2625.461717] wlan0: authenticate with <MAC address removed>
[ 2625.466339] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2625.471393] wlan0: authenticated
[ 2625.472541] wlan0: associate with <MAC address removed> (try 1/3)
[ 2625.475090] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=10523)
[ 2625.475104] wlan0: <MAC address removed> denied association (code=27)
[ 2625.477572] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2626.237833] wlan0: authenticate with <MAC address removed>
[ 2626.241740] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2626.244572] wlan0: authenticated
[ 2626.248189] wlan0: associate with <MAC address removed> (try 1/3)
[ 2626.252700] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=3094)
[ 2626.252723] wlan0: <MAC address removed> denied association (code=27)
[ 2626.261026] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2627.021602] wlan0: authenticate with <MAC address removed>
[ 2627.024922] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2627.029239] wlan0: authenticated
[ 2627.032088] wlan0: associate with <MAC address removed> (try 1/3)
[ 2627.034705] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 2627.034758] wlan0: <MAC address removed> denied association (code=27)
[ 2627.044604] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2627.805934] wlan0: authenticate with <MAC address removed>
[ 2627.810330] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2627.819879] wlan0: authenticated
[ 2627.824077] wlan0: associate with <MAC address removed> (try 1/3)
[ 2627.827202] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=12303)
[ 2627.827217] wlan0: <MAC address removed> denied association (code=27)
[ 2627.840378] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2628.601760] wlan0: authenticate with <MAC address removed>
[ 2628.606119] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2628.612643] wlan0: authenticated
[ 2628.616237] wlan0: associate with <MAC address removed> (try 1/3)
[ 2628.619355] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=7449)
[ 2628.619371] wlan0: <MAC address removed> denied association (code=27)
[ 2628.625022] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2629.385630] wlan0: authenticate with <MAC address removed>
[ 2629.391097] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2629.396981] wlan0: authenticated
[ 2629.400454] wlan0: associate with <MAC address removed> (try 1/3)
[ 2629.403394] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 2629.403410] wlan0: <MAC address removed> denied association (code=27)
[ 2629.412556] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2630.173593] wlan0: authenticate with <MAC address removed>
[ 2630.178296] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2630.181102] wlan0: authenticated
[ 2630.184180] wlan0: associate with <MAC address removed> (try 1/3)
[ 2630.186818] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=128)
[ 2630.186843] wlan0: <MAC address removed> denied association (code=27)
[ 2630.197020] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2630.957788] wlan0: authenticate with <MAC address removed>
[ 2630.963975] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2630.968612] wlan0: authenticated
[ 2630.972143] wlan0: associate with <MAC address removed> (try 1/3)
[ 2630.975594] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=128)
[ 2630.975610] wlan0: <MAC address removed> denied association (code=27)
[ 2631.008598] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2631.773871] wlan0: authenticate with <MAC address removed>
[ 2631.777681] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2631.781017] wlan0: authenticated
[ 2631.784170] wlan0: associate with <MAC address removed> (try 1/3)
[ 2631.786845] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=10523)
[ 2631.786859] wlan0: <MAC address removed> denied association (code=27)
[ 2631.793011] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2632.553912] wlan0: authenticate with <MAC address removed>
[ 2632.557783] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2632.562782] wlan0: authenticated
[ 2632.564438] wlan0: associate with <MAC address removed> (try 1/3)
[ 2632.567070] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=3094)
[ 2632.567092] wlan0: <MAC address removed> denied association (code=27)
[ 2632.576572] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2633.339039] wlan0: authenticate with <MAC address removed>
[ 2633.345746] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2633.347916] wlan0: authenticated
[ 2633.352172] wlan0: associate with <MAC address removed> (try 1/3)
[ 2633.354792] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=10523)
[ 2633.354807] wlan0: <MAC address removed> denied association (code=27)
[ 2633.365015] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2634.125777] wlan0: authenticate with <MAC address removed>
[ 2634.129745] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2634.133433] wlan0: authenticated
[ 2634.136131] wlan0: associate with <MAC address removed> (try 1/3)
[ 2634.139365] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=128)
[ 2634.139380] wlan0: <MAC address removed> denied association (code=27)
[ 2634.148580] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2634.911953] wlan0: authenticate with <MAC address removed>
[ 2634.916195] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2634.918099] wlan0: authenticated
[ 2634.921154] wlan0: associate with <MAC address removed> (try 1/3)
[ 2634.923756] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=3094)
[ 2634.923781] wlan0: <MAC address removed> denied association (code=27)
[ 2634.932859] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2635.693819] wlan0: authenticate with <MAC address removed>
[ 2635.698530] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2635.701919] wlan0: authenticated
[ 2635.704208] wlan0: associate with <MAC address removed> (try 1/3)
[ 2635.706902] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 2635.706923] wlan0: <MAC address removed> denied association (code=27)
[ 2635.727028] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2636.489866] wlan0: authenticate with <MAC address removed>
[ 2636.493885] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2636.495809] wlan0: authenticated
[ 2636.500109] wlan0: associate with <MAC address removed> (try 1/3)
[ 2636.502877] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=13328)
[ 2636.502895] wlan0: <MAC address removed> denied association (code=27)
[ 2636.505230] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2637.265786] wlan0: authenticate with <MAC address removed>
[ 2637.268882] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2637.273008] wlan0: authenticated
[ 2637.276097] wlan0: associate with <MAC address removed> (try 1/3)
[ 2637.278728] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=10523)
[ 2637.278749] wlan0: <MAC address removed> denied association (code=27)
[ 2637.285013] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2638.045784] wlan0: authenticate with <MAC address removed>
[ 2638.048908] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2638.051661] wlan0: authenticated
[ 2638.056174] wlan0: associate with <MAC address removed> (try 1/3)
[ 2638.059511] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=4634)
[ 2638.059527] wlan0: <MAC address removed> denied association (code=27)
[ 2638.068588] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2638.829588] wlan0: authenticate with <MAC address removed>
[ 2638.832846] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2638.836399] wlan0: authenticated
[ 2638.841502] wlan0: associate with <MAC address removed> (try 1/3)
[ 2638.844145] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=4653)
[ 2638.844171] wlan0: <MAC address removed> denied association (code=27)
[ 2638.848998] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2639.609984] wlan0: authenticate with <MAC address removed>
[ 2639.615044] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2639.618961] wlan0: authenticated
[ 2639.620561] wlan0: associate with <MAC address removed> (try 1/3)
[ 2639.623733] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=128)
[ 2639.623749] wlan0: <MAC address removed> denied association (code=27)
[ 2639.636531] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2640.389833] wlan0: authenticate with <MAC address removed>
[ 2640.393725] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2640.397273] wlan0: authenticated
[ 2640.400159] wlan0: associate with <MAC address removed> (try 1/3)
[ 2640.403103] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=10523)
[ 2640.403119] wlan0: <MAC address removed> denied association (code=27)
[ 2640.416581] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2641.177766] wlan0: authenticate with <MAC address removed>
[ 2641.181738] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2641.185174] wlan0: authenticated
[ 2641.188243] wlan0: associate with <MAC address removed> (try 1/3)
[ 2641.190939] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 2641.190955] wlan0: <MAC address removed> denied association (code=27)
[ 2641.200980] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2641.961902] wlan0: authenticate with <MAC address removed>
[ 2641.965817] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2641.970862] wlan0: authenticated
[ 2641.972412] wlan0: associate with <MAC address removed> (try 1/3)
[ 2641.975035] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=10523)
[ 2641.975048] wlan0: <MAC address removed> denied association (code=27)
[ 2641.980571] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2642.741904] wlan0: authenticate with <MAC address removed>
[ 2642.745752] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2642.749446] wlan0: authenticated
[ 2642.753271] wlan0: associate with <MAC address removed> (try 1/3)
[ 2642.756778] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=10523)
[ 2642.756795] wlan0: <MAC address removed> denied association (code=27)
[ 2642.780521] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2643.541763] wlan0: authenticate with <MAC address removed>
[ 2643.545728] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2643.548464] wlan0: authenticated
[ 2643.552185] wlan0: associate with <MAC address removed> (try 1/3)
[ 2643.554786] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=3094)
[ 2643.554801] wlan0: <MAC address removed> denied association (code=27)
[ 2643.564667] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2644.333837] wlan0: authenticate with <MAC address removed>
[ 2644.338630] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2644.341941] wlan0: authenticated
[ 2644.348360] wlan0: associate with <MAC address removed> (try 1/3)
[ 2644.351048] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=128)
[ 2644.351070] wlan0: <MAC address removed> denied association (code=27)
[ 2644.360600] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2645.125808] wlan0: authenticate with <MAC address removed>
[ 2645.130396] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2645.133519] wlan0: authenticated
[ 2645.136188] wlan0: associate with <MAC address removed> (try 1/3)
[ 2645.138970] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=3094)
[ 2645.138988] wlan0: <MAC address removed> denied association (code=27)
[ 2645.148553] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2645.909758] wlan0: authenticate with <MAC address removed>
[ 2645.914274] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2645.917448] wlan0: authenticated
[ 2645.920249] wlan0: associate with <MAC address removed> (try 1/3)
[ 2645.922845] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=1041)
[ 2645.922857] wlan0: <MAC address removed> denied association (code=27)
[ 2645.928573] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2646.689940] wlan0: authenticate with <MAC address removed>
[ 2646.694049] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2646.698802] wlan0: authenticated
[ 2646.700500] wlan0: associate with <MAC address removed> (try 1/3)
[ 2646.703194] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=10523)
[ 2646.703206] wlan0: <MAC address removed> denied association (code=27)
[ 2646.712546] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2647.473842] wlan0: authenticate with <MAC address removed>
[ 2647.477731] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2647.482274] wlan0: authenticated
[ 2647.484124] wlan0: associate with <MAC address removed> (try 1/3)
[ 2647.486792] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 2647.486815] wlan0: <MAC address removed> denied association (code=27)
[ 2647.496619] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2648.257743] wlan0: authenticate with <MAC address removed>
[ 2648.261791] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2648.265138] wlan0: authenticated
[ 2648.268173] wlan0: associate with <MAC address removed> (try 1/3)
[ 2648.271259] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=4654)
[ 2648.271275] wlan0: <MAC address removed> denied association (code=27)
[ 2648.276590] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2649.037838] wlan0: authenticate with <MAC address removed>
[ 2649.041767] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2649.046142] wlan0: authenticated
[ 2649.048158] wlan0: associate with <MAC address removed> (try 1/3)
[ 2649.050785] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 2649.050805] wlan0: <MAC address removed> denied association (code=27)
[ 2649.056966] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2649.817649] wlan0: authenticate with <MAC address removed>
[ 2649.820737] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2649.825220] wlan0: authenticated
[ 2649.828091] wlan0: associate with <MAC address removed> (try 1/3)
[ 2649.830726] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 2649.830748] wlan0: <MAC address removed> denied association (code=27)
[ 2649.909023] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2650.669817] wlan0: authenticate with <MAC address removed>
[ 2650.674494] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2650.678175] wlan0: authenticated
[ 2650.680125] wlan0: associate with <MAC address removed> (try 1/3)
[ 2650.683408] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=4653)
[ 2650.683429] wlan0: <MAC address removed> denied association (code=27)
[ 2650.716530] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2651.477872] wlan0: authenticate with <MAC address removed>
[ 2651.481781] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2651.485443] wlan0: authenticated
[ 2651.488244] wlan0: associate with <MAC address removed> (try 1/3)
[ 2651.490963] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=10523)
[ 2651.490981] wlan0: <MAC address removed> denied association (code=27)
[ 2651.496593] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2652.257839] wlan0: authenticate with <MAC address removed>
[ 2652.262640] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2652.266615] wlan0: authenticated
[ 2652.268089] wlan0: associate with <MAC address removed> (try 1/3)
[ 2652.270999] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 2652.271020] wlan0: <MAC address removed> denied association (code=27)
[ 2652.276606] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2653.037873] wlan0: authenticate with <MAC address removed>
[ 2653.041926] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2653.047189] wlan0: authenticated
[ 2653.048103] wlan0: associate with <MAC address removed> (try 1/3)
[ 2653.050811] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 2653.050826] wlan0: <MAC address removed> denied association (code=27)
[ 2653.060592] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2653.821874] wlan0: authenticate with <MAC address removed>
[ 2653.826625] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2653.829241] wlan0: authenticated
[ 2653.832197] wlan0: associate with <MAC address removed> (try 1/3)
[ 2653.834927] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=128)
[ 2653.834956] wlan0: <MAC address removed> denied association (code=27)
[ 2653.840668] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2654.601819] wlan0: authenticate with <MAC address removed>
[ 2654.606463] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2654.610000] wlan0: authenticated
[ 2654.612106] wlan0: associate with <MAC address removed> (try 1/3)
[ 2654.614743] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=2321)
[ 2654.614764] wlan0: <MAC address removed> denied association (code=27)
[ 2654.620597] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2778.689695] wlan0: authenticate with <MAC address removed>
[ 2778.693042] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2778.719530] wlan0: send auth to <MAC address removed> (try 2/3)
[ 2778.743709] wlan0: authenticated
[ 2778.748181] wlan0: associate with <MAC address removed> (try 1/3)
[ 2778.784092] wlan0: RX AssocResp from <MAC address removed> (capab=0x421 status=0 aid=8)
[ 2778.784829] wlan0: associated
[ 2794.198019] wlan0: authenticate with <MAC address removed>
[ 2794.202974] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2794.215790] wlan0: send auth to <MAC address removed> (try 2/3)
[ 2794.238178] wlan0: send auth to <MAC address removed> (try 3/3)
[ 2794.260545] wlan0: authentication with <MAC address removed> timed out
[ 2795.036500] wlan0: authenticate with <MAC address removed>
[ 2795.043051] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2795.244141] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2795.448176] wlan0: send auth to <MAC address removed> (try 3/3)
[ 2795.556119] wlan0: authentication with <MAC address removed> timed out
[ 2799.206172] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2807.050617] wlan0: authenticate with <MAC address removed>
[ 2807.050972] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2807.252091] wlan0: send auth to <MAC address removed> (try 2/3)
[ 2807.280331] wlan0: authenticated
[ 2807.284136] wlan0: associate with <MAC address removed> (try 1/3)
[ 2807.307643] wlan0: RX AssocResp from <MAC address removed> (capab=0x421 status=0 aid=67)
[ 2807.308473] wlan0: associated
[ 2824.217476] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2827.682456] wlan0: authenticate with <MAC address removed>
[ 2827.682828] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2827.690196] wlan0: authenticated
[ 2827.692099] wlan0: associate with <MAC address removed> (try 1/3)
[ 2827.733887] wlan0: RX AssocResp from <MAC address removed> (capab=0x421 status=0 aid=67)
[ 2827.734581] wlan0: associated
[ 2867.475218] wlan0: authenticate with <MAC address removed>
[ 2867.479489] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2867.584125] wlan0: send auth to <MAC address removed> (try 2/3)
[ 2867.589665] wlan0: authenticated
[ 2867.592168] wlan0: associate with <MAC address removed> (try 1/3)
[ 2867.708176] wlan0: associate with <MAC address removed> (try 2/3)
[ 2867.733774] wlan0: RX AssocResp from <MAC address removed> (capab=0x421 status=0 aid=67)
[ 2867.734475] wlan0: associated
[ 2946.772125] wlan0: authenticate with <MAC address removed>
[ 2946.778532] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2946.980175] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2947.184145] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2947.388095] wlan0: authentication with <MAC address removed> timed out
[ 2951.779802] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2953.837548] wlan0: authenticate with <MAC address removed>
[ 2953.845337] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2953.851703] wlan0: authenticated
[ 2953.856173] wlan0: associate with <MAC address removed> (try 1/3)
[ 2953.879545] wlan0: RX AssocResp from <MAC address removed> (capab=0x421 status=0 aid=67)
[ 2953.880424] wlan0: associated
[ 2968.078745] wlan0: authenticate with <MAC address removed>
[ 2968.079100] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2968.138452] wlan0: authenticated
[ 2968.140137] wlan0: associate with <MAC address removed> (try 1/3)
[ 2968.166802] wlan0: RX AssocResp from <MAC address removed> (capab=0x421 status=0 aid=67)
[ 2968.167601] wlan0: associated
[ 2982.765839] wlan0: authenticate with <MAC address removed>
[ 2982.766198] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2982.772469] wlan0: authenticated
[ 2982.776679] wlan0: associate with <MAC address removed> (try 1/3)
[ 2982.924108] wlan0: associate with <MAC address removed> (try 2/3)
[ 2982.941755] wlan0: RX AssocResp from <MAC address removed> (capab=0x421 status=0 aid=67)
[ 2982.942460] wlan0: associated
[ 2992.777954] wlan0: authenticate with <MAC address removed>
[ 2992.778229] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2992.854530] wlan0: authenticated
[ 2992.856145] wlan0: associate with <MAC address removed> (try 1/3)
[ 2992.947518] wlan0: RX AssocResp from <MAC address removed> (capab=0x421 status=0 aid=67)
[ 2992.948464] wlan0: associated
[ 3031.442187] wlan0: authenticate with <MAC address removed>
[ 3031.442543] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3031.478831] wlan0: authenticated
[ 3031.480138] wlan0: associate with <MAC address removed> (try 1/3)
[ 3031.515135] wlan0: RX AssocResp from <MAC address removed> (capab=0x421 status=0 aid=67)
[ 3031.515809] wlan0: associated
[ 3119.254179] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3121.770548] wlan0: authenticate with <MAC address removed>
[ 3121.776244] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3121.980156] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3122.184085] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3122.388093] wlan0: authentication with <MAC address removed> timed out
[ 3126.780119] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 3140.151501] wlan0: authenticate with <MAC address removed>
[ 3140.168518] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3140.372141] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3140.576048] wlan0: send auth to <MAC address removed> (try 3/3)
[ 3140.594196] wlan0: authenticated
[ 3140.596135] wlan0: associate with <MAC address removed> (try 1/3)
[ 3140.656971] wlan0: RX AssocResp from <MAC address removed> (capab=0x421 status=0 aid=67)
[ 3140.657634] wlan0: associated
[ 3140.657737] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3181.616476] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 3182.219681] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3184.385852] wlan0: authenticate with <MAC address removed>
[ 3184.386198] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3184.588099] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3184.792115] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3184.996100] wlan0: authentication with <MAC address removed> timed out
[ 3185.181211] wlan0: authenticate with <MAC address removed>
[ 3185.189301] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3185.392111] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3185.596152] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3185.800147] wlan0: authentication with <MAC address removed> timed out
[ 3186.573574] wlan0: authenticate with <MAC address removed>
[ 3186.580938] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3186.784113] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3186.988135] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3187.192174] wlan0: authentication with <MAC address removed> timed out
[ 3193.025932] wlan0: authenticate with <MAC address removed>
[ 3193.031361] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3193.032701] wlan0: authenticated
[ 3193.036492] wlan0: associate with <MAC address removed> (try 1/3)
[ 3193.040284] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=1)
[ 3193.040906] wlan0: associated
[ 3193.041023] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4411.781348] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4412.784370] wlan0: authenticate with <MAC address removed>
[ 4412.785706] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4412.787921] wlan0: authenticated
[ 4412.796152] wlan0: associate with <MAC address removed> (try 1/3)
[ 4412.800849] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 4412.800864] wlan0: <MAC address removed> denied association (code=27)
[ 4412.820545] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4413.582020] wlan0: authenticate with <MAC address removed>
[ 4413.592231] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4413.601984] wlan0: authenticated
[ 4413.604089] wlan0: associate with <MAC address removed> (try 1/3)
[ 4413.607343] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=4648)
[ 4413.607357] wlan0: <MAC address removed> denied association (code=27)
[ 4413.624535] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4414.387602] wlan0: authenticate with <MAC address removed>
[ 4414.389640] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4414.391724] wlan0: authenticated
[ 4414.396100] wlan0: associate with <MAC address removed> (try 1/3)
[ 4414.399821] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=10523)
[ 4414.399837] wlan0: <MAC address removed> denied association (code=27)
[ 4414.408587] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4415.169709] wlan0: authenticate with <MAC address removed>
[ 4415.173764] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4415.178470] wlan0: authenticated
[ 4415.180470] wlan0: associate with <MAC address removed> (try 1/3)
[ 4415.183069] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=128)
[ 4415.183089] wlan0: <MAC address removed> denied association (code=27)
[ 4415.209048] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4415.971893] wlan0: authenticate with <MAC address removed>
[ 4415.975193] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4415.977555] wlan0: authenticated
[ 4415.981067] wlan0: associate with <MAC address removed> (try 1/3)
[ 4415.989255] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 4415.989273] wlan0: <MAC address removed> denied association (code=27)
[ 4415.996671] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4416.757667] wlan0: authenticate with <MAC address removed>
[ 4416.761777] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4416.770116] wlan0: authenticated
[ 4416.776073] wlan0: associate with <MAC address removed> (try 1/3)
[ 4416.778685] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=2170)
[ 4416.778701] wlan0: <MAC address removed> denied association (code=27)
[ 4416.785018] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4417.545535] wlan0: authenticate with <MAC address removed>
[ 4417.549008] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4417.554160] wlan0: authenticated
[ 4417.556186] wlan0: associate with <MAC address removed> (try 1/3)
[ 4417.561605] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 4417.561626] wlan0: <MAC address removed> denied association (code=27)
[ 4417.569018] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4418.329821] wlan0: authenticate with <MAC address removed>
[ 4418.333681] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4418.336857] wlan0: authenticated
[ 4418.340169] wlan0: associate with <MAC address removed> (try 1/3)
[ 4418.342765] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=8314)
[ 4418.342779] wlan0: <MAC address removed> denied association (code=27)
[ 4418.352601] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4419.113611] wlan0: authenticate with <MAC address removed>
[ 4419.116866] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4419.125328] wlan0: authenticated
[ 4419.132282] wlan0: associate with <MAC address removed> (try 1/3)
[ 4419.134894] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=4645)
[ 4419.134914] wlan0: <MAC address removed> denied association (code=27)
[ 4419.145810] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4419.901735] wlan0: authenticate with <MAC address removed>
[ 4419.905889] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4419.912238] wlan0: authenticated
[ 4419.916139] wlan0: associate with <MAC address removed> (try 1/3)
[ 4419.920634] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=3094)
[ 4419.920650] wlan0: <MAC address removed> denied association (code=27)
[ 4419.929001] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4420.689840] wlan0: authenticate with <MAC address removed>
[ 4420.694468] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4420.702608] wlan0: authenticated
[ 4420.704108] wlan0: associate with <MAC address removed> (try 1/3)
[ 4420.707551] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=3094)
[ 4420.707572] wlan0: <MAC address removed> denied association (code=27)
[ 4420.769472] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4421.529830] wlan0: authenticate with <MAC address removed>
[ 4421.534112] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4421.538443] wlan0: authenticated
[ 4421.540105] wlan0: associate with <MAC address removed> (try 1/3)
[ 4421.542855] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 4421.542882] wlan0: <MAC address removed> denied association (code=27)
[ 4421.609267] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4422.369554] wlan0: authenticate with <MAC address removed>
[ 4422.372752] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4422.383272] wlan0: authenticated
[ 4422.392129] wlan0: associate with <MAC address removed> (try 1/3)
[ 4422.394793] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 4422.394810] wlan0: <MAC address removed> denied association (code=27)
[ 4422.400675] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4423.161706] wlan0: authenticate with <MAC address removed>
[ 4423.165836] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4423.168602] wlan0: authenticated
[ 4423.172128] wlan0: associate with <MAC address removed> (try 1/3)
[ 4423.174980] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 4423.175001] wlan0: <MAC address removed> denied association (code=27)
[ 4423.220959] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4423.983021] wlan0: authenticate with <MAC address removed>
[ 4423.986267] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4423.991955] wlan0: authenticated
[ 4423.996178] wlan0: associate with <MAC address removed> (try 1/3)
[ 4424.004973] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 4424.004994] wlan0: <MAC address removed> denied association (code=27)
[ 4424.016652] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4424.777724] wlan0: authenticate with <MAC address removed>
[ 4424.781750] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4424.788759] wlan0: authenticated
[ 4424.792217] wlan0: associate with <MAC address removed> (try 1/3)
[ 4424.794958] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=15156)
[ 4424.794979] wlan0: <MAC address removed> denied association (code=27)
[ 4424.801014] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4425.563752] wlan0: authenticate with <MAC address removed>
[ 4425.565847] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4425.570176] wlan0: authenticated
[ 4425.572489] wlan0: associate with <MAC address removed> (try 1/3)
[ 4425.576326] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=10630)
[ 4425.576341] wlan0: <MAC address removed> denied association (code=27)
[ 4425.596633] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4426.357880] wlan0: authenticate with <MAC address removed>
[ 4426.361722] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4426.365573] wlan0: authenticated
[ 4426.368246] wlan0: associate with <MAC address removed> (try 1/3)
[ 4426.373171] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=80)
[ 4426.373192] wlan0: <MAC address removed> denied association (code=27)
[ 4426.420716] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4427.181878] wlan0: authenticate with <MAC address removed>
[ 4427.185753] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4427.203927] wlan0: authenticated
[ 4427.208177] wlan0: associate with <MAC address removed> (try 1/3)
[ 4427.212908] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=10629)
[ 4427.212924] wlan0: <MAC address removed> denied association (code=27)
[ 4427.221015] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4427.989835] wlan0: authenticate with <MAC address removed>
[ 4427.993766] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4427.999759] wlan0: authenticated
[ 4428.004191] wlan0: associate with <MAC address removed> (try 1/3)
[ 4428.006930] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=3094)
[ 4428.006943] wlan0: <MAC address removed> denied association (code=27)
[ 4428.016567] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4428.777848] wlan0: authenticate with <MAC address removed>
[ 4428.781680] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4428.785529] wlan0: authenticated
[ 4428.788171] wlan0: associate with <MAC address removed> (try 1/3)
[ 4428.791650] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 4428.791664] wlan0: <MAC address removed> denied association (code=27)
[ 4428.800618] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4429.563665] wlan0: authenticate with <MAC address removed>
[ 4429.567146] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4429.569728] wlan0: authenticated
[ 4429.572463] wlan0: associate with <MAC address removed> (try 1/3)
[ 4429.575126] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=3094)
[ 4429.575142] wlan0: <MAC address removed> denied association (code=27)
[ 4429.584595] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4430.345780] wlan0: authenticate with <MAC address removed>
[ 4430.349742] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4430.353447] wlan0: authenticated
[ 4430.356178] wlan0: associate with <MAC address removed> (try 1/3)
[ 4430.361196] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=3094)
[ 4430.361218] wlan0: <MAC address removed> denied association (code=27)
[ 4430.381036] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4431.141812] wlan0: authenticate with <MAC address removed>
[ 4431.144853] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4431.148868] wlan0: authenticated
[ 4431.152879] wlan0: associate with <MAC address removed> (try 1/3)
[ 4431.156306] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 4431.156322] wlan0: <MAC address removed> denied association (code=27)
[ 4431.184553] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4431.945705] wlan0: authenticate with <MAC address removed>
[ 4431.948993] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4431.952067] wlan0: authenticated
[ 4431.956151] wlan0: associate with <MAC address removed> (try 1/3)
[ 4431.959988] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=2330)
[ 4431.960123] wlan0: <MAC address removed> denied association (code=27)
[ 4431.989134] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4432.749755] wlan0: authenticate with <MAC address removed>
[ 4432.753864] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4432.757358] wlan0: authenticated
[ 4432.760251] wlan0: associate with <MAC address removed> (try 1/3)
[ 4432.763209] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 4432.763233] wlan0: <MAC address removed> denied association (code=27)
[ 4432.768486] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4433.529750] wlan0: authenticate with <MAC address removed>
[ 4433.534441] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4433.537483] wlan0: authenticated
[ 4433.540536] wlan0: associate with <MAC address removed> (try 1/3)
[ 4433.543633] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 4433.543661] wlan0: <MAC address removed> denied association (code=27)
[ 4433.549022] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4434.305816] wlan0: authenticate with <MAC address removed>
[ 4434.310452] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4434.316482] wlan0: authenticated
[ 4434.320229] wlan0: associate with <MAC address removed> (try 1/3)
[ 4434.323807] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 4434.323823] wlan0: <MAC address removed> denied association (code=27)
[ 4434.336544] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4435.093753] wlan0: authenticate with <MAC address removed>
[ 4435.097737] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4435.101344] wlan0: authenticated
[ 4435.104174] wlan0: associate with <MAC address removed> (try 1/3)
[ 4435.107173] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 4435.107189] wlan0: <MAC address removed> denied association (code=27)
[ 4435.119180] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4435.881781] wlan0: authenticate with <MAC address removed>
[ 4435.886358] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4435.890500] wlan0: authenticated
[ 4435.892322] wlan0: associate with <MAC address removed> (try 1/3)
[ 4435.896392] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=11387)
[ 4435.896425] wlan0: <MAC address removed> denied association (code=27)
[ 4435.904975] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4436.666310] wlan0: authenticate with <MAC address removed>
[ 4436.670508] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4436.673406] wlan0: authenticated
[ 4436.676095] wlan0: associate with <MAC address removed> (try 1/3)
[ 4436.679202] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=10523)
[ 4436.679224] wlan0: <MAC address removed> denied association (code=27)
[ 4436.727667] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4437.489880] wlan0: authenticate with <MAC address removed>
[ 4437.493756] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4437.497648] wlan0: authenticated
[ 4437.500334] wlan0: associate with <MAC address removed> (try 1/3)
[ 4437.506867] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=128)
[ 4437.506890] wlan0: <MAC address removed> denied association (code=27)
[ 4437.516623] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4438.277771] wlan0: authenticate with <MAC address removed>
[ 4438.282058] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4438.285735] wlan0: authenticated
[ 4438.288165] wlan0: associate with <MAC address removed> (try 1/3)
[ 4438.290845] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=4645)
[ 4438.290864] wlan0: <MAC address removed> denied association (code=27)
[ 4438.296581] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4439.057859] wlan0: authenticate with <MAC address removed>
[ 4439.062196] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4439.067854] wlan0: authenticated
[ 4439.072099] wlan0: associate with <MAC address removed> (try 1/3)
[ 4439.076371] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=10631)
[ 4439.076386] wlan0: <MAC address removed> denied association (code=27)
[ 4439.084609] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4439.845831] wlan0: authenticate with <MAC address removed>
[ 4439.850321] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4439.854705] wlan0: authenticated
[ 4439.860126] wlan0: associate with <MAC address removed> (try 1/3)
[ 4439.867782] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=10523)
[ 4439.867798] wlan0: <MAC address removed> denied association (code=27)
[ 4439.876636] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4440.637768] wlan0: authenticate with <MAC address removed>
[ 4440.641735] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4440.645720] wlan0: authenticated
[ 4440.648297] wlan0: associate with <MAC address removed> (try 1/3)
[ 4440.651662] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=13691)
[ 4440.651677] wlan0: <MAC address removed> denied association (code=27)
[ 4440.660594] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4441.421827] wlan0: authenticate with <MAC address removed>
[ 4441.426364] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4441.431793] wlan0: authenticated
[ 4441.436177] wlan0: associate with <MAC address removed> (try 1/3)
[ 4441.440701] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=3094)
[ 4441.440722] wlan0: <MAC address removed> denied association (code=27)
[ 4441.448842] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4442.210428] wlan0: authenticate with <MAC address removed>
[ 4442.215738] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4442.219044] wlan0: authenticated
[ 4442.228117] wlan0: associate with <MAC address removed> (try 1/3)
[ 4442.287430] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=6522)
[ 4442.287442] wlan0: <MAC address removed> denied association (code=27)
[ 4442.303403] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4443.061827] wlan0: authenticate with <MAC address removed>
[ 4443.065754] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4443.070570] wlan0: authenticated
[ 4443.072130] wlan0: associate with <MAC address removed> (try 1/3)
[ 4443.077665] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 4443.077683] wlan0: <MAC address removed> denied association (code=27)
[ 4443.088703] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4443.853819] wlan0: authenticate with <MAC address removed>
[ 4443.858836] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4443.866955] wlan0: authenticated
[ 4443.868108] wlan0: associate with <MAC address removed> (try 1/3)
[ 4443.870763] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=10109)
[ 4443.870781] wlan0: <MAC address removed> denied association (code=27)
[ 4443.880762] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4444.641750] wlan0: authenticate with <MAC address removed>
[ 4444.645767] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4444.752112] wlan0: send auth to <MAC address removed> (try 2/3)
[ 4444.856177] wlan0: send auth to <MAC address removed> (try 3/3)
[ 4444.863590] wlan0: authenticated
[ 4444.868109] wlan0: associate with <MAC address removed> (try 1/3)
[ 4444.872077] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=10631)
[ 4444.872093] wlan0: <MAC address removed> denied association (code=27)
[ 4444.909484] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4445.670974] wlan0: authenticate with <MAC address removed>
[ 4445.673527] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4445.678208] wlan0: authenticated
[ 4445.684160] wlan0: associate with <MAC address removed> (try 1/3)
[ 4445.687554] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 4445.687580] wlan0: <MAC address removed> denied association (code=27)
[ 4445.693135] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4446.453843] wlan0: authenticate with <MAC address removed>
[ 4446.457756] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4446.461843] wlan0: authenticated
[ 4446.464100] wlan0: associate with <MAC address removed> (try 1/3)
[ 4446.467521] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 4446.467534] wlan0: <MAC address removed> denied association (code=27)
[ 4446.520665] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4447.281688] wlan0: authenticate with <MAC address removed>
[ 4447.285784] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4447.290496] wlan0: authenticated
[ 4447.292189] wlan0: associate with <MAC address removed> (try 1/3)
[ 4447.295890] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=2048)
[ 4447.295910] wlan0: <MAC address removed> denied association (code=27)
[ 4447.308806] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4448.069773] wlan0: authenticate with <MAC address removed>
[ 4448.073747] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4448.077695] wlan0: authenticated
[ 4448.080165] wlan0: associate with <MAC address removed> (try 1/3)
[ 4448.083554] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=10629)
[ 4448.083569] wlan0: <MAC address removed> denied association (code=27)
[ 4448.122570] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4448.882532] wlan0: authenticate with <MAC address removed>
[ 4448.886478] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4448.889166] wlan0: authenticated
[ 4448.896098] wlan0: associate with <MAC address removed> (try 1/3)
[ 4448.898884] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=10523)
[ 4448.898906] wlan0: <MAC address removed> denied association (code=27)
[ 4448.908573] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4449.665855] wlan0: authenticate with <MAC address removed>
[ 4449.669753] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4449.675303] wlan0: authenticated
[ 4449.676160] wlan0: associate with <MAC address removed> (try 1/3)
[ 4449.678808] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=4634)
[ 4449.678821] wlan0: <MAC address removed> denied association (code=27)
[ 4449.693355] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4450.454201] wlan0: authenticate with <MAC address removed>
[ 4450.456805] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4450.461850] wlan0: authenticated
[ 4450.464103] wlan0: associate with <MAC address removed> (try 1/3)
[ 4450.466835] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=2069)
[ 4450.466854] wlan0: <MAC address removed> denied association (code=27)
[ 4450.476605] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4451.237769] wlan0: authenticate with <MAC address removed>
[ 4451.240760] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4451.245333] wlan0: authenticated
[ 4451.248362] wlan0: associate with <MAC address removed> (try 1/3)
[ 4451.253295] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=4647)
[ 4451.253312] wlan0: <MAC address removed> denied association (code=27)
[ 4451.261020] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4452.021788] wlan0: authenticate with <MAC address removed>
[ 4452.025747] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4452.034037] wlan0: authenticated
[ 4452.036100] wlan0: associate with <MAC address removed> (try 1/3)
[ 4452.042224] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 4452.042246] wlan0: <MAC address removed> denied association (code=27)
[ 4452.054329] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4452.814616] wlan0: authenticate with <MAC address removed>
[ 4452.820214] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4452.824362] wlan0: authenticated
[ 4452.828069] wlan0: associate with <MAC address removed> (try 1/3)
[ 4452.831244] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=11264)
[ 4452.831260] wlan0: <MAC address removed> denied association (code=27)
[ 4452.839882] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4453.601702] wlan0: authenticate with <MAC address removed>
[ 4453.606350] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4453.614055] wlan0: authenticated
[ 4453.616273] wlan0: associate with <MAC address removed> (try 1/3)
[ 4453.625840] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=11593)
[ 4453.625861] wlan0: <MAC address removed> denied association (code=27)
[ 4453.632557] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4454.393905] wlan0: authenticate with <MAC address removed>
[ 4454.398223] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4454.402998] wlan0: authenticated
[ 4454.404145] wlan0: associate with <MAC address removed> (try 1/3)
[ 4454.407105] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 4454.407126] wlan0: <MAC address removed> denied association (code=27)
[ 4454.481015] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4455.241561] wlan0: authenticate with <MAC address removed>
[ 4455.246194] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4455.248926] wlan0: authenticated
[ 4455.256202] wlan0: associate with <MAC address removed> (try 1/3)
[ 4455.259211] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=3094)
[ 4455.259232] wlan0: <MAC address removed> denied association (code=27)
[ 4455.269018] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4456.029813] wlan0: authenticate with <MAC address removed>
[ 4456.034282] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4456.039719] wlan0: authenticated
[ 4456.044143] wlan0: associate with <MAC address removed> (try 1/3)
[ 4456.047017] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 4456.047029] wlan0: <MAC address removed> denied association (code=27)
[ 4456.059236] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4456.825762] wlan0: authenticate with <MAC address removed>
[ 4456.830074] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4456.833263] wlan0: authenticated
[ 4456.836159] wlan0: associate with <MAC address removed> (try 1/3)
[ 4456.840807] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 4456.840828] wlan0: <MAC address removed> denied association (code=27)
[ 4456.849193] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4457.614628] wlan0: authenticate with <MAC address removed>
[ 4457.618735] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4457.625282] wlan0: authenticated
[ 4457.628127] wlan0: associate with <MAC address removed> (try 1/3)
[ 4457.632453] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=3094)
[ 4457.632466] wlan0: <MAC address removed> denied association (code=27)
[ 4457.641011] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4458.405764] wlan0: authenticate with <MAC address removed>
[ 4458.410310] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4458.412254] wlan0: authenticated
[ 4458.416115] wlan0: associate with <MAC address removed> (try 1/3)
[ 4458.436756] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=522)
[ 4458.436777] wlan0: <MAC address removed> denied association (code=27)
[ 4458.444978] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4459.205975] wlan0: authenticate with <MAC address removed>
[ 4459.210544] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4459.219874] wlan0: authenticated
[ 4459.224089] wlan0: associate with <MAC address removed> (try 1/3)
[ 4459.226823] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=3094)
[ 4459.226839] wlan0: <MAC address removed> denied association (code=27)
[ 4459.232558] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4459.993848] wlan0: authenticate with <MAC address removed>
[ 4459.998173] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4460.002613] wlan0: authenticated
[ 4460.004255] wlan0: associate with <MAC address removed> (try 1/3)
[ 4460.010944] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 4460.010960] wlan0: <MAC address removed> denied association (code=27)
[ 4460.020428] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4460.781773] wlan0: authenticate with <MAC address removed>
[ 4460.785877] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4460.790482] wlan0: authenticated
[ 4460.792116] wlan0: associate with <MAC address removed> (try 1/3)
[ 4460.799033] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=10523)
[ 4460.799054] wlan0: <MAC address removed> denied association (code=27)
[ 4460.808608] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4461.565855] wlan0: authenticate with <MAC address removed>
[ 4461.569735] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4461.575675] wlan0: authenticated
[ 4461.580160] wlan0: associate with <MAC address removed> (try 1/3)
[ 4461.583558] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=16383)
[ 4461.583573] wlan0: <MAC address removed> denied association (code=27)
[ 4461.588979] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4462.349819] wlan0: authenticate with <MAC address removed>
[ 4462.353787] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4462.357742] wlan0: authenticated
[ 4462.360126] wlan0: associate with <MAC address removed> (try 1/3)
[ 4462.370904] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=3094)
[ 4462.370926] wlan0: <MAC address removed> denied association (code=27)
[ 4462.377006] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4463.133789] wlan0: authenticate with <MAC address removed>
[ 4463.137878] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4463.141806] wlan0: authenticated
[ 4463.144208] wlan0: associate with <MAC address removed> (try 1/3)
[ 4463.146882] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 4463.146897] wlan0: <MAC address removed> denied association (code=27)
[ 4463.157446] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4463.918134] wlan0: authenticate with <MAC address removed>
[ 4463.921721] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4463.925878] wlan0: authenticated
[ 4463.928102] wlan0: associate with <MAC address removed> (try 1/3)
[ 4463.932585] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=3094)
[ 4463.932601] wlan0: <MAC address removed> denied association (code=27)
[ 4463.940695] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4464.705833] wlan0: authenticate with <MAC address removed>
[ 4464.709938] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4464.720131] wlan0: authenticated
[ 4464.724164] wlan0: associate with <MAC address removed> (try 1/3)
[ 4464.728473] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=4984)
[ 4464.728488] wlan0: <MAC address removed> denied association (code=27)
[ 4464.736561] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4465.497702] wlan0: authenticate with <MAC address removed>
[ 4465.501758] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4465.504685] wlan0: authenticated
[ 4465.508163] wlan0: associate with <MAC address removed> (try 1/3)
[ 4465.511345] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=128)
[ 4465.511361] wlan0: <MAC address removed> denied association (code=27)
[ 4465.516619] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4466.278060] wlan0: authenticate with <MAC address removed>
[ 4466.281089] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4466.285719] wlan0: authenticated
[ 4466.288148] wlan0: associate with <MAC address removed> (try 1/3)
[ 4466.291571] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=15485)
[ 4466.291587] wlan0: <MAC address removed> denied association (code=27)
[ 4466.302170] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4467.061679] wlan0: authenticate with <MAC address removed>
[ 4467.065742] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4467.069044] wlan0: authenticated
[ 4467.072161] wlan0: associate with <MAC address removed> (try 1/3)
[ 4467.076074] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 4467.076089] wlan0: <MAC address removed> denied association (code=27)
[ 4467.084547] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4467.845739] wlan0: authenticate with <MAC address removed>
[ 4467.850296] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4467.854451] wlan0: authenticated
[ 4467.856095] wlan0: associate with <MAC address removed> (try 1/3)
[ 4467.859595] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=10631)
[ 4467.859616] wlan0: <MAC address removed> denied association (code=27)
[ 4467.864579] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4468.625453] wlan0: authenticate with <MAC address removed>
[ 4468.628928] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4468.632802] wlan0: authenticated
[ 4468.636167] wlan0: associate with <MAC address removed> (try 1/3)
[ 4468.638996] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=10523)
[ 4468.639011] wlan0: <MAC address removed> denied association (code=27)
[ 4468.676593] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4469.437680] wlan0: authenticate with <MAC address removed>
[ 4469.442390] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4469.445891] wlan0: authenticated
[ 4469.448156] wlan0: associate with <MAC address removed> (try 1/3)
[ 4469.451075] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 4469.451096] wlan0: <MAC address removed> denied association (code=27)
[ 4469.453741] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4470.209450] wlan0: authenticate with <MAC address removed>
[ 4470.212776] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4470.214730] wlan0: authenticated
[ 4470.216102] wlan0: associate with <MAC address removed> (try 1/3)
[ 4470.229290] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=10628)
[ 4470.229317] wlan0: <MAC address removed> denied association (code=27)
[ 4470.240621] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4471.001631] wlan0: authenticate with <MAC address removed>
[ 4471.004868] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4471.008420] wlan0: authenticated
[ 4471.012561] wlan0: associate with <MAC address removed> (try 1/3)
[ 4471.016457] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=1149)
[ 4471.016473] wlan0: <MAC address removed> denied association (code=27)
[ 4471.021187] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4471.781703] wlan0: authenticate with <MAC address removed>
[ 4471.785697] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4471.790170] wlan0: authenticated
[ 4471.796225] wlan0: associate with <MAC address removed> (try 1/3)
[ 4471.798829] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 4471.798845] wlan0: <MAC address removed> denied association (code=27)
[ 4471.808878] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4485.706569] wlan0: authenticate with <MAC address removed>
[ 4485.712550] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4485.720445] wlan0: authenticated
[ 4485.724122] wlan0: associate with <MAC address removed> (try 1/3)
[ 4485.726941] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=1)
[ 4485.727636] wlan0: associated
[ 4487.689715] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4495.701831] wlan0: authenticate with <MAC address removed>
[ 4495.706304] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4495.707401] wlan0: authenticated
[ 4495.712136] wlan0: associate with <MAC address removed> (try 1/3)
[ 4495.713934] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=1)
[ 4495.714568] wlan0: associated
[ 6082.964255] wlan0: deauthenticated from <MAC address removed> (Reason: 3)
[ 6083.849224] wlan0: authenticate with <MAC address removed>
[ 6083.849509] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6083.952124] wlan0: send auth to <MAC address removed> (try 2/3)
[ 6084.056166] wlan0: send auth to <MAC address removed> (try 3/3)
[ 6084.160147] wlan0: authentication with <MAC address removed> timed out
[ 6088.850381] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6104.323399] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6161.613534] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6203.565592] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6205.735535] wlan0: authenticate with <MAC address removed>
[ 6205.735899] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6205.737017] wlan0: authenticated
[ 6205.744126] wlan0: associate with <MAC address removed> (try 1/3)
[ 6205.746241] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 6205.746897] wlan0: associated
[ 6205.746994] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 6241.841012] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6242.842615] wlan0: authenticate with <MAC address removed>
[ 6242.860480] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6242.867659] wlan0: authenticated
[ 6242.872102] wlan0: associate with <MAC address removed> (try 1/3)
[ 6242.875060] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=8935)
[ 6242.875075] wlan0: <MAC address removed> denied association (code=27)
[ 6242.884565] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6243.649681] wlan0: authenticate with <MAC address removed>
[ 6243.664152] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6243.666663] wlan0: authenticated
[ 6243.668578] wlan0: associate with <MAC address removed> (try 1/3)
[ 6243.671764] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=4651)
[ 6243.671780] wlan0: <MAC address removed> denied association (code=27)
[ 6243.688553] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6244.449588] wlan0: authenticate with <MAC address removed>
[ 6244.453774] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6244.457308] wlan0: authenticated
[ 6244.460240] wlan0: associate with <MAC address removed> (try 1/3)
[ 6244.462916] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 6244.462943] wlan0: <MAC address removed> denied association (code=27)
[ 6244.468635] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6245.229629] wlan0: authenticate with <MAC address removed>
[ 6245.233819] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6245.237576] wlan0: authenticated
[ 6245.240093] wlan0: associate with <MAC address removed> (try 1/3)
[ 6245.242989] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=10523)
[ 6245.243005] wlan0: <MAC address removed> denied association (code=27)
[ 6245.248589] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6246.009577] wlan0: authenticate with <MAC address removed>
[ 6246.016009] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6246.018913] wlan0: authenticated
[ 6246.020482] wlan0: associate with <MAC address removed> (try 1/3)
[ 6246.023194] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=10523)
[ 6246.023212] wlan0: <MAC address removed> denied association (code=27)
[ 6246.048725] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6246.809574] wlan0: authenticate with <MAC address removed>
[ 6246.814703] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6246.818429] wlan0: authenticated
[ 6246.820171] wlan0: associate with <MAC address removed> (try 1/3)
[ 6246.823158] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=10523)
[ 6246.823174] wlan0: <MAC address removed> denied association (code=27)
[ 6246.828447] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6247.589567] wlan0: authenticate with <MAC address removed>
[ 6247.593696] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6247.595982] wlan0: authenticated
[ 6247.600157] wlan0: associate with <MAC address removed> (try 1/3)
[ 6247.604400] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=4651)
[ 6247.604415] wlan0: <MAC address removed> denied association (code=27)
[ 6247.616590] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6248.377958] wlan0: authenticate with <MAC address removed>
[ 6248.380821] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6248.385658] wlan0: authenticated
[ 6248.388492] wlan0: associate with <MAC address removed> (try 1/3)
[ 6248.391106] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=10523)
[ 6248.391132] wlan0: <MAC address removed> denied association (code=27)
[ 6248.402237] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6249.164136] wlan0: authenticate with <MAC address removed>
[ 6249.166303] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6249.172079] wlan0: authenticated
[ 6249.174796] wlan0: associating with AP with corrupt beacon
[ 6249.176535] wlan0: associate with <MAC address removed> (try 1/3)
[ 6249.183626] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=4617)
[ 6249.183647] wlan0: <MAC address removed> denied association (code=27)
[ 6249.189023] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6249.975150] wlan0: authenticate with <MAC address removed>
[ 6249.998171] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6250.000436] wlan0: authenticated
[ 6250.004441] wlan0: associate with <MAC address removed> (try 1/3)
[ 6250.007682] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=128)
[ 6250.007699] wlan0: <MAC address removed> denied association (code=27)
[ 6250.024493] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6250.789705] wlan0: authenticate with <MAC address removed>
[ 6250.793939] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6250.799268] wlan0: authenticated
[ 6250.804172] wlan0: associate with <MAC address removed> (try 1/3)
[ 6250.806992] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=10523)
[ 6250.807006] wlan0: <MAC address removed> denied association (code=27)
[ 6250.816965] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6251.577608] wlan0: authenticate with <MAC address removed>
[ 6251.582343] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6251.585536] wlan0: authenticated
[ 6251.588200] wlan0: associate with <MAC address removed> (try 1/3)
[ 6251.590792] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 6251.590812] wlan0: <MAC address removed> denied association (code=27)
[ 6251.604557] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6252.369726] wlan0: authenticate with <MAC address removed>
[ 6252.373788] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6252.377292] wlan0: authenticated
[ 6252.380160] wlan0: associate with <MAC address removed> (try 1/3)
[ 6252.385249] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 6252.385265] wlan0: <MAC address removed> denied association (code=27)
[ 6252.396589] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6253.157687] wlan0: authenticate with <MAC address removed>
[ 6253.161694] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6253.165437] wlan0: authenticated
[ 6253.168171] wlan0: associate with <MAC address removed> (try 1/3)
[ 6253.171956] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=10523)
[ 6253.171971] wlan0: <MAC address removed> denied association (code=27)
[ 6253.176995] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6253.953522] wlan0: authenticate with <MAC address removed>
[ 6253.981724] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6253.986113] wlan0: authenticated
[ 6253.988287] wlan0: associate with <MAC address removed> (try 1/3)
[ 6253.991593] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=128)
[ 6253.991616] wlan0: <MAC address removed> denied association (code=27)
[ 6253.996650] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6254.757660] wlan0: authenticate with <MAC address removed>
[ 6254.762431] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6254.766851] wlan0: authenticated
[ 6254.768125] wlan0: associate with <MAC address removed> (try 1/3)
[ 6254.772453] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=4651)
[ 6254.772474] wlan0: <MAC address removed> denied association (code=27)
[ 6254.781021] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6255.541467] wlan0: authenticate with <MAC address removed>
[ 6255.545650] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6255.547869] wlan0: authenticated
[ 6255.552156] wlan0: associate with <MAC address removed> (try 1/3)
[ 6255.555270] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=3094)
[ 6255.555304] wlan0: <MAC address removed> denied association (code=27)
[ 6255.601015] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6256.358754] wlan0: authenticate with <MAC address removed>
[ 6256.362059] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6256.364485] wlan0: authenticated
[ 6256.368199] wlan0: associate with <MAC address removed> (try 1/3)
[ 6256.371380] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=4651)
[ 6256.371396] wlan0: <MAC address removed> denied association (code=27)
[ 6256.384684] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6257.145539] wlan0: authenticate with <MAC address removed>
[ 6257.150630] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6257.152820] wlan0: authenticated
[ 6257.160103] wlan0: associate with <MAC address removed> (try 1/3)
[ 6257.162700] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 6257.162716] wlan0: <MAC address removed> denied association (code=27)
[ 6257.168917] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6257.933538] wlan0: authenticate with <MAC address removed>
[ 6257.937999] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6257.941603] wlan0: authenticated
[ 6257.944225] wlan0: associate with <MAC address removed> (try 1/3)
[ 6257.946945] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=2280)
[ 6257.946964] wlan0: <MAC address removed> denied association (code=27)
[ 6258.021019] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6258.782883] wlan0: authenticate with <MAC address removed>
[ 6258.789104] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6258.796486] wlan0: authenticated
[ 6258.800109] wlan0: associate with <MAC address removed> (try 1/3)
[ 6258.804452] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=5608)
[ 6258.804467] wlan0: <MAC address removed> denied association (code=27)
[ 6258.821053] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6259.581722] wlan0: authenticate with <MAC address removed>
[ 6259.586064] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6259.590357] wlan0: authenticated
[ 6259.592177] wlan0: associate with <MAC address removed> (try 1/3)
[ 6259.594821] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=128)
[ 6259.594842] wlan0: <MAC address removed> denied association (code=27)
[ 6259.621015] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6260.381692] wlan0: authenticate with <MAC address removed>
[ 6260.386092] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6260.388226] wlan0: authenticated
[ 6260.392280] wlan0: associate with <MAC address removed> (try 1/3)
[ 6260.395077] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=11752)
[ 6260.395114] wlan0: <MAC address removed> denied association (code=27)
[ 6260.401008] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6261.165639] wlan0: authenticate with <MAC address removed>
[ 6261.169735] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6261.171770] wlan0: authenticated
[ 6261.176167] wlan0: associate with <MAC address removed> (try 1/3)
[ 6261.179123] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 6261.179140] wlan0: <MAC address removed> denied association (code=27)
[ 6261.184587] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6261.941708] wlan0: authenticate with <MAC address removed>
[ 6261.945920] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6261.948927] wlan0: authenticated
[ 6261.952175] wlan0: associate with <MAC address removed> (try 1/3)
[ 6261.955683] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 6261.955699] wlan0: <MAC address removed> denied association (code=27)
[ 6261.960623] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6262.721668] wlan0: authenticate with <MAC address removed>
[ 6262.724579] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6262.726872] wlan0: authenticated
[ 6262.728132] wlan0: associate with <MAC address removed> (try 1/3)
[ 6262.730756] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=128)
[ 6262.730773] wlan0: <MAC address removed> denied association (code=27)
[ 6262.749612] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6263.516735] wlan0: authenticate with <MAC address removed>
[ 6263.517095] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6263.522234] wlan0: authenticated
[ 6263.524440] wlan0: associate with <MAC address removed> (try 1/3)
[ 6263.529156] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=3094)
[ 6263.529172] wlan0: <MAC address removed> denied association (code=27)
[ 6263.536674] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6264.297717] wlan0: authenticate with <MAC address removed>
[ 6264.302403] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6264.304812] wlan0: authenticated
[ 6264.308116] wlan0: associate with <MAC address removed> (try 1/3)
[ 6264.310817] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=128)
[ 6264.310834] wlan0: <MAC address removed> denied association (code=27)
[ 6264.401020] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6265.161727] wlan0: authenticate with <MAC address removed>
[ 6265.165828] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6265.168080] wlan0: authenticated
[ 6265.172157] wlan0: associate with <MAC address removed> (try 1/3)
[ 6265.174783] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=10523)
[ 6265.174802] wlan0: <MAC address removed> denied association (code=27)
[ 6265.180662] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6265.945682] wlan0: authenticate with <MAC address removed>
[ 6265.950199] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6265.952687] wlan0: authenticated
[ 6265.956166] wlan0: associate with <MAC address removed> (try 1/3)
[ 6265.959300] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=744)
[ 6265.959316] wlan0: <MAC address removed> denied association (code=27)
[ 6265.965010] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6266.725710] wlan0: authenticate with <MAC address removed>
[ 6266.729867] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6266.735645] wlan0: authenticated
[ 6266.740163] wlan0: associate with <MAC address removed> (try 1/3)
[ 6266.743401] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=3094)
[ 6266.743417] wlan0: <MAC address removed> denied association (code=27)
[ 6266.757750] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6267.518594] wlan0: authenticate with <MAC address removed>
[ 6267.524409] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6267.527960] wlan0: authenticated
[ 6267.532149] wlan0: associate with <MAC address removed> (try 1/3)
[ 6267.534868] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=4651)
[ 6267.534885] wlan0: <MAC address removed> denied association (code=27)
[ 6267.588903] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6268.349712] wlan0: authenticate with <MAC address removed>
[ 6268.353622] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6268.356179] wlan0: authenticated
[ 6268.360102] wlan0: associate with <MAC address removed> (try 1/3)
[ 6268.362658] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=128)
[ 6268.362671] wlan0: <MAC address removed> denied association (code=27)
[ 6268.369010] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6269.129679] wlan0: authenticate with <MAC address removed>
[ 6269.133746] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6269.136811] wlan0: authenticated
[ 6269.140169] wlan0: associate with <MAC address removed> (try 1/3)
[ 6269.143835] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=10523)
[ 6269.143851] wlan0: <MAC address removed> denied association (code=27)
[ 6269.148992] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6269.914490] wlan0: authenticate with <MAC address removed>
[ 6269.920926] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6269.925829] wlan0: authenticated
[ 6269.928155] wlan0: associate with <MAC address removed> (try 1/3)
[ 6269.931045] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 6269.931066] wlan0: <MAC address removed> denied association (code=27)
[ 6269.937163] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6270.697624] wlan0: authenticate with <MAC address removed>
[ 6270.710830] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6270.715596] wlan0: authenticated
[ 6270.720085] wlan0: associate with <MAC address removed> (try 1/3)
[ 6270.722841] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=10523)
[ 6270.722856] wlan0: <MAC address removed> denied association (code=27)
[ 6270.732658] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6271.493593] wlan0: authenticate with <MAC address removed>
[ 6271.511082] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6271.516844] wlan0: authenticated
[ 6271.520266] wlan0: associate with <MAC address removed> (try 1/3)
[ 6271.523979] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=4651)
[ 6271.523995] wlan0: <MAC address removed> denied association (code=27)
[ 6271.552601] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6272.313446] wlan0: authenticate with <MAC address removed>
[ 6272.340091] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6272.344400] wlan0: authenticated
[ 6272.348290] wlan0: associate with <MAC address removed> (try 1/3)
[ 6272.350921] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 6272.350936] wlan0: <MAC address removed> denied association (code=27)
[ 6272.385182] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6273.145680] wlan0: authenticate with <MAC address removed>
[ 6273.150455] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6273.153436] wlan0: authenticated
[ 6273.156156] wlan0: associate with <MAC address removed> (try 1/3)
[ 6273.159292] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=3094)
[ 6273.159308] wlan0: <MAC address removed> denied association (code=27)
[ 6273.164591] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6273.925540] wlan0: authenticate with <MAC address removed>
[ 6273.929799] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6273.932802] wlan0: authenticated
[ 6273.936170] wlan0: associate with <MAC address removed> (try 1/3)
[ 6273.939382] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=4652)
[ 6273.939397] wlan0: <MAC address removed> denied association (code=27)
[ 6273.948347] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6274.713566] wlan0: authenticate with <MAC address removed>
[ 6274.718746] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6274.720719] wlan0: authenticated
[ 6274.724142] wlan0: associate with <MAC address removed> (try 1/3)
[ 6274.726740] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=4650)
[ 6274.726755] wlan0: <MAC address removed> denied association (code=27)
[ 6274.736584] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6275.497561] wlan0: authenticate with <MAC address removed>
[ 6275.508704] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6275.516202] wlan0: authenticated
[ 6275.520960] wlan0: associate with <MAC address removed> (try 1/3)
[ 6275.523557] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 6275.523572] wlan0: <MAC address removed> denied association (code=27)
[ 6275.528524] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6276.289752] wlan0: authenticate with <MAC address removed>
[ 6276.294007] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6276.298229] wlan0: authenticated
[ 6276.300214] wlan0: associate with <MAC address removed> (try 1/3)
[ 6276.302916] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 6276.302937] wlan0: <MAC address removed> denied association (code=27)
[ 6276.317248] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6277.077762] wlan0: authenticate with <MAC address removed>
[ 6277.082076] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6277.085200] wlan0: authenticated
[ 6277.088157] wlan0: associate with <MAC address removed> (try 1/3)
[ 6277.091772] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=10523)
[ 6277.091789] wlan0: <MAC address removed> denied association (code=27)
[ 6277.096585] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6277.857776] wlan0: authenticate with <MAC address removed>
[ 6277.862696] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6277.867146] wlan0: authenticated
[ 6277.868197] wlan0: associate with <MAC address removed> (try 1/3)
[ 6277.873101] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=10523)
[ 6277.873116] wlan0: <MAC address removed> denied association (code=27)
[ 6277.884588] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6278.645708] wlan0: authenticate with <MAC address removed>
[ 6278.650408] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6278.652592] wlan0: authenticated
[ 6278.656165] wlan0: associate with <MAC address removed> (try 1/3)
[ 6278.659069] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=128)
[ 6278.659085] wlan0: <MAC address removed> denied association (code=27)
[ 6278.664584] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6279.425755] wlan0: authenticate with <MAC address removed>
[ 6279.430008] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6279.433503] wlan0: authenticated
[ 6279.440131] wlan0: associate with <MAC address removed> (try 1/3)
[ 6279.442781] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=3094)
[ 6279.442797] wlan0: <MAC address removed> denied association (code=27)
[ 6279.457921] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6280.218721] wlan0: authenticate with <MAC address removed>
[ 6280.225229] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6280.230442] wlan0: authenticated
[ 6280.232093] wlan0: associate with <MAC address removed> (try 1/3)
[ 6280.244321] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=128)
[ 6280.244343] wlan0: <MAC address removed> denied association (code=27)
[ 6280.253012] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6281.013541] wlan0: authenticate with <MAC address removed>
[ 6281.020193] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6281.025980] wlan0: authenticated
[ 6281.028179] wlan0: associate with <MAC address removed> (try 1/3)
[ 6281.033368] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=10523)
[ 6281.033389] wlan0: <MAC address removed> denied association (code=27)
[ 6281.050284] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6281.814788] wlan0: authenticate with <MAC address removed>
[ 6281.821599] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6281.825762] wlan0: authenticated
[ 6281.828476] wlan0: associate with <MAC address removed> (try 1/3)
[ 6281.831097] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=10523)
[ 6281.831113] wlan0: <MAC address removed> denied association (code=27)
[ 6281.852518] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6282.614626] wlan0: authenticate with <MAC address removed>
[ 6282.618649] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6282.626070] wlan0: authenticated
[ 6282.628465] wlan0: associate with <MAC address removed> (try 1/3)
[ 6282.631058] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 6282.631074] wlan0: <MAC address removed> denied association (code=27)
[ 6282.644552] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6283.406904] wlan0: authenticate with <MAC address removed>
[ 6283.409131] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6283.411567] wlan0: authenticated
[ 6283.412195] wlan0: associate with <MAC address removed> (try 1/3)
[ 6283.417660] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 6283.417677] wlan0: <MAC address removed> denied association (code=27)
[ 6283.442326] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6284.202482] wlan0: authenticate with <MAC address removed>
[ 6284.208744] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6284.215170] wlan0: authenticated
[ 6284.216399] wlan0: associate with <MAC address removed> (try 1/3)
[ 6284.226604] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=10523)
[ 6284.226621] wlan0: <MAC address removed> denied association (code=27)
[ 6284.240591] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6284.940140] ath5k: ath5k_hw_get_isr: ISR: 0x00001000 IMR: 0x00000000
[ 6285.002443] wlan0: authenticate with <MAC address removed>
[ 6285.008572] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6285.015782] wlan0: authenticated
[ 6285.020111] wlan0: associate with <MAC address removed> (try 1/3)
[ 6285.027186] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=10523)
[ 6285.027204] wlan0: <MAC address removed> denied association (code=27)
[ 6285.040580] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6285.803174] wlan0: authenticate with <MAC address removed>
[ 6285.809753] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6285.817545] wlan0: authenticated
[ 6285.820477] wlan0: associate with <MAC address removed> (try 1/3)
[ 6285.824131] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=4652)
[ 6285.824145] wlan0: <MAC address removed> denied association (code=27)
[ 6285.844541] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6286.606865] wlan0: authenticate with <MAC address removed>
[ 6286.611289] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6286.613422] wlan0: authenticated
[ 6286.616772] wlan0: associate with <MAC address removed> (try 1/3)
[ 6286.622581] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=128)
[ 6286.622596] wlan0: <MAC address removed> denied association (code=27)
[ 6286.644453] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6287.406757] wlan0: authenticate with <MAC address removed>
[ 6287.410754] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6287.414900] wlan0: authenticated
[ 6287.416197] wlan0: associate with <MAC address removed> (try 1/3)
[ 6287.422590] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 6287.422607] wlan0: <MAC address removed> denied association (code=27)
[ 6287.436503] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6288.197594] wlan0: authenticate with <MAC address removed>
[ 6288.205733] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6288.208095] wlan0: authenticated
[ 6288.216150] wlan0: associate with <MAC address removed> (try 1/3)
[ 6288.219364] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=4651)
[ 6288.219380] wlan0: <MAC address removed> denied association (code=27)
[ 6288.232906] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6288.994528] wlan0: authenticate with <MAC address removed>
[ 6289.000265] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6289.010180] wlan0: authenticated
[ 6289.012477] wlan0: associate with <MAC address removed> (try 1/3)
[ 6289.017015] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=128)
[ 6289.017031] wlan0: <MAC address removed> denied association (code=27)
[ 6289.032960] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6289.793668] wlan0: authenticate with <MAC address removed>
[ 6289.797865] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6289.800577] wlan0: authenticated
[ 6289.804122] wlan0: associate with <MAC address removed> (try 1/3)
[ 6289.810410] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=4652)
[ 6289.810429] wlan0: <MAC address removed> denied association (code=27)
[ 6289.816806] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6290.581795] wlan0: authenticate with <MAC address removed>
[ 6290.586746] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6290.593963] wlan0: authenticated
[ 6290.596463] wlan0: associate with <MAC address removed> (try 1/3)
[ 6290.599061] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=3094)
[ 6290.599076] wlan0: <MAC address removed> denied association (code=27)
[ 6290.608577] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6291.369607] wlan0: authenticate with <MAC address removed>
[ 6291.373804] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6291.379214] wlan0: authenticated
[ 6291.388427] wlan0: associate with <MAC address removed> (try 1/3)
[ 6291.392808] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 6291.392823] wlan0: <MAC address removed> denied association (code=27)
[ 6291.408463] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6292.169889] wlan0: authenticate with <MAC address removed>
[ 6292.174286] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6292.180081] wlan0: authenticated
[ 6292.184206] wlan0: associate with <MAC address removed> (try 1/3)
[ 6292.191321] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=10523)
[ 6292.191342] wlan0: <MAC address removed> denied association (code=27)
[ 6292.197022] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6292.957708] wlan0: authenticate with <MAC address removed>
[ 6292.961827] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6292.965252] wlan0: authenticated
[ 6292.968240] wlan0: associate with <MAC address removed> (try 1/3)
[ 6292.979044] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=128)
[ 6292.979065] wlan0: <MAC address removed> denied association (code=27)
[ 6292.993046] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6293.753880] wlan0: authenticate with <MAC address removed>
[ 6293.758987] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6293.761409] wlan0: authenticated
[ 6293.764092] wlan0: associate with <MAC address removed> (try 1/3)
[ 6293.768675] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=10986)
[ 6293.768690] wlan0: <MAC address removed> denied association (code=27)
[ 6293.780603] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6294.541949] wlan0: authenticate with <MAC address removed>
[ 6294.546317] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6294.552180] wlan0: authenticated
[ 6294.556163] wlan0: associate with <MAC address removed> (try 1/3)
[ 6294.562601] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=3094)
[ 6294.562628] wlan0: <MAC address removed> denied association (code=27)
[ 6294.574653] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6295.333911] wlan0: authenticate with <MAC address removed>
[ 6295.338271] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6295.341665] wlan0: authenticated
[ 6295.344103] wlan0: associate with <MAC address removed> (try 1/3)
[ 6295.346758] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=10523)
[ 6295.346778] wlan0: <MAC address removed> denied association (code=27)
[ 6295.356971] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6296.117611] wlan0: authenticate with <MAC address removed>
[ 6296.122100] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6296.126740] wlan0: authenticated
[ 6296.128139] wlan0: associate with <MAC address removed> (try 1/3)
[ 6296.130760] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 6296.130780] wlan0: <MAC address removed> denied association (code=27)
[ 6296.137156] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6296.897721] wlan0: authenticate with <MAC address removed>
[ 6296.901737] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6296.904953] wlan0: authenticated
[ 6296.908170] wlan0: associate with <MAC address removed> (try 1/3)
[ 6296.914752] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=128)
[ 6296.914765] wlan0: <MAC address removed> denied association (code=27)
[ 6296.945024] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6297.104168] ath5k: ath5k_hw_get_isr: ISR: 0x00040001 IMR: 0x00000000
[ 6297.705980] wlan0: authenticate with <MAC address removed>
[ 6297.710322] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6297.714847] wlan0: authenticated
[ 6297.716618] wlan0: associate with <MAC address removed> (try 1/3)
[ 6297.721553] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=4650)
[ 6297.721569] wlan0: <MAC address removed> denied association (code=27)
[ 6297.732637] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6298.494581] wlan0: authenticate with <MAC address removed>
[ 6298.499834] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6298.505287] wlan0: authenticated
[ 6298.509026] wlan0: associate with <MAC address removed> (try 1/3)
[ 6298.513395] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=10523)
[ 6298.513410] wlan0: <MAC address removed> denied association (code=27)
[ 6298.525745] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6299.286611] wlan0: authenticate with <MAC address removed>
[ 6299.292861] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6299.300722] wlan0: authenticated
[ 6299.304422] wlan0: associate with <MAC address removed> (try 1/3)
[ 6299.309065] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=10624)
[ 6299.309081] wlan0: <MAC address removed> denied association (code=27)
[ 6299.320518] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6300.081820] wlan0: authenticate with <MAC address removed>
[ 6300.085734] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6300.089406] wlan0: authenticated
[ 6300.092248] wlan0: associate with <MAC address removed> (try 1/3)
[ 6300.094972] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 6300.094999] wlan0: <MAC address removed> denied association (code=27)
[ 6300.100631] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6300.861656] wlan0: authenticate with <MAC address removed>
[ 6300.864858] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6300.866767] wlan0: authenticated
[ 6300.868701] wlan0: associate with <MAC address removed> (try 1/3)
[ 6300.871311] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=10523)
[ 6300.871332] wlan0: <MAC address removed> denied association (code=27)
[ 6300.929018] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6301.690303] wlan0: authenticate with <MAC address removed>
[ 6301.693226] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6301.697357] wlan0: authenticated
[ 6301.700152] wlan0: associate with <MAC address removed> (try 1/3)
[ 6301.703577] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=9450)
[ 6301.703594] wlan0: <MAC address removed> denied association (code=27)
[ 6301.716547] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6311.326565] wlan0: authenticate with <MAC address removed>
[ 6311.330735] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6311.332669] wlan0: authenticated
[ 6311.336096] wlan0: associate with <MAC address removed> (try 1/3)
[ 6311.339070] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=128)
[ 6311.339087] wlan0: <MAC address removed> denied association (code=27)
[ 6311.350729] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6312.113956] wlan0: authenticate with <MAC address removed>
[ 6312.118301] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6312.121911] wlan0: authenticated
[ 6312.124524] wlan0: associate with <MAC address removed> (try 1/3)
[ 6312.128589] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=4650)
[ 6312.128605] wlan0: <MAC address removed> denied association (code=27)
[ 6312.137152] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6312.897744] wlan0: authenticate with <MAC address removed>
[ 6312.900816] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6312.902821] wlan0: authenticated
[ 6312.908111] wlan0: associate with <MAC address removed> (try 1/3)
[ 6312.911664] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=10523)
[ 6312.911680] wlan0: <MAC address removed> denied association (code=27)
[ 6312.920645] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6313.681844] wlan0: authenticate with <MAC address removed>
[ 6313.686276] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6313.688556] wlan0: authenticated
[ 6313.696148] wlan0: associate with <MAC address removed> (try 1/3)
[ 6313.699017] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 6313.699038] wlan0: <MAC address removed> denied association (code=27)
[ 6313.705167] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6314.465709] wlan0: authenticate with <MAC address removed>
[ 6314.469791] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6314.473725] wlan0: authenticated
[ 6314.476244] wlan0: associate with <MAC address removed> (try 1/3)
[ 6314.479078] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=4651)
[ 6314.479108] wlan0: <MAC address removed> denied association (code=27)
[ 6314.484627] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6315.245643] wlan0: authenticate with <MAC address removed>
[ 6315.250583] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6315.258984] wlan0: authenticated
[ 6315.260423] wlan0: associate with <MAC address removed> (try 1/3)
[ 6315.263017] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=128)
[ 6315.263032] wlan0: <MAC address removed> denied association (code=27)
[ 6315.272565] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6316.033528] wlan0: authenticate with <MAC address removed>
[ 6316.037738] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6316.042434] wlan0: authenticated
[ 6316.044230] wlan0: associate with <MAC address removed> (try 1/3)
[ 6316.046922] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=4651)
[ 6316.046943] wlan0: <MAC address removed> denied association (code=27)
[ 6316.053012] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6316.818808] wlan0: authenticate with <MAC address removed>
[ 6316.822845] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6316.825202] wlan0: authenticated
[ 6316.828435] wlan0: associate with <MAC address removed> (try 1/3)
[ 6316.831747] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=128)
[ 6316.831763] wlan0: <MAC address removed> denied association (code=27)
[ 6316.852518] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6317.614247] wlan0: authenticate with <MAC address removed>
[ 6317.619035] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6317.623589] wlan0: authenticated
[ 6317.629368] wlan0: associate with <MAC address removed> (try 1/3)
[ 6317.634254] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=10523)
[ 6317.634271] wlan0: <MAC address removed> denied association (code=27)
[ 6317.644970] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6318.406665] wlan0: authenticate with <MAC address removed>
[ 6318.412544] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6318.420323] wlan0: authenticated
[ 6318.424109] wlan0: associate with <MAC address removed> (try 1/3)
[ 6318.426875] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=10523)
[ 6318.426893] wlan0: <MAC address removed> denied association (code=27)
[ 6318.440477] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6319.201714] wlan0: authenticate with <MAC address removed>
[ 6319.204895] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6319.209757] wlan0: authenticated
[ 6319.216128] wlan0: associate with <MAC address removed> (try 1/3)
[ 6319.219492] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=128)
[ 6319.219509] wlan0: <MAC address removed> denied association (code=27)
[ 6319.224586] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6319.985819] wlan0: authenticate with <MAC address removed>
[ 6319.988886] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6319.991243] wlan0: authenticated
[ 6319.996169] wlan0: associate with <MAC address removed> (try 1/3)
[ 6319.998890] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 6319.998910] wlan0: <MAC address removed> denied association (code=27)
[ 6320.004563] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6320.704189] ath5k: ath5k_hw_get_isr: ISR: 0x00001000 IMR: 0x00000000
[ 6320.765712] wlan0: authenticate with <MAC address removed>
[ 6320.770271] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6320.773956] wlan0: authenticated
[ 6320.776247] wlan0: associate with <MAC address removed> (try 1/3)
[ 6320.778874] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=4652)
[ 6320.778894] wlan0: <MAC address removed> denied association (code=27)
[ 6320.784614] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6321.545743] wlan0: authenticate with <MAC address removed>
[ 6321.550876] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6321.554812] wlan0: authenticated
[ 6321.556417] wlan0: associate with <MAC address removed> (try 1/3)
[ 6321.559019] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=128)
[ 6321.559038] wlan0: <MAC address removed> denied association (code=27)
[ 6321.562016] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6322.321780] wlan0: authenticate with <MAC address removed>
[ 6322.325732] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6322.328762] wlan0: authenticated
[ 6322.332182] wlan0: associate with <MAC address removed> (try 1/3)
[ 6322.334813] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=128)
[ 6322.334834] wlan0: <MAC address removed> denied association (code=27)
[ 6322.377023] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6323.137706] wlan0: authenticate with <MAC address removed>
[ 6323.141756] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6323.145901] wlan0: authenticated
[ 6323.148246] wlan0: associate with <MAC address removed> (try 1/3)
[ 6323.150872] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=3094)
[ 6323.150892] wlan0: <MAC address removed> denied association (code=27)
[ 6323.161011] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6323.923293] wlan0: authenticate with <MAC address removed>
[ 6323.925296] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6323.927389] wlan0: authenticated
[ 6323.932119] wlan0: associate with <MAC address removed> (try 1/3)
[ 6323.937335] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=3094)
[ 6323.937350] wlan0: <MAC address removed> denied association (code=27)
[ 6323.949189] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6324.709655] wlan0: authenticate with <MAC address removed>
[ 6324.714437] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6324.718484] wlan0: authenticated
[ 6324.720304] wlan0: associate with <MAC address removed> (try 1/3)
[ 6324.723254] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=27 aid=0)
[ 6324.723273] wlan0: <MAC address removed> denied association (code=27)
[ 6324.732596] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)


****************** done ******************
```

---

### Post by wildmanne39 on 2014-02-15
*Thread moved to **Networking & Wireless**.*

---

### Post by varunendra on 2014-02-16
Hi jmorri36! Welcome to the Ubuntu Forums !

It seems to me that you have a Samsung Notebook, not an Asus. So I requested the mods to move your post to your own thread.

Something doesn't look right with your wireless_script report. You said you could join other networks, but the **iwlist scan** part of the script doesn't show any available networks around (the nm-tool part shows cached results, could be from some other place).

Besides, your system doesn't even have the /etc/network/interfaces file or the /etc/resolv.conf files????
That's very surprising and a possible indication of a broken install, but you say your are able to join other networks?

Please post the outputs of these commands separately -
```
cat /etc/network/interfaces
cat /etc/resolv.conf
sudo iwlist scan
```

And is your home network "The Feinberg" ? Which one if not?

In the meanwhile, you may try a temporary parameter with your driver. Open a terminal (Ctrl-Alt-T) and run these commands -
```
sudo modprobe -rv ath5k
sudo modprobe -v ath5k nohwcrypt=Y
```
This will be a temporary change that will be lost at next boot. So try scanning/connecting without rebooting after running above codes. If it seems to help, we'll make it permanent.

---

