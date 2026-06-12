---
title: "Problems whit unstable wireless (Ralink RT5390)"
date: 2014-02-07
forum: Networking &amp; Wireless
---

### Post by Nathal on 2014-02-07
Hello 

First some details: Nootebook Compaq Presario CQ57
OS: Xubuntu 12.04.4 LTS
Build in wireless card:  Ralink RT5390


Iwconfig results:  IEEE 802.11bgn  ESSID:"HG655D-339CB3"  
          Mode:Managed  Frequency:2.437 GHz
          Bit Rate=36 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS throff   Fragment throff
          Power Managementoff
          Link Quality=29/70  Signal level=-81 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:3893  Invalid misc:14706   Missed beacon:0

Edit: Some ohter info: Network controller: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe	Subsystem: Hewlett-Packard Company U98Z077.00 Half-size Mini PCIe Card
	Flags: bus master, fast devsel, latency 0, IRQ 23
	Memory at f0200000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: rt2800pci
	Kernel modules: rt2800pci


Installed driver: rt2800pci

It change every time, and sometimes its very slow connection.
Have looking on the Internet for solutions, but its hard to find.


I hope someone can help me whit this.

Thx already

---

### Post by varunendra on 2014-02-07
Welcome to the forums Nathal !

Please try this in a terminal -
```
sudo modprobe -rv rt2800pci
sudo modprobe -v rt2800pci nohwcrypt=Y
```
The first command will remove the driver (thus disabling the wifi) and the second one will reload it with parameter "nohwcrypt=Y". This will be a temporary change that will be lost at next boot. If it seems to help, we can make it permanent.

If it doesn't help, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by Nathal on 2014-02-07
sudo modprobe -rv rt2800pci
sudo modprobe -v rt2800pci nohwcrypt=Y

