---
title: "DWA-131 Problems when offline"
date: 2014-08-26
forum: Networking &amp; Wireless
---

### Post by db60462 on 2014-08-26
I am running Ubuntu 14.04 kernel 3.13.0-34 on older Compaq machine with a D-Link DWA-131 wireless USB which comes up and works fine.  But if I want to go offline, I do the "Disconnect"  from the wireless icon.   If an hour or so goes by and want to reconnect my network name is gone.   I have used the system settings/Network and shows my network name but I can't do anything to it.   Have run commands to try and restart like "sudo ifup -v wlan0" , "sudo /etc/init.d/networking restart" and others I found in the forum and tried just logout, but it takes a reboot to bring back.  When its down, I can't get the LED on the device to relight up.   I loaded the new driver from REALTEK

---

### Post by varunendra on 2014-08-27
I see that you have been registered long ago, but since it seems your first post here, Welcome to the Forums! :)

To give us a detailed report about your wireless chip/driver and other related stuff, please follow the instructions in this post to download and run 'wireless_script' (experimental version) when the adapter is plugged in but not working, and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by db60462 on 2014-08-27
Got the script and will run next time it fails.   I was at IBM and worked in AIX/UNIX and retired 8 years ago.  Am getting back into UNIX/LINUX now and trying to reteach myself. I have been able to get most problems solved, but this is bugging me.  Thanks

---

### Post by db60462 on 2014-08-31
Here is the output from the script when the wifi was done

