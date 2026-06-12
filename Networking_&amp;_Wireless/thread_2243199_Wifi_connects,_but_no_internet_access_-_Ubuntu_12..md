---
title: "Wifi connects, but no internet access - Ubuntu 12.04.5 LTS"
date: 2014-09-07
forum: Networking &amp; Wireless
---

### Post by carl19 on 2014-09-07
Hi, i am quite new to linux and i have a problem with my Samsung np535u3c-a05se.

As the title says, the wifi connects but it doesnt give me internet access, if i put a cable between my router and the laptop, i get internet access.

Heres the script results from the sticky:

```



########## wireless info START ##########


Report from: 07 Sep 2014 13:26 CEST +0200


Script from: 05 Sep 2014 22:42 UTC +0000


##### release #####


Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:    12.04
Codename:    precise


##### kernel #####


Linux 3.13.0-35-generic #62~precise1-Ubuntu SMP Mon Aug 18 14:53:38 UTC 2014 i686 athlon i386 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop #####


Ubuntu


##### lspci #####


01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Samsung Electronics Co Ltd Device [144d:c660]
    Kernel driver in use: r8169


03:00.0 Network controller [0280]: Qualcomm Atheros AR9462 Wireless Network Adapter [168c:0034] (rev 01)
    Subsystem: Samsung Electronics Co Ltd Device [144d:4112]
    Kernel driver in use: ath9k


##### lsusb #####


Bus 002 Device 003: ID 2232:1035  
Bus 004 Device 003: ID 0cf3:3004 Atheros Communications, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub


##### PCMCIA card info #####


##### rfkill #####


0: samsung-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: samsung-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #####


ath9k                 150514  0 
mac80211              564446  1 ath9k
ath9k_common           13359  1 ath9k
ath9k_hw              446556  2 ath9k,ath9k_common
ath                    24297  3 ath9k,ath9k_common,ath9k_hw
ath3k                  13152  0 
cfg80211              423921  3 ath9k,mac80211,ath
bluetooth             356727  25 bnep,rfcomm,ath3k,btusb
wmi                    18827  0 


##### interfaces #####


auto lo
iface lo inet loopback


##### ifconfig #####


eth0      Link encap:Ethernet  HWaddr <MAC addr eth0>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan0     Link encap:Ethernet  HWaddr <MAC addr wlan0>  
          inet addr:192.168.0.106  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::52b7:c3ff:fef2:1e90/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:64 errors:0 dropped:0 overruns:0 frame:0
          TX packets:112 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7195 (7.1 KB)  TX bytes:16202 (16.2 KB)


##### iwconfig #####


lo        no wireless extensions.


eth0      no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:"swagyoloswag"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC addr swagyoloswag>   
          Bit Rate=65 Mb/s   Tx-Power=17 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=66/70  Signal level=-44 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:32   Missed beacon:0


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0


##### resolv.conf #####


nameserver 127.0.0.1


##### nm-tool #####


NetworkManager Tool


State: connected (global)


- Device: wlan0  [swagyoloswag] ------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        <MAC addr wlan0>


  Capabilities:
    Speed:           65 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    TN_private_48:   Infra, <MAC addr TN_private_48>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA
    Ohlssons:        Infra, <MAC addr Ohlssons>, Freq 2412 MHz, Rate 54 Mb/s, Strength 89 WPA WPA2
    NETGEAR66:       Infra, <MAC addr NETGEAR66>, Freq 2437 MHz, Rate 54 Mb/s, Strength 89 WPA2
    Kronan:          Infra, <MAC addr Kronan>, Freq 2412 MHz, Rate 54 Mb/s, Strength 85 WPA2
    ASUS_jonte:      Infra, <MAC addr ASUS_jonte>, Freq 2412 MHz, Rate 54 Mb/s, Strength 65 WPA2
    Where is your god now: Infra, <MAC addr Where is your god now>, Freq 2437 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2
    D-Link:          Infra, <MAC addr D-Link>, Freq 2442 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2
    TP-LINK_442406:  Infra, <MAC addr TP-LINK_442406>, Freq 2462 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2
    In tha house:    Infra, <MAC addr In tha house>, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WPA
    Tettes:          Infra, <MAC addr Tettes>, Freq 2462 MHz, Rate 54 Mb/s, Strength 55 WPA WPA2
    NETGEAR28:       Infra, <MAC addr NETGEAR28>, Freq 2437 MHz, Rate 54 Mb/s, Strength 54 WPA2
    Swedish Mafia:   Infra, <MAC addr Swedish Mafia>, Freq 2447 MHz, Rate 54 Mb/s, Strength 50 WPA2
    Rakhyvel:        Infra, <MAC addr Rakhyvel>, Freq 2442 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    Why Fy:          Infra, <MAC addr Why Fy>, Freq 2417 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    Josef:           Infra, <MAC addr Josef>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA
    *swagyoloswag:   Infra, <MAC addr swagyoloswag>, Freq 2462 MHz, Rate 54 Mb/s, Strength 59 WPA WPA2
    Gustafismybitch: Infra, <MAC addr Gustafismybitch>, Freq 2462 MHz, Rate 54 Mb/s, Strength 50 WPA2
    local buckling:  Infra, <MAC addr local buckling>, Freq 2452 MHz, Rate 54 Mb/s, Strength 29 WPA2
    NETGEAR94:       Infra, <MAC addr NETGEAR94>, Freq 2412 MHz, Rate 54 Mb/s, Strength 55 WPA2
    EnLitenKo:       Infra, <MAC addr EnLitenKo>, Freq 2412 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    belkin54g:       Infra, <MAC addr belkin54g>, Freq 2462 MHz, Rate 54 Mb/s, Strength 39 WPA
    Bobonet:         Infra, <MAC addr Bobonet>, Freq 2462 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    BlueFire:        Infra, <MAC addr BlueFire>, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    LeMansion24:     Infra, <MAC addr LeMansion24>, Freq 2467 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    William:         Infra, <MAC addr William>, Freq 2457 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    Nisseshund_Network: Infra, <MAC addr Nisseshund_Network>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA2
    SV:              Infra, <MAC addr SV>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WEP
    Enrique:         Infra, <MAC addr Enrique>, Freq 2412 MHz, Rate 54 Mb/s, Strength 59 WPA2
    TP-LINK_75E710:  Infra, <MAC addr TP-LINK_75E710>, Freq 2412 MHz, Rate 54 Mb/s, Strength 59
    PrettyflyforaWiFi: Infra, <MAC addr PrettyflyforaWiFi>, Freq 2412 MHz, Rate 54 Mb/s, Strength 49 WPA2
    Buffup:          Infra, <MAC addr Buffup>, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA2


  IPv4 Settings:
    Address:         192.168.0.106
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             192.168.0.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC addr eth0>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


##### NetworkManager.state #####


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf #####


[main]
plugins=ifupdown,keyfile
dns=dnsmasq


no-auto-default=<MAC addr eth0>,


[ifupdown]
managed=false


##### iw reg get #####


country GB:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5490 - 5710 @ 40), (N/A, 27), DFS


##### iwlist channels #####


lo        no frequency information.


eth0      no frequency information.


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
          Current Frequency=2.462 GHz (Channel 11)


##### iwlist scan #####


wlan0     Interface doesn't support scanning : Device or resource busy


lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


##### module infos #####


[ath9k]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     DF02272C2FA4678C49046E5
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 686 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)


[ath9k_common]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     696B00A6C59713EC0966997
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 686 


[ath9k_hw]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     4809F3842A0542CD6B556D3
depends:        ath
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 686 


[ath]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 686 


[ath3k]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     98A5245588C09E5E41690D0
depends:        bluetooth
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 686 


##### module parameters #####


[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
nohwcrypt: 1
ps_enable: 0


##### /etc/modules #####


lp


##### blacklists #####


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


##### rc.local #####


exit 0


##### udev rules #####


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:04.0/0000:01:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:15.0/0000:03:00.0 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #####


[   14.110457] psmouse serio1: elantech: assuming hardware version 3 (with firmware version 0x450f00)
[   15.294475] ath: phy0: ASPM enabled: 0x42
[   15.294480] ath: EEPROM regdomain: 0x6a
[   15.294482] ath: EEPROM indicates we should expect a direct regpair map
[   15.294487] ath: Country alpha2 being used: 00
[   15.294489] ath: Regpair used: 0x6a
[   21.576653] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[   29.359670] wlan0: authenticate with <MAC addr swagyoloswag>
[   29.376296] wlan0: send auth to <MAC addr swagyoloswag> (try 1/3)
[   29.378517] wlan0: authenticated
[   29.381876] wlan0: associate with <MAC addr swagyoloswag> (try 1/3)
[   29.400787] wlan0: RX AssocResp from <MAC addr swagyoloswag> (capab=0xc11 status=0 aid=2)
[   29.400848] wlan0: associated
[   29.400893] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   29.406843] ath: EEPROM regdomain: 0x833a
[   29.406847] ath: EEPROM indicates we should expect a country code
[   29.406850] ath: doing EEPROM country->regdmn map search
[   29.406853] ath: country maps to regdmn code: 0x37
[   29.406855] ath: Country alpha2 being used: GB
[   29.406857] ath: Regpair used: 0x37
[   29.406859] ath: regdomain 0x833a dynamically updated by country IE
[   32.439136] wlan0: deauthenticated from <MAC addr swagyoloswag> (Reason: 2)
[   36.024939] wlan0: authenticate with <MAC addr swagyoloswag>
[   36.040548] wlan0: send auth to <MAC addr swagyoloswag> (try 1/3)
[   36.048217] wlan0: authenticated
[   36.051241] wlan0: associate with <MAC addr swagyoloswag> (try 1/3)
[   36.058520] wlan0: RX AssocResp from <MAC addr swagyoloswag> (capab=0xc11 status=0 aid=2)
[   36.058580] wlan0: associated
[   36.064201] ath: EEPROM regdomain: 0x833a
[   36.064206] ath: EEPROM indicates we should expect a country code
[   36.064209] ath: doing EEPROM country->regdmn map search
[   36.064212] ath: country maps to regdmn code: 0x37
[   36.064215] ath: Country alpha2 being used: GB
[   36.064217] ath: Regpair used: 0x37
[   36.064220] ath: regdomain 0x833a dynamically updated by country IE


########## wireless info END ############



```

