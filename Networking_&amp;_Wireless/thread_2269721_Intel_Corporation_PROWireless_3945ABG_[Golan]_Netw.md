---
title: "Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection Problem"
date: 2015-03-17
forum: Networking &amp; Wireless
---

### Post by Sumzare on 2015-03-17
Hello friends ! I'm new here, and i'm asking You for help. I'm not so green with ubuntu but i started to have a problem and i can't resolve it myself.

 Today i took old laptop from my father-in-law just for work with coding in PHP. I imagine that this laptop will be enough for this task. It is old IBM ThinkPad Lenovo R60.

 But... When i erased brrr... MS XP and installed my lovely Ubuntu 14.04.2 LTS then i meet problem with WiFi connection. 

Firstable in right upper corner in network managment(i guess that is calls?) all WiFi options are blocked(grey) and says that WiFi is turned of. hmmm... in settings->network-> there is WiFi connection but i can't turn it on, it automatickly and quickly turning back to off and says that airplaine mode is ON .

 Then i started to looking resolve on this forum and others too. I won't say how long i was looking to solve that problem but it was so long that i have decide to post ask for help here. 
And "here is pearl!" when i used this commadns 
```

sudo modprobe -rv iwl3945
sudo modprobe -v iwl3945 swcrypto=1 

```

     ```

sudo modprobe -rv iwl3945
sudo modprobe -v iwlegacy bt_coex_active=N
sudo modprobe -v iwl3945 

```
from [**[COLOR=#DD4814][B]varunendra**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1043629") from this thread [http://ubuntuforums.org/showthread.php?t=2180049](http://ubuntuforums.org/showthread.php?t=2180049) 
then it magickly started to be visable. I mean when i used this then airplane mode turned off and WiFi was turned on but that's all ... sad isn't it ? No reaction, no searching only comunicate that device is not ready.

I'm asking You for help asap. Thanks for any answer!

I forgot! In bios all support for wifi, networks, usb etc. are enabled. And one importnant thing, i don't have any fn+something button to physically turn on WiFi adapter/card/network.

EDIT:
 After  
sudo modprobe -rv iwl3945
sudo modprobe -v iwl3945 swcrypto=1

on rfkill list all i have

1: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: yes
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

and when i use sudo wifi-radar i have :
wlan0     Interface doesn't support scanning : Network is down




 Here are information from varunendra script.

```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

IBM-R60 3.16.0-31-generic i686,  Ubuntu 14.04.2 LTS, trusty

CPU    : Genuine Intel(R) CPU           T2300  @ 1.66GHz
Memory : 1002 MB
Uptime : 20:00:49 up 3 min,  2 users,  load average: 0,61, 0,74, 0,34


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express [14e4:167d] (rev 21)
    Subsystem: Lenovo ThinkPad R60e [17aa:2081]
    Kernel driver in use: tg3
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4227] (rev 02)
    Subsystem: Intel Corporation ThinkPad T60/R60e/X60s [8086:1011]
    Kernel driver in use: iwl3945


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255


iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface                    Soft blocked  Hard blocked
0: phy0: Wireless LAN                  no            yes
1: tpacpi_bluetooth_sw: Bluetooth      no            yes


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

iwl3945                63639  0 
iwlegacy               87977  1 iwl3945
mac80211              559049  2 iwl3945,iwlegacy
cfg80211              418839  3 iwl3945,iwlegacy,mac80211


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
iwl3945       (4): antenna=0 | disable_hw_scan=1 | fw_restart=1 | swcrypto=0
iwlegacy      (2): bt_coex_active=Y | led_mode=0
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
=================================o=============o=========o=============o=========o===========o==============o===========
 Interface & ID                  | Type        | Driver  | State       | Default | Speed     | Support      | HW Addr   
=================================o=============o=========o=============o=========o===========o==============o===========
 wlan0                           | 802.11 WiFi | iwl3945 | unavailable | no      |           | WEP/WPA/WPA2 | <MAC wlan0>
---------------------------------+-------------+---------+-------------+---------+-----------+--------------+-----------
 eth0  [Po&#322;&#261;czenie przewodowe 1]| Wired       | tg3     | connected   | yes     | 100 Mb/s  |              | <MAC eth0>

    Address:         192.168.1.108
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             192.168.1.1
---------------------------------+-------------+---------+-------------+---------+-----------+--------------+-----------


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

Po&#322;&#261;czenie Wi-Fi 1 : ssid=TP-LINK | mac-address=<MAC ID removed> | ipv6=auto | ipv4=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1000ms
rtt min/avg/max/mdev = 0.265/0.271/0.277/0.006 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.037/0.043/0.049/0.006 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "pl_PL.UTF-8")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     32 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)
          Channel 34 (5.17 GHz)
          Channel 36 (5.18 GHz)
          Channel 38 (5.19 GHz)
          Channel 40 (5.2 GHz)
          Channel 42 (5.21 GHz)
          Channel 44 (5.22 GHz)
          Channel 46 (5.23 GHz)
          Channel 48 (5.24 GHz)
          Channel 52 (5.26 GHz)
          Channel 56 (5.28 GHz)
          Channel 60 (5.3 GHz)
          Channel 64 (5.32 GHz)
          Channel 100 (5.5 GHz)
          Channel 104 (5.52 GHz)
          Channel 108 (5.54 GHz)
          Channel 112 (5.56 GHz)
          Channel 116 (5.58 GHz)
          Channel 120 (5.6 GHz)
          Channel 124 (5.62 GHz) - 13 (2.472 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~



blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[iwl3945]
filename:       /lib/modules/3.16.0-31-generic/kernel/drivers/net/wireless/iwlegacy/iwl3945.ko
firmware:       iwlwifi-3945-2.ucode
version:        in-tree:s
srcversion:     74607945F172262E502CED2
depends:        iwlegacy,cfg80211,mac80211
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           swcrypto:using software crypto (default 1 [software]) (int)
parm:           disable_hw_scan:disable hardware scanning (default 1) (int)
parm:           fw_restart:restart firmware in case of error (int)

[iwlegacy]
filename:       /lib/modules/3.16.0-31-generic/kernel/drivers/net/wireless/iwlegacy/iwlegacy.ko
version:        in-tree:
srcversion:     1FA10C0B834AAF4AE219899
depends:        mac80211,cfg80211
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking (int)
parm:           bt_coex_active:enable wifi/bluetooth co-exist (bool)

[mac80211]
filename:       /lib/modules/3.16.0-31-generic/kernel/net/mac80211/mac80211.ko
srcversion:     D0CBADABD6F74A53B0BE7CC
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.16.0-31-generic/kernel/net/wireless/cfg80211.ko
srcversion:     88153DA7841870E4F2012EE
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x8086:0x4227 (iwl3945)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x14e4:0x167d (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modprobe.d]
iwl3945.conf      : options iwl3945 swcrypto=0
mlx4.conf         : softdep mlx4_core post: mlx4_en
modesetting.conf  : options cirrus modeset=1
                    options mgag200 modeset=1


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.16.0-31-generic root=UUID=8bee90d7-3ac7-4ff4-afb1-21aa88a1a7c0 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.036712] Initializing cgroup subsys net_cls
[    0.036739] Initializing cgroup subsys net_prio
[    0.834799] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.835471] audit: initializing netlink subsys (disabled)
[    2.216077] tg3 0000:02:00.0 eth0: attached PHY is 5750 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[    7.705770] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   19.262561] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   19.262566] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   19.262634] iwl3945 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[   19.316765] iwl3945 0000:03:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   19.316771] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   19.316844] iwl3945 0000:03:00.0: irq 46 for MSI/MSI-X
[   19.335807] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   19.401876] thinkpad_acpi: http://ibm-acpi.sf.net/
[   24.602909] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   30.784830] audit: type=1400 audit(1426618646.354:62): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1055 comm="nm-dhcp-client." lport=49256 family="inet" sock_type="dgram" protocol=17
[   30.784867] audit: type=1400 audit(1426618646.354:63): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1055 comm="nm-dhcp-client." lport=37205 family="inet6" sock_type="dgram" protocol=17
[   30.798482] audit: type=1400 audit(1426618646.366:64): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1056 comm="nm-dhcp-client." lport=49256 family="inet" sock_type="dgram" protocol=17
[   30.798499] audit: type=1400 audit(1426618646.366:65): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1056 comm="nm-dhcp-client." lport=37205 family="inet6" sock_type="dgram" protocol=17

    ======== Done ========


```

---

