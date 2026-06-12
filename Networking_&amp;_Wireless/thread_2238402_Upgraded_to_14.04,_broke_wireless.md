---
title: "Upgraded to 14.04, broke wireless"
date: 2014-08-07
forum: Networking &amp; Wireless
---

### Post by PaulBx on 2014-08-07
```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

len780 3.13.0-32-generic x86_64,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Core(TM) i5-3230M CPU @ 2.60GHz
Memory : 5834 MB
Uptime : 15:27:11 up 1 min,  2 users,  load average: 0.55, 0.28, 0.11


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8162 Fast Ethernet [1969:1090] (rev 10)
    Subsystem: Lenovo Device [17aa:3979]
    Kernel driver in use: alx
02:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: Lenovo Device [17aa:3218]
    Kernel driver in use: ath9k


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 003: ID 5986:0295 Acer, Inc 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 004: ID 0cf3:3004 Atheros Communications, Inc. 
Bus 001 Device 003: ID 046d:c06c Logitech, Inc. Optical Mouse
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface                  Soft blocked  Hard blocked
0: ideapad_wlan: Wireless LAN        yes           no
1: ideapad_bluetooth: Bluetooth      no            no
2: hci0: Bluetooth                   no            no
3: phy0: Wireless LAN                yes           no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              630653  1 ath9k
cfg80211              484040  3 ath,ath9k,mac80211


module parameters ~~~~~~~~~~~~~~~~~~

ath9k         (5): blink=0 | bt_ant_diversity=0 | btcoex_enable=0 | nohwcrypt=0 | ps_enable=0
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
===================o=============o========o=============o=========o===========o==============o===========
 Interface & ID    | Type        | Driver | State       | Default | Speed     | Support      | HW Addr   
===================o=============o========o=============o=========o===========o==============o===========
 wlan0             | 802.11 WiFi | ath9k  | unavailable | no      |           | WEP/WPA/WPA2 | <MAC wlan0>
-------------------+-------------+--------+-------------+---------+-----------+--------------+-----------
 eth0  [Ethernet1] | Wired       | alx    | connected   | yes     | 100 Mb/s  |              | <MAC eth0>

    Address:         192.168.5.103
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.5.1
    DNS:             192.168.5.1
    DNS:             8.8.8.8
    DNS:             8.8.4.4
-------------------+-------------+--------+-------------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=false
WWANEnabled=true
WimaxEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~

<edited to remove most entries - the following is the one I'm trying to connect to>
OregonHome3          : ssid=OregonHome3 | autoconnect=false | ipv4=auto | ipv6=ignore 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1
search paul.local


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.5.1     0.0.0.0         UG    0      0        0 eth0
192.168.5.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

--- 192.168.5.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.489/0.529/0.570/0.046 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.057/0.059/0.062/0.008 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~



blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/libpisock9.conf]
blacklist visor


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

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


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x1969:/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0 (alx)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# USB device 0x1410:0xb00b (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth1>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Not Default
/etc/rc.local       : Not Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modules]
loop

[/etc/rc.local]
/usr/local/bin/chkboot.sh&
echo deadline > /sys/block/sda/queue/scheduler
echo 1        > /sys/block/sda/queue/iosched/fifo_batch
exit 0

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/vmlinuz-3.13.0-32-generic root=/dev/mapper/lubuntu--vg-root ro elevator=deadline


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    4.073307] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    4.073548] audit: initializing netlink socket (disabled)
[    4.864686] alx 0000:01:00.0 eth0: Qualcomm Atheros AR816x/AR817x Ethernet [<MAC eth0>]
[   22.528482] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   22.612525] ath: phy0: Set BT/WLAN RX diversity capability
[   22.672358] ath: phy0: ASPM enabled: 0x42
[   22.672362] ath: EEPROM regdomain: 0x65
[   22.672364] ath: EEPROM indicates we should expect a direct regpair map
[   22.672366] ath: Country alpha2 being used: 00
[   22.672367] ath: Regpair used: 0x65
[   23.296263] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

    ======== Done ========


```

