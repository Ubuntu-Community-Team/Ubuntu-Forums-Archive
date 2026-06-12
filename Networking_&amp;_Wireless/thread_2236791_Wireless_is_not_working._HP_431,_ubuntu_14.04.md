---
title: "Wireless is not working. HP 431, ubuntu 14.04"
date: 2014-07-29
forum: Networking &amp; Wireless
---

### Post by Adhityo_Yudhono on 2014-07-29
Hi, I am new user for ubuntu

this is first time I install ubuntu, and the wifi is not working

I already see some thread, they put wireless script.

Here's my wireless script

```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

AYS-PC 3.13.0-32-generic x86_64,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Core(TM) i3-2310M CPU @ 2.10GHz
Memory : 3806 MB
Uptime : 11:37:24 up 20 min,  2 users,  load average: 0,32, 0,35, 0,32


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Hewlett-Packard Company Device [103c:3673]
    Kernel driver in use: r8169
08:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:1461]
    Kernel driver in use: ath9k


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 009: ID 12d1:1001 Huawei Technologies Co., Ltd. E169/E620/E800 HSDPA Modem
Bus 002 Device 004: ID 045e:0719 Microsoft Corp. Xbox 360 Wireless Adapter
Bus 002 Device 003: ID 0e1f:2021  
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth
Bus 001 Device 003: ID 05c8:021e Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface             Soft blocked  Hard blocked
0: phy0: Wireless LAN           no            yes
1: hci0: Bluetooth              yes           no
2: hp-wifi: Wireless LAN        yes           no
3: hp-bluetooth: Bluetooth      yes           no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

hp_wmi                 14062  0 
sparse_keymap          13948  1 hp_wmi
ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              630653  1 ath9k
cfg80211              484040  3 ath,ath9k,mac80211
wmi                    19177  1 hp_wmi


module parameters ~~~~~~~~~~~~~~~~~~

ath9k         (5): blink=0 | bt_ant_diversity=0 | btcoex_enable=0 | nohwcrypt=0 | ps_enable=0
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
=========================o========================o=========o=============o=========o===========o==============o===========
 Interface & ID          | Type                   | Driver  | State       | Default | Speed     | Support      | HW Addr   
=========================o========================o=========o=============o=========o===========o==============o===========
 ttyUSB2  [du Default 1] | Mobile Broadband (GSM) | option1 | connected   | yes     |           |              |           

    Address:         10.178.110.150
    Prefix:          32 (255.255.255.255)
    Gateway:         10.64.64.64
    DNS:             91.74.74.74
    DNS:             94.200.200.200
-------------------------+------------------------+---------+-------------+---------+-----------+--------------+-----------
 wlan0                   | 802.11 WiFi            | ath9k   | unavailable | no      |           | WEP/WPA/WPA2 | <MAC wlan0>
-------------------------+------------------------+---------+-------------+---------+-----------+--------------+-----------
 eth0                    | Wired                  | r8169   | unavailable | no      |           |              | <MAC eth0>
-------------------------+------------------------+---------+-------------+---------+-----------+--------------+-----------


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


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.64.64.64     0.0.0.0         UG    0      0        0 ppp0
10.64.64.64     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0

--- 10.64.64.64 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3022ms


--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.036/0.040/0.045/0.007 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : id_ID.UTF-8)
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     14 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 14 (2.484 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~



blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[hp_wmi]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/platform/x86/hp-wmi.ko
srcversion:     22DCD1B7DA09178B45B1068
depends:        wmi,sparse-keymap

[ath9k]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
srcversion:     7EAAD420ADF6B9354F0C8C1
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

[ath9k_common]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
srcversion:     696B00A6C59713EC0966997
depends:        ath,ath9k_hw

[ath9k_hw]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
srcversion:     4809F3842A0542CD6B556D3
depends:        ath

[ath]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath.ko
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211

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

[wmi]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:0x002b (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


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

BOOT_IMAGE=/boot/vmlinuz-3.13.0-32-generic root=UUID=90f1d12b-a98a-485c-9c26-67930c347b41 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    1.176819] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.177162] audit: initializing netlink socket (disabled)
[    1.447180] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    8.334978] wmi: Mapper loaded
[    9.087224] ath: phy0: ASPM enabled: 0x43
[    9.087226] ath: EEPROM regdomain: 0x60
[    9.087227] ath: EEPROM indicates we should expect a direct regpair map
[    9.087229] ath: Country alpha2 being used: 00
[    9.087230] ath: Regpair used: 0x60
[   15.045103] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   21.252212] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  344.968728] sierra_net 2-1.3:1.7 wwan0: register 'sierra_net' at usb-0000:00:1d.0-1.3, Sierra Wireless USB-to-WWAN Modem, <MAC ID removed>
[  344.970819] usbcore: registered new interface driver sierra_net
[  622.939229] sierra_net 2-1.3:1.7 wwan0: unregister 'sierra_net' usb-0000:00:1d.0-1.3, Sierra Wireless USB-to-WWAN Modem
[  622.970334] sierra_net 2-1.3:1.7 (unregistered net_device): Submit Shutdown failed -71
[  622.970342] sierra_net 2-1.3:1.7 (unregistered net_device): usb_control_msg failed, status -71
[  622.990588] usb 2-1.3: Error in usbnet_get_endpoints (-19)

    ======== Done ========
```

I hope somebody can help me

thanks

---

### Post by praseodym on 2014-07-29
```
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=[COLOR="#FF0000"]off[/COLOR]   
```
Hi, your card is turned off, any button, switch or key combination?

---

### Post by Adhityo_Yudhono on 2014-07-29
yes, it's off

I already press it but nothin happen

it not going to switch on

---

### Post by praseodym on 2014-07-29
Lets try:
```

echo "options hp_wmi wireless=1" | sudo tee /etc/modprobe.d/hp.conf
```
Reboot.

---

### Post by roger_1960 on 2014-08-01
Hi

I have just installed 14.04.1 on an asus eeePC seashell 1011PX with an AR9285 wifi card and have the same issue.  Ubuntu reports the wifi is disabled by a hardware switch.  The key combination to switch networking on and off says it is working but does not enable wifi.  Is there a cure for this?  Happy to use CLI if needed.  Is this a bug in 14.04.1?

EDIT Found my solution!  Boot into windows 7, turn on wifi, shut down and reboot into Ubuntu.  It seems that windows can turn wifi on and off in a way Ubuntu cannot.

Roger

---

### Post by praseodym on 2014-08-01
Please show:
```

lspci -nnk | grep -iA2 net
lsmod
rfkill list
iwconfig
```

---

