---
title: "Atheros AR9285"
date: 2013-10-02
forum: Networking &amp; Wireless
---

### Post by timbo3 on 2013-10-02
I found many posts on this but not a solution that works for me.

I installed Ubuntu 12.04 on my ASUS X52J via a USB-stick yesterday night. It previously had Windows 7. 
When I booted via the USB-stick to make the install the network connection worked as usual. But the installation failed and I had to do it over again to make Ubuntu work. But after Ubuntu was installed the first time with a failed Boot setting (it didn't boot) when I tried to install again it never was able to connect to the network. It could see the network but the authentisation failed. 

So now Ubuntu is working and I can see the network which works on my other laptop with Ubuntu. But I cannot connect to it. It should work since I have the same version of Ubuntu on my other laptop and it is connecting to the network as usual.

Here is some info:

```
$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 48:5d:60:98:5c:2e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-23-generic-pae firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d2a00000-d2a0ffff
  *-network
       description: Ethernet interface
       product: JMC250 PCI Express Gigabit Ethernet Controller
       vendor: JMicron Technology Corp.
       physical id: 0.5
       bus info: pci@0000:05:00.5
       logical name: eth0
       version: 03
       serial: bc:ae:c5:9e:ba:8d
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msix msi bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=jme driverversion=1.0.8 duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:50 memory:d0200000-d0203fff ioport:9100(size=128) ioport:9000(size=256)
```

---

### Post by varunendra on 2013-10-03
Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

---

### Post by timbo3 on 2013-10-03
```

*************** info trace ***************

***** uname -a *****

Linux kjersti-K52JU 3.2.0-54-generic-pae #82-Ubuntu SMP Tue Sep 10 20:29:22 UTC 2013 i686 i686 i386 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise

***** lspci *****

03:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: AzureWave AW-NE785 / AW-NE785H 802.11bgn Wireless Full or Half-size Mini PCIe Card [1a3b:1089]
    Kernel driver in use: ath9k
--
05:00.5 Ethernet controller [0200]: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller [197b:0250] (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1905]
    Kernel driver in use: jme

***** lsusb *****

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 004: ID 0b05:1788 ASUSTek Computer, Inc. 
Bus 001 Device 005: ID 13d3:5130 IMC Networks 
Bus 002 Device 003: ID 1241:1177 Belkin F8E842-DL Mouse

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

***** rfkill *****

0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** lsmod *****

ath9k                 116025  0 
mac80211              449740  1 ath9k
ath9k_common           13781  1 ath9k
ath9k_hw              375997  2 ath9k,ath9k_common
ath                    19187  3 ath9k,ath9k_common,ath9k_hw
cfg80211              178892  3 ath9k,mac80211,ath
compat                 13247  9 bnep,rfcomm,ath9k,mac80211,ath9k_common,ath9k_hw,cfg80211,btusb,bluetooth

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            jme
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         10.0.0.66
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.138

    DNS:             193.212.1.10
    DNS:             130.67.60.68
    DNS:             10.0.0.138


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    ER4:             Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 65 WPA2



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


***** resolv.conf *****

nameserver 127.0.0.1
search lan

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

filename:       /lib/modules/3.2.0-54-generic-pae/updates/cw-3.4/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     4786F8E5E3BD987861D0590
alias:          platform:ar934x_wmac
alias:          platform:ar933x_wmac
alias:          platform:ath9k
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
depends:        ath9k_hw,ath9k_common,mac80211,ath,cfg80211,compat
vermagic:       3.2.0-54-generic-pae SMP mod_unload modversions 686 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)

filename:       /lib/modules/3.2.0-54-generic-pae/updates/cw-3.4/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     C96A18C18D58C8FEB170600
depends:        compat,ath,ath9k_hw
vermagic:       3.2.0-54-generic-pae SMP mod_unload modversions 686 

filename:       /lib/modules/3.2.0-54-generic-pae/updates/cw-3.4/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     C3BD85970434D20D41124A0
depends:        ath,compat
vermagic:       3.2.0-54-generic-pae SMP mod_unload modversions 686 
parm:           force_new_ani:Force new ANI for AR5008, AR9001, AR9002 (int)

filename:       /lib/modules/3.2.0-54-generic-pae/updates/cw-3.4/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     5E74C72DD65871010555B24
depends:        cfg80211
vermagic:       3.2.0-54-generic-pae SMP mod_unload modversions 686 


***** udev rules *****

# PCI device 0x197b:/sys/devices/pci0000:00/0000:00:1c.5/0000:05:00.5 (jme)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[  149.565457] wlan0: authenticate with <MAC address removed>
[  149.578208] wlan0: send auth to <MAC address removed> (try 1/3)
[  149.580210] wlan0: authenticated
[  149.587021] wlan0: associating with AP with corrupt beacon
[  149.588863] wlan0: associate with <MAC address removed> (try 1/3)
[  149.592844] wlan0: RX AssocResp from <MAC address removed> (capab=0xc11 status=0 aid=3)
[  149.592854] wlan0: associated
[  149.613658] ath: regdomain 0x8242 updated by CountryIE
[  149.613662] ath: EEPROM regdomain: 0x8242
[  149.613665] ath: EEPROM indicates we should expect a country code
[  149.613670] ath: doing EEPROM country->regdmn map search
[  149.613674] ath: country maps to regdmn code: 0x37
[  149.613678] ath: Country alpha2 being used: NO
[  149.613681] ath: Regpair used: 0x37
[  156.308138] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  157.409350] wlan0: authenticate with <MAC address removed>
[  157.421686] wlan0: send auth to <MAC address removed> (try 1/3)
[  157.423763] wlan0: authenticated
[  157.430574] wlan0: associating with AP with corrupt beacon
[  157.432478] wlan0: associate with <MAC address removed> (try 1/3)
[  157.436651] wlan0: RX AssocResp from <MAC address removed> (capab=0xc11 status=0 aid=3)
[  157.436661] wlan0: associated
[  157.452586] ath: regdomain 0x8242 updated by CountryIE
[  157.452588] ath: EEPROM regdomain: 0x8242
[  157.452589] ath: EEPROM indicates we should expect a country code
[  157.452591] ath: doing EEPROM country->regdmn map search
[  157.452592] ath: country maps to regdmn code: 0x37
[  157.452594] ath: Country alpha2 being used: NO
[  157.452595] ath: Regpair used: 0x37
[  164.303814] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  165.444602] wlan0: authenticate with <MAC address removed>
[  165.457336] wlan0: send auth to <MAC address removed> (try 1/3)
[  165.459446] wlan0: authenticated
[  165.466208] wlan0: associating with AP with corrupt beacon
[  165.468039] wlan0: associate with <MAC address removed> (try 1/3)
[  165.472111] wlan0: RX AssocResp from <MAC address removed> (capab=0xc11 status=0 aid=3)
[  165.472119] wlan0: associated
[  165.488845] ath: regdomain 0x8242 updated by CountryIE
[  165.488849] ath: EEPROM regdomain: 0x8242
[  165.488852] ath: EEPROM indicates we should expect a country code
[  165.488857] ath: doing EEPROM country->regdmn map search
[  165.488861] ath: country maps to regdmn code: 0x37
[  165.488865] ath: Country alpha2 being used: NO
[  165.488868] ath: Regpair used: 0x37
[  172.099668] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  173.212249] wlan0: authenticate with <MAC address removed>
[  173.225020] wlan0: send auth to <MAC address removed> (try 1/3)
[  173.227061] wlan0: authenticated
[  173.234038] wlan0: associating with AP with corrupt beacon
[  173.235811] wlan0: associate with <MAC address removed> (try 1/3)
[  173.239712] wlan0: RX AssocResp from <MAC address removed> (capab=0xc11 status=0 aid=3)
[  173.239722] wlan0: associated
[  173.250375] ath: regdomain 0x8242 updated by CountryIE
[  173.250377] ath: EEPROM regdomain: 0x8242
[  173.250378] ath: EEPROM indicates we should expect a country code
[  173.250380] ath: doing EEPROM country->regdmn map search
[  173.250381] ath: country maps to regdmn code: 0x37
[  173.250383] ath: Country alpha2 being used: NO
[  173.250384] ath: Regpair used: 0x37
[  179.675561] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  180.808207] wlan0: authenticate with <MAC address removed>
[  180.820722] wlan0: send auth to <MAC address removed> (try 1/3)
[  180.822622] wlan0: authenticated
[  180.829514] wlan0: associating with AP with corrupt beacon
[  180.831378] wlan0: associate with <MAC address removed> (try 1/3)
[  180.835384] wlan0: RX AssocResp from <MAC address removed> (capab=0xc11 status=0 aid=3)
[  180.835392] wlan0: associated
[  180.848223] ath: regdomain 0x8242 updated by CountryIE
[  180.848227] ath: EEPROM regdomain: 0x8242
[  180.848229] ath: EEPROM indicates we should expect a country code
[  180.848233] ath: doing EEPROM country->regdmn map search
[  180.848236] ath: country maps to regdmn code: 0x37
[  180.848239] ath: Country alpha2 being used: NO
[  180.848241] ath: Regpair used: 0x37
[  181.028783] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  463.430742] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  466.242934] wlan0: authenticate with <MAC address removed>
[  466.253023] wlan0: send auth to <MAC address removed> (try 1/3)
[  466.255055] wlan0: authenticated
[  466.261802] wlan0: associating with AP with corrupt beacon
[  466.263781] wlan0: associate with <MAC address removed> (try 1/3)
[  466.267819] wlan0: RX AssocResp from <MAC address removed> (capab=0xc11 status=0 aid=3)
[  466.267829] wlan0: associated
[  466.274629] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  466.282985] ath: regdomain 0x8242 updated by CountryIE
[  466.282989] ath: EEPROM regdomain: 0x8242
[  466.282992] ath: EEPROM indicates we should expect a country code
[  466.282997] ath: doing EEPROM country->regdmn map search
[  466.283001] ath: country maps to regdmn code: 0x37
[  466.283005] ath: Country alpha2 being used: NO
[  466.283008] ath: Regpair used: 0x37
[  473.138857] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  474.279667] wlan0: authenticate with <MAC address removed>
[  474.296399] wlan0: send auth to <MAC address removed> (try 1/3)
[  474.298317] wlan0: authenticated
[  474.305001] wlan0: associating with AP with corrupt beacon
[  474.307318] wlan0: associate with <MAC address removed> (try 1/3)
[  474.311272] wlan0: RX AssocResp from <MAC address removed> (capab=0xc11 status=0 aid=3)
[  474.311277] wlan0: associated
[  474.322797] ath: regdomain 0x8242 updated by CountryIE
[  474.322798] ath: EEPROM regdomain: 0x8242
[  474.322800] ath: EEPROM indicates we should expect a country code
[  474.322801] ath: doing EEPROM country->regdmn map search
[  474.322803] ath: country maps to regdmn code: 0x37
[  474.322804] ath: Country alpha2 being used: NO
[  474.322806] ath: Regpair used: 0x37
[  481.083696] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  482.235259] wlan0: authenticate with <MAC address removed>
[  482.248044] wlan0: send auth to <MAC address removed> (try 1/3)
[  482.249942] wlan0: authenticated
[  482.256853] wlan0: associating with AP with corrupt beacon
[  482.258806] wlan0: associate with <MAC address removed> (try 1/3)
[  482.262830] wlan0: RX AssocResp from <MAC address removed> (capab=0xc11 status=0 aid=3)
[  482.262834] wlan0: associated
[  482.273066] ath: regdomain 0x8242 updated by CountryIE
[  482.273068] ath: EEPROM regdomain: 0x8242
[  482.273069] ath: EEPROM indicates we should expect a country code
[  482.273071] ath: doing EEPROM country->regdmn map search
[  482.273073] ath: country maps to regdmn code: 0x37
[  482.273074] ath: Country alpha2 being used: NO
[  482.273075] ath: Regpair used: 0x37
[  484.104976] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  513.413783] wlan0: authenticate with <MAC address removed>
[  513.426720] wlan0: send auth to <MAC address removed> (try 1/3)
[  513.430323] wlan0: authenticated
[  513.437016] wlan0: associating with AP with corrupt beacon
[  513.437370] wlan0: associate with <MAC address removed> (try 1/3)
[  513.441366] wlan0: RX AssocResp from <MAC address removed> (capab=0xc11 status=0 aid=3)
[  513.441373] wlan0: associated
[  513.456694] ath: regdomain 0x8242 updated by CountryIE
[  513.456700] ath: EEPROM regdomain: 0x8242
[  513.456705] ath: EEPROM indicates we should expect a country code
[  513.456711] ath: doing EEPROM country->regdmn map search
[  513.456716] ath: country maps to regdmn code: 0x37
[  513.456722] ath: Country alpha2 being used: NO
[  513.456726] ath: Regpair used: 0x37
[  520.072733] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  521.181614] wlan0: authenticate with <MAC address removed>
[  521.194531] wlan0: send auth to <MAC address removed> (try 1/3)
[  521.196527] wlan0: authenticated
[  521.203291] wlan0: associating with AP with corrupt beacon
[  521.205106] wlan0: associate with <MAC address removed> (try 1/3)
[  521.209661] wlan0: RX AssocResp from <MAC address removed> (capab=0xc11 status=0 aid=3)
[  521.209669] wlan0: associated
[  521.224851] ath: regdomain 0x8242 updated by CountryIE
[  521.224855] ath: EEPROM regdomain: 0x8242
[  521.224858] ath: EEPROM indicates we should expect a country code
[  521.224863] ath: doing EEPROM country->regdmn map search
[  521.224867] ath: country maps to regdmn code: 0x37
[  521.224871] ath: Country alpha2 being used: NO
[  521.224874] ath: Regpair used: 0x37
[  527.958509] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  529.101185] wlan0: authenticate with <MAC address removed>
[  529.114033] wlan0: send auth to <MAC address removed> (try 1/3)
[  529.115975] wlan0: authenticated
[  529.122755] wlan0: associating with AP with corrupt beacon
[  529.124653] wlan0: associate with <MAC address removed> (try 1/3)
[  529.128658] wlan0: RX AssocResp from <MAC address removed> (capab=0xc11 status=0 aid=3)
[  529.128664] wlan0: associated
[  529.144014] ath: regdomain 0x8242 updated by CountryIE
[  529.144018] ath: EEPROM regdomain: 0x8242
[  529.144021] ath: EEPROM indicates we should expect a country code
[  529.144026] ath: doing EEPROM country->regdmn map search
[  529.144030] ath: country maps to regdmn code: 0x37
[  529.144034] ath: Country alpha2 being used: NO
[  529.144037] ath: Regpair used: 0x37
[  535.834284] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  536.952939] wlan0: authenticate with <MAC address removed>
[  536.965450] wlan0: send auth to <MAC address removed> (try 1/3)
[  536.968687] wlan0: authenticated
[  536.975473] wlan0: associating with AP with corrupt beacon
[  536.976228] wlan0: associate with <MAC address removed> (try 1/3)
[  536.980316] wlan0: RX AssocResp from <MAC address removed> (capab=0xc11 status=0 aid=3)
[  536.980324] wlan0: associated
[  536.995608] ath: regdomain 0x8242 updated by CountryIE
[  536.995612] ath: EEPROM regdomain: 0x8242
[  536.995615] ath: EEPROM indicates we should expect a country code
[  536.995619] ath: doing EEPROM country->regdmn map search
[  536.995624] ath: country maps to regdmn code: 0x37
[  536.995627] ath: Country alpha2 being used: NO
[  536.995631] ath: Regpair used: 0x37
[  543.310244] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  544.420871] wlan0: authenticate with <MAC address removed>
[  544.433433] wlan0: send auth to <MAC address removed> (try 1/3)
[  544.435547] wlan0: authenticated
[  544.442297] wlan0: associating with AP with corrupt beacon
[  544.444075] wlan0: associate with <MAC address removed> (try 1/3)
[  544.448131] wlan0: RX AssocResp from <MAC address removed> (capab=0xc11 status=0 aid=3)
[  544.448139] wlan0: associated
[  544.465198] ath: regdomain 0x8242 updated by CountryIE
[  544.465204] ath: EEPROM regdomain: 0x8242
[  544.465209] ath: EEPROM indicates we should expect a country code
[  544.465215] ath: doing EEPROM country->regdmn map search
[  544.465221] ath: country maps to regdmn code: 0x37
[  544.465226] ath: Country alpha2 being used: NO
[  544.465231] ath: Regpair used: 0x37
[  551.086127] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  552.212417] wlan0: authenticate with <MAC address removed>
[  552.225514] wlan0: send auth to <MAC address removed> (try 1/3)
[  552.227450] wlan0: authenticated
[  552.234225] wlan0: associating with AP with corrupt beacon
[  552.235708] wlan0: associate with <MAC address removed> (try 1/3)
[  552.239744] wlan0: RX AssocResp from <MAC address removed> (capab=0xc11 status=0 aid=3)
[  552.239752] wlan0: associated
[  552.254208] ath: regdomain 0x8242 updated by CountryIE
[  552.254212] ath: EEPROM regdomain: 0x8242
[  552.254215] ath: EEPROM indicates we should expect a country code
[  552.254220] ath: doing EEPROM country->regdmn map search
[  552.254224] ath: country maps to regdmn code: 0x37
[  552.254228] ath: Country alpha2 being used: NO
[  552.254231] ath: Regpair used: 0x37
[  559.091751] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  560.211981] wlan0: authenticate with <MAC address removed>
[  560.224514] wlan0: send auth to <MAC address removed> (try 1/3)
[  560.226573] wlan0: authenticated
[  560.233459] wlan0: associating with AP with corrupt beacon
[  560.239173] wlan0: associate with <MAC address removed> (try 1/3)
[  560.243179] wlan0: RX AssocResp from <MAC address removed> (capab=0xc11 status=0 aid=3)
[  560.243192] wlan0: associated
[  560.258331] ath: regdomain 0x8242 updated by CountryIE
[  560.258335] ath: EEPROM regdomain: 0x8242
[  560.258338] ath: EEPROM indicates we should expect a country code
[  560.258342] ath: doing EEPROM country->regdmn map search
[  560.258346] ath: country maps to regdmn code: 0x37
[  560.258350] ath: Country alpha2 being used: NO
[  560.258353] ath: Regpair used: 0x37
[  567.087457] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  568.199097] wlan0: authenticate with <MAC address removed>
[  568.211982] wlan0: send auth to <MAC address removed> (try 1/3)
[  568.214003] wlan0: authenticated
[  568.221772] wlan0: associating with AP with corrupt beacon
[  568.222718] wlan0: associate with <MAC address removed> (try 1/3)
[  568.226754] wlan0: RX AssocResp from <MAC address removed> (capab=0xc11 status=0 aid=3)
[  568.226759] wlan0: associated
[  568.237929] ath: regdomain 0x8242 updated by CountryIE
[  568.237930] ath: EEPROM regdomain: 0x8242
[  568.237931] ath: EEPROM indicates we should expect a country code
[  568.237933] ath: doing EEPROM country->regdmn map search
[  568.237935] ath: country maps to regdmn code: 0x37
[  568.237936] ath: Country alpha2 being used: NO
[  568.237937] ath: Regpair used: 0x37
[  572.881099] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  876.738703] wlan0: authenticate with <MAC address removed>
[  876.751561] wlan0: send auth to <MAC address removed> (try 1/3)
[  876.753544] wlan0: authenticated
[  876.760306] wlan0: associating with AP with corrupt beacon
[  876.762226] wlan0: associate with <MAC address removed> (try 1/3)
[  876.766274] wlan0: RX AssocResp from <MAC address removed> (capab=0xc11 status=0 aid=3)
[  876.766282] wlan0: associated
[  876.781402] ath: regdomain 0x8242 updated by CountryIE
[  876.781406] ath: EEPROM regdomain: 0x8242
[  876.781410] ath: EEPROM indicates we should expect a country code
[  876.781414] ath: doing EEPROM country->regdmn map search
[  876.781419] ath: country maps to regdmn code: 0x37
[  876.781423] ath: Country alpha2 being used: NO
[  876.781426] ath: Regpair used: 0x37
[  883.597399] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  884.734323] wlan0: authenticate with <MAC address removed>
[  884.747042] wlan0: send auth to <MAC address removed> (try 1/3)
[  884.749158] wlan0: authenticated
[  884.755982] wlan0: associating with AP with corrupt beacon
[  884.757727] wlan0: associate with <MAC address removed> (try 1/3)
[  884.761642] wlan0: RX AssocResp from <MAC address removed> (capab=0xc11 status=0 aid=3)
[  884.761677] wlan0: associated
[  884.778060] ath: regdomain 0x8242 updated by CountryIE
[  884.778065] ath: EEPROM regdomain: 0x8242
[  884.778070] ath: EEPROM indicates we should expect a country code
[  884.778076] ath: doing EEPROM country->regdmn map search
[  884.778082] ath: country maps to regdmn code: 0x37
[  884.778087] ath: Country alpha2 being used: NO
[  884.778092] ath: Regpair used: 0x37
[  891.383173] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  892.489985] wlan0: authenticate with <MAC address removed>
[  892.502846] wlan0: send auth to <MAC address removed> (try 1/3)
[  892.504918] wlan0: authenticated
[  892.511824] wlan0: associating with AP with corrupt beacon
[  892.513344] wlan0: associate with <MAC address removed> (try 1/3)
[  892.517389] wlan0: RX AssocResp from <MAC address removed> (capab=0xc11 status=0 aid=3)
[  892.517397] wlan0: associated
[  892.529513] ath: regdomain 0x8242 updated by CountryIE
[  892.529515] ath: EEPROM regdomain: 0x8242
[  892.529517] ath: EEPROM indicates we should expect a country code
[  892.529519] ath: doing EEPROM country->regdmn map search
[  892.529520] ath: country maps to regdmn code: 0x37
[  892.529522] ath: Country alpha2 being used: NO
[  892.529524] ath: Regpair used: 0x37
[  898.909125] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  900.017770] wlan0: authenticate with <MAC address removed>
[  900.030514] wlan0: send auth to <MAC address removed> (try 1/3)
[  900.034362] wlan0: authenticated
[  900.041149] wlan0: associating with AP with corrupt beacon
[  900.045144] wlan0: associate with <MAC address removed> (try 1/3)
[  900.049169] wlan0: RX AssocResp from <MAC address removed> (capab=0xc11 status=0 aid=3)
[  900.049178] wlan0: associated
[  900.069841] ath: regdomain 0x8242 updated by CountryIE
[  900.069843] ath: EEPROM regdomain: 0x8242
[  900.069844] ath: EEPROM indicates we should expect a country code
[  900.069846] ath: doing EEPROM country->regdmn map search
[  900.069848] ath: country maps to regdmn code: 0x37
[  900.069849] ath: Country alpha2 being used: NO
[  900.069850] ath: Regpair used: 0x37
[  906.904820] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  908.065250] wlan0: authenticate with <MAC address removed>
[  908.078070] wlan0: send auth to <MAC address removed> (try 1/3)
[  908.080048] wlan0: authenticated
[  908.086774] wlan0: associating with AP with corrupt beacon
[  908.088635] wlan0: associate with <MAC address removed> (try 1/3)
[  908.092512] wlan0: RX AssocResp from <MAC address removed> (capab=0xc11 status=0 aid=3)
[  908.092517] wlan0: associated
[  908.103880] ath: regdomain 0x8242 updated by CountryIE
[  908.103882] ath: EEPROM regdomain: 0x8242
[  908.103883] ath: EEPROM indicates we should expect a country code
[  908.103885] ath: doing EEPROM country->regdmn map search
[  908.103887] ath: country maps to regdmn code: 0x37
[  908.103888] ath: Country alpha2 being used: NO
[  908.103889] ath: Regpair used: 0x37
[  914.900526] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  916.016835] wlan0: authenticate with <MAC address removed>
[  916.029600] wlan0: send auth to <MAC address removed> (try 1/3)
[  916.031642] wlan0: authenticated
[  916.038540] wlan0: associating with AP with corrupt beacon
[  916.040329] wlan0: associate with <MAC address removed> (try 1/3)
[  916.044324] wlan0: RX AssocResp from <MAC address removed> (capab=0xc11 status=0 aid=3)
[  916.044328] wlan0: associated
[  916.057320] ath: regdomain 0x8242 updated by CountryIE
[  916.057324] ath: EEPROM regdomain: 0x8242
[  916.057326] ath: EEPROM indicates we should expect a country code
[  916.057330] ath: doing EEPROM country->regdmn map search
[  916.057334] ath: country maps to regdmn code: 0x37
[  916.057337] ath: Country alpha2 being used: NO
[  916.057340] ath: Regpair used: 0x37
[  922.896251] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  924.060326] wlan0: authenticate with <MAC address removed>
[  924.073152] wlan0: send auth to <MAC address removed> (try 1/3)
[  924.075186] wlan0: authenticated
[  924.082072] wlan0: associating with AP with corrupt beacon
[  924.083698] wlan0: associate with <MAC address removed> (try 1/3)
[  924.087725] wlan0: RX AssocResp from <MAC address removed> (capab=0xc11 status=0 aid=3)
[  924.087735] wlan0: associated
[  924.100469] ath: regdomain 0x8242 updated by CountryIE
[  924.100472] ath: EEPROM regdomain: 0x8242
[  924.100473] ath: EEPROM indicates we should expect a country code
[  924.100476] ath: doing EEPROM country->regdmn map search
[  924.100478] ath: country maps to regdmn code: 0x37
[  924.100480] ath: Country alpha2 being used: NO
[  924.100482] ath: Regpair used: 0x37
[  930.892575] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  931.991887] wlan0: authenticate with <MAC address removed>
[  932.004687] wlan0: send auth to <MAC address removed> (try 1/3)
[  932.006697] wlan0: authenticated
[  932.013517] wlan0: associating with AP with corrupt beacon
[  932.019269] wlan0: associate with <MAC address removed> (try 1/3)
[  932.023207] wlan0: RX AssocResp from <MAC address removed> (capab=0xc11 status=0 aid=3)
[  932.023212] wlan0: associated
[  932.034292] ath: regdomain 0x8242 updated by CountryIE
[  932.034293] ath: EEPROM regdomain: 0x8242
[  932.034294] ath: EEPROM indicates we should expect a country code
[  932.034296] ath: doing EEPROM country->regdmn map search
[  932.034298] ath: country maps to regdmn code: 0x37
[  932.034299] ath: Country alpha2 being used: NO
[  932.034300] ath: Regpair used: 0x37
[  935.675211] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1239.535746] wlan0: authenticate with <MAC address removed>
[ 1239.548579] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1239.550537] wlan0: authenticated
[ 1239.557297] wlan0: associating with AP with corrupt beacon
[ 1239.559364] wlan0: associate with <MAC address removed> (try 1/3)
[ 1239.564721] wlan0: RX AssocResp from <MAC address removed> (capab=0xc11 status=0 aid=3)
[ 1239.564726] wlan0: associated
[ 1239.579666] ath: regdomain 0x8242 updated by CountryIE
[ 1239.579670] ath: EEPROM regdomain: 0x8242
[ 1239.579673] ath: EEPROM indicates we should expect a country code
[ 1239.579678] ath: doing EEPROM country->regdmn map search
[ 1239.579682] ath: country maps to regdmn code: 0x37
[ 1239.579686] ath: Country alpha2 being used: NO
[ 1239.579689] ath: Regpair used: 0x37
[ 1246.722821] wlan0: deauthenticated from <MAC address removed> (Reason: 15)

****************** done ******************

```

---

### Post by varunendra on 2013-10-04
> **timbo3 said:**
> ```

[ 1239.579666] ath: regdomain 0x8242 updated by CountryIE
[ 1239.579670] ath: EEPROM regdomain: 0x8242
[ 1239.579673] ath: EEPROM indicates we should expect a country code
[ 1239.579678] ath: doing EEPROM country->regdmn map search
[ 1239.579682] ath: country maps to regdmn code: 0x37
[ 1239.579686] ath: Country alpha2 being used: NO
[ 1239.579689] ath: Regpair used: 0x37
[ 1246.722821] wlan0: deauthenticated from <MAC address removed> (Reason: 15)

```

I don't remember having seen this many regdomain messages (probably errors) before.

Are you in Norway?

Please post back the output of -
```
dmesg | egrep -i '80211|ath|wlan|network'
```

---

### Post by timbo3 on 2013-10-05
I'm quite new to Ubuntu and I'm also quite desperate (because it's not my laptop) so I have tried a lot of solutions found in other posts about this very same problem with Atheros AR9285. So maybe these errors are caused by me changing to many things in the system..

I was definite that the ndiswrapper solution with an old windows 7 driver would work but it did not. And after tweaking to many things I can't even enable wireless anymore. So what I'm doing is reinstalling Ubuntu and then I'll run your script again and also post the output of 
dmesg | egrep -i '80211|ath|wlan|network.

be back to you in a while

---

### Post by timbo3 on 2013-10-27
I ended up reinstalling Ubuntu 12.10 and this seemed to do the trick. I had actually tried to do this before with out any results. But this time I had an internet connection via cable (as opposed to the othertime where I had no conection at all). This probably made the installation a bit more comprehensive. Anyway, no more problems and I'm happy again ^^

---

### Post by varunendra on 2013-10-27
Not the best solution, but glad it made you happy. Let's hope the next LTS, or even Saucy after a few more updates, can make you happier. :)

---

