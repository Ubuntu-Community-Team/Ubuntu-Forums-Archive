---
title: "Wifi is connected but I am uble to ping."
date: 2014-08-13
forum: Networking &amp; Wireless
---

### Post by xcieo on 2014-08-13
I installed Ubuntu Latest and connected to wifi during Installation. After Installation i tried to open the Web but i failed. The other laptop with same Ubuntu and installed from same Bootable USB is connected to same router, and it's WIFI is working properly.
```
root@xcieo:~# ping 8.8.8.8 -c5
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
From 192.168.0.102 icmp_seq=1 Destination Host Unreachable
From 192.168.0.102 icmp_seq=2 Destination Host Unreachable
From 192.168.0.102 icmp_seq=3 Destination Host Unreachable
From 192.168.0.102 icmp_seq=4 Destination Host Unreachable
From 192.168.0.102 icmp_seq=5 Destination Host Unreachable

--- 8.8.8.8 ping statistics ---
5 packets transmitted, 0 received, +5 errors, 100% packet loss, time 4000ms
pipe 4

```

```
root@xcieo:~# iwconfig
wlan1     IEEE 802.11abg  ESSID:"Xcieo"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: 64:66:B3:CF:86:B2   
          Bit Rate=72 Mb/s   Tx-Power=200 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=70/70  Signal level=-20 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth1      no wireless extensions.

lo        no wireless extensions.

```

```
root@xcieo:~# ifconfig
eth1      Link encap:Ethernet  HWaddr 24:b6:fd:19:2b:1c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:453 errors:0 dropped:0 overruns:0 frame:0
          TX packets:453 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:35385 (35.3 KB)  TX bytes:35385 (35.3 KB)

wlan1     Link encap:Ethernet  HWaddr e4:d5:3d:f1:b6:b5  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::e6d5:3dff:fef1:b6b5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:32
          TX packets:168 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1789 (1.7 KB)  TX bytes:15165 (15.1 KB)
          Interrupt:19 

```

---

### Post by nerdtron on 2014-08-13
What is the output of "route -n"

---

### Post by xcieo on 2014-08-13
```
root@xcieo:~# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan1
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan1
```

---

### Post by nerdtron on 2014-08-13
Can you ping the gateway?
ping 192.168.0.1

---

### Post by xcieo on 2014-08-13
No

```
root@xcieo:~# ping 192.168.0.1 -c5
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
From 192.168.0.102 icmp_seq=1 Destination Host Unreachable
From 192.168.0.102 icmp_seq=2 Destination Host Unreachable
From 192.168.0.102 icmp_seq=3 Destination Host Unreachable
From 192.168.0.102 icmp_seq=4 Destination Host Unreachable
From 192.168.0.102 icmp_seq=5 Destination Host Unreachable

--- 192.168.0.1 ping statistics ---
5 packets transmitted, 0 received, +5 errors, 100% packet loss, time 4025ms
pipe 3

```

---

### Post by nerdtron on 2014-08-13
Routing table is fine but you can't even ping the router? Hmmm this is odd.
Can you ping other IP addresses on your LAN? Do you have ACL on the router?

