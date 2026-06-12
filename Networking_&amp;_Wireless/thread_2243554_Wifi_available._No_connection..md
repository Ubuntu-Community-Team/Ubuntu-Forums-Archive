---
title: "Wifi available. No connection."
date: 2014-09-09
forum: Networking &amp; Wireless
---

### Post by wyoming on 2014-09-09
It's a laptop with 14.04. Was working fine until a problem ocurred with the Linksys EA 6500 router. Was reset and since then nm sees the available wifi but cannot connect to it no matter what.
Here's the wireless.info text.

```



	======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

laptop 3.13.0-32-generic i686,  Ubuntu 14.04.1 LTS, trusty

CPU    : Pentium(R) Dual-Core CPU       T4300  @ 2.10GHz
Memory : 2991 MB
Uptime : 16:33:40 up  2:48,  2 users,  load average: 0.14, 0.18, 0.21


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

04:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
	Subsystem: Broadcom Corporation Device [14e4:04b5]
	Kernel driver in use: wl
07:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
	Subsystem: Lenovo IdeaPad S10e [17aa:3a23]
	Kernel driver in use: tg3


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 003: ID 5986:0145 Acer, Inc 
Bus 002 Device 002: ID 03f0:f807 Hewlett-Packard 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11abg  ESSID:"Suzy"  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface            Soft blocked  Hard blocked
0: phy0: Wireless LAN          no            no
1: brcmwl-0: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

brcmsmac              529837  0 
cordic                 12518  1 brcmsmac
brcmutil               15066  1 brcmsmac
mac80211              546051  1 brcmsmac
bcma                   42043  1 brcmsmac
wl                   3999690  0 
lib80211               14040  2 wl,lib80211_crypt_tkip
cfg80211              409394  3 wl,brcmsmac,mac80211


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
============================o=============o========o==============o=========o===========o==============o===========
 Interface & ID             | Type        | Driver | State        | Default | Speed     | Support      | HW Addr   
============================o=============o========o==============o=========o===========o==============o===========
 eth1  [Wired connection 1] | Wired       | tg3    | connected    | yes     | 100 Mb/s  |              | <MAC eth1>

    Address:         192.168.1.119
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             192.168.1.1
----------------------------+-------------+--------+--------------+---------+-----------+--------------+-----------
 wlan0                      | 802.11 WiFi | wl     | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>

    CenturyLink2450: Infra, <MAC C-NA CenturyLink2450 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    ZyXEL_E0A:       Infra, <MAC C-NA ZyXEL_E0A 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WEP
    CenturyLink6430: Infra, <MAC C-NA CenturyLink6430 1>, Freq 2422 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    Suzy:            Infra, <MAC C-NA Suzy 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100
----------------------------+-------------+--------+--------------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~
 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1
search allegiance.tv


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth1

--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 0.729/3.707/6.686/2.979 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.029/0.034/0.039/0.005 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")
country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     26 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 14 (2.484 GHz)
          Channel 36 (5.18 GHz)
          Channel 38 (5.19 GHz)
          Channel 40 (5.2 GHz)
          Channel 42 (5.21 GHz)
          Channel 44 (5.22 GHz)
          Channel 46 (5.23 GHz)
          Channel 48 (5.24 GHz)
          Channel 149 (5.745 GHz)
          Channel 153 (5.765 GHz)
          Channel 157 (5.785 GHz)
          Channel 161 (5.805 GHz)
          Channel 165 (5.825 GHz) - 14 (2.484 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

No way to aquire root rights found.


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist b43
blacklist ssb


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[brcmsmac]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fw
srcversion:     43D6897F7EB716081DF69BE
depends:        bcma,mac80211,brcmutil,cfg80211,cordic

[cordic]
filename:       /lib/modules/3.13.0-32-generic/kernel/lib/cordic.ko
srcversion:     810E6E73D80DD7F75AC5B42
depends:        

[brcmutil]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
srcversion:     E81EE4CBB6A7A689150D93D
depends:        

[mac80211]
filename:       /lib/modules/3.13.0-32-generic/kernel/net/mac80211/mac80211.ko
srcversion:     8ADA881D348148A3358334C
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[bcma]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/bcma/bcma.ko
srcversion:     E41B811D88783DD5BC38565
depends:        

[wl]

[lib80211]
filename:       /lib/modules/3.13.0-32-generic/kernel/net/wireless/lib80211.ko
srcversion:     84DEF767F03D28E373F18E5
depends:        

[cfg80211]
filename:       /lib/modules/3.13.0-32-generic/kernel/net/wireless/cfg80211.ko
srcversion:     E786D076B61F97809B04B64
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x1106:0x3065 (via-rhine)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x1713 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth1>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# PCI device 0x14e4:0x4315 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Not Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/rc.local]
exit 0
iw reg set US
iwlist scan
exit 0

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-32-generic root=UUID=f8c11c48-7827-4516-8699-3c2e26fef8d3 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.756189] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.756484] audit: initializing netlink socket (disabled)
[    1.341376] tg3 0000:07:00.0 eth0: attached PHY is 5906 (10/100Base-TX Ethernet) (WireSpeed[0], EEE[0])
[   13.860245] systemd-udevd[309]: renamed network interface eth0 to eth1
[   13.918398] wl: module license 'MIXED/Proprietary' taints kernel.
[   13.957257] wl: module verification failed: signature and/or  required key missing - tainting kernel
[   13.995434] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   14.341965] wlan0: Broadcom BCM4315 802.11 Hybrid Wireless Controller 6.30.223.141 (r415941)
[   16.623255] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.149666] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   18.150094] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[  424.891262] tg3 0000:07:00.0 eth1: Link is up at 100 Mbps, full duplex
[  424.891276] tg3 0000:07:00.0 eth1: Flow control is on for TX and on for RX
[  424.891341] IPv6: ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  659.912451] ERROR @wl_dev_intvar_get : error (-1)
[  659.912461] ERROR @wl_cfg80211_get_tx_power : error (-1)
[  859.110490] tg3 0000:07:00.0 eth1: Link is down
[  863.201597] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[  908.567117] tg3 0000:07:00.0 eth1: Link is up at 100 Mbps, full duplex
[  908.567125] tg3 0000:07:00.0 eth1: Flow control is on for TX and on for RX
[  908.567184] IPv6: ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 6690.950847] ERROR @wl_dev_intvar_get : error (-1)
[ 6690.950856] ERROR @wl_cfg80211_get_tx_power : error (-1)
[ 6895.139376] ERROR @wl_dev_intvar_get : error (-1)
[ 6895.139385] ERROR @wl_cfg80211_get_tx_power : error (-1)
[ 7026.400836] ERROR @wl_dev_intvar_get : error (-1)
[ 7026.400844] ERROR @wl_cfg80211_get_tx_power : error (-1)
[ 7075.254281] tg3 0000:07:00.0 eth1: Link is down
[ 7080.206093] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 7083.240451] tg3 0000:07:00.0 eth1: Link is up at 100 Mbps, full duplex
[ 7083.240466] tg3 0000:07:00.0 eth1: Flow control is on for TX and on for RX
[ 7083.240534] IPv6: ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 7219.312091] ERROR @wl_dev_intvar_get : error (-1)
[ 7219.312101] ERROR @wl_cfg80211_get_tx_power : error (-1)
[ 7308.313379] ERROR @wl_dev_intvar_get : error (-1)
[ 7308.313388] ERROR @wl_cfg80211_get_tx_power : error (-1)
[ 9719.642327] tg3 0000:07:00.0 eth1: Link is down
[ 9724.206396] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 9762.908477] tg3 0000:07:00.0 eth1: Link is up at 100 Mbps, full duplex
[ 9762.908497] tg3 0000:07:00.0 eth1: Flow control is on for TX and on for RX
[ 9762.908563] IPv6: ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 9920.142406] tg3 0000:07:00.0 eth1: Link is down
[ 9924.206524] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 9946.013934] ERROR @wl_dev_intvar_get : error (-1)
[ 9946.013943] ERROR @wl_cfg80211_get_tx_power : error (-1)
[ 9961.840165] tg3 0000:07:00.0 eth1: Link is up at 100 Mbps, full duplex
[ 9961.840180] tg3 0000:07:00.0 eth1: Flow control is on for TX and on for RX
[ 9961.840245] IPv6: ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[10122.149436] ERROR @wl_dev_intvar_get : error (-1)
[10122.149443] ERROR @wl_cfg80211_get_tx_power : error (-1)

	======== Done ========

```