```

    ======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


bob-sr1762nx 3.13.0-35-generic i686,  Ubuntu 14.04.1 LTS, trusty


CPU    : AMD Athlon(tm) 64 Processor 3400+
Memory : 2458 MB
Uptime : 18:58:42 up 11:18,  2 users,  load average: 0.28, 0.41, 0.22




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless [11ab:1faa] (rev 03)
    Subsystem: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless [11ab:1faa]
02:01.0 Communication controller [0780]: LSI Corporation Lucent V.92 Data/Fax Modem [11c1:0620]
--
02:03.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [10ec:8139] (rev 10)
    Subsystem: Hewlett-Packard Company Device [103c:2a24]
    Kernel driver in use: 8139too




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 001 Device 003: ID 07d1:3303 D-Link System DWA-131 802.11n Wireless N Nano Adapter(rev.A1) [Realtek RTL8192SU]
Bus 001 Device 002: ID 04f9:0281 Brother Industries, Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     unassociated  Nickname:"rtl_wifi"
          Mode:Managed  Access Point: Not-Associated   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0






rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~








lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


r8712u                158706  0 




module parameters ~~~~~~~~~~~~~~~~~~


r8712u       (21): ampdu_enable=1 | busy_thresh=40 | cbw40_enable=1 | channel=1 | chip_version=2 | hci=1 | ht_enable=1 | ifname=wlan0 | initmac=(null) | lbkmode=0 | low_power=0 | mp_mode=0 | network_mode=0 | power_mgnt=0 | rf_config=1 | rfintfs=2 | vcs_type=1 | video_mode=1 | vrtl_carrier_sense=2 | wifi_test=0 | wmm_enable=0




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: disconnected
================o=============o=========o==============o=========o===========o==============o===========
 Interface & ID | Type        | Driver  | State        | Default | Speed     | Support      | HW Addr   
================o=============o=========o==============o=========o===========o==============o===========
 eth0           | Wired       | 8139too | unavailable  | no      |           |              | <MAC eth0>
----------------+-------------+---------+--------------+---------+-----------+--------------+-----------
 wlan0          | 802.11 WiFi | r8712u  | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>
----------------+-------------+---------+--------------+---------+-----------+--------------+-----------




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


2WIRE990             : ssid=2WIRE990 | permissions=user:rdsully49:; | bssid=<MAC ID removed> | mac-address=<MAC wlan0> | ipv4=auto | ipv6=dhcp 
xfinitywifi          : ssid=xfinitywifi | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 




interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~






Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface




iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~


(Region : "en_US.UTF-8")
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


[r8712u]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/staging/rtl8712/r8712u.ko
firmware:       rtlwifi/rtl8712u.bin
srcversion:     5A7B13CC2FA1D2F4B5820F9
depends:        
parm:           wifi_test:int
parm:           video_mode:int
parm:           chip_version:int
parm:           rfintfs:int
parm:           lbkmode:int
parm:           hci:int
parm:           network_mode:int
parm:           channel:int
parm:           mp_mode:int
parm:           wmm_enable:int
parm:           vrtl_carrier_sense:int
parm:           vcs_type:int
parm:           busy_thresh:int
parm:           ht_enable:int
parm:           cbw40_enable:int
parm:           ampdu_enable:int
parm:           rf_config:int
parm:           power_mgnt:int
parm:           low_power:int
parm:           ifname: Net interface name, wlan%d=default (string)
parm:           initmac:MAC-Address, default: use FUSE (charp)




udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~


# PCI device 0x10ec:0x8139 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# USB device 0x:0x (r8712u)
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


BOOT_IMAGE=/boot/vmlinuz-3.13.0-35-generic root=UUID=7faecc57-362d-48d0-b0d1-d18c23f91b5b ro quiet splash vt.handoff=7




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    0.570510] audit: initializing netlink socket (disabled)
[    1.181289] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    1.202288] 8139too: 8139too Fast Ethernet driver 0.9.28
[   24.183937] r8712u: module is from the staging directory, the quality is unknown, you have been warned.
[   24.311142] r8712u: Staging version
[   24.311173] r8712u: register rtl8712_netdev_ops to netdev_ops
[   24.311179] usb 1-2: r8712u: USB_SPEED_HIGH with 4 endpoints
[   24.315526] usb 1-2: r8712u: Boot from EFUSE: Autoload OK
[   25.001595] usb 1-2: r8712u: CustomerID = 0x0000
[   25.001601] usb 1-2: r8712u: MAC Address from efuse = <MAC wlan0>
[   25.001605] usb 1-2: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[   32.562194] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   37.088462] r8712u 1-2:1.0 wlan0: 1 RCR=0x153f00e
[   37.089202] r8712u 1-2:1.0 wlan0: 2 RCR=0x553f00e
[   37.196390] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   37.196749] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   37.504308] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  224.056478] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  228.819991] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:00:80:92:93:e2:cd:08:00 SRC=192.168.1.13 DST=224.0.0.251 LEN=32 TOS=0x0A PREC=0xE0 TTL=1 ID=2917 PROTO=2 
[  344.284671] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:3c:ea:4f:5c:81:59:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=19985 PROTO=2 
[  353.064472] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:00:80:92:93:e2:cd:08:00 SRC=192.168.1.13 DST=224.0.0.251 LEN=32 TOS=0x0A PREC=0xE0 TTL=1 ID=2921 PROTO=2 
[  469.288730] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:3c:ea:4f:5c:81:59:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=57842 PROTO=2 
[  477.080551] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:00:80:92:93:e2:cd:08:00 SRC=192.168.1.13 DST=224.0.0.251 LEN=32 TOS=0x0A PREC=0xE0 TTL=1 ID=2922 PROTO=2 
[  594.291821] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:3c:ea:4f:5c:81:59:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=22785 PROTO=2 
[  719.294862] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:3c:ea:4f:5c:81:59:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=64421 PROTO=2 
[  726.689719] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:00:80:92:93:e2:cd:08:00 SRC=192.168.1.13 DST=224.0.0.251 LEN=32 TOS=0x0A PREC=0xE0 TTL=1 ID=2927 PROTO=2 
[  844.299923] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:3c:ea:4f:5c:81:59:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=13466 PROTO=2 
[  969.303103] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:3c:ea:4f:5c:81:59:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=52322 PROTO=2 
[  974.132133] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:00:80:92:93:e2:cd:08:00 SRC=192.168.1.13 DST=224.0.0.251 LEN=32 TOS=0x0A PREC=0xE0 TTL=1 ID=2932 PROTO=2 
[ 1094.308288] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:3c:ea:4f:5c:81:59:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=22746 PROTO=2 
[ 1096.849380] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:00:80:92:93:e2:cd:08:00 SRC=192.168.1.13 DST=224.0.0.251 LEN=32 TOS=0x0A PREC=0xE0 TTL=1 ID=2936 PROTO=2 
[ 1219.312140] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:3c:ea:4f:5c:81:59:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=2394 PROTO=2 
[ 1223.706368] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:00:80:92:93:e2:cd:08:00 SRC=192.168.1.13 DST=224.0.0.251 LEN=32 TOS=0x0A PREC=0xE0 TTL=1 ID=2939 PROTO=2 
[ 1344.315378] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:3c:ea:4f:5c:81:59:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=8866 PROTO=2 
[ 1347.219505] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:00:80:92:93:e2:cd:08:00 SRC=192.168.1.13 DST=224.0.0.251 LEN=32 TOS=0x0A PREC=0xE0 TTL=1 ID=2940 PROTO=2 
[ 1469.319203] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:3c:ea:4f:5c:81:59:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=9893 PROTO=2 
[ 1472.320732] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:00:80:92:93:e2:cd:08:00 SRC=192.168.1.13 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=2952 PROTO=2 
[12520.589940] r8712u 1-2:1.0 wlan0: Suspending...
[12520.589941] r8712u 1-2:1.0 wlan0: Unable to suspend
[12521.095384] r8712u 1-2:1.0 wlan0: Resuming...
[12521.095386] r8712u 1-2:1.0 wlan0: Unable to resume
[12528.276386] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[12528.319985] r8712u 1-2:1.0 wlan0: In r8711_wx_set_scan: bDriverStopped=1
[12528.321612] r8712u 1-2:1.0 wlan0: In r8711_wx_set_scan: bDriverStopped=1
[12552.005308] r8712u 1-2:1.0 wlan0: In r8711_wx_set_scan: bDriverStopped=1
[12585.002932] r8712u 1-2:1.0 wlan0: In r8711_wx_set_scan: bDriverStopped=1
[12628.003836] r8712u 1-2:1.0 wlan0: In r8711_wx_set_scan: bDriverStopped=1
[12681.003098] r8712u 1-2:1.0 wlan0: In r8711_wx_set_scan: bDriverStopped=1
[12744.005459] r8712u 1-2:1.0 wlan0: In r8711_wx_set_scan: bDriverStopped=1
[12769.704723] r8712u 1-2:1.0 wlan0: In r8711_wx_set_scan: bDriverStopped=1


    ======== Done ========
```

