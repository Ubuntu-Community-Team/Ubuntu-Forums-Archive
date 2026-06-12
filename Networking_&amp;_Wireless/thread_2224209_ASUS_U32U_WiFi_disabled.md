---
title: "ASUS U32U WiFi disabled"
date: 2014-05-15
forum: Networking &amp; Wireless
---

### Post by Norbert_Szucs on 2014-05-15
Hi there, I just installed the latest version of **lubuntu** on my **asus u32u notebook** and the **wifi is not working**. The* FN+F2* is also not working. I mention that I had no problems with wifi connection while on win 8.1 or 7. 

I used *sudo lshw -C network. *Please help me out. Thank you.

*-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.2
       bus info: pci@0000:04:00.2
       logical name: eth0
       version: 0a
       serial: 50:46:5d:47:e3:a8
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8411-1_0.0.3 06/18/12 ip=192.168.0.107 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:44 ioport:e000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003fff
  *-network **DISABLED**
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 01
       serial: dc:85:de:25:7c:bd
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.13.0-24-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 memory:fe800000-fe80ffff

---

### Post by varunendra on 2014-05-15
Welcome to the forums Norbert_Szucs !

Please check out this thread to see if it is caused by a known bug : [http://ubuntuforums.org/showthread.php?t=2181558](http://ubuntuforums.org/showthread.php?t=2181558)

The current workaround is also suggested in the same post, if the problem is indeed what is mentioned there.

---

### Post by Norbert_Szucs on 2014-05-15
Thank you!

---

### Post by Norbert_Szucs on 2014-05-15
norbert@norbert-U32U:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

I managed to unblock it but how do I access a wireless connection now? No icon shows up near the watch or any wifi connections in the Preferences>Network Connections. What should I do next?

---

### Post by varunendra on 2014-05-15
**[SIZE=3]If you can connect to internet[/SIZE]** via cable or other means, please open a terminal (Ctrl-Alt-T) and run (copy-paste) the following code in it -
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \
chmod +x wireless-info && \
./wireless-info
```
It will automatically download and run the script, and generate a "wireless-info.txt" file in your home directory (or "wireless-info.txt.tar.gz" file, if the text file size exceeds 19.5 KB). Post back this report file (or its contents) here.

If posting the contents of the file, please use '**Code**' tags. Follow the "Use Code Tags" link in my signature below to see a quick guide with screenshots.

[SIZE=3]**If you have no way to connect the machine to internet**[/SIZE] while running Ubuntu, please manually download the script from **[this link]("https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info")** (right-click it > click "Save as"), then follow this link : [http://ubuntuforums.org/showthread.php?p=12350385#post12350385](http://ubuntuforums.org/showthread.php?p=12350385#post12350385) and use "Method 2" to run the script.

---

### Post by Norbert_Szucs on 2014-05-15
there you go:
```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

norbert-U32U 3.13.0-24-generic i686,  Ubuntu 14.04 LTS, trusty

CPU    : AMD E-450 APU with Radeon(tm) HD Graphics
Memory : 3629 MB
Uptime : 16:38:42 up 11 min,  2 users,  load average: 1,78, 1,28, 0,74


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

04:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0a)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1437]
    Kernel driver in use: r8169
--
06:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: AzureWave AW-NB037H 802.11bgn Wireless Half-size Mini PCIe Card [AR9002WB-1NGCD] [1a3b:2c37]
    Kernel driver in use: ath9k


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 13d3:5710 IMC Networks UVC VGA Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface               Soft blocked  Hard blocked
0: hci0: Bluetooth                no            no
1: phy0: Wireless LAN             no            yes
2: asus-wlan: Wireless LAN        no            no
3: asus-bluetooth: Bluetooth      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

asus_nb_wmi            16862  0 
asus_wmi               23495  1 asus_nb_wmi
sparse_keymap          13708  1 asus_wmi
ath9k                 144602  0 
ath9k_common           13359  1 ath9k
ath9k_hw              438205  2 ath9k_common,ath9k
ath                    23922  3 ath9k_common,ath9k,ath9k_hw
mac80211              545990  1 ath9k
cfg80211              409394  3 ath,ath9k,mac80211
wmi                    18673  1 asus_wmi
video                  18903  1 asus_wmi


module parameters ~~~~~~~~~~~~~~~~~~

asus_nb_wmi   (1): wapf=0
ath9k         (5): blink=0 | bt_ant_diversity=0 | btcoex_enable=0 | nohwcrypt=0 | ps_enable=0
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=-1
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
============================o=============o========o==============o=========o===========o==============o===========
 Interface & ID             | Type        | Driver | State        | Default | Speed     | Support      | HW Addr   
============================o=============o========o==============o=========o===========o==============o===========
 wlan0                      | 802.11 WiFi | ath9k  | unavailable  | no      |           | WEP/WPA/WPA2 | <MAC wlan0>