The machine is a Lenovo G780, wireless worked under 13.10 but I just might have had to fiddle something to get it going originally (my memory ain't what it was - in fact it never was).

I am kinda wondering why the rfkill command shows two of everything. I don't have an ideapad. BTW I tried unblocking all and they all unblocked but it didn't change anything.

---

### Post by PaulBx on 2014-08-07
Additional info:
I found the wireless switch Fn+F5. If I toggle it, the rfkill state toggles also, the same way as if I did it at the command line. However it does not turn the wireless on. Also the LED indicator for wireless always stays off.

---

### Post by jeremy31 on 2014-08-07
Strange since I have a Lenovo G710 with similar hardware and it works with Ubuntu 14.04 and I see the same with rfkill list

The difference that I can tell is that my keyboard uses FN+F7 for the wifi toggle

What do you see from terminal with ```
iw reg get
```

If you are in the US and see anything other than ```
country US:	(2402 - 2472 @ 40), (3, 27)
	(5170 - 5250 @ 40), (3, 17)
	(5250 - 5330 @ 40), (3, 20), DFS
	(5490 - 5600 @ 40), (3, 20), DFS
	(5650 - 5710 @ 40), (3, 20), DFS
	(5735 - 5835 @ 40), (3, 30)
	(57240 - 63720 @ 2160), (N/A, 40)
```
You might want to ```
sudo iw reg set US
```

---

### Post by PaulBx on 2014-08-07
I got this:
```

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

```

...so I ran that command and it changed to what you said it should be. Wireless still not working though. I will try a reboot...

---

### Post by PaulBx on 2014-08-07
...

Huh, the reboot set it back to the old output.

---

### Post by PaulBx on 2014-08-07
BTW "iwlist scan" gives "wlan0     Failed to read scan data : Network is down"

```

--- 192.168.5.1 ping statistics ---

```

The above is for the ethernet of course. When wireless shows up, it will connect to 192.168.10.1. The router is pfsense.

---

### Post by Hadaka on 2014-08-07
Hi,PaulBx
 Please do the following..from a wired connection
please do..
```
sudo gedit /etc/rc.local
```
Enter this ONE line of code..above exit0
```
iw reg set US
```
Save and close gedit....then REMOVE your USB wifi
and do.
```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```
then COPY and paste
```
sed -i 's/^REG.*=$/&US/' /etc/default/crda
```
finally do.
```
sudo apt-get update
sudo apt-get upgrade
```
BOOT
are you able to connect now??

---

### Post by PaulBx on 2014-08-08
Your instructions were a little unclear - "REMOVE your USB wifi"? What does that mean? My wifi is internal, not a dongle. "then COPY and paste"? Copy and paste what? The sed command didn't work, but I just edited the file and stuck US on the end of it. That or the thing in rc.local seems to work, at least the "iw reg get" returns the right thing now.

I saved the old persistent net rules and re-ran things and got a new one. This one has two devices, alx and ath9k, while the old one had three, with an extra device called usb with a name "eth1" - but I didn't have an eth1...

The new one looks like this:
```

# PCI device 0x168c:0x0032 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="2c:d0:5a:c7:98:0f", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

```

Anyway, it didn't work.

---

### Post by PaulBx on 2014-08-08
Here's the latest wireless script output:
```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

len780 3.13.0-32-generic x86_64,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Core(TM) i5-3230M CPU @ 2.60GHz
Memory : 5834 MB
Uptime : 22:21:14 up 28 min,  2 users,  load average: 0.05, 0.12, 0.13


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8162 Fast Ethernet [1969:1090] (rev 10)
    Subsystem: Lenovo Device [17aa:3979]
    Kernel driver in use: alx
02:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: Lenovo Device [17aa:3218]
    Kernel driver in use: ath9k


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 003: ID 5986:0295 Acer, Inc 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 006: ID 0cf3:3004 Atheros Communications, Inc. 
Bus 001 Device 003: ID 046d:c06c Logitech, Inc. Optical Mouse
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface                  Soft blocked  Hard blocked
0: ideapad_wlan: Wireless LAN        yes           no
1: ideapad_bluetooth: Bluetooth      no            no
2: phy0: Wireless LAN                yes           no
3: hci0: Bluetooth                   no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              630653  1 ath9k
cfg80211              484040  3 ath,ath9k,mac80211


module parameters ~~~~~~~~~~~~~~~~~~

ath9k         (5): blink=0 | bt_ant_diversity=0 | btcoex_enable=0 | nohwcrypt=0 | ps_enable=0
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
===================o=============o========o=============o=========o===========o==============o===========
 Interface & ID    | Type        | Driver | State       | Default | Speed     | Support      | HW Addr   
===================o=============o========o=============o=========o===========o==============o===========
 wlan0             | 802.11 WiFi | ath9k  | unavailable | no      |           | WEP/WPA/WPA2 | <MAC wlan0>
-------------------+-------------+--------+-------------+---------+-----------+--------------+-----------
 eth0  [Ethernet1] | Wired       | alx    | connected   | yes     | 100 Mb/s  |              | <MAC eth0>

    Address:         192.168.5.103
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.5.1
    DNS:             192.168.5.1
    DNS:             8.8.8.8
    DNS:             8.8.4.4
-------------------+-------------+--------+-------------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=false
WWANEnabled=true
WimaxEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~


OregonHome3          : ssid=OregonHome3 | autoconnect=false | ipv4=auto | ipv6=ignore 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1
search paul.local


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.5.1     0.0.0.0         UG    0      0        0 eth0
192.168.5.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

--- 192.168.5.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.488/0.516/0.545/0.036 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.053/0.058/0.064/0.009 ms


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



blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/libpisock9.conf]
blacklist visor


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

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


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x1969:0x1090 (alx)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:0x0032 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Not Default
/etc/rc.local       : Not Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modules]
loop

[/etc/rc.local]
/usr/local/bin/chkboot.sh&
echo deadline > /sys/block/sda/queue/scheduler
echo 1        > /sys/block/sda/queue/iosched/fifo_batch
iw reg set US
exit 0

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/vmlinuz-3.13.0-32-generic root=/dev/mapper/lubuntu--vg-root ro elevator=deadline


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    4.074108] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    4.074346] audit: initializing netlink socket (disabled)
[    4.369491] alx 0000:01:00.0 eth0: Qualcomm Atheros AR816x/AR817x Ethernet [<MAC eth0>]
[   18.300209] ath: phy0: Set BT/WLAN RX diversity capability
[   18.313412] ath: phy0: ASPM enabled: 0x42
[   18.313416] ath: EEPROM regdomain: 0x65
[   18.313417] ath: EEPROM indicates we should expect a direct regpair map
[   18.313420] ath: Country alpha2 being used: 00
[   18.313421] ath: Regpair used: 0x65
[   18.372142] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.880115] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

    ======== Done ========

```

---

### Post by Hadaka on 2014-08-08
Hi, from a wired connection please do.
```
sudo apt-get remove --purge resolvconf && sudo apt-get install --reinstall resolvconf

```
and please post the output of..
```
cat /etc/default/crda
```
thanks.

---

### Post by PaulBx on 2014-08-08
```

paul@len780:~$ cat /etc/default/crda
# Set REGDOMAIN to a ISO/IEC 3166-1 alpha2 country code so that iw(8) may set
# the initial regulatory domain setting for IEEE 802.11 devices which operate
# on this system.
#
# Governments assert the right to regulate usage of radio spectrum within
# their respective territories so make sure you select a ISO/IEC 3166-1 alpha2
# country code suitable for your location or you may infringe on local
# legislature. See `/usr/share/zoneinfo/zone.tab' for a table of timezone
# descriptions containing ISO/IEC 3166-1 alpha2 country codes.

REGDOMAIN=US
paul@len780:~$ 

```

Strangely, before your above suggestions I had tried to get wlan0 going with "ifconfig wlan0 up" and it came up, as far as ifconfig was concerned. I was trying to find out how to get an IP address from the command line when I saw your post and ran that command. Now, "ifconfig wlan0 up" doesn't work any more (sigh). It gives me 
SIOCSIFFLAGS: Operation not permitted
or, if I run it with sudo, 
SIOCSIFFLAGS: Operation not possible due to RF-kill

---

### Post by Hadaka on 2014-08-08
Hi, please do
```
sudo rfkill unblock all
```
and post the output of
```
cat /etc/resolv.conf
```
thanks.

---

### Post by jeremy31 on 2014-08-08
Have you tried toggling wifi with the keyboard hotkey when the Lenovo splash logo is on the display during boot?

Did the wifi work during install?

---

### Post by PaulBx on 2014-08-08
```

paul@len780:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search paul.local
nameserver 127.0.1.1
search paul.local
paul@len780:~$ 

```

> Have you tried toggling wifi with the keyboard hotkey when the Lenovo splash logo is on the display during boot?

No. I will give that a try though.

> Did the wifi work during install?

I wasn't paying attention to it since I was using ethernet then and had no reason to wonder if wireless had stopped working.

---

### Post by PaulBx on 2014-08-08
I just tried "sudo ifconfig wlan0 up" again and it worked:
```

paul@len780:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 20:89:84:8e:e6:8c  
          inet addr:192.168.5.103  Bcast:192.168.5.255  Mask:255.255.255.0
          inet6 addr: fe80::2289:84ff:fe8e:e68c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:8717 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8717 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:708568 (708.5 KB)  TX bytes:708568 (708.5 KB)

wlan0     Link encap:Ethernet  HWaddr 2c:d0:5a:c7:98:0f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

paul@len780:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

The only difference with the iwconfig is the Tx-Power is no longer zero. And in ifconfig, before doing this, wlan0 did not show up at all.

How does one get the IP address from the command line? A dhclient command, or something?

Still no other indications the wireless is alive...

---

### Post by jeremy31 on 2014-08-08
You might be able to use network manager now

---

### Post by PaulBx on 2014-08-08
No, when I click on the icon I still see the "Wi-Fi" section is still greyed out, whatever that means (this is so whether wlan0 is visible from "ifconfig" or not). Anyway "ifconfig" now shows no wlan0 again, so it must have dropped out again.

I wonder if the driver is different from what was in 13.10?

I had tried 14.04 when it first came out but gave up and went back. I can't recall, but maybe this is one of the reasons.

---

### Post by Hadaka on 2014-08-09
Hi, please do..
```
sudo apt-get remove --purge resolvconf
echo "nameserver 127.0.0.1" | sudo tee /etc/resolv.conf
```
thanks.

---

### Post by PaulBx on 2014-08-09
OK, I tried that and rebooted. Now my resolv.conf is:
```

paul@len780:~$ cat /etc/resolv.conf
# Generated by NetworkManager
domain paul.local
search paul.local
nameserver 127.0.1.1
paul@len780:~$ 

```

I wonder where those domain and search fields came from.

I found the cause of that SIOCSIFFLAGS error. If I do "rfkill list" and see some things locked, and attempt "sudo ifconfig wlan0 up", I get the error. If I remove the locks (e.g. via the switch), and attempt it, it goes through and I see wlan0 in "ifconfig". Also if I turn off the wireless switch, it goes away again, and I have to re-enter "sudo ifconfig wlan0 up" again to get it back. However, the wireless section in the Network Connections always remains greyed out, no matter what.

---

### Post by praseodym on 2014-08-10
Try to reset the BIOS and show

```
iwconfig
rfkill list
cat /var/lib/NetworkManager/NetworkManager.state
```

---

### Post by PaulBx on 2014-08-10
```

paul@len780:~$ iwconfig
eth0      no wireless extensions.

eth1      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
paul@len780:~$ rfkill list
0: ideapad_wlan: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
paul@len780:~$ cat /var/lib/NetworkManager/NetworkManager.state
[main]
NetworkingEnabled=true
WirelessEnabled=false
WWANEnabled=true
WimaxEnabled=true
paul@len780:~$ 

```

I used the non-Windows-specific bios load defaults. It wouldn't boot that way, saying "Ubuntu has been blocked by the current security policy" so I set the boot mode to "Legacy" and then it booted. I could again unblock the rfkill states with Fn-F5, and bring wlan0 up with the ifconfig command, but the network manager never shows the wireless as available.

The next step is usually to get an IP address, and I want to try that; can anyone give me the command line for that?

Another thing that occurs to me is the health of the upgrade. I did get a lot of those pixbuf errors that other people have reported, but I'm assuming they have nothing to do with wireless. Should I look for anything else in the upgrade logs?

---

### Post by praseodym on 2014-08-10
It only looks "soft blocked". Lets try
```

sudo rfkill unblock all
```

---

### Post by PaulBx on 2014-08-10
That does the same thing as Fn+F5. "rfkill list" shows everything unblocked in either case.

---

### Post by praseodym on 2014-08-10
Lets try it the "stupid" way:

```
gksudo gedit /var/lib/NetworkManager/NetworkManager.state
```
Change "false" to "true", save, close the editor and check the connection and/or Reboot

---

### Post by PaulBx on 2014-08-10
"Stupid" works! I'm now posting this via my wireless connection. ):P

I wonder how that got screwed up by the upgrade...

Thanks everyone, for your help and patience.

---

### Post by praseodym on 2014-08-10
Glad, it worked. Now, that was one "soft block", eh?! ;)

---

### Post by PaulBx on 2014-08-10
Now I'm thinking I was being stupid. It used to be that everything in Network Connections was accessed via a left click on the icon. I just noticed that the wireless enable is now accessed via a right click on that icon. ](*,)   You'd never guess I've been working on computers since 1969, and designed computer hardware for years...

Why would they change that? It's "improvements" like this that drive me nuts.

---

