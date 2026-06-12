---
title: "Rosewill RNX-N150UBE not working properly"
date: 2014-09-18
forum: Networking &amp; Wireless
---

### Post by Averyvh on 2014-09-18
Just installed Ubuntu on my new desktop a few days ago, but my wireless adapter has been way too slow. i tried googling a fix, but nothing has worked. My download speeds are stuck between 150 kbps and 50kbps and constantly jumping up and down. I tried ```
wget http://svn.debian.org/wsvn/kernel/dists/trunk/firmware-nonfree/realtek/RTL8192SU/rtl8192sfw.bin 
sudo mkdir /lib/firmware/RTL8192SU
sudo cp rtl8192sfw.bin /lib/firmware/RTL8192SU
```
but that didnt change anything. i tried getting the drivers from the Rosewill site, but when i try installing them (using the instructions in the .ppt file) i keep getting errors. 
Right now I have my moto g doing usb tethering just to get on the internet! 
Should I just send the wifi adapter back to newegg?

---

### Post by varunendra on 2014-09-20
Welcome to the forums Averyvh!

Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by Averyvh on 2014-09-21
```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

BlackPenguin 3.13.0-35-generic x86_64,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Celeron(R) CPU G1840 @ 2.80GHz
Memory : 3831 MB
Uptime : 21:54:09 up  6:36,  2 users,  load average: 0.52, 0.38, 0.22


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7817]
    Kernel driver in use: r8169


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 04d9:a067 Holtek Semiconductor, Inc. 
Bus 003 Device 002: ID 0bda:8171 Realtek Semiconductor Corp. RTL8188SU 802.11n WLAN Adapter
Bus 003 Device 004: ID 0461:4dbf Primax Electronics, Ltd 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:"TELUS3055"  Nickname:"rtl_wifi"
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC C-01 TELUS3055>   
          Bit Rate:72 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=71/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

r8712u                184158  0 
mxm_wmi                13021  0 
wmi                    19177  1 mxm_wmi


module parameters ~~~~~~~~~~~~~~~~~~

r8712u       (21): ampdu_enable=1 | busy_thresh=40 | cbw40_enable=1 | channel=1 | chip_version=2 | hci=1 | ht_enable=1 | ifname=wlan0 | initmac=(null) | lbkmode=0 | low_power=0 | mp_mode=0 | network_mode=0 | power_mgnt=0 | rf_config=1 | rfintfs=2 | vcs_type=1 | video_mode=1 | vrtl_carrier_sense=2 | wifi_test=0 | wmm_enable=0
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
====================o=============o========o=============o=========o===========o==============o===========
 Interface & ID     | Type        | Driver | State       | Default | Speed     | Support      | HW Addr   
====================o=============o========o=============o=========o===========o==============o===========
 eth0               | Wired       | r8169  | unavailable | no      |           |              | <MAC eth0>
--------------------+-------------+--------+-------------+---------+-----------+--------------+-----------
 wlan0  [TELUS3055] | 802.11 WiFi | r8712u | connected   | yes     | 72 Mb/s   | WEP/WPA/WPA2 | <MAC wlan0>

    *TELUS3055:      Infra, <MAC C-01 TELUS3055>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    Saunders:        Infra, <MAC C-NA Saunders 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2

    Address:         192.168.1.66
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254
    DNS:             192.168.1.254
    DNS:             75.153.176.1
--------------------+-------------+--------+-------------+---------+-----------+--------------+-----------


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

TELUS3055            : ssid=TELUS3055 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1
search telus


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

--- 192.168.1.254 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 1.992/2.163/2.335/0.177 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.023/0.031/0.039/0.008 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_CA.UTF-8")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     14 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 14 (2.484 GHz)

          Current Frequency:2.462 GHz (Channel 11)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 TELUS3055>
                    ESSID:"TELUS3055"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:wpa_ie=dd1c0050f20101000050f20202000050f2040050f20201000050f2020c00
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Signal level=100/100  


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

[mxm_wmi]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/platform/x86/mxm-wmi.ko
srcversion:     62CBD37DE87DF0C4CD7FBA3
depends:        wmi

[wmi]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8168 (r8169)
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

BOOT_IMAGE=/boot/vmlinuz-3.13.0-35-generic.efi.signed root=UUID=f5d27b7e-db26-4f6d-839b-40df4d29fb9c ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.385167] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.385375] audit: initializing netlink socket (disabled)
[    2.698057] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    9.923699] wmi: Mapper loaded
[   11.044143] r8712u: module is from the staging directory, the quality is unknown, you have been warned.
[   11.044614] r8712u: Staging version
[   11.044624] r8712u: register rtl8712_netdev_ops to netdev_ops
[   11.044627] usb 3-7: r8712u: USB_SPEED_HIGH with 4 endpoints
[   11.044932] usb 3-7: r8712u: Boot from EFUSE: Autoload OK
[   11.344152] usb 3-7: r8712u: CustomerID = 0x0000
[   11.344155] usb 3-7: r8712u: MAC Address from efuse = <MAC wlan0>
[   11.344157] usb 3-7: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[   12.847758] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   15.689798] r8712u 3-7:1.0 wlan0: 1 RCR=0x153f00e
[   15.690318] r8712u 3-7:1.0 wlan0: 2 RCR=0x553f00e
[   15.797744] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.797950] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.105963] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   36.852584] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   36.863210] r8712u 3-7:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-01 TELUS3055>, seq = 0, tid = 0
[   37.272922] r8712u 3-7:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-01 TELUS3055>, seq = 0, tid = 0
[   39.854358] r8712u 3-7:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-01 TELUS3055>, seq = 0, tid = 2
[ 1629.916536] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1650.403435] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1650.421611] r8712u 3-7:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-01 TELUS3055>, seq = 0, tid = 0
[ 1650.825785] r8712u 3-7:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-01 TELUS3055>, seq = 0, tid = 0
[ 1692.228429] r8712u 3-7:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-01 TELUS3055>, seq = 0, tid = 2
[13293.817914] r8712u 3-7:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-01 TELUS3055>, seq = 0, tid = 0
[13295.359976] r8712u 3-7:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-01 TELUS3055>, seq = 0, tid = 2
[16777.558525] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[22933.574971] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[22933.584944] r8712u 3-7:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-01 TELUS3055>, seq = 0, tid = 0
[23344.120465] r8712u 3-7:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-01 TELUS3055>, seq = 0, tid = 0
[23345.409176] r8712u 3-7:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-01 TELUS3055>, seq = 0, tid = 2
[23398.588810] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[23419.124794] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[23419.138508] r8712u 3-7:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-01 TELUS3055>, seq = 0, tid = 0
[23419.543112] r8712u 3-7:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-01 TELUS3055>, seq = 0, tid = 0
[23421.247817] r8712u 3-7:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-01 TELUS3055>, seq = 0, tid = 2
[23425.928771] r8712u 3-7:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-01 TELUS3055>, seq = 224, tid = 0

    ======== Done ========
```