----------------------------+-------------+--------+--------------+---------+-----------+--------------+-----------
 eth0  [Wired connection 1] | Wired       | r8169  | connected    | yes     | 100 Mb/s  |              | <MAC eth0>

    Address:         192.168.0.107
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1
    DNS:             213.125.222.129
    DNS:             193.231.252.1
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


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

--- 192.168.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1000ms
rtt min/avg/max/mdev = 0.232/0.370/0.509/0.139 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.075/0.075/0.076/0.008 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : ro_RO.UTF-8)


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     14 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 14 (2.484 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~



blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/libpisock9.conf]
blacklist visor


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[ath9k]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
srcversion:     BAF225EEB618908380B28DA
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

[ath9k_common]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
srcversion:     696B00A6C59713EC0966997
depends:        ath,ath9k_hw

[ath9k_hw]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
srcversion:     4809F3842A0542CD6B556D3
depends:        ath

[ath]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/ath/ath.ko
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211

[mac80211]
filename:       /lib/modules/3.13.0-24-generic/kernel/net/mac80211/mac80211.ko
srcversion:     C0F95BBF832E05DEFD722F4
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-24-generic/kernel/net/wireless/cfg80211.ko
srcversion:     8B3D642D1F2E6406EF33F74
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


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
asus_nb_wmi.conf  : option asus_nb_wmi wapf=1
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=7f95190d-3484-405b-ab90-08d7c25f367b ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    1.764409] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.765063] audit: initializing netlink socket (disabled)
[    2.458472] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   12.527917] wmi: Mapper loaded
[   12.961093] ath: phy0: Set BT/WLAN RX diversity capability
[   13.028023] ath: EEPROM regdomain: 0x60
[   13.028031] ath: EEPROM indicates we should expect a direct regpair map
[   13.028036] ath: Country alpha2 being used: 00
[   13.028039] ath: Regpair used: 0x60
[   13.989220] asus_wmi: ASUS WMI generic driver loaded
[   13.996545] asus_wmi: Initialization: 0x1
[   13.996606] asus_wmi: BIOS WMI version: 7.6
[   13.996689] asus_wmi: SFUN value: 0xa0877
[   13.998045] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input15
[   14.136260] asus_wmi: Backlight controlled by ACPI video driver
[   14.899407] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.774114] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.774800] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  258.625316] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  329.192939] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  357.632607] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  375.374876] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

    ======== Done ========


```

---

### Post by Norbert_Szucs on 2014-05-15
phy0 keeps getting hard bloctked yet I don't know why.

---

### Post by varunendra on 2014-05-15
The conf file you created (following my first post) contains this line -
```
option asus_nb_wmi wapf=1
```
..which is wrong and will be ignored, hence why the option doesn't come into effect. The error is in the word '**option**', it should be '**option[COLOR="#FF0000"]s[/COLOR]**'

Please repeat this command in a terminal -
```
echo "options asus_nb_wmi wapf=1" | sudo tee /etc/modprobe.d/asus_nb_wmi.conf
```
It will overwrite the current file, creating correct entry this time. Check the entry with -
```
cat /etc/modprobe.d/asus_nb_wmi.conf
```
The output should be -
```
**option[COLOR="#FF0000"]s[/COLOR]** asus_nb_wmi wapf=1
```
If yes, reboot and let us know if the problem got solved or not.

---

### Post by Soren_van_Zorin on 2014-06-19
Hey man this is what I got (you replied to my Q here [http://ubuntuforums.org/showthread.php?t=2230061](http://ubuntuforums.org/showthread.php?t=2230061))

```
======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~




BroPC 3.11.0-23-generic i686,  Zorin OS 8, saucy




CPU    : AMD Athlon Dual-Core QL-62
Memory : 3776 MB
Uptime : 12:54:40 up 6 min,  2 users,  load average: 0.46, 0.49, 0.26








lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~




00:0a.0 Ethernet controller [0200]: NVIDIA Corporation MCP77 Ethernet [10de:0760] (rev a2)
    Subsystem: Hewlett-Packard Company Device [103c:360a]
    Kernel driver in use: forcedeth
--
07:00.0 Ethernet controller [0200]: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: Hewlett-Packard Company AR5BXB63 (Foxconn) 802.11bg Mini PCIe NIC [103c:137a]
    Kernel driver in use: ath5k








lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~




Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub








PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~












iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~




wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          








rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~




      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            no








lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~




hp_wmi                 13702  0 
sparse_keymap          13708  1 hp_wmi
ath5k                 135055  0 
ath                    19187  1 ath5k
mac80211              517482  1 ath5k
cfg80211              401762  3 ath,ath5k,mac80211
mxm_wmi                12893  1 nouveau
wmi                    18590  3 hp_wmi,mxm_wmi,nouveau








module parameters ~~~~~~~~~~~~~~~~~~




ath5k         (3): fastchanswitch=N | nohwcrypt=N | no_hw_rfkill_switch=N
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N








nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~




State: connected (global)
============================o=============o===========o==============o=========o===========o==============o===========
 Interface & ID             | Type        | Driver    | State        | Default | Speed     | Support      | HW Addr   
