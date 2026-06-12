---
title: "Wireless extremely weak Toshiba laptop"
date: 2014-09-25
forum: Networking &amp; Wireless
---

### Post by jtmcc on 2014-09-25
Man, it's been a while since I was last on here.

Hello. My school laptop has been replaced and I can finally install Ubuntu on the old one. I loaded on 14.04 and it works beautifully, except for one problem. My wireless connection is very weak, occasionally not picking up any signal at all. I have updated all the kernel headers like I saw suggested in one post, and it did increase signal strength a little bit, but everything is still very slow and unreliable. Any help with this matter would be greatly appreciated. Full name is Toshiba Satellite L775-S7355. I am not at the PC right now, but I can edit with the card name if required. I do know it is a Realtek card.

---

### Post by varunendra on 2014-09-26
Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by jtmcc on 2014-09-27
Sorry for the late reply, I forgot to subsccribe to email updates. Here is the output:

```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

alternative-Satellite-L775 3.13.0-24-generic x86_64,  Ubuntu 14.04 LTS, trusty

CPU    : Intel(R) Core(TM) i5-2430M CPU @ 2.40GHz
Memory : 5879 MB
Uptime : 10:33:29 up 10 min,  2 users,  load average: 1.03, 0.96, 0.59


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8182]
    Kernel driver in use: rtl8192ce
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Toshiba America Info Systems Device [1179:fc66]
    Kernel driver in use: r8169


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 003: ID 047d:2048 Kensington Orbit Trackball with Scroll Ring
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:"Belkin.4EE4"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC C-01 Belkin.4EE4>   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

rtl8192ce              53550  0 
rtl_pci                26690  1 rtl8192ce
rtlwifi                63475  2 rtl_pci,rtl8192ce
rtl8192c_common        53172  1 rtl8192ce
mac80211              626489  3 rtl_pci,rtlwifi,rtl8192ce
cfg80211              484040  2 mac80211,rtlwifi
wmi                    19177  0 


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
rtl8192ce     (5): debug=0 | fwlps=Y | ips=Y | swenc=N | swlps=N
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
======================o=============o===========o=============o=========o===========o==============o===========
 Interface & ID       | Type        | Driver    | State       | Default | Speed     | Support      | HW Addr   
======================o=============o===========o=============o=========o===========o==============o===========
 eth0                 | Wired       | r8169     | unavailable | no      |           |              | <MAC eth0>
----------------------+-------------+-----------+-------------+---------+-----------+--------------+-----------
 wlan0  [Belkin.4EE4] | 802.11 WiFi | rtl8192ce | connected   | yes     | 150 Mb/s  | WEP/WPA/WPA2 | <MAC wlan0>

    *Belkin.4EE4:    Infra, <MAC C-01 Belkin.4EE4>, Freq 2412 MHz, Rate 54 Mb/s, Strength 76

    Address:         192.168.2.86
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1
    DNS:             192.168.2.1
----------------------+-------------+-----------+-------------+---------+-----------+--------------+-----------


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

att wifi             : ssid=att wifi | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Belkin.4EE4          : ssid=Belkin.4EE4 | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Tuckwiller           : ssid=Tuckwiller | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
wf                   : ssid=wf | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
wf 1                 : ssid=wf | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1
search Belkin


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0
192.168.2.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

--- 192.168.2.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 1.080/1.090/1.100/0.010 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.018/0.020/0.022/0.002 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)

          Current Frequency:2.412 GHz (Channel 1)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 Belkin.4EE4>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:off
                    ESSID:"Belkin.4EE4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005660c504a2
                    Extra: Last beacon: 4ms ago


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[rtl8192ce]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfwU_B.bin
firmware:       rtlwifi/rtl8192cfwU.bin
firmware:       rtlwifi/rtl8192cfw.bin
srcversion:     BF8278DF19B67D7D6C6B8C5
depends:        rtlwifi,rtl_pci,rtl8192c-common,mac80211
parm:           swenc:Set to 1 for software crypto (default 0)
parm:           ips:Set to 0 to not use link power save (default 1)
parm:           swlps:Set to 1 to use SW control power save (default 0)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl_pci]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
srcversion:     B6B8AA929B5F982954A6DE1
depends:        mac80211,rtlwifi

[rtlwifi]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
srcversion:     C21FC2F90947540319DE390
depends:        mac80211,cfg80211

[rtl8192c_common]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
srcversion:     32F826C623BC49F764F7974
depends:        

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

[wmi]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:0x8176 (rtl8192ce)
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

BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=d7863164-1b45-4ddf-922a-bc5417433dab ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    1.109883] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.110419] audit: initializing netlink socket (disabled)
[    1.351676] wmi: Mapper loaded
[    1.371391] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   10.939906] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[   11.433361] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   11.433606] rtlwifi: wireless switch is on
[   12.777070] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   14.013744] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.014179] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.111515] wlan0: authenticate with <MAC C-01 Belkin.4EE4>
[   15.128093] wlan0: send auth to <MAC C-01 Belkin.4EE4> (try 1/3)
[   15.130345] wlan0: authenticated
[   15.131686] wlan0: associate with <MAC C-01 Belkin.4EE4> (try 1/3)
[   15.134985] wlan0: RX AssocResp from <MAC C-01 Belkin.4EE4> (capab=0x401 status=0 aid=1)
[   15.135127] wlan0: associated
[   15.135134] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

    ======== Done ========
```