---

### Post by varunendra on 2014-09-02
Please edit your above post to wrap the output part within 'Code' tags as I requested in my first post. Please see that post or the link in my signature.

And for now, please try this -
```
sudo modprobe -rv r8712u
sudo modprobe -v r8712u power_mgnt=1
```
The first command will remove the driver, the second one will reload it with parameter "power_mgnt=1". This will be a temporary change that will be lost at next boot. If it helps, we can make it permanent.

---

### Post by db60462 on 2014-09-03
Tried both the modprobe commands and it showed it was connected but unable to get to the internet or ping my router. Also tried "sudo /etc/init.d/dbus restart" and "sudo /etc/init.d/networking restart" and nothing, had to reboot.  Here is latest wireless-tool file

```
 

	======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~
bob-sr1762nx 3.13.0-35-generic i686,  Ubuntu 14.04.1 LTS, trusty


CPU    : AMD Athlon(tm) 64 Processor 3400+
Memory : 2458 MB
Uptime : 15:16:33 up 43 min,  2 users,  load average: 1.16, 1.70, 1.65


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless [11ab:1faa] (rev 03)
	Subsystem: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless [11ab:1faa]
02:01.0 Communication controller [0780]: LSI Corporation Lucent V.92 Data/Fax Modem [11c1:0620]
--
02:03.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [10ec:8139] (rev 10)
	Subsystem: Hewlett-Packard Company Device [103c:2a24]
	Kernel driver in use: 8139too


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 001 Device 003: ID 07d1:3303 D-Link System DWA-131 802.11n Wireless N Nano Adapter(rev.A1) [Realtek RTL8192SU]
Bus 001 Device 002: ID 04f9:0281 Brother Industries, Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~


iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~
wlan0     IEEE 802.11bg  ESSID:"2WIRE990"  Nickname:"rtl_wifi"
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC C-01 2WIRE990>   
          Bit Rate:54 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:100  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0




rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


r8712u                158706  0 




module parameters ~~~~~~~~~~~~~~~~~~


r8712u       (21): ampdu_enable=1 | busy_thresh=40 | cbw40_enable=1 | channel=1 | chip_version=2 | hci=1 | ht_enable=1 | ifname=wlan0 | initmac=(null) | lbkmode=0 | low_power=0 | mp_mode=0 | network_mode=0 | power_mgnt=1 | rf_config=1 | rfintfs=2 | vcs_type=1 | video_mode=1 | vrtl_carrier_sense=2 | wifi_test=0 | wmm_enable=0




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: connected (global)
===================o=============o=========o=============o=========o===========o==============o===========
 Interface & ID    | Type        | Driver  | State       | Default | Speed     | Support      | HW Addr   
===================o=============o=========o=============o=========o===========o==============o===========
 wlan0  [2WIRE990] | 802.11 WiFi | r8712u  | connected   | yes     | 54 Mb/s   | WEP/WPA/WPA2 | <MAC wlan0>


    HOME-50D2:       Infra, <MAC C-NA HOME-50D2 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 26 WPA WPA2
    *2WIRE990:       Infra, <MAC C-01 2WIRE990>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2


    Address:         192.168.1.6
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254
    DNS:             192.168.1.254
-------------------+-------------+---------+-------------+---------+-----------+--------------+-----------
 eth0              | Wired       | 8139too | unavailable | no      |           |              | <MAC eth0>
-------------------+-------------+---------+-------------+---------+-----------+--------------+-----------




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


2WIRE990             : ssid=2WIRE990 | permissions=user:rdsully49:; | bssid=<MAC C-01 2WIRE990> | mac-address=<MAC wlan0> | ipv4=auto | ipv6=dhcp 
xfinitywifi          : ssid=xfinitywifi | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~


nameserver 127.0.1.1
search attlocal.net




Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


--- 192.168.1.254 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2016ms
pipe 3


--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.062/0.067/0.072/0.005 ms




iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~


(Region : "en_US.UTF-8")
country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     14 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 14 (2.484 GHz)


          Current Frequency=2.412 GHz (Channel 1)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 2WIRE990>
                    ESSID:"2WIRE990"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2040050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Signal level=72/100  




blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[r8712u]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/staging/rtl8712/r8712u.ko
firmware:       rtlwifi/rtl8712u.bin
srcversion:     5A7B13CC2FA1D2F4B5820F9
depends:        
parm:           wifi_test:int
parm:           video_mode:int
parm:           chip_version:int
parm:           rfintfs:int
parm:           lbkmode:int
parm:           hci:int
parm:           network_mode:int
parm:           channel:int
parm:           mp_mode:int
parm:           wmm_enable:int
parm:           vrtl_carrier_sense:int
parm:           vcs_type:int
parm:           busy_thresh:int
parm:           ht_enable:int
parm:           cbw40_enable:int
parm:           ampdu_enable:int
parm:           rf_config:int
parm:           power_mgnt:int
parm:           low_power:int
parm:           ifname: Net interface name, wlan%d=default (string)
parm:           initmac:MAC-Address, default: use FUSE (charp)




udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~


# PCI device 0x10ec:0x8139 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# USB device 0x:0x (r8712u)
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


BOOT_IMAGE=/boot/vmlinuz-3.13.0-35-generic root=UUID=7faecc57-362d-48d0-b0d1-d18c23f91b5b ro quiet splash vt.handoff=7




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    0.578472] audit: initializing netlink socket (disabled)
[    1.194467] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    1.215556] 8139too: 8139too Fast Ethernet driver 0.9.28
[   23.577090] r8712u: module is from the staging directory, the quality is unknown, you have been warned.
[   23.607371] r8712u: Staging version
[   23.607396] r8712u: register rtl8712_netdev_ops to netdev_ops
[   23.607402] usb 1-2: r8712u: USB_SPEED_HIGH with 4 endpoints
[   23.610259] usb 1-2: r8712u: Boot from EFUSE: Autoload OK
[   24.278834] usb 1-2: r8712u: CustomerID = 0x0000
[   24.278841] usb 1-2: r8712u: MAC Address from efuse = <MAC wlan0>
[   24.278844] usb 1-2: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[   31.850933] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   36.224557] r8712u 1-2:1.0 wlan0: 1 RCR=0x153f00e
[   36.225298] r8712u 1-2:1.0 wlan0: 2 RCR=0x553f00e
[   36.332371] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   36.332745] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   36.640406] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  124.027213] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  245.191768] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:<MAC C-01 2WIRE990>:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=15138 PROTO=2 
[  249.295540] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:00:80:92:93:e2:cd:08:00 SRC=192.168.1.13 DST=224.0.0.251 LEN=32 TOS=0x0A PREC=0xE0 TTL=1 ID=8548 PROTO=2 
[  370.195610] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:<MAC C-01 2WIRE990>:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=63538 PROTO=2 
[  372.209727] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:00:80:92:93:e2:cd:08:00 SRC=192.168.1.13 DST=224.0.0.251 LEN=32 TOS=0x0A PREC=0xE0 TTL=1 ID=8550 PROTO=2 
[  495.199489] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:<MAC C-01 2WIRE990>:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=7690 PROTO=2 
[  501.826036] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:00:80:92:93:e2:cd:08:00 SRC=192.168.1.13 DST=224.0.0.251 LEN=32 TOS=0x0A PREC=0xE0 TTL=1 ID=8554 PROTO=2 
[  620.201955] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:<MAC C-01 2WIRE990>:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=44202 PROTO=2 
[  624.743189] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:00:80:92:93:e2:cd:08:00 SRC=192.168.1.13 DST=224.0.0.251 LEN=32 TOS=0x0A PREC=0xE0 TTL=1 ID=8556 PROTO=2 
[  745.205600] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:<MAC C-01 2WIRE990>:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=42002 PROTO=2 
[  746.949089] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:00:80:92:93:e2:cd:08:00 SRC=192.168.1.13 DST=224.0.0.251 LEN=32 TOS=0x0A PREC=0xE0 TTL=1 ID=8558 PROTO=2 
[  870.209289] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:<MAC C-01 2WIRE990>:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=1090 PROTO=2 
[  879.303030] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:00:80:92:93:e2:cd:08:00 SRC=192.168.1.13 DST=224.0.0.251 LEN=32 TOS=0x0A PREC=0xE0 TTL=1 ID=8560 PROTO=2 
[  995.212104] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:<MAC C-01 2WIRE990>:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=52538 PROTO=2 
[ 1003.170308] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:00:80:92:93:e2:cd:08:00 SRC=192.168.1.13 DST=224.0.0.251 LEN=32 TOS=0x0A PREC=0xE0 TTL=1 ID=8563 PROTO=2 
[ 1120.215774] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:<MAC C-01 2WIRE990>:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=65274 PROTO=2 
[ 1126.075309] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:00:80:92:93:e2:cd:08:00 SRC=192.168.1.13 DST=224.0.0.251 LEN=32 TOS=0x0A PREC=0xE0 TTL=1 ID=8565 PROTO=2 
[ 1245.219489] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:<MAC C-01 2WIRE990>:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=39298 PROTO=2 
[ 1246.238984] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:00:80:92:93:e2:cd:08:00 SRC=192.168.1.13 DST=224.0.0.251 LEN=32 TOS=0x0A PREC=0xE0 TTL=1 ID=8566 PROTO=2 
[ 1370.222290] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:<MAC C-01 2WIRE990>:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=40146 PROTO=2 
[ 1370.245764] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:00:80:92:93:e2:cd:08:00 SRC=192.168.1.13 DST=224.0.0.251 LEN=32 TOS=0x0A PREC=0xE0 TTL=1 ID=8568 PROTO=2 
[ 1495.226194] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:<MAC C-01 2WIRE990>:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=2282 PROTO=2 
[ 1502.822476] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:00:80:92:93:e2:cd:08:00 SRC=192.168.1.13 DST=224.0.0.251 LEN=32 TOS=0x0A PREC=0xE0 TTL=1 ID=8572 PROTO=2 
[ 1620.229254] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:<MAC C-01 2WIRE990>:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=56778 PROTO=2 
[ 1628.910564] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:00:80:92:93:e2:cd:08:00 SRC=192.168.1.13 DST=224.0.0.251 LEN=32 TOS=0x0A PREC=0xE0 TTL=1 ID=8576 PROTO=2 
[ 1745.232209] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:<MAC C-01 2WIRE990>:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=7026 PROTO=2 
[ 1750.268846] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:00:80:92:93:e2:cd:08:00 SRC=192.168.1.13 DST=224.0.0.251 LEN=32 TOS=0x0A PREC=0xE0 TTL=1 ID=8579 PROTO=2 
[ 1870.236387] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:<MAC C-01 2WIRE990>:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=56901 PROTO=2 
[ 1877.525854] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:00:80:92:93:e2:cd:08:00 SRC=192.168.1.13 DST=224.0.0.251 LEN=32 TOS=0x0A PREC=0xE0 TTL=1 ID=8581 PROTO=2 
[ 1995.240953] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:<MAC C-01 2WIRE990>:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=53530 PROTO=2 
[ 1997.660011] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:00:80:92:93:e2:cd:08:00 SRC=192.168.1.13 DST=224.0.0.251 LEN=32 TOS=0x0A PREC=0xE0 TTL=1 ID=8582 PROTO=2 
[ 2120.244373] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:<MAC C-01 2WIRE990>:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=39858 PROTO=2 
[ 2122.444297] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:00:80:92:93:e2:cd:08:00 SRC=192.168.1.13 DST=224.0.0.251 LEN=32 TOS=0x0A PREC=0xE0 TTL=1 ID=8584 PROTO=2 
[ 2245.247915] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:<MAC C-01 2WIRE990>:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=45313 PROTO=2 
[ 2249.797417] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:00:80:92:93:e2:cd:08:00 SRC=192.168.1.13 DST=224.0.0.251 LEN=32 TOS=0x0A PREC=0xE0 TTL=1 ID=8588 PROTO=2 
[ 2311.910723] r8712u 1-2:1.0 wlan0: r8712u: pipe error: (-108)
[ 2311.910730] r8712u 1-2:1.0 wlan0: xmit_bh => bDriverStopped or bSurpriseRemoved
[ 2344.289543] r8712u: module is from the staging directory, the quality is unknown, you have been warned.
[ 2344.297350] r8712u: Staging version
[ 2344.297380] r8712u: register rtl8712_netdev_ops to netdev_ops
[ 2344.297387] usb 1-2: r8712u: USB_SPEED_HIGH with 4 endpoints
[ 2344.299692] usb 1-2: r8712u: Boot from EFUSE: Autoload OK
[ 2345.043785] usb 1-2: r8712u: CustomerID = 0x0000
[ 2345.043798] usb 1-2: r8712u: MAC Address from efuse = <MAC wlan0>
[ 2345.043804] usb 1-2: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[ 2345.792513] r8712u 1-2:1.0 wlan0: 1 RCR=0x153f00e
[ 2345.793257] r8712u 1-2:1.0 wlan0: 2 RCR=0x553f00e
[ 2345.900351] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2345.901233] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2346.208391] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2356.831776] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2370.251235] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:<MAC C-01 2WIRE990>:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=7717 PROTO=2 


	======== Done ========

```

