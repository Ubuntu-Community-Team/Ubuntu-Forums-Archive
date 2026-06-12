---
title: "Atheros ar9285 random disconnections Ubuntu 13.10 (and previous)"
date: 2014-06-14
forum: Networking &amp; Wireless
---

### Post by lorecupe on 2014-06-14
Hello everyone, this is my first post on this forum. I come to you in a  time of great need for a solution to the problem i've been afflicted for  so long: my wireless connection (sometimes immediately after boot,  sometimes after a while) drops, and the only solution to have it back is  to reboot. When the disconnection happens, i can see the other wifi  networks on the network manager, but the one i was connected too is gone  and i can't connect to the others. The problem is independent from the  single network, because it happens at my parents' home, at my work and  at my own home, all with different networks. I have this problem since i  think ubuntu 10.10 or so, i tried sometimes to fix it with the various  solutions found here and there, such as the nohwcrypt one, the  blacklist.conf one, etc. but none worked. A search for a solution here  (searching for ar9285 in networking and wireless) has made me go back to  2-4 years ago with no success for my issue. I think i've said enough,  time to put the result of the script here (when the wireless was already  disconnected):

```

########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy

##### kernel #####

Linux lorenzo-1011PX 3.11.6-031106-generic #201310181453 SMP Fri Oct 18 19:02:28 UTC 2013 i686 i686 i686 GNU/Linux

##### lspci #####

01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8468]
    Kernel driver in use: atl1c
02:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: AzureWave AW-NE785 / AW-NE785H 802.11bgn Wireless Full or Half-size Mini PCIe Card [1a3b:1089]
    Kernel driver in use: ath9k

##### lsusb #####

Bus 001 Device 002: ID 13d3:5711 IMC Networks 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA Card Info #####

##### rfkill #####

1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### iw reg get #####

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### interfaces #####

auto lo
iface lo inet loopback

##### iwconfig #####

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #####

Tabella di routing IP del kernel
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #####

nameserver 208.67.222.222
nameserver 208.67.220.220
nameserver 192.168.1.1

##### nm-tool #####

NetworkManager Tool

State: disconnected

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
    D-Link:          Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WEP

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

wlan0     No scan results

##### iwlist channel #####

wlan0     14 channels in total; available frequencies :
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
          Channel 14 : 2.484 GHz

##### lsmod #####

ath9k                 141839  0 
ath9k_common           13619  1 ath9k
ath9k_hw              437356  2 ath9k_common,ath9k
ath                    19435  3 ath9k_common,ath9k,ath9k_hw
mac80211              534734  1 ath9k
cfg80211              415946  3 ath,ath9k,mac80211

##### modinfo #####

filename:       /lib/modules/3.11.6-031106-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
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
vermagic:       3.11.6-031106-generic SMP mod_unload modversions 686 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           enable_diversity:Enable Antenna diversity for AR9565 (int)

filename:       /lib/modules/3.11.6-031106-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     2DB88A2876852DC1D8C5A1D
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.11.6-031106-generic SMP mod_unload modversions 686 

filename:       /lib/modules/3.11.6-031106-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     57A1E15BE088B8A5C4BE74F
depends:        ath
intree:         Y
vermagic:       3.11.6-031106-generic SMP mod_unload modversions 686 

filename:       /lib/modules/3.11.6-031106-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     A890CDBC88E6EF28CD751DD
depends:        cfg80211
intree:         Y
vermagic:       3.11.6-031106-generic SMP mod_unload modversions 686 

##### modules #####

lp

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
blacklist acer-wmi

##### udev rules #####

# PCI device 0x1969:0x2062 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:0x002b (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[   15.425235] ath: phy0: ASPM enabled: 0x42
[   15.425244] ath: EEPROM regdomain: 0x60
[   15.425246] ath: EEPROM indicates we should expect a direct regpair map
[   15.425251] ath: Country alpha2 being used: 00
[   15.425253] ath: Regpair used: 0x60
[   15.792664] psmouse serio1: elantech: assuming hardware version 2 (with firmware version 0x140100)
[   24.934463] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   27.516267] wlan0: authenticate with <MAC address removed>
[   27.541020] wlan0: send auth to <MAC address removed> (try 1/3)
[   27.546762] wlan0: authenticated
[   27.548097] wlan0: associate with <MAC address removed> (try 1/3)
[   27.553851] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=8)
[   27.554001] wlan0: associated
[   27.554077] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   31.448167] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   31.605207] ath9k: ath9k: Driver unloaded
[   32.099944] ath: phy0: ASPM enabled: 0x42
[   32.099955] ath: EEPROM regdomain: 0x60
[   32.099960] ath: EEPROM indicates we should expect a direct regpair map
[   32.099966] ath: Country alpha2 being used: 00
[   32.099970] ath: Regpair used: 0x60
[   32.121375] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   32.324652] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   34.361674] wlan0: authenticate with <MAC address removed>
[   34.384391] wlan0: send auth to <MAC address removed> (try 1/3)
[   34.386422] wlan0: authenticated
[   34.388160] wlan0: associate with <MAC address removed> (try 1/3)
[   34.391870] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=8)
[   34.391988] wlan0: associated
[   34.392068] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2324.439828] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2324.453522] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2324.453542] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2324.572637] ath: phy0: Chip reset failed
[ 2324.572653] ath: phy0: Unable to reset channel, reset status -22
[ 2325.046245] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2325.059722] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2325.059741] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2325.178273] ath: phy0: Chip reset failed
[ 2325.178291] ath: phy0: Unable to reset channel, reset status -22
[ 2325.247069] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2325.260633] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2325.260652] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2325.379983] ath: phy0: Chip reset failed
[ 2325.379997] ath: phy0: Unable to reset channel, reset status -22
[ 2325.459197] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2325.472697] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2325.472710] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2325.590734] ath: phy0: Chip reset failed
[ 2325.590742] ath: phy0: Unable to reset channel, reset status -22
[ 2325.590779] ath: phy0: Unable to set channel
[ 2325.592012] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
[ 2325.592012] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2325.740027] ath: phy0: Failed to wakeup in 500us
[ 2325.753331] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
[ 2325.753331] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2325.884253] ath: phy0: Failed to wakeup in 500us
[ 2325.960943] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2325.974755] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2325.974789] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2326.094404] ath: phy0: Chip reset failed
[ 2326.094416] ath: phy0: Unable to reset channel, reset status -22
[ 2326.094473] ath: phy0: Unable to set channel
[ 2326.163917] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2326.177501] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2326.177520] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2326.296445] ath: phy0: Chip reset failed
[ 2326.296458] ath: phy0: Unable to reset channel, reset status -22
[ 2326.364971] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2326.378419] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2326.378432] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2326.496477] ath: phy0: Chip reset failed
[ 2326.496484] ath: phy0: Unable to reset channel, reset status -22
[ 2326.496516] ath: phy0: Unable to set channel
[ 2326.564505] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2326.577979] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2326.577991] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2326.695995] ath: phy0: Chip reset failed
[ 2326.696002] ath: phy0: Unable to reset channel, reset status -22
[ 2326.696123] ath: phy0: Unable to set channel
[ 2326.764259] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2326.777745] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2326.777758] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2326.895739] ath: phy0: Chip reset failed
[ 2326.895747] ath: phy0: Unable to reset channel, reset status -22
[ 2326.895779] ath: phy0: Unable to set channel
[ 2326.964056] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2326.977508] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2326.977521] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2327.095525] ath: phy0: Chip reset failed
[ 2327.095536] ath: phy0: Unable to reset channel, reset status -22
[ 2327.095568] ath: phy0: Unable to set channel
[ 2327.163884] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2327.177351] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2327.177365] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2327.295398] ath: phy0: Chip reset failed
[ 2327.295406] ath: phy0: Unable to reset channel, reset status -22
[ 2327.295438] ath: phy0: Unable to set channel
[ 2327.363653] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2327.377189] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2327.377203] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2327.495359] ath: phy0: Chip reset failed
[ 2327.495367] ath: phy0: Unable to reset channel, reset status -22
[ 2327.495396] ath: phy0: Unable to set channel
[ 2327.563826] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2327.577301] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2327.577315] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2327.695421] ath: phy0: Chip reset failed
[ 2327.695429] ath: phy0: Unable to reset channel, reset status -22
[ 2327.695461] ath: phy0: Unable to set channel
[ 2327.763580] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2327.777040] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2327.777053] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2327.895034] ath: phy0: Chip reset failed
[ 2327.895042] ath: phy0: Unable to reset channel, reset status -22
[ 2327.895084] ath: phy0: Unable to set channel
[ 2327.963003] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2327.976515] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2327.976529] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2328.094494] ath: phy0: Chip reset failed
[ 2328.094502] ath: phy0: Unable to reset channel, reset status -22
[ 2328.094529] ath: phy0: Unable to set channel
[ 2328.162724] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2328.176207] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2328.176221] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2328.294223] ath: phy0: Chip reset failed
[ 2328.294230] ath: phy0: Unable to reset channel, reset status -22
[ 2328.294253] ath: phy0: Unable to set channel
[ 2328.363504] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2328.377106] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2328.377126] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2328.495886] ath: phy0: Chip reset failed
[ 2328.495900] ath: phy0: Unable to reset channel, reset status -22
[ 2328.495941] ath: phy0: Unable to set channel
[ 2328.565257] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2328.578806] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2328.578832] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2328.697722] ath: phy0: Chip reset failed
[ 2328.697738] ath: phy0: Unable to reset channel, reset status -22
[ 2328.697784] ath: phy0: Unable to set channel
[ 2328.765797] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2328.779302] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2328.779319] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2328.897330] ath: phy0: Chip reset failed
[ 2328.897343] ath: phy0: Unable to reset channel, reset status -22
[ 2328.897397] ath: phy0: Unable to set channel
[ 2328.965945] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2328.979562] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2328.979580] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2329.098533] ath: phy0: Chip reset failed
[ 2329.098546] ath: phy0: Unable to reset channel, reset status -22
[ 2329.098607] ath: phy0: Unable to set channel
[ 2329.167883] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2329.181405] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2329.181422] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2329.301702] ath: phy0: Chip reset failed
[ 2329.301719] ath: phy0: Unable to reset channel, reset status -22
[ 2329.301776] ath: phy0: Unable to set channel
[ 2329.304033] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
[ 2329.304033] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2332.992039] ath: phy0: Failed to wakeup in 500us
[ 2333.002832] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
[ 2333.002832] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2334.108083] ath: phy0: Failed to wakeup in 500us
[ 2334.185263] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2334.198855] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2334.198881] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2334.317550] ath: phy0: Chip reset failed
[ 2334.317562] ath: phy0: Unable to reset channel, reset status -22
[ 2334.317671] ath: phy0: Unable to set channel
[ 2334.387282] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2334.400918] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2334.400944] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2334.521291] ath: phy0: Chip reset failed
[ 2334.521307] ath: phy0: Unable to reset channel, reset status -22
[ 2334.591057] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2334.604727] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2334.604750] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2334.723785] ath: phy0: Chip reset failed
[ 2334.723798] ath: phy0: Unable to reset channel, reset status -22
[ 2334.723846] ath: phy0: Unable to set channel
[ 2334.792519] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2334.806010] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2334.806029] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2334.924373] ath: phy0: Chip reset failed
[ 2334.924390] ath: phy0: Unable to reset channel, reset status -22
[ 2334.924441] ath: phy0: Unable to set channel
[ 2334.992972] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2335.006468] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2335.006491] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2335.125208] ath: phy0: Chip reset failed
[ 2335.125221] ath: phy0: Unable to reset channel, reset status -22
[ 2335.125254] ath: phy0: Unable to set channel
[ 2335.193613] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2335.207248] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2335.207267] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2335.325642] ath: phy0: Chip reset failed
[ 2335.325655] ath: phy0: Unable to reset channel, reset status -22
[ 2335.325739] ath: phy0: Unable to set channel
[ 2335.394614] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2335.408299] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2335.408315] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2335.526977] ath: phy0: Chip reset failed
[ 2335.526988] ath: phy0: Unable to reset channel, reset status -22
[ 2335.527062] ath: phy0: Unable to set channel
[ 2335.595189] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2335.608726] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2335.608742] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2335.726750] ath: phy0: Chip reset failed
[ 2335.726761] ath: phy0: Unable to reset channel, reset status -22
[ 2335.726797] ath: phy0: Unable to set channel
[ 2335.795055] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2335.808558] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2335.808574] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2335.926581] ath: phy0: Chip reset failed
[ 2335.926592] ath: phy0: Unable to reset channel, reset status -22
[ 2335.926629] ath: phy0: Unable to set channel
[ 2335.994703] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2336.008163] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2336.008180] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2336.126084] ath: phy0: Chip reset failed
[ 2336.126095] ath: phy0: Unable to reset channel, reset status -22
[ 2336.126128] ath: phy0: Unable to set channel
[ 2336.194091] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2336.207590] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2336.207607] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2336.325475] ath: phy0: Chip reset failed
[ 2336.325484] ath: phy0: Unable to reset channel, reset status -22
[ 2336.325516] ath: phy0: Unable to set channel
[ 2336.393572] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2336.407023] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2336.407038] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2336.524899] ath: phy0: Chip reset failed
[ 2336.524909] ath: phy0: Unable to reset channel, reset status -22
[ 2336.524937] ath: phy0: Unable to set channel
[ 2336.593010] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2336.606460] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2336.606480] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2336.724398] ath: phy0: Chip reset failed
[ 2336.724407] ath: phy0: Unable to reset channel, reset status -22
[ 2336.724434] ath: phy0: Unable to set channel
[ 2336.792305] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2336.805807] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2336.805823] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2336.923698] ath: phy0: Chip reset failed
[ 2336.923708] ath: phy0: Unable to reset channel, reset status -22
[ 2336.923736] ath: phy0: Unable to set channel
[ 2336.991757] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2337.005306] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2337.005321] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2337.123305] ath: phy0: Chip reset failed
[ 2337.123316] ath: phy0: Unable to reset channel, reset status -22
[ 2337.123343] ath: phy0: Unable to set channel
[ 2337.191538] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2337.205024] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2337.205040] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2337.323128] ath: phy0: Chip reset failed
[ 2337.323140] ath: phy0: Unable to reset channel, reset status -22
[ 2337.323175] ath: phy0: Unable to set channel
[ 2337.391300] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2337.404812] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2337.404828] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2337.522731] ath: phy0: Chip reset failed
[ 2337.522741] ath: phy0: Unable to reset channel, reset status -22
[ 2337.522770] ath: phy0: Unable to set channel
[ 2337.524006] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
[ 2337.524006] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2338.000040] ath: phy0: Failed to wakeup in 500us
[ 2338.010837] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
[ 2338.010837] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2341.396116] ath: phy0: Failed to wakeup in 500us
[ 2341.410327] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
[ 2341.410327] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2341.539548] ath: phy0: Failed to wakeup in 500us
[ 2341.621409] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2341.635141] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2341.635161] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2341.754393] ath: phy0: Chip reset failed
[ 2341.754412] ath: phy0: Unable to reset channel, reset status -22
[ 2341.754498] ath: phy0: Unable to set channel
[ 2341.823466] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2341.837002] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2341.837018] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2341.955943] ath: phy0: Chip reset failed
[ 2341.955963] ath: phy0: Unable to reset channel, reset status -22
[ 2342.024914] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2342.038546] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2342.038577] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2342.157250] ath: phy0: Chip reset failed
[ 2342.157263] ath: phy0: Unable to reset channel, reset status -22
[ 2342.157309] ath: phy0: Unable to set channel
[ 2342.226019] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2342.239502] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2342.239518] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2342.357937] ath: phy0: Chip reset failed
[ 2342.357949] ath: phy0: Unable to reset channel, reset status -22
[ 2342.357984] ath: phy0: Unable to set channel
[ 2342.426834] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2342.440328] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2342.440344] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2342.559089] ath: phy0: Chip reset failed
[ 2342.559110] ath: phy0: Unable to reset channel, reset status -22
[ 2342.559171] ath: phy0: Unable to set channel
[ 2342.627391] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2342.641050] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2342.641074] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2342.759358] ath: phy0: Chip reset failed
[ 2342.759371] ath: phy0: Unable to reset channel, reset status -22
[ 2342.759419] ath: phy0: Unable to set channel
[ 2342.828072] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2342.841505] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2342.841520] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2342.959710] ath: phy0: Chip reset failed
[ 2342.959723] ath: phy0: Unable to reset channel, reset status -22
[ 2342.959752] ath: phy0: Unable to set channel
[ 2343.028356] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2343.041800] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2343.041815] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2343.160468] ath: phy0: Chip reset failed
[ 2343.160485] ath: phy0: Unable to reset channel, reset status -22
[ 2343.160541] ath: phy0: Unable to set channel
[ 2343.228686] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2343.242410] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2343.242435] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2343.360704] ath: phy0: Chip reset failed
[ 2343.360717] ath: phy0: Unable to reset channel, reset status -22
[ 2343.360743] ath: phy0: Unable to set channel
[ 2343.429281] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2343.442741] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2343.442760] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2343.560973] ath: phy0: Chip reset failed
[ 2343.560986] ath: phy0: Unable to reset channel, reset status -22
[ 2343.561015] ath: phy0: Unable to set channel
[ 2343.629586] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2343.643045] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2343.643063] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2343.761676] ath: phy0: Chip reset failed
[ 2343.761694] ath: phy0: Unable to reset channel, reset status -22
[ 2343.761746] ath: phy0: Unable to set channel
[ 2343.829675] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2343.843409] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2343.843434] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2343.961794] ath: phy0: Chip reset failed
[ 2343.961807] ath: phy0: Unable to reset channel, reset status -22
[ 2343.961837] ath: phy0: Unable to set channel
[ 2344.030498] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2344.043948] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2344.043966] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2344.162221] ath: phy0: Chip reset failed
[ 2344.162234] ath: phy0: Unable to reset channel, reset status -22
[ 2344.162263] ath: phy0: Unable to set channel
[ 2344.230841] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2344.244284] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2344.244302] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2344.362722] ath: phy0: Chip reset failed
[ 2344.362735] ath: phy0: Unable to reset channel, reset status -22
[ 2344.362766] ath: phy0: Unable to set channel
[ 2344.431205] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2344.444829] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2344.444848] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2344.563137] ath: phy0: Chip reset failed
[ 2344.563150] ath: phy0: Unable to reset channel, reset status -22
[ 2344.563186] ath: phy0: Unable to set channel
[ 2344.631643] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2344.645110] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2344.645127] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2344.763342] ath: phy0: Chip reset failed
[ 2344.763356] ath: phy0: Unable to reset channel, reset status -22
[ 2344.763390] ath: phy0: Unable to set channel
[ 2344.832098] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2344.845554] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2344.845570] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2344.964072] ath: phy0: Chip reset failed
[ 2344.964086] ath: phy0: Unable to reset channel, reset status -22
[ 2344.964123] ath: phy0: Unable to set channel
[ 2344.968017] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
[ 2344.968017] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2345.100552] ath: phy0: Failed to wakeup in 500us
[ 2345.176917] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2345.190488] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2345.190509] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2345.309230] ath: phy0: Chip reset failed
[ 2345.309243] ath: phy0: Unable to reset channel, reset status -22
[ 2345.309302] ath: phy0: Unable to set channel
[ 2345.378437] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2345.391996] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2345.392053] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2345.510596] ath: phy0: Chip reset failed
[ 2345.510608] ath: phy0: Unable to reset channel, reset status -22
[ 2345.579865] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2345.593435] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2345.593456] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2345.712156] ath: phy0: Chip reset failed
[ 2345.712172] ath: phy0: Unable to reset channel, reset status -22
[ 2345.712214] ath: phy0: Unable to set channel
[ 2345.780250] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2345.793719] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2345.793734] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2345.911584] ath: phy0: Chip reset failed
[ 2345.911593] ath: phy0: Unable to reset channel, reset status -22
[ 2345.911619] ath: phy0: Unable to set channel
[ 2345.979631] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2345.993097] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2345.993112] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2346.110936] ath: phy0: Chip reset failed
[ 2346.110946] ath: phy0: Unable to reset channel, reset status -22
[ 2346.110980] ath: phy0: Unable to set channel
[ 2346.179030] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2346.192461] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2346.192477] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2346.310331] ath: phy0: Chip reset failed
[ 2346.310338] ath: phy0: Unable to reset channel, reset status -22
[ 2346.310429] ath: phy0: Unable to set channel
[ 2346.378657] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2346.392157] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2346.392172] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2346.511111] ath: phy0: Chip reset failed
[ 2346.511124] ath: phy0: Unable to reset channel, reset status -22
[ 2346.511199] ath: phy0: Unable to set channel
[ 2346.579620] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2346.593110] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2346.593127] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2346.711185] ath: phy0: Chip reset failed
[ 2346.711197] ath: phy0: Unable to reset channel, reset status -22
[ 2346.711275] ath: phy0: Unable to set channel
[ 2346.779315] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2346.792844] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2346.792861] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2346.910981] ath: phy0: Chip reset failed
[ 2346.910993] ath: phy0: Unable to reset channel, reset status -22
[ 2346.911014] ath: phy0: Unable to set channel
[ 2346.979677] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2346.993257] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2346.993281] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2347.112171] ath: phy0: Chip reset failed
[ 2347.112186] ath: phy0: Unable to reset channel, reset status -22
[ 2347.112224] ath: phy0: Unable to set channel
[ 2347.180658] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2347.194131] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2347.194147] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2347.312215] ath: phy0: Chip reset failed
[ 2347.312226] ath: phy0: Unable to reset channel, reset status -22
[ 2347.312259] ath: phy0: Unable to set channel
[ 2347.380452] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2347.393981] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2347.393997] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2347.512787] ath: phy0: Chip reset failed
[ 2347.512808] ath: phy0: Unable to reset channel, reset status -22
[ 2347.512869] ath: phy0: Unable to set channel
[ 2347.581297] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2347.594779] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2347.594795] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2347.712839] ath: phy0: Chip reset failed
[ 2347.712849] ath: phy0: Unable to reset channel, reset status -22
[ 2347.712882] ath: phy0: Unable to set channel
[ 2347.780922] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2347.794447] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2347.794467] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2347.912447] ath: phy0: Chip reset failed
[ 2347.912458] ath: phy0: Unable to reset channel, reset status -22
[ 2347.912494] ath: phy0: Unable to set channel
[ 2347.980624] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2347.994086] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2347.994101] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2348.112085] ath: phy0: Chip reset failed
[ 2348.112097] ath: phy0: Unable to reset channel, reset status -22
[ 2348.112129] ath: phy0: Unable to set channel
[ 2348.181419] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2348.194888] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2348.194904] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2348.314519] ath: phy0: Chip reset failed
[ 2348.314537] ath: phy0: Unable to reset channel, reset status -22
[ 2348.314587] ath: phy0: Unable to set channel
[ 2348.383998] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2348.397587] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2348.397601] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2348.516096] ath: phy0: Chip reset failed
[ 2348.516103] ath: phy0: Unable to reset channel, reset status -22
[ 2348.516137] ath: phy0: Unable to set channel
[ 2348.520010] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
[ 2348.520010] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2352.992062] ath: phy0: Failed to wakeup in 500us
[ 2353.002881] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
[ 2353.002881] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2358.000020] ath: phy0: Failed to wakeup in 500us
[ 2358.010775] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
[ 2358.010775] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2362.992026] ath: phy0: Failed to wakeup in 500us
[ 2363.002817] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
[ 2363.002817] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2368.000018] ath: phy0: Failed to wakeup in 500us
[ 2368.010819] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
[ 2368.010819] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2368.012015] ath: phy0: Failed to wakeup in 500us
[ 2368.218601] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2368.232105] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2368.232120] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2368.350069] ath: phy0: Chip reset failed
[ 2368.350082] ath: phy0: Unable to reset channel, reset status -22
[ 2368.350171] ath: phy0: Unable to set channel
[ 2368.419510] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2368.433052] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2368.433070] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2368.551809] ath: phy0: Chip reset failed
[ 2368.551826] ath: phy0: Unable to reset channel, reset status -22
[ 2368.621294] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2368.634816] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2368.634834] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2368.753491] ath: phy0: Chip reset failed
[ 2368.753508] ath: phy0: Unable to reset channel, reset status -22
[ 2368.753554] ath: phy0: Unable to set channel
[ 2368.821788] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2368.835291] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2368.835304] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2368.953537] ath: phy0: Chip reset failed
[ 2368.953550] ath: phy0: Unable to reset channel, reset status -22
[ 2368.953585] ath: phy0: Unable to set channel
[ 2369.021842] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2369.035363] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2369.035377] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2369.153628] ath: phy0: Chip reset failed
[ 2369.153636] ath: phy0: Unable to reset channel, reset status -22
[ 2369.153678] ath: phy0: Unable to set channel
[ 2369.223104] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2369.236953] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2369.236978] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2369.356146] ath: phy0: Chip reset failed
[ 2369.356159] ath: phy0: Unable to reset channel, reset status -22
[ 2369.356193] ath: phy0: Unable to set channel
[ 2369.424167] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2369.437595] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2369.437610] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2369.555705] ath: phy0: Chip reset failed
[ 2369.555724] ath: phy0: Unable to reset channel, reset status -22
[ 2369.555790] ath: phy0: Unable to set channel
[ 2369.623917] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2369.637395] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2369.637411] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2369.755455] ath: phy0: Chip reset failed
[ 2369.755468] ath: phy0: Unable to reset channel, reset status -22
[ 2369.755501] ath: phy0: Unable to set channel
[ 2369.823416] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2369.836874] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2369.836887] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2369.954686] ath: phy0: Chip reset failed
[ 2369.954693] ath: phy0: Unable to reset channel, reset status -22
[ 2369.954722] ath: phy0: Unable to set channel
[ 2370.022468] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2370.035889] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2370.035901] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2370.153585] ath: phy0: Chip reset failed
[ 2370.153594] ath: phy0: Unable to reset channel, reset status -22
[ 2370.153623] ath: phy0: Unable to set channel
[ 2370.221454] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2370.234911] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2370.234924] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2370.352959] ath: phy0: Chip reset failed
[ 2370.352973] ath: phy0: Unable to reset channel, reset status -22
[ 2370.353003] ath: phy0: Unable to set channel
[ 2370.422373] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2370.436043] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2370.436066] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2370.555614] ath: phy0: Chip reset failed
[ 2370.555634] ath: phy0: Unable to reset channel, reset status -22
[ 2370.555699] ath: phy0: Unable to set channel
[ 2370.625301] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2370.638964] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2370.638983] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2370.757227] ath: phy0: Chip reset failed
[ 2370.757240] ath: phy0: Unable to reset channel, reset status -22
[ 2370.757283] ath: phy0: Unable to set channel
[ 2370.825559] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2370.839031] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2370.839046] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2370.957121] ath: phy0: Chip reset failed
[ 2370.957133] ath: phy0: Unable to reset channel, reset status -22
[ 2370.957160] ath: phy0: Unable to set channel
[ 2371.025300] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2371.038769] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2371.038783] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2371.156839] ath: phy0: Chip reset failed
[ 2371.156848] ath: phy0: Unable to reset channel, reset status -22
[ 2371.156881] ath: phy0: Unable to set channel
[ 2371.224785] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2371.238258] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2371.238276] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2371.356498] ath: phy0: Chip reset failed
[ 2371.356510] ath: phy0: Unable to reset channel, reset status -22
[ 2371.356538] ath: phy0: Unable to set channel
[ 2371.425183] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2371.438701] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2371.438716] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2371.557260] ath: phy0: Chip reset failed
[ 2371.557278] ath: phy0: Unable to reset channel, reset status -22
[ 2371.557346] ath: phy0: Unable to set channel
[ 2371.560017] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
[ 2371.560017] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2372.992021] ath: phy0: Failed to wakeup in 500us
[ 2373.002807] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
[ 2373.002807] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2378.000035] ath: phy0: Failed to wakeup in 500us
[ 2378.010787] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
[ 2378.010787] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2381.640022] ath: phy0: Failed to wakeup in 500us
[ 2381.716273] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2381.729729] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2381.729744] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2381.847607] ath: phy0: Chip reset failed
[ 2381.847617] ath: phy0: Unable to reset channel, reset status -22
[ 2381.847670] ath: phy0: Unable to set channel
[ 2381.916679] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2381.930225] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2381.930246] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2382.049004] ath: phy0: Chip reset failed
[ 2382.049023] ath: phy0: Unable to reset channel, reset status -22
[ 2382.118299] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2382.131853] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2382.131875] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2382.250536] ath: phy0: Chip reset failed
[ 2382.250554] ath: phy0: Unable to reset channel, reset status -22
[ 2382.250610] ath: phy0: Unable to set channel
[ 2382.318453] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2382.331889] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2382.331904] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2382.449675] ath: phy0: Chip reset failed
[ 2382.449686] ath: phy0: Unable to reset channel, reset status -22
[ 2382.449719] ath: phy0: Unable to set channel
[ 2382.517532] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2382.530959] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2382.530976] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2382.648783] ath: phy0: Chip reset failed
[ 2382.648793] ath: phy0: Unable to reset channel, reset status -22
[ 2382.648821] ath: phy0: Unable to set channel
[ 2382.716685] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2382.730106] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2382.730121] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2382.847828] ath: phy0: Chip reset failed
[ 2382.847839] ath: phy0: Unable to reset channel, reset status -22
[ 2382.847868] ath: phy0: Unable to set channel
[ 2382.915679] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2382.929110] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2382.929126] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2383.046839] ath: phy0: Chip reset failed
[ 2383.046851] ath: phy0: Unable to reset channel, reset status -22
[ 2383.046877] ath: phy0: Unable to set channel
[ 2383.114675] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2383.128110] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2383.128126] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2383.245828] ath: phy0: Chip reset failed
[ 2383.245839] ath: phy0: Unable to reset channel, reset status -22
[ 2383.245869] ath: phy0: Unable to set channel
[ 2383.313695] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2383.327131] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2383.327148] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2383.444887] ath: phy0: Chip reset failed
[ 2383.444897] ath: phy0: Unable to reset channel, reset status -22
[ 2383.444924] ath: phy0: Unable to set channel
[ 2383.512745] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2383.526159] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2383.526173] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2383.644000] ath: phy0: Chip reset failed
[ 2383.644033] ath: phy0: Unable to reset channel, reset status -22
[ 2383.644068] ath: phy0: Unable to set channel
[ 2383.712003] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2383.725445] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2383.725461] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2383.843141] ath: phy0: Chip reset failed
[ 2383.843151] ath: phy0: Unable to reset channel, reset status -22
[ 2383.843179] ath: phy0: Unable to set channel
[ 2383.910982] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2383.924426] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2383.924442] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2384.042167] ath: phy0: Chip reset failed
[ 2384.042178] ath: phy0: Unable to reset channel, reset status -22
[ 2384.042204] ath: phy0: Unable to set channel
[ 2384.110030] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2384.123467] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2384.123483] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2384.241243] ath: phy0: Chip reset failed
[ 2384.241254] ath: phy0: Unable to reset channel, reset status -22
[ 2384.241282] ath: phy0: Unable to set channel
[ 2384.309088] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2384.322524] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2384.322544] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2384.440266] ath: phy0: Chip reset failed
[ 2384.440276] ath: phy0: Unable to reset channel, reset status -22
[ 2384.440309] ath: phy0: Unable to set channel
[ 2384.508096] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2384.521519] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2384.521534] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2384.639380] ath: phy0: Chip reset failed
[ 2384.639390] ath: phy0: Unable to reset channel, reset status -22
[ 2384.639422] ath: phy0: Unable to set channel
[ 2384.707342] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2384.720776] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2384.720791] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2384.838520] ath: phy0: Chip reset failed
[ 2384.838530] ath: phy0: Unable to reset channel, reset status -22
[ 2384.838558] ath: phy0: Unable to set channel
[ 2384.906691] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 2384.920214] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2384.920232] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2385.038848] ath: phy0: Chip reset failed
[ 2385.038868] ath: phy0: Unable to reset channel, reset status -22
[ 2385.038921] ath: phy0: Unable to set channel
[ 2385.148090] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
[ 2385.148090] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff

########## wireless info END ############

```

Any help would be much appreciated.

---

### Post by wulong710 on 2014-08-07
I met the same question. No solution.

---

