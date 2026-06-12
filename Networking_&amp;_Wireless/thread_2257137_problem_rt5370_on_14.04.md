---
title: "problem rt5370 on 14.04"
date: 2014-12-17
forum: Networking &amp; Wireless
---

### Post by jesus_zafra on 2014-12-17
I'm trrying to install RT5370 wifi dondle on mu laptop but there're no way, this is the output of the wireless script
the device appears as switched of, and i can't install any driver, the provided in a cd can't be extracted
Please assits, thanks in advance


```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

ubuntu 3.13.0-43-generic i686,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Core(TM)2 Duo CPU     P8400  @ 2.26GHz
Memory : 4033 MB
Uptime : 13:18:08 up 37 min,  2 users,  load average: 0,03, 0,20, 0,29


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

00:04.0 Ethernet controller [0200]: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter [1039:0191] (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1815]
    Kernel driver in use: sis190
--
02:00.0 Network controller [0280]: Qualcomm Atheros AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)
    Subsystem: AzureWave AW-NE771 802.11bgn Wireless Mini PCIe Card [AR9281] [1a3b:1067]
    Kernel driver in use: ath9k


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 005: ID 0bda:0116 Realtek Semiconductor Corp. RTS5116 Card Reader Controller
Bus 001 Device 004: ID 064e:a111 Suyin Corp. 
Bus 001 Device 006: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan3     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            yes
1: phy1: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

ath9k                 144602  0 
rt2800usb              26581  0 
ath9k_common           13359  1 ath9k
rt2x00usb              20041  1 rt2800usb
ath9k_hw              438205  2 ath9k_common,ath9k
rt2800lib              83150  1 rt2800usb
rt2x00lib              48886  3 rt2x00usb,rt2800lib,rt2800usb
ath                    23922  3 ath9k_common,ath9k,ath9k_hw
mac80211              546051  4 ath9k,rt2x00lib,rt2x00usb,rt2800lib
cfg80211              409394  4 ath,ath9k,mac80211,rt2x00lib
crc_ccitt              12627  1 rt2800lib


module parameters ~~~~~~~~~~~~~~~~~~

ath9k         (5): blink=0 | bt_ant_diversity=0 | btcoex_enable=0 | nohwcrypt=0 | ps_enable=0
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
rt2800usb     (1): nohwcrypt=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
=============================o=============o===========o=============o=========o===========o==============o===========
 Interface & ID              | Type        | Driver    | State       | Default | Speed     | Support      | HW Addr   
=============================o=============o===========o=============o=========o===========o==============o===========
 wlan3                       | 802.11 WiFi | rt2800usb | unavailable | no      |           | WEP/WPA/WPA2 | <MAC wlan3>
-----------------------------+-------------+-----------+-------------+---------+-----------+--------------+-----------
 wlan0                       | 802.11 WiFi | ath9k     | unavailable | no      |           | WEP/WPA/WPA2 | <MAC wlan0>
-----------------------------+-------------+-----------+-------------+---------+-----------+--------------+-----------
 eth0  [Conexión cableada 1]| Wired       | sis190    | connected   | yes     | 100 Mb/s  |              | <MAC ID removed>

    Address:         192.168.1.23
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             192.168.1.1
-----------------------------+-------------+-----------+-------------+---------+-----------+--------------+-----------


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
search hitronhub.home


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Tabla de rutas IP del núcleo
Destino         Pasarela        Genmask         Indic Métric Ref    Uso Interfaz
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1000ms
rtt min/avg/max/mdev = 0.476/0.488/0.500/0.012 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.028/0.035/0.043/0.009 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "es_ES.UTF-8")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan3     14 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 14 (2.484 GHz)

          wlan0     14 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 14 (2.484 GHz)
          Channel 01 (2.412 GHz) - 14 (2.484 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~



blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[ath9k]
filename:       /lib/modules/3.13.0-43-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
srcversion:     ADAEAFEC0FFEB04BC97E45D
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

[rt2800usb]
filename:       /lib/modules/3.13.0-43-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
firmware:       rt2870.bin
version:        2.3.0
srcversion:     81F4CDE501CE72D2443EE38
depends:        rt2x00lib,rt2800lib,rt2x00usb
parm:           nohwcrypt:Disable hardware encryption. (bool)

[ath9k_common]
filename:       /lib/modules/3.13.0-43-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
srcversion:     696B00A6C59713EC0966997
depends:        ath,ath9k_hw

[rt2x00usb]
filename:       /lib/modules/3.13.0-43-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
version:        2.3.0
srcversion:     C8AA2904FC6A58104E65BCC
depends:        rt2x00lib,mac80211

[ath9k_hw]
filename:       /lib/modules/3.13.0-43-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
srcversion:     4809F3842A0542CD6B556D3
depends:        ath

[rt2800lib]
filename:       /lib/modules/3.13.0-43-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
version:        2.3.0
srcversion:     3AF2621F166C8604D7D8AA5
depends:        rt2x00lib,mac80211,crc-ccitt

[rt2x00lib]
filename:       /lib/modules/3.13.0-43-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
version:        2.3.0
srcversion:     6B233AA4E9B794582FA258B
depends:        mac80211,cfg80211

[ath]
filename:       /lib/modules/3.13.0-43-generic/kernel/drivers/net/wireless/ath/ath.ko
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211

[mac80211]
filename:       /lib/modules/3.13.0-43-generic/kernel/net/mac80211/mac80211.ko
srcversion:     446B3604A9C5461044DD691
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-43-generic/kernel/net/wireless/cfg80211.ko
srcversion:     C2478077E22138832B71659
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[crc_ccitt]
filename:       /lib/modules/3.13.0-43-generic/kernel/lib/crc-ccitt.ko
srcversion:     2294FCAD06D727386004EEB
depends:        


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x1039:0x0191 (sis190)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:0x002a (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan1>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan1>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan2"

# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan3>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan3"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-43-generic root=UUID=45e131fd-0c2c-4dba-aa34-cbb2960f1afc ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.753752] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.754249] audit: initializing netlink socket (disabled)
[    1.206665] sis190: sis190 Gigabit Ethernet driver 1.4 loaded
[    1.792210] sis190 0000:00:04.0 eth0: 0000:00:04.0: SiS 191 PCI Gigabit Ethernet adapter at f841ac00 (IRQ: 19), <MAC ID removed>
[   14.321588] ath: EEPROM regdomain: 0x60
[   14.321591] ath: EEPROM indicates we should expect a direct regpair map
[   14.321595] ath: Country alpha2 being used: 00
[   14.321596] ath: Regpair used: 0x60
[   21.660210] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   28.053551] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  134.590810] ieee80211 phy1: rt2x00_set_rt: Info - RT chipset 5390, rev 0502 detected
[  134.618953] ieee80211 phy1: rt2x00_set_rf: Info - RF chipset 5370 detected
[  134.668298] systemd-udevd[2265]: renamed network interface wlan1 to wlan3
[  134.669483] IPv6: ADDRCONF(NETDEV_UP): wlan3: link is not ready

    ======== Done ========
```

