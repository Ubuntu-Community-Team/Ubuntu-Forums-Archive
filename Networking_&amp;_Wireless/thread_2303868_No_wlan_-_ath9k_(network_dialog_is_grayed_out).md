---
title: "No wlan - ath9k (network dialog is grayed out)"
date: 2015-11-22
forum: Networking &amp; Wireless
---

### Post by h-trader on 2015-11-22
I had wlan working without any problem since weeks/months. ([COLOR=#000000][FONT=Consolas]elementary OS Freya, based on ubuntu [/FONT][/COLOR]14.04.1)

Today I installed the printer driver for a Canon Pixma MG2950. Because I can't set up this printer for wireless printing in linux I started Win8 and set it up there with the cd rom from the printer.

In this setup there were a notice that the network is shutting down for a short time (or something like that)...

Don't know if this has something to do with my problem but since that time when I start my ubuntu again I see shortly after the desktop is there a notice which states "the network gots shut down - offline". When I click the WLAN icon all entries there are grayed out :(

(connecting a cable still works and I get a working connection)

Here are some debugging infos/outputs from my system [http://pastebin.com/ihTej3VL](http://pastebin.com/ihTej3VL)

```
    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

zinth-laptop 3.16.0-53-generic x86_64,  elementary OS Freya, freya

CPU    : AMD E1-2500 APU with Radeon(TM) HD Graphics
Memory : 1438 MB
Uptime : 13:57:16 up 1 min,  2 users,  load average: 1,18, 0,67, 0,26


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

01:00.0 Ethernet controller [0200]: Qualcomm Atheros QCA8171 Gigabit Ethernet [1969:10a1] (rev 13)
    Subsystem: Acer Incorporated [ALI] Device [1025:076b]
    Kernel driver in use: alx
--
05:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
    Subsystem: Lite-On Communications Inc Device [11ad:0632]
    Kernel driver in use: ath9k


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 002: ID 064e:e330 Suyin Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 04ca:300b Lite-On Technology Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 045e:07b2 Microsoft Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface                 Soft blocked  Hard blocked
0: phy0: Wireless LAN               no            no
1: acer-wireless: Wireless LAN      no            no
2: hci0: Bluetooth                  no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

wl                   6367833  0 
acer_wmi               32522  0 
sparse_keymap          13948  1 acer_wmi
ath9k                 141379  0 
ath9k_common           25638  1 ath9k
ath9k_hw              446521  2 ath9k_common,ath9k
ath                    29006  3 ath9k_common,ath9k,ath9k_hw
mac80211              652777  1 ath9k
cfg80211              498458  5 wl,ath,ath9k_common,ath9k,mac80211
wmi                    19193  1 acer_wmi
video                  20128  1 acer_wmi


module parameters ~~~~~~~~~~~~~~~~~~

acer_wmi      (5): brightness=-1 | ec_raw_mode=N | force_series=0 | mailled=-1 | threeg=-1
ath9k         (6): blink=0 | bt_ant_diversity=0 | btcoex_enable=0 | nohwcrypt=0 | ps_enable=0 | use_chanctx=0
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=-1
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: disconnected
================o=============o========o==========  ===o=========o===========o==============o=========  ==
 Interface & ID | Type        | Driver | State       | Default | Speed     | Support      | HW Addr   
================o=============o========o==========  ===o=========o===========o==============o=========  ==
 wlan0          | 802.11 WiFi | ath9k  | unavailable | no      |           | WEP/WPA/WPA2 | <MAC wlan0>
----------------+-------------+--------+-------------+---------+-----------+--------------+-----------
 eth0           | Wired       | alx    | unavailable | no      |           |              | <MAC eth0>
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

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~

EasyBox-76D950       : ssid=EasyBox-76D950 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
FRITZ!Box 7272       : ssid=FRITZ!Box 7272 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Linux                : ssid=Linux | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Zinth                : ssid=Zinth | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~



Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel-IP-Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : de_AT.UTF-8)
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 Waldmann>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"Waldmann"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000018e0a262704
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 allgaeudsl-mh>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"allgaeudsl-mh"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000006192ebddbc
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 allgaeudsl-r>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"allgaeudsl-r"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000766934f900
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 allgaeudsl-rm>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"allgaeudsl-rm"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000acf2e02d6c6
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC C-05 Linux>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=70/70  Signal level=-31 dBm  
                    Encryption key:on
                    ESSID:"Linux"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000012844f7d5d
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC C-06 Linux>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"Linux"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002e46e03f56a
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC C-07 allgaeudsl>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"allgaeudsl"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000cda5b3339
                    Extra: Last beacon: 8ms ago


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
filename:       /lib/modules/3.16.0-53-generic/extra/wl.ko
srcversion:     9A49255BA90267D99664757
depends:        cfg80211
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[acer_wmi]
filename:       /lib/modules/3.16.0-53-generic/kernel/drivers/platform/x86/acer-wmi.ko
srcversion:     97414F2256FC3B7919CD979
depends:        wmi,sparse-keymap,video
parm:           mailled:Set initial state of Mail LED (int)
parm:           brightness:Set initial LCD backlight brightness (int)
parm:           threeg:Set initial state of 3G hardware (int)
parm:           force_series:Force a different laptop series (int)
parm:           ec_raw_mode:Enable EC raw mode (bool)

[ath9k]
filename:       /lib/modules/3.16.0-53-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
srcversion:     CED1D76477A777795A07D73
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)

[ath9k_common]
filename:       /lib/modules/3.16.0-53-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
srcversion:     265A5990B1258ECC29235FC
depends:        cfg80211,ath9k_hw,ath

[ath9k_hw]
filename:       /lib/modules/3.16.0-53-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
srcversion:     0D1161FC3B202FBE214F25D
depends:        ath

[ath]
filename:       /lib/modules/3.16.0-53-generic/kernel/drivers/net/wireless/ath/ath.ko
srcversion:     165C1DF76AF8C8B6A45DA4F
depends:        cfg80211

[mac80211]
filename:       /lib/modules/3.16.0-53-generic/kernel/net/mac80211/mac80211.ko
srcversion:     477882071593B10E01388C8
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.16.0-53-generic/kernel/net/wireless/cfg80211.ko
srcversion:     046346857FD53951C911443
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[wmi]
filename:       /lib/modules/3.16.0-53-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     347CF30B94B5549A75865A8
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)

[video]
filename:       /lib/modules/3.16.0-53-generic/kernel/drivers/acpi/video.ko
srcversion:     2C29072BDC57BA9481E70D2
depends:        
parm:           brightness_switch_enabled:bool
parm:           allow_duplicates:bool
parm:           use_native_backlight:int


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x1969:0x10a1 (alx)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:0x0036 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modprobe.d]
asus_nb_wmi.conf  : options asus_nb_wmi wapf=4
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en
modesetting.conf  : options cirrus modeset=1
                    options mgag200 modeset=1


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.16.0-53-generic root=UUID=a88f5e9f-7602-4a4a-b8a9-4ce07b5e25e4 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.044298] Initializing cgroup subsys net_cls
[    0.044327] Initializing cgroup subsys net_prio
[    2.542754] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    2.543708] audit: initializing netlink subsys (disabled)
[    2.923429] wmi: Mapper loaded
[    2.966218] alx 0000:01:00.0 eth0: Qualcomm Atheros AR816x/AR817x Ethernet [<MAC eth0>]
[    3.003568] [drm] Found VCE firmware/feedback version 40.2.2 / 15!
[    4.111637] psmouse serio1: elantech: assuming hardware version 3 (with firmware version 0x254f00)
[   21.528112] ath: phy0: WB335 1-ANT card detected
[   21.537009] ath: phy0: Enable LNA combining
[   21.538629] ath: phy0: ASPM enabled: 0x42
[   21.538639] ath: EEPROM regdomain: 0x65
[   21.538642] ath: EEPROM indicates we should expect a direct regpair map
[   21.538649] ath: Country alpha2 being used: 00
[   21.538651] ath: Regpair used: 0x65
[   22.300878] acer_wmi: Acer Laptop ACPI-WMI Extras
[   22.301134] acer_wmi: Function bitmap for Communication Button: 0x801
[   22.338549] acer_wmi: Brightness must be controlled by acpi video driver
[   22.382246] wl: module license 'MIXED/Proprietary' taints kernel.
[   22.444026] wl: module verification failed: signature and/or  required key missing - tainting kernel
[   22.500659] acer_wmi: Enabling Launch Manager failed: 0xe2 - 0x0
[   29.260630] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   31.049340] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

    ======== Done ========

```

---

### Post by Hadaka on 2015-11-22
Hi,your wireless isnt working because you loaded a Broadcom wireless driver "wl"
broadcom-kernel-source and you dont have a broadcom wireless card. Please do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo modprobe ath9k
```
got wireless??

---

### Post by h-trader on 2015-11-22
Done these two commands, rebooted, but nothing changed... everything is still grayed out in network icon click. No wlan possible (although iwlist scan shows my networks nearby) :(

Did again the wireless-info script (when I was connected to cable to write that here) and uploaded it here ([http://pastebin.com/S8tk6sxi](http://pastebin.com/S8tk6sxi)) or attached.

---

### Post by Hadaka on 2015-11-22
Try going back into windows and deleting the files you used to
add the printer. also please copy and paste.. To Ubuntu
```
sudo iw reg set DE
sudo sed -i 's/^REG.*=$/&IN/' /etc/default/crda
```
*This is your country code and is needed for your wireless card.
once you have deleted the printer from windows and corrected your
country code in ubuntu..boot and test wireless.
thanks.

---

### Post by Hadaka on 2015-11-22
Try going back into windows and deleting the files you used to
add the printer. also please copy and paste.. To Ubuntu
```
sudo iw reg set DE
sudo sed -i 's/^REG.*=$/&IN/' /etc/default/crda
```
*This is your country code and is needed for your wireless card.
once you have deleted the printer from windows and corrected your
country code in ubuntu..boot and test wireless.
Here is a recent link to add your printer to ubuntu
[http://ubuntuforums.org/showthread.php?t=2292587](http://ubuntuforums.org/showthread.php?t=2292587)
thanks.

---

### Post by h-trader on 2015-11-22
Adding the country code doesn't changed anything... and I can't delete the printer driver in win8 because I also need to be able to print there.

So I did install wicd (and purged network-manager) and voila, with wicd I had no problem with my wlan. Wlan worked again with wicd.

Because I haven't installed/changed my ubuntu/freya installation that much I tested again the live system (usb stick) and there the network manager worked. So I reinstalled the os to my root partition (let my /home partition unchanged) and now everything is ok again.

---

### Post by Hadaka on 2015-11-22
Glad you got it working again ! so are you satisfied with the printer only being able
to print from windows ? or did you want to download that link i gave you to load the
ubuntu driver as well ? If you are indeed satisfied, please take the time to click tools
on this thread and mark it solved.
thanks.

---

### Post by h-trader on 2015-11-23
> **Hadaka said:**
> Glad you got it working again ! so are you satisfied with the printer only being able
to print from windows ? or did you want to download that link i gave you to load the
ubuntu driver as well ? 
You missunderstood me... I've installed the canon packages/driver and everything worked (print/scan) but only with **usb cable plugged in** not cordless (it's also a wlan printer).
And this priceless printer hasn't any display where you can configure/pair the printer with the acces point/router so I had to that with the windows setup cd rom canon provided. Now that the printed is paired with my access point I hope I can find the printer also in linux.

*(When installing the printer on linux you were asked if you would like an usb connection or wireless. With 2nd option you can't pair it with a router but you only can scan for already paired/present wireless printers.)*

> **Hadaka said:**
> If you are indeed satisfied, please take the time to click tools
on this thread and mark it solved.
thanks.

Done

---

