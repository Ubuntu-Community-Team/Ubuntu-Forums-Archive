---
title: "WiFi Problems"
date: 2014-08-28
forum: Networking &amp; Wireless
---

### Post by ntdyok on 2014-08-28
I can connect to my home WiFi network but I cannot access the internet on it. All of my other wireless devices are connecting okay. I am running Ubuntu 14.04 LTS. Thanks in advance.

---

### Post by Hadaka on 2014-08-28
Hi,please follow this link on how to create a wireless info printout
it will greatly help in finding your problem.
[http://ubuntuforums.org/showthread.php?p=13024222#post13024222](http://ubuntuforums.org/showthread.php?p=13024222#post13024222)
you might also ask a mod to move this to networks/wireless for quicker
resolution.
thanks

---

### Post by wildmanne39 on 2014-08-29
*Thread moved to **Networking & Wireless**.*

---

### Post by ntdyok on 2014-08-29
@[I]Hadaka
[/I]
```
    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


NTDyokLaptop 3.13.0-35-generic x86_64,  Ubuntu 14.04.1 LTS, trusty


CPU    : Intel(R) Pentium(R) CPU 2020M @ 2.40GHz
Memory : 3821 MB
Uptime : 16:56:03 up 5 min,  2 users,  load average: 0.81, 0.74, 0.36




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8162 Fast Ethernet [1969:1090] (rev 10)
    Subsystem: Lenovo Device [17aa:3979]
    Kernel driver in use: alx
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:051b]
    Kernel driver in use: wl




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 002 Device 003: ID 5986:0295 Acer, Inc 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     IEEE 802.11abg  ESSID:"TRENDnet639"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC C-01 TRENDnet639>   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          




rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


      Interface                  Soft blocked  Hard blocked
0: ideapad_wlan: Wireless LAN        no            no
1: ideapad_bluetooth: Bluetooth      no            no
2: phy0: Wireless LAN                no            no
3: brcmwl-0: Wireless LAN            no            no




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


wl                   4207846  0 
lib80211               14381  2 wl,lib80211_crypt_tkip
cfg80211              484040  1 wl




module parameters ~~~~~~~~~~~~~~~~~~


cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: connected (global)
=======================o=============o========o===========o=========o===========o==============o===========
 Interface & ID        | Type        | Driver | State     | Default | Speed     | Support      | HW Addr   
=======================o=============o========o===========o=========o===========o==============o===========
 wlan0  [TRENDnet639]  | 802.11 WiFi | wl     | connected | no      | 65 Mb/s   | WEP/WPA/WPA2 | <MAC wlan0>


    dlink:           Infra, <MAC C-02 dlink>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    *TRENDnet639:    Infra, <MAC C-01 TRENDnet639>, Freq 2462 MHz, Rate 54 Mb/s, Strength 62


    Address:         192.168.10.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.10.1
    DNS:             192.168.10.1
-----------------------+-------------+--------+-----------+---------+-----------+--------------+-----------
 eth0  [Auto Ethernet] | Wired       | alx    | connected | yes     | 100 Mb/s  |              | <MAC eth0>


    Address:         192.168.0.104
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1
    DNS:             192.168.0.1
-----------------------+-------------+--------+-----------+---------+-----------+--------------+-----------




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


no-auto-default=<MAC eth0>,


[ifupdown]
managed=false




NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~


TRENDnet639          : ssid=TRENDnet639 | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 




interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~


nameserver 127.0.1.1
search asqhsk.yourlink.ca




Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.10.0    0.0.0.0         255.255.255.0   U     9      0        0 wlan0


--- 192.168.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.480/0.515/0.550/0.035 ms


--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.030/0.035/0.041/0.008 ms




iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~


(Region : "en_CA.UTF-8")
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
          Channel 165 (5.825 GHz)


          Current Frequency:2.462 GHz (Channel 11)




iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 TRENDnet639>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:off
                    ESSID:"TRENDnet639"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 20ms ago
          Cell 02 - Address: <MAC C-02 dlink>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-34 dBm  
                    Encryption key:on
                    ESSID:"dlink"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 20ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK




blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[wl]
filename:       /lib/modules/3.13.0-35-generic/updates/dkms/wl.ko
srcversion:     FF25FE784DC6BDFF69DAFCB
depends:        cfg80211,lib80211
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string


[lib80211]
filename:       /lib/modules/3.13.0-35-generic/kernel/net/wireless/lib80211.ko
srcversion:     84DEF767F03D28E373F18E5
depends:        


[cfg80211]
filename:       /lib/modules/3.13.0-35-generic/kernel/net/wireless/cfg80211.ko
srcversion:     C2478077E22138832B71659
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)




udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~


# PCI device 0x1969:0x1090 (alx)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x14e4:0x4727 (brcmsmac)
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


BOOT_IMAGE=/vmlinuz-3.13.0-35-generic root=/dev/mapper/ubuntu--vg-root ro quiet splash vt.handoff=7




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    3.930853] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    3.931145] audit: initializing netlink socket (disabled)
[    4.352141] alx 0000:01:00.0 eth0: Qualcomm Atheros AR816x/AR817x Ethernet [<MAC eth0>]
[    5.402347] psmouse serio1: elantech: assuming hardware version 3 (with firmware version 0x450f02)
[   16.768925] wl: module license 'MIXED/Proprietary' taints kernel.
[   16.770663] wl: module verification failed: signature and/or  required key missing - tainting kernel
[   16.805961] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   16.968042] wlan0: Broadcom BCM4727 802.11 Hybrid Wireless Controller 6.30.223.141 (r415941)
[   20.201062] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  312.346103] ERROR @wl_dev_intvar_get : error (-1)
[  312.346110] ERROR @wl_cfg80211_get_tx_power : error (-1)


    ======== Done ========
```

Btw, sorry for the long response time.

---

### Post by westie457 on 2014-08-29
I claim no credit for this solution.
It has been copied from this post. [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)
```
sudo -i
echo "blacklist b43" >>  /etc/modprobe.d/blacklist.conf
echo "blacklist ssb" >>  /etc/modprobe.d/blacklist.conf
exit
```

---

### Post by ntdyok on 2014-08-29
@*westie457*

That didn't work :(

---

### Post by Hadaka on 2014-08-29
Hi, you have some odd looking ip addressing between your wired and wireless
please shut down your computer, then router, then of course turn the router
back up and then computer,,then do..
```
sudo apt-get update
sudo apt-get remove --purge bcmwl-kernel-source
sudo modprobe bcma
sudo modprobe brcmsmac
```
remove the ethernet cable and test

---

### Post by ntdyok on 2014-08-30
@*Hadaka*

Still nothing. I can connect to the WiFi network but I can't get any internet connectivity. :(

---

### Post by ntdyok on 2014-08-30
@*Hadaka*

Okay then... nevermind... I'm now getting internet connectivity. Thank you for helping me with this problem; it is very appreciated.

---

### Post by Hadaka on 2014-08-30
Glad you got it going !!
have fun.

---