[COLOR=#222222][FONT=Verdana][SIZE=2]In begin it works, but then later y get the same slow connection.

---------------------
So here my info.[/SIZE][/FONT][/COLOR]

```

 

*************** info trace ***************


***** uname -a *****


Linux nahtal 3.2.0-58-generic-pae #88-Ubuntu SMP Tue Dec 3 18:00:02 UTC 2013 i686 athlon i386 GNU/Linux


***** lsb_release *****


Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise


***** lspci *****


06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:3577]
    Kernel driver in use: r8169
--
07:00.0 Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390]
    Subsystem: Hewlett-Packard Company U98Z077.00 Half-size Mini PCIe Card [103c:1636]
    Kernel driver in use: rt2800pci


***** lsusb *****


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 07ab:fc8e Freecom Technologies 
Bus 002 Device 002: ID 0c45:6321 Microdia 
Bus 003 Device 002: ID 1532:001c Razer USA, Ltd RZ01-0036 Optical Gaming Mouse [Abyssus]
Bus 003 Device 003: ID 04d9:1702 Holtek Semiconductor, Inc. 


***** PCMCIA Card Info *****




***** iwconfig *****


wlan0     IEEE 802.11bgn  ESSID:"HG655D-339CB3"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC address removed>   
          Bit Rate=36 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=33/70  Signal level=-77 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:600  Invalid misc:1702   Missed beacon:0




***** rfkill *****


0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


***** lsmod *****


rt2800pci              18340  0 
rt2800lib              53298  1 rt2800pci
crc_ccitt              12627  1 rt2800lib
rt2x00pci              14237  1 rt2800pci
rt2x00lib              48923  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              436493  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              178877  2 rt2x00lib,mac80211
eeprom_93cx6           12687  1 rt2800pci


***** nm-tool *****


NetworkManager Tool


State: connected (global)


- Device: wlan0  [HG655D-339CB3] -----------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           36 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    SitecomCC6670:   Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 15 WPA2
    SitecomA12C48:   Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    *HG655D-339CB3:  Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 43 WPA2
    ICIDU:           Infra, <MAC address removed>, Freq 2442 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    Thomson4BB892:   Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    SpeedTouchD009F2:Infra, <MAC address removed>, Freq 2452 MHz, Rate 54 Mb/s, Strength 9
    linksys:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 12 WPA WPA2
    dlink Riemens:   Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    ARV75192D9282:   Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 12 WPA WPA2


  IPv4 Settings:
    Address:         192.168.1.67
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1




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
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"HG655D-339CB3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001ba8076644
                    Extra: Last beacon: 72ms ago
                    IE: Unknown: 000D4847363535442D333339434233
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DDA20050F204104A0001101044000102103B00010310470010BC329E001DD811B286017A6E5C339CB01021001D48756177656920546563686E6F6C6F6769657320436F2E2C204C74642E1023001C48756177656920576972656C6573732041636365737320506F696E74102400065254323836301042000831323334353637381054000800060050F204000110110009487561776569415053100800020004103C000100
                    IE: Unknown: 0B0502001D127A
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706434120010D10
          Cell 02 - Address: <MAC address removed>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"SitecomA12C48"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000003b859d80
                    Extra: Last beacon: 768ms ago
                    IE: Unknown: 000D53697465636F6D413132433438
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030104
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101870003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34040D0A00000000000000000000000000000000000000
                    IE: Unknown: 3D16040D0A00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010006004000
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 03 - Address: <MAC address removed>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"ICIDU"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000013c8793ec
                    Extra: Last beacon: 568ms ago
                    IE: Unknown: 00054943494455
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030107
                    IE: Unknown: 050400010008
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34070F0800000000000000000000000000000000000000
                    IE: Unknown: 3D16070F0800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000004000
          Cell 04 - Address: <MAC address removed>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:off
                    ESSID:"SpeedTouchD009F2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000ebea2a936d
                    Extra: Last beacon: 236ms ago
                    IE: Unknown: 00105370656564546F756368443030394632
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030109
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD050010180109
          Cell 05 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"SitecomCC6670"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000164ca9f8180
                    Extra: Last beacon: 104ms ago
                    IE: Unknown: 000D53697465636F6D434336363730
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD070050F202000100
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B07190000000F000000000000000000000000000000
                    IE: Unknown: DD1E00904C336E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B07010000000F000000000000000000000000000000
                    IE: Unknown: 050400010000
                    IE: Unknown: DD130050F204104A0001101044000101103C000102




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


filename:       /lib/modules/3.2.0-58-generic-pae/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     B814F1B7538F8B99ECC7D4E
alias:          pci:v00001814d0000539Fsv*sd*bc*sc*i*
alias:          pci:v00001814d0000539Asv*sd*bc*sc*i*
alias:          pci:v00001814d00005390sv*sd*bc*sc*i*
alias:          pci:v00001814d00003593sv*sd*bc*sc*i*
alias:          pci:v00001814d00003592sv*sd*bc*sc*i*
alias:          pci:v00001814d00003562sv*sd*bc*sc*i*
alias:          pci:v00001814d00003062sv*sd*bc*sc*i*
alias:          pci:v00001814d00003060sv*sd*bc*sc*i*
alias:          pci:v00001432d00007722sv*sd*bc*sc*i*
alias:          pci:v00001432d00007711sv*sd*bc*sc*i*
alias:          pci:v00001814d00003390sv*sd*bc*sc*i*
alias:          pci:v00001A3Bd00001059sv*sd*bc*sc*i*
alias:          pci:v00001462d0000891Asv*sd*bc*sc*i*
alias:          pci:v00001432d00007768sv*sd*bc*sc*i*
alias:          pci:v00001432d00007758sv*sd*bc*sc*i*
alias:          pci:v00001432d00007748sv*sd*bc*sc*i*
alias:          pci:v00001432d00007738sv*sd*bc*sc*i*
alias:          pci:v00001432d00007728sv*sd*bc*sc*i*
alias:          pci:v00001432d00007727sv*sd*bc*sc*i*
alias:          pci:v00001432d00007708sv*sd*bc*sc*i*
alias:          pci:v00001814d00003092sv*sd*bc*sc*i*
alias:          pci:v00001814d00003091sv*sd*bc*sc*i*
alias:          pci:v00001814d00003090sv*sd*bc*sc*i*
alias:          pci:v00001814d00000781sv*sd*bc*sc*i*
alias:          pci:v00001814d00000701sv*sd*bc*sc*i*
alias:          pci:v00001814d00000681sv*sd*bc*sc*i*
alias:          pci:v00001814d00000601sv*sd*bc*sc*i*
depends:        rt2x00lib,rt2800lib,rt2x00pci,eeprom_93cx6
intree:         Y
vermagic:       3.2.0-58-generic-pae SMP mod_unload modversions 686 
parm:           nohwcrypt:Disable hardware encryption. (bool)


filename:       /lib/modules/3.2.0-58-generic-pae/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     5EABEA0AE546B2B7B7EBC1A
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       3.2.0-58-generic-pae SMP mod_unload modversions 686 


filename:       /lib/modules/3.2.0-58-generic-pae/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     08908183858CCF43D7F7541
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.2.0-58-generic-pae SMP mod_unload modversions 686 


filename:       /lib/modules/3.2.0-58-generic-pae/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     E604D2DEC4141A1B32A11E7
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.2.0-58-generic-pae SMP mod_unload modversions 686 




***** udev rules *****


# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:15.1/0000:06:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x1814:/sys/devices/pci0000:00/0000:00:15.3/0000:07:00.0 (rt2800pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


***** dmesg *****


[26671.760950] wlan0: authenticate with <MAC address removed> (try 1)
[26671.765466] wlan0: authenticated
[26671.767185] wlan0: associate with <MAC address removed> (try 1)
[26671.776605] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[26671.776620] wlan0: associated
[27508.492406] ieee80211 phy0: wlan0: No probe response from AP <MAC address removed> after 500ms, disconnecting.
[27509.756247] wlan0: authenticate with <MAC address removed> (try 1)
[27509.759330] wlan0: authenticated
[27509.760457] wlan0: associate with <MAC address removed> (try 1)
[27509.960140] wlan0: associate with <MAC address removed> (try 2)
[27509.966149] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[27509.966164] wlan0: associated
[27513.031641] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[27514.269360] wlan0: authenticate with <MAC address removed> (try 1)
[27514.274256] wlan0: authenticated
[27514.275280] wlan0: associate with <MAC address removed> (try 1)
[27514.472409] wlan0: associate with <MAC address removed> (try 2)
[27514.672409] wlan0: associate with <MAC address removed> (try 3)
[27514.872404] wlan0: association with <MAC address removed> timed out
[27522.240547] wlan0: authenticate with <MAC address removed> (try 1)
[27522.440405] wlan0: authenticate with <MAC address removed> (try 2)
[27522.444605] wlan0: authenticated
[27522.445560] wlan0: associate with <MAC address removed> (try 1)
[27522.451599] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[27522.451614] wlan0: associated
[27548.504339] ieee80211 phy0: wlan0: No probe response from AP <MAC address removed> after 500ms, disconnecting.
[27549.765085] wlan0: authenticate with <MAC address removed> (try 1)
[27549.766765] wlan0: authenticated
[27549.769363] wlan0: associate with <MAC address removed> (try 1)
[27549.789322] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[27549.789336] wlan0: associated
[27555.504412] ieee80211 phy0: wlan0: No probe response from AP <MAC address removed> after 500ms, disconnecting.
[27556.748521] wlan0: authenticate with <MAC address removed> (try 1)
[27556.750119] wlan0: authenticated
[27556.750814] wlan0: associate with <MAC address removed> (try 1)
[27556.948404] wlan0: associate with <MAC address removed> (try 2)
[27556.954417] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[27556.954433] wlan0: associated
[27561.143692] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[27562.380638] wlan0: authenticate with <MAC address removed> (try 1)
[27562.383414] wlan0: authenticated
[27562.384887] wlan0: associate with <MAC address removed> (try 1)
[27562.404848] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[27562.404863] wlan0: associated
[27567.500412] ieee80211 phy0: wlan0: No probe response from AP <MAC address removed> after 500ms, disconnecting.
[27568.740756] wlan0: authenticate with <MAC address removed> (try 1)
[27568.745600] wlan0: authenticated
[27568.746631] wlan0: associate with <MAC address removed> (try 1)
[27568.760689] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[27568.760704] wlan0: associated
[27571.259056] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[27572.610322] wlan0: authenticate with <MAC address removed> (try 1)
[27572.612054] wlan0: authenticated
[27572.613506] wlan0: associate with <MAC address removed> (try 1)
[27572.617154] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[27572.617163] wlan0: associated
[27583.496260] wlan0: no IPv6 routers present
[27638.492409] ieee80211 phy0: wlan0: No probe response from AP <MAC address removed> after 500ms, disconnecting.
[27639.749424] wlan0: authenticate with <MAC address removed> (try 1)
[27639.751086] wlan0: authenticated
[27639.751796] wlan0: associate with <MAC address removed> (try 1)
[27639.764261] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[27639.764276] wlan0: associated
[27815.504414] ieee80211 phy0: wlan0: No probe response from AP <MAC address removed> after 500ms, disconnecting.
[27816.752530] wlan0: authenticate with <MAC address removed> (try 1)
[27816.754103] wlan0: authenticated
[27816.757180] wlan0: associate with <MAC address removed> (try 1)
[27816.956298] wlan0: associate with <MAC address removed> (try 2)
[27816.959103] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[27816.959118] wlan0: associated
[27820.504440] ieee80211 phy0: wlan0: No probe response from AP <MAC address removed> after 500ms, disconnecting.
[27834.038867] wlan0: direct probe to <MAC address removed> (try 1/3)
[27834.236412] wlan0: direct probe to <MAC address removed> (try 2/3)
[27834.436135] wlan0: direct probe to <MAC address removed> (try 3/3)
[27834.636403] wlan0: direct probe to <MAC address removed> timed out
[27836.243828] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[27837.613041] wlan0: direct probe to <MAC address removed> (try 1/3)
[27837.812410] wlan0: direct probe to <MAC address removed> (try 2/3)
[27837.819835] wlan0: direct probe responded
[27837.820412] wlan0: authenticate with <MAC address removed> (try 1)
[27837.822713] wlan0: authenticated
[27837.823602] wlan0: associate with <MAC address removed> (try 1)
[27837.828935] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[27837.828951] wlan0: associated
[27837.830545] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[27848.624306] wlan0: no IPv6 routers present
[27871.504421] ieee80211 phy0: wlan0: No probe response from AP <MAC address removed> after 500ms, disconnecting.
[27878.882787] wlan0: direct probe to <MAC address removed> (try 1/3)
[27879.080383] wlan0: direct probe to <MAC address removed> (try 2/3)
[27879.280399] wlan0: direct probe to <MAC address removed> (try 3/3)
[27879.480387] wlan0: direct probe to <MAC address removed> timed out
[27885.052952] wlan0: direct probe to <MAC address removed> (try 1/3)
[27885.252407] wlan0: direct probe to <MAC address removed> (try 2/3)
[27885.452362] wlan0: direct probe to <MAC address removed> (try 3/3)
[27885.652419] wlan0: direct probe to <MAC address removed> timed out
[27887.265428] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[27898.960894] wlan0: direct probe to <MAC address removed> (try 1/3)
[27899.160182] wlan0: direct probe to <MAC address removed> (try 2/3)
[27899.360334] wlan0: direct probe to <MAC address removed> (try 3/3)
[27899.560406] wlan0: direct probe to <MAC address removed> timed out
[27912.860892] wlan0: direct probe to <MAC address removed> (try 1/3)
[27913.060410] wlan0: direct probe to <MAC address removed> (try 2/3)
[27913.260411] wlan0: direct probe to <MAC address removed> (try 3/3)
[27913.460244] wlan0: direct probe to <MAC address removed> timed out
[27938.892859] wlan0: direct probe to <MAC address removed> (try 1/3)
[27939.092373] wlan0: direct probe to <MAC address removed> (try 2/3)
[27939.292372] wlan0: direct probe to <MAC address removed> (try 3/3)
[27939.492369] wlan0: direct probe to <MAC address removed> timed out
[28381.296069] wlan0: direct probe to <MAC address removed> (try 1/3)
[28381.496348] wlan0: direct probe to <MAC address removed> (try 2/3)
[28381.696412] wlan0: direct probe to <MAC address removed> (try 3/3)
[28381.896294] wlan0: direct probe to <MAC address removed> timed out
[28389.132782] wlan0: direct probe to <MAC address removed> (try 1/3)
[28389.332086] wlan0: direct probe to <MAC address removed> (try 2/3)
[28389.532090] wlan0: direct probe to <MAC address removed> (try 3/3)
[28389.732216] wlan0: direct probe to <MAC address removed> timed out
[28409.123290] wlan0: direct probe to <MAC address removed> (try 1/3)
[28409.320411] wlan0: direct probe to <MAC address removed> (try 2/3)
[28409.520296] wlan0: direct probe to <MAC address removed> (try 3/3)
[28409.720206] wlan0: direct probe to <MAC address removed> timed out
[28423.032965] wlan0: direct probe to <MAC address removed> (try 1/3)
[28423.232295] wlan0: direct probe to <MAC address removed> (try 2/3)
[28423.432220] wlan0: direct probe to <MAC address removed> (try 3/3)
[28423.632174] wlan0: direct probe to <MAC address removed> timed out
[28849.142684] wlan0: authenticate with <MAC address removed> (try 1)
[28849.144997] wlan0: authenticated
[28849.149381] wlan0: associate with <MAC address removed> (try 1)
[28849.156815] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[28849.156824] wlan0: associated
[28849.158380] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[28860.320258] wlan0: no IPv6 routers present
[29708.504442] ieee80211 phy0: wlan0: No probe response from AP <MAC address removed> after 500ms, disconnecting.
[29724.242600] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[29740.118359] wlan0: direct probe to <MAC address removed> (try 1/3)
[29740.316248] wlan0: direct probe to <MAC address removed> (try 2/3)
[29740.516168] wlan0: direct probe to <MAC address removed> (try 3/3)
[29740.716172] wlan0: direct probe to <MAC address removed> timed out
[29778.290945] wlan0: authenticate with <MAC address removed> (try 1)
[29778.292674] wlan0: authenticated
[29778.293595] wlan0: associate with <MAC address removed> (try 1)
[29778.298230] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[29778.298245] wlan0: associated
[29778.299746] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[29783.492215] ieee80211 phy0: wlan0: No probe response from AP <MAC address removed> after 500ms, disconnecting.
[29784.740983] wlan0: authenticate with <MAC address removed> (try 1)
[29784.940370] wlan0: authenticate with <MAC address removed> (try 2)
[29784.947121] wlan0: authenticated
[29784.948274] wlan0: associate with <MAC address removed> (try 1)
[29785.148129] wlan0: associate with <MAC address removed> (try 2)
[29785.348211] wlan0: associate with <MAC address removed> (try 3)
[29785.548237] wlan0: association with <MAC address removed> timed out
[30206.226939] wlan0: direct probe to <MAC address removed> (try 1/3)
[30206.424323] wlan0: direct probe to <MAC address removed> (try 2/3)
[30206.624284] wlan0: direct probe to <MAC address removed> (try 3/3)
[30206.824376] wlan0: direct probe to <MAC address removed> timed out
[30212.465181] wlan0: direct probe to <MAC address removed> (try 1/3)
[30212.664462] wlan0: direct probe to <MAC address removed> (try 2/3)
[30212.864292] wlan0: direct probe to <MAC address removed> (try 3/3)
[30213.064282] wlan0: direct probe to <MAC address removed> timed out
[30218.640758] wlan0: direct probe to <MAC address removed> (try 1/3)
[30218.840386] wlan0: direct probe to <MAC address removed> (try 2/3)
[30219.040411] wlan0: direct probe to <MAC address removed> (try 3/3)
[30219.240407] wlan0: direct probe to <MAC address removed> timed out
[30232.556786] wlan0: direct probe to <MAC address removed> (try 1/3)
[30232.756408] wlan0: direct probe to <MAC address removed> (try 2/3)
[30232.956408] wlan0: direct probe to <MAC address removed> (try 3/3)
[30233.156407] wlan0: direct probe to <MAC address removed> timed out
[30238.729035] wlan0: direct probe to <MAC address removed> (try 1/3)
[30238.928407] wlan0: direct probe to <MAC address removed> (try 2/3)
[30239.128407] wlan0: direct probe to <MAC address removed> (try 3/3)
[30239.328407] wlan0: direct probe to <MAC address removed> timed out
[30258.712472] wlan0: authenticate with <MAC address removed> (try 1)
[30258.912293] wlan0: authenticate with <MAC address removed> (try 2)
[30259.112404] wlan0: authenticate with <MAC address removed> (try 3)
[30259.312402] wlan0: authentication with <MAC address removed> timed out
[31294.056101] wlan0: authenticate with <MAC address removed> (try 1)
[31294.057729] wlan0: authenticated
[31294.058934] wlan0: associate with <MAC address removed> (try 1)
[31294.061454] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[31294.061463] wlan0: associated
[31304.720257] wlan0: no IPv6 routers present
[73244.864879] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[73244.972473] rt2800pci 0000:07:00.0: PCI INT A disabled
[73260.749494] rt2800pci 0000:07:00.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[73260.749566] rt2800pci 0000:07:00.0: setting latency timer to 64
[73260.763273] Registered led device: rt2800pci-phy0::radio
[73260.763367] Registered led device: rt2800pci-phy0::assoc
[73260.763408] Registered led device: rt2800pci-phy0::quality
[73260.965140] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[73260.966811] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[73264.120542] wlan0: authenticate with <MAC address removed> (try 1)
[73264.123109] wlan0: authenticated
[73264.140376] wlan0: associate with <MAC address removed> (try 1)
[73264.143111] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[73264.143126] wlan0: associated
[73264.145282] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[73265.425905] wlan0: IPv6 duplicate address fe80::7ee9:d3ff:fe35:1ae8 detected!
[75900.448744] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[75901.855694] rt2800pci 0000:07:00.0: PCI INT A disabled
[75913.186117] rt2800pci 0000:07:00.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[75913.186138] rt2800pci 0000:07:00.0: setting latency timer to 64
[75913.190861] Registered led device: rt2800pci-phy0::radio
[75913.190905] Registered led device: rt2800pci-phy0::assoc
[75913.190950] Registered led device: rt2800pci-phy0::quality
[75913.325123] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[75913.326206] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[75916.428776] wlan0: authenticate with <MAC address removed> (try 1)
[75916.430362] wlan0: authenticated
[75916.448185] wlan0: associate with <MAC address removed> (try 1)
[75916.450698] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[75916.450708] wlan0: associated
[75916.453824] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[75917.691894] wlan0: IPv6 duplicate address fe80::7ee9:d3ff:fe35:1ae8 detected!


****************** done ******************

```

---

### Post by varunendra on 2014-02-08
Are you using TKIP with WPA2?? From the result it seems so -
> **Nathal said:**
> ```

  Wireless Access Points (* = current AP)
....
    ***HG655D-339CB3**:  Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 43 WPA2
....
....
wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"HG655D-339CB3"
....
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : **[COLOR="#FF0000"]TKIP[/COLOR]**
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK

```

Please change the encryption in the router to WPA2-AES(CCMP), no TKIP anywhere. Change it > Save it > Reboot both the router and the laptop.

Let us know if it helps. If not, we'll try the proprietary driver from [s]Realtek's[/s] Ralink's official website. The problem with that one is that it will only work with your current kernel (maybe a couple later ones too, but not the latest ones).

**EDIT:**
While you are at the router for changing the encryption, also try changing the channel to **1** or **11**, as they usually work better with Linux drivers. Currently it is set at channel 6.

---

### Post by Nathal on 2014-02-09
Hello yesterday someone give me the advise to install this 
wget [http://www.laptopke.be/files/rt5390sta_2.5.0.3_all.deb](http://www.laptopke.be/files/rt5390sta_2.5.0.3_all.deb)

My laptop build in wifi can not start anymore because that 'driver' rt5390 (Terrible advise from a Ubuntu Dutch forum) Now i have a fresh install
of Ubuntu and because the instable connection, updates are terrible to install (Many corrupt packages)My Xbox360 has a
perfect connection. I have done everything you say, and if y change to channel (router) 1 or 11 its even not possible to connect.
Channel 1 not more then 50KB download same whit 11, something is terrible wrong, because i have reach 8MB of download capacity. And now not more then 200KB
Its make me insane :(

---

### Post by varunendra on 2014-02-09
Make sure the encryption in the router is pure WPA2-AES, and not TKIP anywhere. Then in Ubuntu, try the temporary parameter, it won't hurt if couldn't help -
```
sudo modprobe -rv rt2800pci
sudo modprobe -v rt2800pci nohwcrypt=Y
```

If these don't help, we have only a few options left. The driver that you tried seems to be the same version that we can get from Ralink's website, only precompiled/packaged as a .deb binary. The one we'd download will have to be compiled manually and whether it'll succeed or not depends upon the kernel version you are using.

We can also try a newer version of the open source driver if you are still using an older kernel.

I think run the wireless_script again and post back its fresh report, so we know what are the options we have.

---

### Post by Nathal on 2014-02-09
Hello

It seems after i have installed (Ubuntu 64 bit) and all updates the slow connection is gone. Have installed XFCE Xubuntu desktop and for now it seems its works fine.

But im afraid this problem will come back soon, its not the first time.

For now Txh for the help, and if i get problems again i will post it.

---

### Post by varunendra on 2014-02-09
Sure! I'd be glad to assist where I can. But I'm hopeful that the latest drivers shouldn't trouble you again. And XFCE is a good choice. :)

---

### Post by Nathal on 2014-02-11
All (Wifi) problems are 100% solved, i like the support here and have more questions about 'other' things.

Thx again and i mark this thread as solved.

---