Found a thread very similar to yours [http://ubuntuforums.org/showthread.php?t=2143634](http://ubuntuforums.org/showthread.php?t=2143634)
This one is wired: [http://ubuntuforums.org/showthread.php?t=1414306](http://ubuntuforums.org/showthread.php?t=1414306)

---

### Post by xcieo on 2014-08-13
No i can not ping on other IP Addresses. Yes I have ACL on router.

---

### Post by nerdtron on 2014-08-13
> **xcieo said:**
> No i can not ping on other IP Addresses. Yes I have ACL on router.

Try disabling the ACLs on the router first. This may not be Ubuntu related.

Did you enable/modified the firewall on the Ubuntu?

---

### Post by xcieo on 2014-08-13
No I did'nt did anything after installing Ubuntu.

---

### Post by xcieo on 2014-08-13
Disabling ACL did'nt worked. Will Reinstalling Ubuntu work for me?

---

### Post by varunendra on 2014-08-13
Can you show us a detailed report of your wifi setup please? Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

And does wifi work on a Live Session?

As a wild shot, please try -
```
sudo iwconfig wlan0 power off
```

---

### Post by xcieo on 2014-08-14
Report :

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

xcieo 3.13.0-32-generic x86_64,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Pentium(R) CPU B950 @ 2.10GHz
Memory : 1843 MB
Uptime : 08:54:29 up 29 min,  2 users,  load average: 0.13, 0.12, 0.14


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Dell Device [1028:0502]
    Kernel driver in use: r8169
09:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Dell Device [1028:0012]
    Kernel driver in use: wl


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0bda:58c1 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 0a5c:21bc Broadcom Corp. BCM2070 Bluetooth 2.1 + EDR
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan1     IEEE 802.11abg  ESSID:"Xcieo"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC C-01 Xcieo>   
          Bit Rate=72 Mb/s   Tx-Power=200 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=70/70  Signal level=-37 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface            Soft blocked  Hard blocked
0: hci0: Bluetooth             no            no
1: phy0: Wireless LAN          no            no
2: brcmwl-0: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

dell_wmi               12761  0 
sparse_keymap          13948  1 dell_wmi
wl                   4207846  0 
lib80211               14381  2 wl,lib80211_crypt_tkip
cfg80211              484040  1 wl
wmi                    19177  1 dell_wmi


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
================o=============o========o=============o=========o===========o==============o===========
 Interface & ID | Type        | Driver | State       | Default | Speed     | Support      | HW Addr   
================o=============o========o=============o=========o===========o==============o===========
 wlan1  [Xcieo] | 802.11 WiFi | wl     | connected   | yes     | 72 Mb/s   | WEP/WPA/WPA2 | <MAC wlan1>

    *Xcieo:          Infra, <MAC C-01 Xcieo>, Freq 2412 MHz, Rate 54 Mb/s, Strength 83 WPA2

    Address:         192.168.0.102
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1
    DNS:             192.168.0.1
----------------+-------------+--------+-------------+---------+-----------+--------------+-----------
 eth1           | Wired       | r8169  | unavailable | no      | 100 Mb/s  |              | <MAC eth1>
----------------+-------------+--------+-------------+---------+-----------+--------------+-----------


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

no-auto-default=<MAC eth1>,

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~

Xcieo                : ssid=Xcieo | mac-address=<MAC wlan1> | ipv4=auto | ipv6=auto 
Xcieo 1              : ssid=Xcieo | mac-address=<MAC wlan1> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan1
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan1

--- 192.168.0.1 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2015ms
pipe 3

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.034/0.050/0.066/0.016 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : ur_PK)
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan1     26 channels in total; available frequencies :
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

          Current Frequency:2.412 GHz (Channel 1)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan1     Scan completed :
          Cell 01 - Address: <MAC C-01 Xcieo>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-39 dBm  
                    Encryption key:on
                    ESSID:"Xcieo"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 60ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
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

[dell_wmi]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/platform/x86/dell-wmi.ko
srcversion:     0ED3A43A5709CF19B7DFD19
depends:        wmi,sparse-keymap

[wl]
filename:       /lib/modules/3.13.0-32-generic/updates/dkms/wl.ko
srcversion:     FF25FE784DC6BDFF69DAFCB
depends:        cfg80211,lib80211
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

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

[wmi]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x1814:0x539a (rt2800pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth1>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# PCI device 0x14e4:0x4727 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan1>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


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

BOOT_IMAGE=/boot/vmlinuz-3.13.0-32-generic root=UUID=1a378205-5117-41fb-a55d-4e950ef061f5 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    1.417201] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.417823] audit: initializing netlink socket (disabled)
[    2.068162] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   18.064321] wmi: Mapper loaded
[   18.173020] systemd-udevd[300]: renamed network interface eth0 to eth1
[   18.273314] wl: module license 'MIXED/Proprietary' taints kernel.
[   18.280128] wl: module verification failed: signature and/or  required key missing - tainting kernel
[   18.434540] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   18.524829] wlan0: Broadcom BCM4727 802.11 Hybrid Wireless Controller 6.30.223.141 (r415941)
[   19.851422] systemd-udevd[306]: renamed network interface wlan0 to wlan1
[   21.262351] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   22.693806] r8169 0000:05:00.0 eth1: link down
[   22.693880] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   22.694824] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[  170.776157] r8169 0000:05:00.0 eth1: link up
[  170.776179] IPv6: ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 1747.400092] r8169 0000:05:00.0 eth1: link down
[ 1752.236166] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready

    ======== Done ========

---

### Post by varunendra on 2014-08-14
Please open a terminal (Ctrl-Alt-T) and run the following code -
```
sudo apt-get purge bcmwl-kernel-source
```
Then reboot. Can you connect and browse now?

---

### Post by xcieo on 2014-08-14
Thanks it helped me.

---

### Post by varunendra on 2014-08-14
It always does, (for this particular device), Congratulations! :D

Just make sure not to install the proprietary driver ("wl", also called the "STA" driver, package name "bcmwl-kernel-source") again. It (the proprietary driver) is the same one that is offered by the "Additional Drivers" program - a wrong offer in this case.

---