Completely ran out of options here. Thanks so much for the help!!

---

### Post by Hadaka on 2014-09-09
Hi, please open a terminal - ctrl/alt/t and do..
from a wired connection
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
```

```
sudo apt-get-update
sudo rm /etc/udev/rules.d/70-persistent-net.rules
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
boot-test wireless

---

### Post by grahammechanical on 2014-09-09
Resetting the router would have put back the factory default wireless key or pass phrase. If you at some point changed the pass phrase (something it is recommended that we do) then network manager cannot authenticate the connection to the router. It now has the wrong pass phrase.

If network manager is showing a list of available wireless access points and your router is in the list, then your WiFi adapter is working and it has a driver. Ubuntu has done as much as it could do. The need to authenticate the connection is between you and the router.

My advice? Delete the connection and start again making sure that you and the router agree what the pass phrase is.

Regards.

---

### Post by wyoming on 2014-09-09
First off, all my thanks to both of you for taking the time and giving a hand.
To Graham: I have 2 laptops (win7) and a desktop (14.04lts) who connect to the router just fine. Only my laptop with 14.04 has this issue so that it doesn't look like a password issue. And I have no security on this router (hiding in plain sight!)
To Hadaka, I entered your code but get to the same point. No connection. Wifi networks are listed but can't be connected to. I use a wire to write this. The wire was disconnected on reboot. Just in case I attach another wireless-script just made.
```


	======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

laptop 3.13.0-32-generic i686,  Ubuntu 14.04.1 LTS, trusty

CPU    : Pentium(R) Dual-Core CPU       T4300  @ 2.10GHz
Memory : 2991 MB
Uptime : 19:46:20 up 1 min,  1 user,  load average: 2.19, 0.77, 0.28


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

04:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
	Subsystem: Broadcom Corporation Device [14e4:04b5]
	Kernel driver in use: b43-pci-bridge
07:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
	Subsystem: Lenovo IdeaPad S10e [17aa:3a23]
	Kernel driver in use: tg3


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 003: ID 5986:0145 Acer, Inc 
Bus 002 Device 002: ID 03f0:f807 Hewlett-Packard 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface                Soft blocked  Hard blocked
0: ideapad_wlan: Wireless LAN      no            no
1: phy0: Wireless LAN              no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

b43                   356470  0 
bcma                   42043  1 b43
mac80211              546051  1 b43
cfg80211              409394  2 b43,mac80211
ssb                    51854  1 b43


module parameters ~~~~~~~~~~~~~~~~~~

b43          (10): allhwsupport=0 | bad_frames_preempt=0 | btcoex=1 | hwpctl=0 | hwtkip=0 | nohwcrypt=0 | pio=0 | qos=1 | verbose=2
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
============================o=============o========o==============o=========o===========o==============o===========
 Interface & ID             | Type        | Driver | State        | Default | Speed     | Support      | HW Addr   
============================o=============o========o==============o=========o===========o==============o===========
 eth0  [Wired connection 1] | Wired       | tg3    | connected    | yes     | 100 Mb/s  |              | <MAC eth0>

    Address:         192.168.1.119
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             192.168.1.1
----------------------------+-------------+--------+--------------+---------+-----------+--------------+-----------
 wlan0                      | 802.11 WiFi | b43    | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>

    CenturyLink2450: Infra, <MAC C-NA CenturyLink2450 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    ZyXEL_E0A:       Infra, <MAC C-NA ZyXEL_E0A 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 35 WEP
    Suzy:            Infra, <MAC C-NA Suzy 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100
    CenturyLink6430: Infra, <MAC C-NA CenturyLink6430 1>, Freq 2422 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    parker:          Infra, <MAC C-NA parker 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WEP
----------------------------+-------------+--------+--------------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~
 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1
search allegiance.tv


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 1.076/1.696/2.317/0.621 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.023/0.031/0.039/0.008 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")
country US:
	(2402 - 2472 @ 40), (3, 27)
	(5170 - 5250 @ 40), (3, 17)
	(5250 - 5330 @ 40), (3, 20), DFS
	(5490 - 5600 @ 40), (3, 20), DFS
	(5650 - 5710 @ 40), (3, 20), DFS
	(5735 - 5835 @ 40), (3, 30)
	(57240 - 63720 @ 2160), (N/A, 40)


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     11 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 11 (2.462 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

No way to aquire root rights found.


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[b43]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
srcversion:     42BAE2DB9BADE3E7ECA2CC0
depends:        bcma,ssb,mac80211,cfg80211
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)

[bcma]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/bcma/bcma.ko
srcversion:     E41B811D88783DD5BC38565
depends:        

[mac80211]
filename:       /lib/modules/3.13.0-32-generic/kernel/net/mac80211/mac80211.ko
srcversion:     8ADA881D348148A3358334C
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-32-generic/kernel/net/wireless/cfg80211.ko
srcversion:     E786D076B61F97809B04B64
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ssb]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/ssb/ssb.ko
srcversion:     3DE188310F77C566C2E8CB3
depends:        


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x14e4:0x1713 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4315 (b43)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Not Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/rc.local]
exit 0
iw reg set US
iwlist scan
exit 0

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-32-generic root=UUID=f8c11c48-7827-4516-8699-3c2e26fef8d3 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.756149] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.756445] audit: initializing netlink socket (disabled)
[    1.280771] ssb: Found chip with id 0x4312, rev 0x01 and package 0x00
[    1.280790] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x16, vendor 0x4243)
[    1.280807] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0F, vendor 0x4243)
[    1.280824] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x0A, vendor 0x4243)
[    1.280842] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x09, vendor 0x4243)
[    1.340259] tg3 0000:07:00.0 eth0: attached PHY is 5906 (10/100Base-TX Ethernet) (WireSpeed[0], EEE[0])
[    1.355538] ssb: Sonics Silicon Backplane found on PCI device 0000:04:00.0
[   12.259546] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   12.300248] b43-phy0: Found PHY: Analog 6, Type 5 (LP), Revision 1
[   13.466450] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   15.368267] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   20.961249] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.961609] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   38.709049] wlan0: authenticate with <MAC C-NA Suzy 1>
[   38.732638] wlan0: send auth to <MAC C-NA Suzy 1> (try 1/3)
[   38.737290] wlan0: authenticated
[   38.740054] wlan0: associate with <MAC C-NA Suzy 1> (try 1/3)
[   38.744113] wlan0: RX AssocResp from <MAC C-NA Suzy 1> (capab=0x1401 status=18 aid=0)
[   38.744119] wlan0: <MAC C-NA Suzy 1> denied association (code=18)
[   38.760652] wlan0: deauthenticating from <MAC C-NA Suzy 1> by local choice (reason=3)
[   39.608752] wlan0: authenticate with <MAC C-NA Suzy 1>
[   39.609316] wlan0: send auth to <MAC C-NA Suzy 1> (try 1/3)
[   39.611247] wlan0: authenticated
[   39.612058] wlan0: associate with <MAC C-NA Suzy 1> (try 1/3)
[   39.614849] wlan0: RX AssocResp from <MAC C-NA Suzy 1> (capab=0x1401 status=18 aid=0)
[   39.614855] wlan0: <MAC C-NA Suzy 1> denied association (code=18)
[   39.636460] wlan0: deauthenticating from <MAC C-NA Suzy 1> by local choice (reason=3)
[   40.884947] wlan0: authenticate with <MAC C-NA Suzy 1>
[   40.885521] wlan0: send auth to <MAC C-NA Suzy 1> (try 1/3)
[   40.891213] wlan0: authenticated
[   40.896052] wlan0: associate with <MAC C-NA Suzy 1> (try 1/3)
[   40.898606] wlan0: RX AssocResp from <MAC C-NA Suzy 1> (capab=0x1401 status=18 aid=0)
[   40.898612] wlan0: <MAC C-NA Suzy 1> denied association (code=18)
[   40.908985] wlan0: deauthenticating from <MAC C-NA Suzy 1> by local choice (reason=3)
[   42.656696] wlan0: authenticate with <MAC C-NA Suzy 1>
[   42.657260] wlan0: send auth to <MAC C-NA Suzy 1> (try 1/3)
[   42.659276] wlan0: authenticated
[   42.660073] wlan0: associate with <MAC C-NA Suzy 1> (try 1/3)
[   42.662759] wlan0: RX AssocResp from <MAC C-NA Suzy 1> (capab=0x1401 status=18 aid=0)
[   42.662765] wlan0: <MAC C-NA Suzy 1> denied association (code=18)
[   42.678183] wlan0: deauthenticating from <MAC C-NA Suzy 1> by local choice (reason=3)
[   54.180698] wlan0: authenticate with <MAC C-NA Suzy 1>
[   54.188715] wlan0: send auth to <MAC C-NA Suzy 1> (try 1/3)
[   54.190693] wlan0: authenticated
[   54.196047] wlan0: associate with <MAC C-NA Suzy 1> (try 1/3)
[   54.198760] wlan0: RX AssocResp from <MAC C-NA Suzy 1> (capab=0x1401 status=18 aid=0)
[   54.198766] wlan0: <MAC C-NA Suzy 1> denied association (code=18)
[   54.208681] wlan0: deauthenticating from <MAC C-NA Suzy 1> by local choice (reason=3)

	======== Done ========

```

Thanks again!

---

### Post by wyoming on 2014-09-10
Investigating the dmsg about deauthentication code 18 I disocvered thta this type of code now refers to mismatch between tghe router asked speed and the capability of the card. Changing the router's setting to mixed mode and switvhign to a lsower channel allowed immedaite connection. Solved this myself like a big boy but with the help of the very good wireless script. Thanks!

---

### Post by varunendra on 2014-09-11
Just a very important pointer wyoming, and anyone following Hadaka's instructions for installing the firmware -

There has been a change in the "linux-firmware-nonfree" package very recently due to licencing issues, and it no longer installs the b43 firmware files. So, if it breaks again (perhaps after an update), the new (actually the older, now has to be embraced again..) method to install the firmware, using a working Ethernet connection is -

```
sudo apt-get install firmware-b43-installer
```

For those who installed the firmware using "linux-firmware-nonfree" package, and the wireless is still working, can simply copy their "**/lib/firmware/b43**" directory as a backup, and restore it manually after purging the "linux-firmware-nonfree" package (sudo apt-get purge linux-firmware-nonfree). It is somewhat the same as what is suggested here : [http://ubuntuforums.org/showpost.php?p=13119224](http://ubuntuforums.org/showpost.php?p=13119224)

---