If it changes anything, I did this on wireless right next to the router, not ethernet.

---

### Post by varunendra on 2014-09-27
Please try this -
```
echo "options rtl8192ce fwlps=N ips=N" | sudo tee /etc/modprobe.d/rtl8192ce.conf
```
Reboot for the change to take effect (reloading the driver on running system should also work). Does it improve connectivity? If not, please generate a fresh report when it is having problem in connecting, and post back that one.

---

### Post by jtmcc on 2014-09-27
Ok, so now it says I can (apparently) get signal a bit farther than I could. I still cannot get full signal right next to the router (3 out of 4 bars on the wireless indicator in the status bar), and with only 2 or 1 bars, I cannot load a web page. When I rebooted, I accidently booted into windows 7, so I double checked and I could go out of the building without loosing a bar and browse extremely fast like usual. When I reran the script, I was in a place with 1 bar of signal and could not load a webpage.

```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

alternative-Satellite-L775 3.13.0-24-generic x86_64,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Core(TM) i5-2430M CPU @ 2.40GHz
Memory : 5879 MB
Uptime : 12:50:18 up 6 min,  2 users,  load average: 1.48, 1.18, 0.59


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8182]
    Kernel driver in use: rtl8192ce
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Toshiba America Info Systems Device [1179:fc66]
    Kernel driver in use: r8169


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 004: ID 12d1:1038 Huawei Technologies Co., Ltd. Ideos (debug mode)
Bus 002 Device 003: ID 047d:2048 Kensington Orbit Trackball with Scroll Ring
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:"Belkin.4EE4"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC C-01 Belkin.4EE4>   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=30/70  Signal level=-80 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:197   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

rtl8192ce              53550  0 
rtl_pci                26690  1 rtl8192ce
rtlwifi                63475  2 rtl_pci,rtl8192ce
rtl8192c_common        53172  1 rtl8192ce
mac80211              626489  3 rtl_pci,rtlwifi,rtl8192ce
cfg80211              484040  2 mac80211,rtlwifi
wmi                    19177  0 


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
rtl8192ce     (5): debug=0 | fwlps=N | ips=N | swenc=N | swlps=N
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
======================o=============o===========o=============o=========o===========o==============o===========
 Interface & ID       | Type        | Driver    | State       | Default | Speed     | Support      | HW Addr   
======================o=============o===========o=============o=========o===========o==============o===========
 eth0                 | Wired       | r8169     | unavailable | no      |           |              | <MAC eth0>
----------------------+-------------+-----------+-------------+---------+-----------+--------------+-----------
 wlan0  [Belkin.4EE4] | 802.11 WiFi | rtl8192ce | connected   | yes     | 150 Mb/s  | WEP/WPA/WPA2 | <MAC wlan0>

    *Belkin.4EE4:    Infra, <MAC C-01 Belkin.4EE4>, Freq 2412 MHz, Rate 54 Mb/s, Strength 40

    Address:         192.168.2.86
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1
    DNS:             192.168.2.1
----------------------+-------------+-----------+-------------+---------+-----------+--------------+-----------


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

att wifi             : ssid=att wifi | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Belkin.4EE4          : ssid=Belkin.4EE4 | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Tuckwiller           : ssid=Tuckwiller | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
wf                   : ssid=wf | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
wf 1                 : ssid=wf | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1
search Belkin


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0
192.168.2.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

--- 192.168.2.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 4.191/98.747/193.304/94.557 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.018/0.020/0.023/0.005 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)

          Current Frequency:2.412 GHz (Channel 1)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 Belkin.4EE4>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:off
                    ESSID:"Belkin.4EE4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005844f8d80d
                    Extra: Last beacon: 128ms ago


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[rtl8192ce]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfwU_B.bin
firmware:       rtlwifi/rtl8192cfwU.bin
firmware:       rtlwifi/rtl8192cfw.bin
srcversion:     BF8278DF19B67D7D6C6B8C5
depends:        rtlwifi,rtl_pci,rtl8192c-common,mac80211
parm:           swenc:Set to 1 for software crypto (default 0)
parm:           ips:Set to 0 to not use link power save (default 1)
parm:           swlps:Set to 1 to use SW control power save (default 0)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl_pci]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
srcversion:     B6B8AA929B5F982954A6DE1
depends:        mac80211,rtlwifi

[rtlwifi]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
srcversion:     C21FC2F90947540319DE390
depends:        mac80211,cfg80211

[rtl8192c_common]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
srcversion:     32F826C623BC49F764F7974
depends:        

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

[wmi]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:0x8176 (rtl8192ce)
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
rtl8192ce.conf    : options rtl8192ce fwlps=N ips=N


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=d7863164-1b45-4ddf-922a-bc5417433dab ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    1.111381] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.111901] audit: initializing netlink socket (disabled)
[    1.351375] wmi: Mapper loaded
[    1.370411] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    8.925930] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    8.963132] rtl8192ce: rtl8192ce: Power Save off (module option)
[    8.963136] rtl8192ce: rtl8192ce: FW Power Save off (module option)
[    8.963143] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[    9.099336] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    9.099547] rtlwifi: wireless switch is on
[   14.985899] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.986222] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.025701] wlan0: authenticate with <MAC C-01 Belkin.4EE4>
[   17.045764] wlan0: send auth to <MAC C-01 Belkin.4EE4> (try 1/3)
[   17.047234] wlan0: authenticated
[   17.049356] wlan0: associate with <MAC C-01 Belkin.4EE4> (try 1/3)
[   17.052672] wlan0: RX AssocResp from <MAC C-01 Belkin.4EE4> (capab=0x401 status=0 aid=2)
[   17.052749] wlan0: associated
[   17.052766] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

    ======== Done ========
```

---

### Post by varunendra on 2014-09-28
Please just update your system first. The current kernel version in Trusty is 3.13.0-36 I think, and the driver in it is also obviously newer. May have bug-fixes if there is any, causing the low signal.

If not, and the signal and behaviour remains the same even after the update, just confirm that and we may then try an even newer backported driver.

To update the system, do it either via the GUI "Update Manager", or via commands -
```
sudo apt-get update
sudo apt-get dist-upgrade
```

To confirm you kernel version after update -
```
uname -r
```

---

### Post by jtmcc on 2014-09-29
I'll be damned. I thought I was completely updated, but apparently not. I now have full signal everywhere again. Thank you.

---

### Post by varunendra on 2014-10-01
Glad the updates fixed it automatically. Thanks for letting us know that. :)

---