If theres any more information you need, just tell me and i will try to provide it.
Thank you for your time.

---

### Post by varunendra on 2014-09-07
Welcome to Ubuntu Forums carl19 !

Wow!! You seem to have run every command in the script manually, that is not how you 'run a script'. :)

You should run it just like -
```
./wireless_script
```
..or
```
bash wireless_script
```
Replace "wireless_script" with "wireless_script.txt" if your browser automatically appended ".txt" to its name during the download (chromium does it, others may too).

It will generate a report file named "wireless-info.txt" or "wireless-info.tar.gz" at the same location where the script is (by default your Home directory, if you used the command line method to download/run it, or "Downloads" directory if you manually downloaded it).

You have to copy-past the contents of this report file, or attach the file itself in your post here.

What you have posted currently looks like a scary jungle of cryptic codes. :p

**PS:**
I suggest you read this post very carefully to download and run the (alternative) script again : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)


**[COLOR="#B22222"]EDIT:[/COLOR]**
For now, please change the encryption type in your router/Access-Point to pure **WPA2-PSK with AES (CCMP)**. Currently it is using WPA/WPA2 mixed mode with TKIP. Reboot the router after saving the change.

---

### Post by carl19 on 2014-09-07
oh lol, well i updated the first post with info and im going to update the encryption on the router, and ill get back to you