---

### Post by varunendra on 2014-09-03
I don't understand those UFW messages very well, but could you try temporarily disabling UFW and see if you can connect now?
```
sudo ufw disable
```

And the router/Access-Point you are trying to connect to is using WPA/WPA2 mixed mode encryption with TKIP. Please change it to pure WPA2 with AES (CCMP). No mixed mode, no TKIP. Reboot the router after saving the change.

---

### Post by db60462 on 2014-09-07
I've changed the settings in the router but have not had a chance to reboot it.   However I am running a dual boot with the other disc being Linux Mint 16 with Cinnamon (also 32bit) and no problems   "uname -a" shows 3.11.0-12-generic #19-Ubuntu.  Any thoughts on what is different?

---

### Post by varunendra on 2014-09-10
> **db60462 said:**
> "uname -a" shows 3.11.0-12-generic #19-Ubuntu.  Any thoughts on what is different?

I think you already picked up the major difference above. Your wireless-info report shows the kernel version to be 3.13.0-35-generic for Ubuntu. Newer *should* be better, but unfortunately sometimes it is not.

Of course the possibility of the problem being something else can't be denied either. Did you try turning UFW off? Do you get the same UFW block messages in Mint also (in 'dmesg' command output)?

---

### Post by db60462 on 2014-10-28
Update:   I upgraded my other drive from Mint 16 (3.11 kernel) to Mint 17 with a 3.13.0-24-generic #46-Ubuntu SMP kernel and had the same problem with the wifi not reconnecting after being turned off for an extended period.   Noticed in the error logs about a hostname problem, searched and did a "sudo apt-get install nss-hostname" and no more problems.  I can go to the wifi icon, click on connect to hidden networks, use the dropdown and find my wifi and click connect and it comes right back up, no problems.   Hope this helps.

---