============================o=============o===========o==============o=========o===========o==============o===========
 wlan0                      | 802.11 WiFi | ath5k     | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>
----------------------------+-------------+-----------+--------------+---------+-----------+--------------+-----------
 eth0  [Wired connection 1] | Wired       | forcedeth | connected    | yes     | 100 Mb/s  |              | <MAC eth0>




    Address:         192.168.1.11
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             192.168.1.1
----------------------------+-------------+-----------+--------------+---------+-----------+--------------+-----------








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
search Home








Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~




Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0




--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.374/0.415/0.457/0.046 ms




--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.050/0.053/0.057/0.008 ms








iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~




(Region : "en_US.UTF-8")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS








iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~




wlan0     11 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 11 (2.462 GHz)








iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~




wlan0     No scan results








blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~




[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci








modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~




[ath5k]
filename:       /lib/modules/3.11.0-23-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
srcversion:     68167C5D7C0F1F5FF5D8D62
depends:        mac80211,cfg80211,ath
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)




[ath]
filename:       /lib/modules/3.11.0-23-generic/kernel/drivers/net/wireless/ath/ath.ko
srcversion:     A890CDBC88E6EF28CD751DD
depends:        cfg80211




[mac80211]
filename:       /lib/modules/3.11.0-23-generic/kernel/net/mac80211/mac80211.ko
srcversion:     839D52631DD36C78B3B909C
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)




[cfg80211]
filename:       /lib/modules/3.11.0-23-generic/kernel/net/wireless/cfg80211.ko
srcversion:     A9AE06A9BEF1DAB62A8C8ED
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)








udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~




# PCI device 0x10de:0x0760 (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"




# PCI device 0x168c:0x001c (ath5k)
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




BOOT_IMAGE=/boot/vmlinuz-3.11.0-23-generic root=UUID=65a10b57-4cf7-4d97-8ac2-2bf523ed5fcd ro quiet splash vt.handoff=7








dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~




[    0.977548] audit: initializing netlink socket (disabled)
[    1.644118] wmi: Mapper loaded
[    1.663340] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[   27.280351] ath5k 0000:07:00.0: can't disable ASPM; OS doesn't have ASPM control
[   27.280497] ath5k 0000:07:00.0: registered as 'phy0'
[   27.297903] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   27.973225] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   28.228783] ath: EEPROM regdomain: 0x64
[   28.228791] ath: EEPROM indicates we should expect a direct regpair map
[   28.228795] ath: Country alpha2 being used: 00
[   28.228797] ath: Regpair used: 0x64
[   28.258627] ath5k: phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   29.827779] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.831178] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready




    ======== Done ========
```

---

### Post by varunendra on 2014-06-20
> **Soren_van_Zorin said:**
> Hey man this is what I got (you replied to my Q here [http://ubuntuforums.org/showthread.php?t=2230061](http://ubuntuforums.org/showthread.php?t=2230061))

Replied in your original thread. I had noticed your post yesterday, but the problem was a bit strange to me and I had no quick suggestions to try. I still have no solid clues to work on, so please try what I suggested in your thread, and report back there. We'll continue the troubleshooting in your own thread, but I can't promise quick responses since I don't get much time these days.

---

### Post by mmcl26554 on 2014-08-16
> **varunendra said:**
> **[SIZE=3]If you can connect to internet[/SIZE]** via cable or other means, please open a terminal (Ctrl-Alt-T) and run (copy-paste) the following code in it -
```
wget -N -t 5 -T 10 https://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will automatically download and run the script, and generate a "wireless-info.txt" file in your home directory (or "wireless-info.txt.tar.gz" file, if the text file size exceeds 19.5 KB). Post back this report file (or its contents) here.

If posting the contents of the file, please use '**Code**' tags. Follow the "Use Code Tags" link in my signature below to see a quick guide with screenshots.

[SIZE=3]**If you have no way to connect the machine to internet**[/SIZE] while running Ubuntu, please manually download the script from **[this link]("https://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script")** (right-click it > click "Save as"), then follow this link : [http://ubuntuforums.org/showthread.php?p=12350385#post12350385](http://ubuntuforums.org/showthread.php?p=12350385#post12350385) and use "Method 2" to run the script (the one downloaded from here, not the one linked in that post, as this new one gives much more info).


[COLOR=#FF0000]**EDIT:**[/COLOR]
Due to a bug in the script, the generated .txt file is sometimes blank. If that happens to you, try once more using the GUI method. If the generated file is still blank, try the original, simpler script mentioned in the original [post=12350385]instructions post[/post].

--
OK here is the file!
Michael

---

### Post by praseodym on 2014-08-17
Any button, switch, key? Try
```

echo "options hp_wmi wireless=1" | sudo tee /etc/modprobe.d/hp.conf
```
Reboot and check
```

rfkill list
sudo rfkill unblock all
rfkill list
```
Alternatively, try to reset the BIOS

---