---

### Post by chili555 on 2014-12-17
The driver rt2800usb is already installed. Until we solve the 'hard blocked: yes' issue, no different wireless device and no different driver is going to help. If an automobile is out of fuel, changing the driver (!!) isn't going to make it go.

I would rather you remove the USB and let's troubleshoot with the internal only.

First, may I see:```
lsmod
```What is the brand and model of laptop? Usually, there is a little helper module that translates key presses into action; in this case, turn on the wireless. I suspect it's missing or not set up properly here. In a few cases, removing the module helps.

---

### Post by jesus_zafra on 2014-12-19
hello
the internal card dont work
I have Win 7 and ubuntu installed, some days ago wifi internal card stop working either win and ubuntu, both system tell me that the card was switched off but the physical button was activates so i bought a usb wifi, ralink 5370, on windows i installed thr drivers provided in cd and it's working, the usb stick don't have any switch button
Please let me know what do you need to continue testing
thanks a lot for your collaboration

this is the product in ebay
[http://www.ebay.com/itm/380756446888](http://www.ebay.com/itm/380756446888)

---

### Post by chili555 on 2014-12-19
Let's blacklist the driver for the internal and see if it helps. Please open a terminal and do:```
sudo -i
echo "blacklist ath9k"  >>  /etc/modprobe.d/blacklist.conf
exit
```Reboot and then please post:```
rfkill list all
lsmod | grep -e laptop -e wmi
```Thanks.

There is nothing, by the way, in your wireless_script that suggests that the internal is broken.

---

### Post by jesus_zafra on 2014-12-24
Hello
after blacklist the internal card, the usb wifi it's working!
thanks very much for your help!!
Kind regards

---