---

### Post by varunendra on 2014-09-21
Please try changing the encryption type in your router to pure WPA2-PSK with AES (CCMP). It is currently using WPA/WPA2 mixed mode with TKIP which can cause performance issues. Reboot the router after saving the change > reconnect and let us know if it helps improving the speed and stability.

---

### Post by Averyvh on 2014-09-21
nope. no difference. My internet performance is fine on other devices; in fact, my internet speed is fine when I use my phone to tether.

---

### Post by varunendra on 2014-09-23
I don't think you can try much with this driver other than explicitly setting your country code for RegDomain settings or trying a newer kernel version.

To set the RegDomain code (assuming from your language settings that you are in Canada) -
```
sudo sed -i 's/^REG.*=$/&CA
sudo iw reg set CA
```

To try a newer kernel, you can install any of the "linux-lts..." packages from the default repositories, or manually download and install "linux-image-<version>-generic" and "linux-headers-<corresponding version>", "linux-headers-<corresponding version>-generic" packages from here : [http://archive.ubuntu.com/ubuntu/pool/main/l/linux/](http://archive.ubuntu.com/ubuntu/pool/main/l/linux/)

If these don't help, I guess it would be a good idea to replace the dongle with a better supported one.

---

### Post by Averyvh on 2014-09-24
thanks i'll return the adapter then.

---

