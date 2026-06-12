---
title: "Belkin Wireless adapter stops working when put under load"
date: 2014-08-02
forum: Networking &amp; Wireless
---

### Post by terrykiwi83 on 2014-08-02
This is more of an observation at the moment, only happens on occasions.

Basically if I put the wireless adapter under load (such as downloading a debian ISO, and Ubuntu ISO plus a game download on Steam), usually around 8.7MBps download speed when all combined (I have a 100Mbit Fibre Internet Connection) the adapter suddenly stops working. The internet stops, the downloads all drop down to 0 and I have to pull out the adapter and plug it back in again for it to work. Unusual?

I am running Ubuntu 14.04 x64.

Any suggestions on where to go from here would be appreciated :)

```

Bus 002 Device 007: ID 050d:845a Belkin Components F7D2101 802.11n Surf & Share Wireless Adapter v1000 [Realtek RTL8192SU]

```

---

### Post by varunendra on 2014-08-04
Yes it's "usual", but a "usual problem" with some realtek chips. Not sure if RTL8192SU is any different in this regard.

For more hints, you might wish to try the wireless_script. I suggest the experimental version since it gives more info than the regular one mentioned in the sticky of the "Networking & Wireless" section. This is the post with instructions : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

### Post by terrykiwi83 on 2014-08-09
Have run that script, attached is output. Still having the problem. Wireless drops out whenever I download anything. :(

```


    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

hades 3.13.0-24-generic x86_64,  Ubuntu 14.04, trusty

CPU    : Intel(R) Core(TM) i7-3770 CPU @ 3.40GHz
Memory : 14994 MB
Uptime : 07:59:54 up 17:59,  2 users,  load average: 0.12, 0.26, 0.34


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

05:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:e000]
    Kernel driver in use: atl1c


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 006: ID 050d:845a Belkin Components F7D2101 802.11n Surf & Share Wireless Adapter v1000 [Realtek RTL8192SU]
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 004: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 005 Device 010: ID 0c45:62e0 Microdia MSI Starcam Racer
Bus 005 Device 002: ID 2109:0811  
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 04f9:003f Brother Industries, Ltd 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:"HOGWARTS"  Nickname:"rtl_wifi"
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC C-01 HOGWARTS>   
          Bit Rate:150 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=98/100  Noise level=0/100
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
========================o=============o========o=============o=========o===========o==============o===========
 Interface & ID         | Type        | Driver | State       | Default | Speed     | Support      | HW Addr   
========================o=============o========o=============o=========o===========o==============o===========
 wlan0  [Auto HOGWARTS] | 802.11 WiFi | r8712u | connected   | yes     | 150 Mb/s  | WEP/WPA/WPA2 | <MAC wlan0>

    *HOGWARTS:       Infra, <MAC C-01 HOGWARTS>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2

    Address:         10.1.1.10
    Prefix:          32 (255.255.255.255)
    Gateway:         10.1.1.1
    DNS:             10.1.1.1
------------------------+-------------+--------+-------------+---------+-----------+--------------+-----------
 eth0                   | Wired       | atl1c  | unavailable | no      |           |              | <MAC eth0>
------------------------+-------------+--------+-------------+---------+-----------+--------------+-----------


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

Auto HOGWARTS        : ssid=HOGWARTS | mac-address=<MAC wlan0> | ipv4=manual | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.1.1.1        0.0.0.0         UG    0      0        0 wlan0
10.1.1.1        0.0.0.0         255.255.255.255 UH    0      0        0 wlan0

--- 10.1.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 1.366/2.666/3.966/1.300 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.019/0.020/0.021/0.001 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_NZ.UTF-8")
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
          Cell 01 - Address: <MAC C-01 HOGWARTS>
                    ESSID:"HOGWARTS"
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
          Cell 02 - Address: <MAC C-02 thenaughtyneighbours>
                    ESSID:"thenaughtyneighbours"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Extra:wpa_ie=dd160050f20101000050f20201000050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Signal level=44/100  


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[r8712u]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/staging/rtl8712/r8712u.ko
firmware:       rtlwifi/rtl8712u.bin
srcversion:     607999565FE22A6079602D8
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
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/platform/x86/mxm-wmi.ko
srcversion:     62CBD37DE87DF0C4CD7FBA3
depends:        wmi

[wmi]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x1969:0x1083 (atl1c)
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

BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=a5cccc12-c70e-4e00-a784-bb0bee254ce0 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.583468] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.583676] audit: initializing netlink socket (disabled)
[    0.906034] wmi: Mapper loaded
[   24.999652] r8712u: module is from the staging directory, the quality is unknown, you have been warned.
[   25.000003] r8712u: Staging version
[   25.000010] r8712u: register rtl8712_netdev_ops to netdev_ops
[   25.000012] usb 2-1.5: r8712u: USB_SPEED_HIGH with 4 endpoints
[   25.000512] usb 2-1.5: r8712u: Boot from EFUSE: Autoload OK
[   25.398793] usb 2-1.5: r8712u: CustomerID = 0x0000
[   25.398795] usb 2-1.5: r8712u: MAC Address from efuse = <MAC wlan0>
[   25.398797] usb 2-1.5: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[   25.902145] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   27.122225] r8712u 2-1.5:1.0 wlan0: 1 RCR=0x153f00e
[   27.123167] r8712u 2-1.5:1.0 wlan0: 2 RCR=0x553f00e
[   27.230241] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   27.232306] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   27.542227] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   38.019893] r8712u 2-1.5:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-01 HOGWARTS>, seq = 0, tid = 0
[   38.019924] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  727.269315] r8712u 2-1.5:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-01 HOGWARTS>, seq = 14080, tid = 0
[ 1306.249830] r8712u 2-1.5:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-01 HOGWARTS>, seq = 19424, tid = 0
[ 1545.232348] r8712u 2-1.5:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-01 HOGWARTS>, seq = 49696, tid = 0
[ 5621.251353] r8712u 2-1.5:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-01 HOGWARTS>, seq = 0, tid = 5
[ 5937.008867] r8712u: Staging version
[ 5937.008883] r8712u: register rtl8712_netdev_ops to netdev_ops
[ 5937.008887] usb 2-1.5: r8712u: USB_SPEED_HIGH with 4 endpoints
[ 5937.009371] usb 2-1.5: r8712u: Boot from EFUSE: Autoload OK
[ 5937.644382] usb 2-1.5: r8712u: CustomerID = 0x0000
[ 5937.644388] usb 2-1.5: r8712u: MAC Address from efuse = <MAC wlan0>
[ 5937.644391] usb 2-1.5: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[ 5938.378124] r8712u 2-1.5:1.0 wlan0: 1 RCR=0x153f00e
[ 5938.378876] r8712u 2-1.5:1.0 wlan0: 2 RCR=0x553f00e
[ 5938.486113] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5938.489260] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5938.798247] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5959.198048] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 5959.209289] r8712u 2-1.5:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-01 HOGWARTS>, seq = 0, tid = 0
[ 5959.671974] r8712u 2-1.5:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-01 HOGWARTS>, seq = 0, tid = 0
[ 5959.756756] r8712u 2-1.5:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-01 HOGWARTS>, seq = 0, tid = 5
[ 6617.474580] r8712u 2-1.5:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-01 HOGWARTS>, seq = 65008, tid = 0
[ 6776.102589] r8712u: Staging version
[ 6776.102599] r8712u: register rtl8712_netdev_ops to netdev_ops
[ 6776.102602] usb 2-1.5: r8712u: USB_SPEED_HIGH with 4 endpoints
[ 6776.103061] usb 2-1.5: r8712u: Boot from EFUSE: Autoload OK
[ 6776.598491] usb 2-1.5: r8712u: CustomerID = 0x0000
[ 6776.598494] usb 2-1.5: r8712u: MAC Address from efuse = <MAC wlan0>
[ 6776.598496] usb 2-1.5: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[ 6777.315772] r8712u 2-1.5:1.0 wlan0: 1 RCR=0x153f00e
[ 6777.316667] r8712u 2-1.5:1.0 wlan0: 2 RCR=0x553f00e
[ 6777.423734] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6777.425786] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6777.731724] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6788.149933] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 6788.150533] r8712u 2-1.5:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-01 HOGWARTS>, seq = 0, tid = 0
[ 6795.997830] r8712u 2-1.5:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-01 HOGWARTS>, seq = 0, tid = 5
[ 7466.373504] r8712u 2-1.5:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-01 HOGWARTS>, seq = 53040, tid = 0
[10937.487454] r8712u 2-1.5:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-01 HOGWARTS>, seq = 1568, tid = 0
[11057.562478] r8712u 2-1.5:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-01 HOGWARTS>, seq = 28752, tid = 0
[11776.898432] r8712u 2-1.5:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-01 HOGWARTS>, seq = 51520, tid = 0
[11777.779481] r8712u 2-1.5:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-01 HOGWARTS>, seq = 51520, tid = 0
[13818.876654] r8712u 2-1.5:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-01 HOGWARTS>, seq = 34096, tid = 0
[14058.804673] r8712u 2-1.5:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-01 HOGWARTS>, seq = 31344, tid = 0
[14779.428450] r8712u 2-1.5:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-01 HOGWARTS>, seq = 46688, tid = 0
[15499.430354] r8712u 2-1.5:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-01 HOGWARTS>, seq = 45776, tid = 0
[16219.619856] r8712u 2-1.5:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-01 HOGWARTS>, seq = 43392, tid = 0
[16938.962275] r8712u 2-1.5:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-01 HOGWARTS>, seq = 65280, tid = 0
[16939.897383] r8712u 2-1.5:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-01 HOGWARTS>, seq = 65280, tid = 0
[17299.208953] r8712u 2-1.5:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-01 HOGWARTS>, seq = 12736, tid = 0
[17798.390161] r8712u 2-1.5:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-01 HOGWARTS>, seq = 16464, tid = 0
[17900.335772] r8712u 2-1.5:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-01 HOGWARTS>, seq = 17376, tid = 0
[19466.429021] r8712u 2-1.5:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-01 HOGWARTS>, seq = 27104, tid = 0
[63278.871027] r8712u 2-1.5:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-01 HOGWARTS>, seq = 55968, tid = 0

    ======== Done ========

```

---

### Post by praseodym on 2014-08-09
Try to change to pure WPA2-AES (CCMP) encryption in your router interface.

---

### Post by terrykiwi83 on 2014-08-09
I don't seem to have that option. All I have is:

[TABLE="width: 80%"]
[TR]
[TD]Disable         		    [/TD]
[/TR]
 					         			[TR]
[TD] WEP (Wired Equivalent Privacy)         		    [/TD]
[/TR]
          		    [TR]
[TD] WPA/WPA2-PSK (Wi-Fi Protected Access Pre-Shared Key)         		    < - This one is selected
[/TD]
[/TR]
         		    [TR]
[TD] WPA/WPA2-802.1x         		    [/TD]
[/TR]
[/TABLE]

---

### Post by praseodym on 2014-08-10
Router firmware is up-to-date? Try Wicd alternatively:
```

wget http://www.elektronenblitz63.de/download/wicd-1.6.x_addon01441.tar.gz
sudo apt-get install --reinstall wicd
tar xvf wicd-1.6.x_addon01441.tar.gz
cd wicd-1.6.x_addon01441
sudo ./install_wicd_addon
sudo service network-manager stop
sudo killall wpa_supplicant
sudo service wicd restart
```
You can chose mixed mode there. Deactivate the NM from autostart

---

### Post by terrykiwi83 on 2014-08-12
Thanks for the reply, have tried what you suggested praseodym. Still having the same problem, plus its getting more frequent :(

---

### Post by varunendra on 2014-08-12
Unless the router is really ancient, not having the option to choose WPA2 only doesn't look right. Can you please give us a link to its user manual?

Apart from the mixed mode issue, there are two more things you may try to optimize the connection quality -

[indent]1) Try disabling IPv6 permanently following this post : [http://ubuntuforums.org/showpost.php?p=12640479](http://ubuntuforums.org/showpost.php?p=12640479) . Also set "IPv6 > Method" to "Ignore" in Network Manager (if you are still using it, not sure how to set this option in WICD)

2) Assuming you are in New Zealand, try explicitly defining your country code for RegDomain settings. To do it permanently -
```
sudo sed -i 's/^REG.*=$/&NZ/' /etc/default/crda
```
This change will take effect after a reboot. To apply it immediately -
```
sudo iw reg set NZ
```
To verify the change took effect -
```
iw reg get
```
The output should show 'NZ' (currently it has been defaulted to '00') along with its pertaining settings.[/indent]

If these two can't help, I guess getting rid of the WPA/WPA2 mixed mode is the only likely solution.

---