edit: wow, it worked to change the encryption.. thanks man. but i guess the problem will still stick around if you try to connect to a router with that encoding, correct?

---

### Post by varunendra on 2014-09-07
> **carl19 said:**
> edit: wow, it worked to change the encryption.. thanks man. but i guess the problem will still stick around if you try to connect to a router with that encoding, correct?

Not always, but yes, if your driver is having trouble with that combination, it may face the same problem at other places.

It is not actually an ideal solution at all, since WPA/WPA2 mixed mode is almost always the default setting for access-points. The drivers are supposed to pick up the part they support, and work with it.

The WPA/TKIP part is kept only and only for backward compatibility, with ancient devices that can't support WPA2/AES. Changing it to pure WPA2/AES is just 'Optimizing' it for modern hardware that can support it properly. AES is both more secure and more efficient than TKIP, so drivers usually work better with it.

It is possible that the problem is actually something else (can be even external), and the WPA/WPA2 mixed mode was just adding to it. In which case, solving that other problem could solve the browsing problem as well.

For example, you can try a driver parameter that is commonly used with your driver (ath9k) -
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
```
Reboot for the change to take effect. This causes the driver to load with "nohwcrypt=1" parameter from next time which disables hardware based encryption and shifts it to software based encryption. It often (but not always) helps in similar cases as yours. If it works in your case as well (with WPA/WPA2 mixed mode), consider it an added measure but keep your router to pure WPA2/AES for best performance. :)

---

### Post by carl19 on 2014-09-07
awesome, think that worked with the old settings, thank you very much.

---

### Post by varunendra on 2014-09-07
You're welcome! Pleased to know it helped. :)

---

