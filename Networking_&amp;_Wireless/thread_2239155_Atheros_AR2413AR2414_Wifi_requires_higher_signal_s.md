---
title: "Atheros AR2413/AR2414: Wifi requires higher signal strength to work"
date: 2014-08-12
forum: Networking &amp; Wireless
---

### Post by Pidge66 on 2014-08-12
I used to be able to access internet via wifi from my room when my Acer 2480-2551 was running Windows XP.  I have no problem surfing via wifi in my room using any other device either.  However, after I replaced Windows XP with Lubunto, I can no longer access the internet from my room -- even though I **do** get wifi connection.  The signal bar would show 2.5 bar out of 4.  And if I move right next to my wifi router, I'd get 3 or 4 bars and everything would be just fine (except occasional connect/disconnect notifications).

Any suggestions? 

Here's my network info:
[sudo] password for henry: 
```
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:16:36:9c:55:4e
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:44000000-44003fff ioport:2000(size=256)
  *-network
       description: Wireless interface
       product: AR2413/AR2414 Wireless Network Adapter [AR5005G(S) 802.11bg]
       vendor: Qualcomm Atheros
       physical id: 3
       bus info: pci@0000:0a:03.0
       logical name: wlan0
       version: 01
       serial: 00:16:cf:a1:05:f7
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=3.13.0-33-generic firmware=N/A ip=192.168.1.188 latency=168 link=yes maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:d0000000-d000ffff



```

---

### Post by varunendra on 2014-08-12
> **Pidge66 said:**
> ```

  *-network
       description: Wireless interface
       product: **AR2413/AR2414** Wireless Network Adapter [AR5005G(S) 802.11bg]
       ..<snip>..
       configuration: broadcast=yes **driver=ath5k** driverversion=3.13.0-33-generic....

```

There seems to be a parameter in the ath5k driver specifically meant for your device. Please try it as follows -
```
sudo modprobe -rv ath5k
sudo modprobe -v ath5k fastchanswitch=Y
```
The first command will remove the driver, thus disabling the wifi. The second one will reload it with the "fastchanswitch=Y" parameter. It'll be a temporary change that will be lost at next boot. If it seems to help, we can make it permanent.

However, if it doesn't seem to help, try another parameter that is common for all athxx drivers -
```
sudo modprobe -rv ath5k
sudo modprobe -v ath5k nohwcrypt=Y
```

If it still doesn't help, please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

### Post by Pidge66 on 2014-08-15
Varun,

Neither parameter helped. Actually each time after I reconfigured the wifi port, I was't able to connect at all.  I'd have to reboot to get the wifi connection back.  

While wifi was down, I hooked up the ethernet cable and ran the wireless-script as you had suggested. Here's the output:

```


    ======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


henry-TravelMate-2480 3.13.0-33-generic i686,  Ubuntu 14.04.1 LTS, trusty


CPU    : Intel(R) Celeron(R) M CPU        420  @ 1.60GHz
Memory : 992 MB
Uptime : 17:25:02 up  3:51,  4 users,  load average: 2.72, 1.49, 0.64




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller [11ab:4352] (rev 14)
    Subsystem: Acer Incorporated [ALI] Device [1025:0110]
    Kernel driver in use: sky2
0a:03.0 Ethernet controller [0200]: Qualcomm Atheros AR2413/AR2414 Wireless Network Adapter [AR5005G(S) 802.11bg] [168c:001a] (rev 01)
    Subsystem: AMBIT Microsystem Corp. Device [1468:0418]
    Kernel driver in use: ath5k




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          




rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


      Interface                 Soft blocked  Hard blocked
0: acer-wireless: Wireless LAN      no            no
4: phy0: Wireless LAN               no            no




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


ath5k                 134977  0 
ath                    23922  1 ath5k
mac80211              546051  1 ath5k
cfg80211              409394  3 ath,ath5k,mac80211
acer_wmi               31735  0 
sparse_keymap          13708  1 acer_wmi
wmi                    18673  1 acer_wmi
video                  18903  2 i915,acer_wmi




module parameters ~~~~~~~~~~~~~~~~~~


acer_wmi      (5): brightness=-1 | ec_raw_mode=N | force_series=0 | mailled=-1 | threeg=-1
ath5k         (3): fastchanswitch=N | nohwcrypt=N | no_hw_rfkill_switch=N
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=-1
wmi           (2): debug_dump_wdg=N | debug_event=N




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: connected (global)
============================o=============o=======  =o==========================o=========o===========  o==============o===========
 Interface & ID             | Type        | Driver | State                    | Default | Speed     | Support      | HW Addr   
============================o=============o=======  =o==========================o=========o===========  o==============o===========
 wlan0  [CRDVD]             | 802.11 WiFi | ath5k  | connecting (configuring) | no      |           | WEP/WPA/WPA2 | <MAC wlan0>


    Prit_Home:       Infra, <MAC C-01 Prit_Home>, Freq 2437 MHz, Rate 54 Mb/s, Strength 62 WPA WPA2
    bubbles:         Infra, <MAC C-05 bubbles>, Freq 2447 MHz, Rate 54 Mb/s, Strength 25 WPA2
    MOTOROLA-559A2:  Infra, <MAC C-03 MOTOROLA-559A2>, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WPA2
    6CNF3 6CNF3:     Infra, <MAC C-NA 6CNF3 6CNF3 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    TScomak:         Infra, <MAC C-NA TScomak 1>, Freq 2442 MHz, Rate 54 Mb/s, Strength 19 WPA2
    Turnpaugh WiFi:  Infra, <MAC C-NA Turnpaugh WiFi 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 12 WPA WPA2
    FFW34:           Infra, <MAC C-04 FFW34>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WEP
    CRDVD:           Infra, <MAC C-02 >, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
----------------------------+-------------+--------+--------------------------+---------+-----------+--------------+-----------
 eth0  [Wired connection 1] | Wired       | sky2   | connected                | yes     | 100 Mb/s  |              | <MAC eth0>


    Address:         10.1.10.16
    Prefix:          24 (255.255.255.0)
    Gateway:         10.1.10.1
    DNS:             10.1.10.1
----------------------------+-------------+--------+--------------------------+---------+-----------+--------------+-----------




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


CRDVD                : ssid=CRDVD | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
MSHOME               : ssid=MSHOME | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 




interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~


nameserver 127.0.1.1
search hsd1.pa.comcast.net




Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.1.10.1       0.0.0.0         UG    0      0        0 eth0
10.1.10.0       0.0.0.0         255.255.255.0   U     1      0        0 eth0


--- 10.1.10.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.380/0.394/0.408/0.014 ms


--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.042/0.045/0.048/0.003 ms




iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~


(Region : en_US.UTF-8)




iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)




iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 Prit_Home>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"Prit_Home"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000070495c9b6e
                    Extra: Last beacon: 72ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 >
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=67/70  Signal level=-43 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000013c9b9d80
                    Extra: Last beacon: 96ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 MOTOROLA-559A2>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"MOTOROLA-559A2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000255ee5855
                    Extra: Last beacon: 13748ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 FFW34>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"FFW34"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000116a6d375f
                    Extra: Last beacon: 1232ms ago
          Cell 05 - Address: <MAC C-05 bubbles>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"bubbles"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000023d970e0b8d
                    Extra: Last beacon: 700ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC C-06 WT778>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"WT778"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000c68b3f180
                    Extra: Last beacon: 3752ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK




blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/libpisock9.conf]
blacklist visor




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[ath5k]
filename:       /lib/modules/3.13.0-33-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
srcversion:     F36818A2F0BCB2B0CC9BB8C
depends:        mac80211,cfg80211,ath
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)


[ath]
filename:       /lib/modules/3.13.0-33-generic/kernel/drivers/net/wireless/ath/ath.ko
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211


[mac80211]
filename:       /lib/modules/3.13.0-33-generic/kernel/net/mac80211/mac80211.ko
srcversion:     8ADA881D348148A3358334C
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.13.0-33-generic/kernel/net/wireless/cfg80211.ko
srcversion:     E786D076B61F97809B04B64
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[acer_wmi]
filename:       /lib/modules/3.13.0-33-generic/kernel/drivers/platform/x86/acer-wmi.ko
srcversion:     15371DC0E403E93954B38E5
depends:        wmi,sparse-keymap,video
parm:           mailled:Set initial state of Mail LED (int)
parm:           brightness:Set initial LCD backlight brightness (int)
parm:           threeg:Set initial state of 3G hardware (int)
parm:           force_series:Force a different laptop series (int)
parm:           ec_raw_mode:Enable EC raw mode (bool)


[wmi]
filename:       /lib/modules/3.13.0-33-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


[video]
filename:       /lib/modules/3.13.0-33-generic/kernel/drivers/acpi/video.ko
srcversion:     274A2250DEAB415D412A67C
depends:        
parm:           brightness_switch_enabled:bool
parm:           allow_duplicates:bool
parm:           use_native_backlight:int




udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~


# PCI device 0x11ab:0x4352 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x168c:0x001a (ath5k)
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


BOOT_IMAGE=/vmlinuz-3.13.0-33-generic root=/dev/mapper/lubuntu--vg-root ro quiet splash vt.handoff=7




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    1.511596] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.512113] audit: initializing netlink socket (disabled)
[   17.462768] wmi: Mapper loaded
[   18.129948] ath5k 0000:0a:03.0: registered as 'phy0'
[   19.732665] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.869117] acer_wmi: Acer Laptop ACPI-WMI Extras
[   19.869576] acer_wmi: Function bitmap for Communication Device: 0x27
[   19.869585] acer_wmi: Disabling ACPI video driver
[   21.181356] ath: EEPROM regdomain: 0x63
[   21.181363] ath: EEPROM indicates we should expect a direct regpair map
[   21.181368] ath: Country alpha2 being used: 00
[   21.181370] ath: Regpair used: 0x63
[   21.246336] ath5k: phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
[   23.020145] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.021155] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   32.504484] wlan0: authenticate with <MAC C-02 >
[   32.518961] wlan0: send auth to <MAC C-02 > (try 1/3)
[   32.584400] wlan0: authenticated
[   32.584920] ath5k 0000:0a:03.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   32.588196] wlan0: associate with <MAC C-02 > (try 1/3)
[   32.619574] wlan0: RX AssocResp from <MAC C-02 > (capab=0x431 status=0 aid=1)
[   32.619945] wlan0: associated
[   32.619960] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   67.858143] wlan0: deauthenticating from <MAC C-02 > by local choice (reason=3)
[   68.832454] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   83.609531] wlan0: authenticate with <MAC C-02 >
[   83.620675] wlan0: send auth to <MAC C-02 > (try 1/3)
[   83.705458] wlan0: authenticated
[   83.705748] ath5k 0000:0a:03.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   83.708239] wlan0: associate with <MAC C-02 > (try 1/3)
[   83.714395] wlan0: RX AssocResp from <MAC C-02 > (capab=0x431 status=0 aid=1)
[   83.714952] wlan0: associated
[   83.714970] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   96.859742] wlan0: deauthenticating from <MAC C-02 > by local choice (reason=3)
[   97.832536] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  100.064845] wlan0: authenticate with <MAC C-02 >
[  100.071175] wlan0: send auth to <MAC C-02 > (try 1/3)
[  100.134779] wlan0: authenticated
[  100.135023] ath5k 0000:0a:03.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  100.136160] wlan0: associate with <MAC C-02 > (try 1/3)
[  100.139759] wlan0: RX AssocResp from <MAC C-02 > (capab=0x431 status=0 aid=1)
[  100.146110] wlan0: associated
[  100.146133] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  100.151527] wlan0: deauthenticating from <MAC C-02 > by local choice (reason=2)
[  100.156552] wlan0: authenticate with <MAC C-02 >
[  100.156783] wlan0: send auth to <MAC C-02 > (try 1/3)
[  100.158191] wlan0: authenticated
[  100.161075] ath5k 0000:0a:03.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  100.164192] wlan0: associate with <MAC C-02 > (try 1/3)
[  100.168136] wlan0: RX AssocResp from <MAC C-02 > (capab=0x431 status=0 aid=1)
[  100.168508] wlan0: associated
[ 2324.116203] wlan0: deauthenticating from <MAC C-02 > by local choice (reason=3)
[ 2328.110296] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2331.314161] wlan0: authenticate with <MAC C-02 >
[ 2331.324957] wlan0: send auth to <MAC C-02 > (try 1/3)
[ 2331.326566] wlan0: authenticated
[ 2331.326939] ath5k 0000:0a:03.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 2331.328215] wlan0: associate with <MAC C-02 > (try 1/3)
[ 2331.331795] wlan0: RX AssocResp from <MAC C-02 > (capab=0x431 status=0 aid=1)
[ 2331.332210] wlan0: associated
[ 2331.333071] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2572.044370] wlan0: deauthenticating from <MAC C-02 > by local choice (reason=3)
[ 2573.016222] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2576.115953] wlan0: authenticate with <MAC C-02 >
[ 2576.125678] wlan0: send auth to <MAC C-02 > (try 1/3)
[ 2576.127696] wlan0: authenticated
[ 2576.128224] ath5k 0000:0a:03.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 2576.132288] wlan0: associate with <MAC C-02 > (try 1/3)
[ 2576.136302] wlan0: RX AssocResp from <MAC C-02 > (capab=0x431 status=0 aid=1)
[ 2576.136750] wlan0: associated
[ 2576.136765] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3672.744397] wlan0: deauthenticating from <MAC C-02 > by local choice (reason=3)
[ 3675.528790] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3677.589141] wlan0: authenticate with <MAC C-02 >
[ 3677.597713] wlan0: send auth to <MAC C-02 > (try 1/3)
[ 3677.600818] wlan0: authenticated
[ 3677.601059] ath5k 0000:0a:03.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 3677.604306] wlan0: associate with <MAC C-02 > (try 1/3)
[ 3677.607713] wlan0: RX AssocResp from <MAC C-02 > (capab=0x431 status=0 aid=1)
[ 3677.608429] wlan0: associated
[ 3677.608446] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[12663.014685] wlan0: deauthenticating from <MAC C-02 > by local choice (reason=3)
[12666.018947] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[12702.492943] wlan0: authenticate with <MAC C-02 >
[12702.505742] wlan0: send auth to <MAC C-02 > (try 1/3)
[12702.578563] wlan0: authenticated
[12702.578848] ath5k 0000:0a:03.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[12702.580172] wlan0: associate with <MAC C-02 > (try 1/3)
[12702.586535] wlan0: RX AssocResp from <MAC C-02 > (capab=0x431 status=0 aid=1)
[12702.586979] wlan0: associated
[12702.587012] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[13056.087117] wlan0: deauthenticating from <MAC C-02 > by local choice (reason=3)
[13057.018242] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[13060.182230] wlan0: authenticate with <MAC C-02 >
[13060.192913] wlan0: send auth to <MAC C-02 > (try 1/3)
[13060.195233] wlan0: authenticated
[13060.195649] ath5k 0000:0a:03.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[13060.196190] wlan0: associate with <MAC C-02 > (try 1/3)
[13060.199773] wlan0: RX AssocResp from <MAC C-02 > (capab=0x431 status=0 aid=1)
[13060.200507] wlan0: associated
[13060.200524] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[13131.044569] wlan0: deauthenticating from <MAC C-02 > by local choice (reason=3)
[13132.017809] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[13135.105823] wlan0: authenticate with <MAC C-02 >
[13135.116642] wlan0: send auth to <MAC C-02 > (try 1/3)
[13135.164481] wlan0: authenticated
[13135.164766] ath5k 0000:0a:03.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[13135.168054] wlan0: associate with <MAC C-02 > (try 1/3)
[13135.171538] wlan0: RX AssocResp from <MAC C-02 > (capab=0x431 status=0 aid=1)
[13135.171915] wlan0: associated
[13135.171956] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[13151.116216] wlan0: deauthenticating from <MAC C-02 > by local choice (reason=3)
[13252.260410] ath5k 0000:0a:03.0: registered as 'phy0'
[13252.992255] ath: EEPROM regdomain: 0x63
[13252.992261] ath: EEPROM indicates we should expect a direct regpair map
[13252.992266] ath: Country alpha2 being used: 00
[13252.992268] ath: Regpair used: 0x63
[13252.996667] ath5k: phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
[13253.185526] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[13253.188494] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[13273.492590] wlan0: authenticate with <MAC C-02 >
[13273.498770] wlan0: send auth to <MAC C-02 > (try 1/3)
[13273.542601] wlan0: authenticated
[13278.504600] wlan0: deauthenticating from <MAC C-02 > by local choice (reason=3)
[13288.614344] wlan0: authenticate with <MAC C-02 >
[13288.614579] wlan0: send auth to <MAC C-02 > (try 1/3)
[13288.618124] wlan0: authenticated
[13289.004518] wlan0: deauthenticating from <MAC C-02 > by local choice (reason=3)
[13299.021345] wlan0: authenticate with <MAC C-02 >
[13299.021583] wlan0: send auth to <MAC C-02 > (try 1/3)
[13299.023643] wlan0: authenticated
[13304.022581] wlan0: deauthenticating from <MAC C-02 > by local choice (reason=3)
[13304.023083] wlan0: authenticate with <MAC C-02 >
[13304.023317] wlan0: send auth to <MAC C-02 > (try 1/3)
[13304.024866] wlan0: authenticated
[13309.027132] wlan0: deauthenticating from <MAC C-02 > by local choice (reason=3)
[13320.138573] wlan0: authenticate with <MAC C-02 >
[13320.138807] wlan0: send auth to <MAC C-02 > (try 1/3)
[13320.140247] wlan0: authenticated
[13325.140963] wlan0: deauthenticating from <MAC C-02 > by local choice (reason=3)
[13340.148354] wlan0: authenticate with <MAC C-02 >
[13340.148589] wlan0: send auth to <MAC C-02 > (try 1/3)
[13340.170518] wlan0: authenticated
[13345.006865] wlan0: deauthenticating from <MAC C-02 > by local choice (reason=3)
[13355.027727] wlan0: authenticate with <MAC C-02 >
[13355.027959] wlan0: send auth to <MAC C-02 > (try 1/3)
[13355.030262] wlan0: authenticated
[13360.029776] wlan0: deauthenticating from <MAC C-02 > by local choice (reason=3)
[13432.997788] ath5k 0000:0a:03.0: registered as 'phy0'
[13433.728518] ath: EEPROM regdomain: 0x63
[13433.728525] ath: EEPROM indicates we should expect a direct regpair map
[13433.728529] ath: Country alpha2 being used: 00
[13433.728531] ath: Regpair used: 0x63
[13433.744661] ath5k: phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
[13433.799940] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[13433.808096] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[13528.853718] ath5k 0000:0a:03.0: registered as 'phy0'
[13529.588529] ath: EEPROM regdomain: 0x63
[13529.588536] ath: EEPROM indicates we should expect a direct regpair map
[13529.588541] ath: Country alpha2 being used: 00
[13529.588543] ath: Regpair used: 0x63
[13529.604644] ath5k: phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
[13529.663249] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[13529.667263] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[13569.847285] wlan0: authenticate with <MAC C-02 >
[13569.859872] wlan0: send auth to <MAC C-02 > (try 1/3)
[13570.004487] wlan0: deauthenticating from <MAC C-02 > by local choice (reason=3)


    ======== Done ========



```

---

### Post by varunendra on 2014-08-15
You seem to be using WPA/WPA2 mixed mode with TKIP in your router. Please change it to pure WPA2-PSK with AES (CCMP), that will slightly improve the signal quality too, besides making the encryption better and more efficient than TKIP.

Also, why have you kept the SSID hidden? If it is for security, be informed that it is no more secure than those with SSID. I suggest you give your AP/router a suitable SSID (simple, short containing no special characters or blank spaces). Although the hidden ssid issue doesn't seem to be related with the current problem, it can confuse the driver in other ways.

Reboot the router after saving the change and retry to connect. Try the "nohwcrypt=Y" parameter again with the changed encryption too, it works better with AES.

---

### Post by Pidge66 on 2014-08-16
I am actually at different residence during the weekends - so my wireless-script dump was for a different network than my original post, with a different SSDI and security, but the **same behavior**. I didn't think it mattered in my case as it seemed to be driver related than router related.  This morning I took the laptop to my kid's karate which has free wifi.  Lubuntu actually froze after I get wifi connection and entered the guest password.  So there's some underlying problem for sure.

But I totally agree it's time to migrate out of the TKIP, which obviously was there for historic reason.  My wife, however, refuses to expose our SSID.  How is hiding SSID not "a bit" more secure?  I could not field that question.

Anyways, I took your suggestions and configure my weekend "B" router to use WPA2/AES and shortened password, and temporarily unhide the SSID.  And it actually improved and operated under lower signal strength (2-2.5 bars out of 4) !!!   I will need to bring my laptop back to my original weekday "A" router to see what happens, though.  Technically I have **NOT** done anything to the Lubuntu configuration at all, only changing the "B" router.  So I am not holding my breath.

Any post bootup mod to the wifi connection would fail.  How do I make the mod permanent so I can attempt connection on bootup?

Just in case there is any info to glean, here's the wireless-script dump after changing the "B" router config and the (failed) attempt to enable nohwcrypt:

```


    ======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


henry-TravelMate-2480 3.13.0-33-generic i686,  Ubuntu 14.04.1 LTS, trusty


CPU    : Intel(R) Celeron(R) M CPU        420  @ 1.60GHz
Memory : 992 MB
Uptime : 13:31:59 up  3:14,  3 users,  load average: 0.28, 0.20, 0.23




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller [11ab:4352] (rev 14)
    Subsystem: Acer Incorporated [ALI] Device [1025:0110]
    Kernel driver in use: sky2
0a:03.0 Ethernet controller [0200]: Qualcomm Atheros AR2413/AR2414 Wireless Network Adapter [AR5005G(S) 802.11bg] [168c:001a] (rev 01)
    Subsystem: AMBIT Microsystem Corp. Device [1468:0418]
    Kernel driver in use: ath5k




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 045e:0095 Microsoft Corp. IntelliMouse Explorer 4.0 (IntelliPoint)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          




rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


      Interface                 Soft blocked  Hard blocked
0: acer-wireless: Wireless LAN      no            no
2: phy0: Wireless LAN               no            no




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


ath5k                 134977  0 
ath                    23922  1 ath5k
mac80211              546051  1 ath5k
cfg80211              409394  3 ath,ath5k,mac80211
acer_wmi               31735  0 
sparse_keymap          13708  1 acer_wmi
wmi                    18673  1 acer_wmi
video                  18903  2 i915,acer_wmi




module parameters ~~~~~~~~~~~~~~~~~~


acer_wmi      (5): brightness=-1 | ec_raw_mode=N | force_series=0 | mailled=-1 | threeg=-1
ath5k         (3): fastchanswitch=N | nohwcrypt=Y | no_hw_rfkill_switch=N
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=-1
wmi           (2): debug_dump_wdg=N | debug_event=N




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: disconnected
================o=============o========o==========  ====o=========o===========o==============o========  ===
 Interface & ID | Type        | Driver | State        | Default | Speed     | Support      | HW Addr   
================o=============o========o==========  ====o=========o===========o==============o========  ===
 wlan0          | 802.11 WiFi | ath5k  | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>


    Prit_Home:       Infra, <MAC C-02 Prit_Home>, Freq 2437 MHz, Rate 54 Mb/s, Strength 60 WPA WPA2
    MOTOROLA-559A2:  Infra, <MAC C-04 MOTOROLA-559A2>, Freq 2412 MHz, Rate 54 Mb/s, Strength 55 WPA2
    HOME-4022:       Infra, <MAC C-05 HOME-4022>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    GZTY3:           Infra, <MAC C-NA GZTY3 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA2
    TScomak:         Infra, <MAC C-NA TScomak 1>, Freq 2442 MHz, Rate 54 Mb/s, Strength 24 WPA2
    DHCS_PCGW7:      Infra, <MAC C-NA DHCS_PCGW7 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    Q7NK3:           Infra, <MAC C-NA Q7NK3 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WEP
    xfinitywifi:     Infra, <MAC C-03 xfinitywifi>, Freq 2462 MHz, Rate 54 Mb/s, Strength 32
    xfinitywifi:     Infra, <MAC C-07 xfinitywifi>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30
    PCIH:            Infra, <MAC C-NA PCIH 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA2
    bubbles:         Infra, <MAC C-NA bubbles 1>, Freq 2447 MHz, Rate 54 Mb/s, Strength 22 WPA2
    CRDVD:           Infra, <MAC C-01 CRDVD>, Freq 2417 MHz, Rate 54 Mb/s, Strength 90 WPA2
    FFW34:           Infra, <MAC C-NA FFW34 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WEP
    Turnpaugh WiFi:  Infra, <MAC C-NA Turnpaugh WiFi 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    WT778:           Infra, <MAC C-NA WT778 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA2
----------------+-------------+--------+--------------+---------+-----------+--------------+-----------
 eth0           | Wired       | sky2   | unavailable  | no      |           |              | <MAC eth0>
----------------+-------------+--------+--------------+---------+-----------+--------------+-----------




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


CRDVD                : ssid=CRDVD | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
MSHOME               : ssid=MSHOME | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Palumbo Pizza        : ssid=Palumbo Pizza | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Palumbo Pizza-guest  : ssid=Palumbo Pizza-guest | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 




interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~






Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface




iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~


(Region : en_US.UTF-8)




iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)




iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 CRDVD>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:"CRDVD"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001226ae0a2
                    Extra: Last beacon: 24ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 Prit_Home>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"Prit_Home"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000812581bc3b
                    Extra: Last beacon: 24ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 xfinitywifi>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000158a84cc180
                    Extra: Last beacon: 10312ms ago
          Cell 04 - Address: <MAC C-04 MOTOROLA-559A2>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"MOTOROLA-559A2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001332389704
                    Extra: Last beacon: 840ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC C-05 HOME-4022>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"HOME-4022"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000042a8f70e172
                    Extra: Last beacon: 4752ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC C-06 >
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000042a8f70eb4c
                    Extra: Last beacon: 4748ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC C-07 xfinitywifi>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=17/70  Signal level=-93 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000042a8f17e25f
                    Extra: Last beacon: 10584ms ago
          Cell 08 - Address: <MAC C-08 >
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001e4bfccc19a
                    Extra: Last beacon: 4596ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK




blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/libpisock9.conf]
blacklist visor




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[ath5k]
filename:       /lib/modules/3.13.0-33-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
srcversion:     F36818A2F0BCB2B0CC9BB8C
depends:        mac80211,cfg80211,ath
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)


[ath]
filename:       /lib/modules/3.13.0-33-generic/kernel/drivers/net/wireless/ath/ath.ko
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211


[mac80211]
filename:       /lib/modules/3.13.0-33-generic/kernel/net/mac80211/mac80211.ko
srcversion:     8ADA881D348148A3358334C
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.13.0-33-generic/kernel/net/wireless/cfg80211.ko
srcversion:     E786D076B61F97809B04B64
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[acer_wmi]
filename:       /lib/modules/3.13.0-33-generic/kernel/drivers/platform/x86/acer-wmi.ko
srcversion:     15371DC0E403E93954B38E5
depends:        wmi,sparse-keymap,video
parm:           mailled:Set initial state of Mail LED (int)
parm:           brightness:Set initial LCD backlight brightness (int)
parm:           threeg:Set initial state of 3G hardware (int)
parm:           force_series:Force a different laptop series (int)
parm:           ec_raw_mode:Enable EC raw mode (bool)


[wmi]
filename:       /lib/modules/3.13.0-33-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


[video]
filename:       /lib/modules/3.13.0-33-generic/kernel/drivers/acpi/video.ko
srcversion:     274A2250DEAB415D412A67C
depends:        
parm:           brightness_switch_enabled:bool
parm:           allow_duplicates:bool
parm:           use_native_backlight:int




udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~


# PCI device 0x11ab:0x4352 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x168c:0x001a (ath5k)
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


BOOT_IMAGE=/vmlinuz-3.13.0-33-generic root=/dev/mapper/lubuntu--vg-root ro quiet splash vt.handoff=7




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    1.399625] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.400139] audit: initializing netlink socket (disabled)
[   18.986809] wmi: Mapper loaded
[   19.765230] ath5k 0000:0a:03.0: registered as 'phy0'
[   20.809910] acer_wmi: Acer Laptop ACPI-WMI Extras
[   20.816563] acer_wmi: Function bitmap for Communication Device: 0x27
[   20.816582] acer_wmi: Disabling ACPI video driver
[   21.999441] ath: EEPROM regdomain: 0x63
[   21.999448] ath: EEPROM indicates we should expect a direct regpair map
[   21.999453] ath: Country alpha2 being used: 00
[   21.999455] ath: Regpair used: 0x63
[   22.033862] ath5k: phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
[   27.327554] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   29.039755] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.040882] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   31.709634] wlan0: authenticate with <MAC ID removed>
[   31.716145] wlan0: send auth to <MAC ID removed> (try 1/3)
[   31.783433] wlan0: authenticated
[   31.784340] wlan0: associate with <MAC ID removed> (try 1/3)
[   31.788107] wlan0: RX AssocResp from <MAC ID removed> (capab=0x401 status=0 aid=3)
[   31.788485] wlan0: associated
[   31.788531] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   31.789943] wlan0: deauthenticating from <MAC ID removed> by local choice (reason=2)
[   31.795008] wlan0: authenticate with <MAC ID removed>
[   31.795254] wlan0: send auth to <MAC ID removed> (try 1/3)
[   31.798786] wlan0: authenticated
[   31.800238] wlan0: associate with <MAC ID removed> (try 1/3)
[   31.802527] wlan0: RX AssocResp from <MAC ID removed> (capab=0x401 status=0 aid=3)
[   31.802897] wlan0: associated
[   41.808177] wlan0: deauthenticating from <MAC ID removed> by local choice (reason=3)
[   42.905487] wlan0: authenticate with <MAC ID removed>
[   42.910967] wlan0: send auth to <MAC ID removed> (try 1/3)
[   42.985972] wlan0: authenticated
[   42.988216] wlan0: associate with <MAC ID removed> (try 1/3)
[   42.990628] wlan0: RX AssocResp from <MAC ID removed> (capab=0x401 status=0 aid=3)
[   42.991011] wlan0: associated
[   47.917319] wlan0: deauthenticating from <MAC ID removed> by local choice (reason=3)
[   48.834512] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   51.288740] wlan0: authenticate with <MAC ID removed>
[   51.294756] wlan0: send auth to <MAC ID removed> (try 1/3)
[   51.366739] wlan0: authenticated
[   51.368149] wlan0: associate with <MAC ID removed> (try 1/3)
[   51.370548] wlan0: RX AssocResp from <MAC ID removed> (capab=0x401 status=0 aid=3)
[   51.370920] wlan0: associated
[   51.370936] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   51.372373] wlan0: deauthenticating from <MAC ID removed> by local choice (reason=2)
[   51.372670] wlan0: authenticate with <MAC ID removed>
[   51.372894] wlan0: send auth to <MAC ID removed> (try 1/3)
[   51.376862] wlan0: authenticated
[   51.380286] wlan0: associate with <MAC ID removed> (try 1/3)
[   51.382881] wlan0: RX AssocResp from <MAC ID removed> (capab=0x401 status=0 aid=3)
[   51.383252] wlan0: associated
[   61.386413] wlan0: deauthenticating from <MAC ID removed> by local choice (reason=3)
[   62.677500] wlan0: authenticate with <MAC ID removed>
[   62.682820] wlan0: send auth to <MAC ID removed> (try 1/3)
[   62.736678] wlan0: authenticated
[   62.740163] wlan0: associate with <MAC ID removed> (try 1/3)
[   62.758809] wlan0: RX AssocResp from <MAC ID removed> (capab=0x401 status=0 aid=4)
[   62.759186] wlan0: associated
[   77.848792] wlan0: deauthenticating from <MAC ID removed> by local choice (reason=3)
[   78.842423] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   81.209445] wlan0: authenticate with <MAC ID removed>
[   81.214739] wlan0: send auth to <MAC ID removed> (try 1/3)
[   81.283259] wlan0: authenticated
[   81.284144] wlan0: associate with <MAC ID removed> (try 1/3)
[   81.286553] wlan0: RX AssocResp from <MAC ID removed> (capab=0x401 status=0 aid=3)
[   81.286924] wlan0: associated
[   81.286940] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   81.289327] wlan0: deauthenticating from <MAC ID removed> by local choice (reason=2)
[   81.294413] wlan0: authenticate with <MAC ID removed>
[   81.294652] wlan0: send auth to <MAC ID removed> (try 1/3)
[   81.296805] wlan0: authenticated
[   81.300279] wlan0: associate with <MAC ID removed> (try 1/3)
[   81.303244] wlan0: RX AssocResp from <MAC ID removed> (capab=0x401 status=0 aid=3)
[   81.303617] wlan0: associated
[   91.308187] wlan0: deauthenticating from <MAC ID removed> by local choice (reason=3)
[   92.729548] wlan0: authenticate with <MAC ID removed>
[   92.735158] wlan0: send auth to <MAC ID removed> (try 1/3)
[   92.804147] wlan0: authenticated
[   92.808192] wlan0: associate with <MAC ID removed> (try 1/3)
[   92.810856] wlan0: RX AssocResp from <MAC ID removed> (capab=0x401 status=0 aid=3)
[   92.811234] wlan0: associated
[  194.860608] wlan0: deauthenticating from <MAC ID removed> by local choice (reason=3)
[  195.833822] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  198.837336] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  201.101633] wlan0: authenticate with <MAC ID removed>
[  201.110132] wlan0: send auth to <MAC ID removed> (try 1/3)
[  201.111861] wlan0: authenticated
[  201.116051] wlan0: associate with <MAC ID removed> (try 1/3)
[  201.181239] wlan0: RX AssocResp from <MAC ID removed> (capab=0x401 status=0 aid=3)
[  201.181639] wlan0: associated
[  201.181736] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  201.182420] wlan0: deauthenticating from <MAC ID removed> by local choice (reason=2)
[  201.184158] wlan0: authenticate with <MAC ID removed>
[  201.184380] wlan0: send auth to <MAC ID removed> (try 1/3)
[  201.188357] wlan0: authenticated
[  201.192211] wlan0: associate with <MAC ID removed> (try 1/3)
[  201.194486] wlan0: RX AssocResp from <MAC ID removed> (capab=0x401 status=0 aid=3)
[  201.194864] wlan0: associated
[  211.198722] wlan0: deauthenticating from <MAC ID removed> by local choice (reason=3)
[  212.569473] wlan0: authenticate with <MAC ID removed>
[  212.574962] wlan0: send auth to <MAC ID removed> (try 1/3)
[  212.643299] wlan0: authenticated
[  212.644210] wlan0: associate with <MAC ID removed> (try 1/3)
[  212.646632] wlan0: RX AssocResp from <MAC ID removed> (capab=0x401 status=0 aid=3)
[  212.647011] wlan0: associated
[  782.715775] wlan0: deauthenticating from <MAC ID removed> by local choice (reason=3)
[  791.240251] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  792.354667] wlan0: authenticate with <MAC ID removed>
[  792.354907] wlan0: send auth to <MAC ID removed> (try 1/3)
[  792.356583] wlan0: authenticated
[  792.360548] wlan0: associate with <MAC ID removed> (try 1/3)
[  792.362816] wlan0: RX AssocResp from <MAC ID removed> (capab=0x401 status=0 aid=3)
[  792.363191] wlan0: associated
[  792.363228] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  799.598191] wlan0: deauthenticating from <MAC ID removed> by local choice (reason=3)
[  808.109438] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  809.611261] wlan0: authenticate with <MAC C-01 CRDVD>
[  809.616131] wlan0: send auth to <MAC C-01 CRDVD> (try 1/3)
[  809.617885] wlan0: authenticated
[  809.620055] wlan0: associate with <MAC C-01 CRDVD> (try 1/3)
[  809.624292] wlan0: RX AssocResp from <MAC C-01 CRDVD> (capab=0x431 status=0 aid=2)
[  809.624732] wlan0: associated
[  809.624766] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  812.626245] wlan0: deauthenticated from <MAC C-01 CRDVD> (Reason: 2)
[  843.057618] wlan0: authenticate with <MAC C-01 CRDVD>
[  843.063672] wlan0: send auth to <MAC C-01 CRDVD> (try 1/3)
[  843.068054] wlan0: authenticated
[  843.072196] wlan0: associate with <MAC C-01 CRDVD> (try 1/3)
[  843.076346] wlan0: RX AssocResp from <MAC C-01 CRDVD> (capab=0x431 status=0 aid=3)
[  843.076794] wlan0: associated
[ 1125.425523] wlan0: deauthenticating from <MAC C-01 CRDVD> by local choice (reason=3)
[ 1127.535729] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1129.914521] wlan0: authenticate with <MAC C-01 CRDVD>
[ 1129.919856] wlan0: send auth to <MAC C-01 CRDVD> (try 1/3)
[ 1129.922200] wlan0: authenticated
[ 1129.924393] wlan0: associate with <MAC C-01 CRDVD> (try 1/3)
[ 1129.930293] wlan0: RX AssocResp from <MAC C-01 CRDVD> (capab=0x431 status=0 aid=1)
[ 1129.930671] wlan0: associated
[ 1129.930712] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1129.961804] wlan0: deauthenticating from <MAC C-01 CRDVD> by local choice (reason=2)
[ 1129.968188] wlan0: authenticate with <MAC C-01 CRDVD>
[ 1129.968412] wlan0: send auth to <MAC C-01 CRDVD> (try 1/3)
[ 1129.970760] wlan0: authenticated
[ 1129.976312] wlan0: associate with <MAC C-01 CRDVD> (try 1/3)
[ 1129.980187] wlan0: RX AssocResp from <MAC C-01 CRDVD> (capab=0x431 status=0 aid=1)
[ 1129.980557] wlan0: associated
[ 1399.216247] wlan0: deauthenticating from <MAC C-01 CRDVD> by local choice (reason=3)
[ 1401.302747] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1404.107252] wlan0: authenticate with <MAC C-01 CRDVD>
[ 1404.111282] wlan0: send auth to <MAC C-01 CRDVD> (try 1/3)
[ 1404.112667] wlan0: authenticated
[ 1404.116334] wlan0: associate with <MAC C-01 CRDVD> (try 1/3)
[ 1404.121449] wlan0: RX AssocResp from <MAC C-01 CRDVD> (capab=0x431 status=0 aid=1)
[ 1404.121904] wlan0: associated
[ 1404.121945] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1404.170584] wlan0: deauthenticating from <MAC C-01 CRDVD> by local choice (reason=2)
[ 1404.176138] wlan0: authenticate with <MAC C-01 CRDVD>
[ 1404.176368] wlan0: send auth to <MAC C-01 CRDVD> (try 1/3)
[ 1404.177782] wlan0: authenticated
[ 1404.184075] wlan0: associate with <MAC C-01 CRDVD> (try 1/3)
[ 1404.189661] wlan0: RX AssocResp from <MAC C-01 CRDVD> (capab=0x431 status=0 aid=1)
[ 1404.190031] wlan0: associated
[ 1685.546123] wlan0: deauthenticating from <MAC C-01 CRDVD> by local choice (reason=3)
[ 1692.091975] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1695.462525] wlan0: authenticate with <MAC C-01 CRDVD>
[ 1695.466457] wlan0: send auth to <MAC C-01 CRDVD> (try 1/3)
[ 1695.470272] wlan0: authenticated
[ 1695.472214] wlan0: associate with <MAC C-01 CRDVD> (try 1/3)
[ 1695.477989] wlan0: RX AssocResp from <MAC C-01 CRDVD> (capab=0x431 status=0 aid=1)
[ 1695.478381] wlan0: associated
[ 1695.478488] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1695.622898] wlan0: deauthenticating from <MAC C-01 CRDVD> by local choice (reason=2)
[ 1695.627285] wlan0: authenticate with <MAC C-01 CRDVD>
[ 1695.627518] wlan0: send auth to <MAC C-01 CRDVD> (try 1/3)
[ 1695.635916] wlan0: authenticated
[ 1695.640056] wlan0: associate with <MAC C-01 CRDVD> (try 1/3)
[ 1695.643753] wlan0: RX AssocResp from <MAC C-01 CRDVD> (capab=0x431 status=0 aid=1)
[ 1695.644161] wlan0: associated
[ 1831.077648] wlan0: deauthenticating from <MAC C-01 CRDVD> by local choice (reason=3)
[ 1832.019023] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1834.174148] wlan0: authenticate with <MAC C-01 CRDVD>
[ 1834.178464] wlan0: send auth to <MAC C-01 CRDVD> (try 1/3)
[ 1834.179877] wlan0: authenticated
[ 1834.185222] wlan0: associate with <MAC C-01 CRDVD> (try 1/3)
[ 1834.189891] wlan0: RX AssocResp from <MAC C-01 CRDVD> (capab=0x431 status=0 aid=1)
[ 1834.190266] wlan0: associated
[ 1834.190308] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1834.197937] wlan0: deauthenticating from <MAC C-01 CRDVD> by local choice (reason=2)
[ 1834.201069] wlan0: authenticate with <MAC C-01 CRDVD>
[ 1834.201302] wlan0: send auth to <MAC C-01 CRDVD> (try 1/3)
[ 1834.211036] wlan0: authenticated
[ 1834.212194] wlan0: associate with <MAC C-01 CRDVD> (try 1/3)
[ 1834.215927] wlan0: RX AssocResp from <MAC C-01 CRDVD> (capab=0x431 status=0 aid=1)
[ 1834.216328] wlan0: associated
[ 2263.072200] wlan0: deauthenticating from <MAC C-01 CRDVD> by local choice (reason=3)
[ 2264.018813] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2266.055403] wlan0: authenticate with <MAC C-01 CRDVD>
[ 2266.060055] wlan0: send auth to <MAC C-01 CRDVD> (try 1/3)
[ 2266.061770] wlan0: authenticated
[ 2266.068065] wlan0: associate with <MAC C-01 CRDVD> (try 1/3)
[ 2266.072870] wlan0: RX AssocResp from <MAC C-01 CRDVD> (capab=0x431 status=0 aid=1)
[ 2266.073259] wlan0: associated
[ 2266.073301] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2266.083682] wlan0: deauthenticating from <MAC C-01 CRDVD> by local choice (reason=2)
[ 2266.091556] wlan0: authenticate with <MAC C-01 CRDVD>
[ 2266.091785] wlan0: send auth to <MAC C-01 CRDVD> (try 1/3)
[ 2266.093198] wlan0: authenticated
[ 2266.100066] wlan0: associate with <MAC C-01 CRDVD> (try 1/3)
[ 2266.105746] wlan0: RX AssocResp from <MAC C-01 CRDVD> (capab=0x431 status=0 aid=1)
[ 2266.106130] wlan0: associated
[ 2360.053086] wlan0: deauthenticating from <MAC C-01 CRDVD> by local choice (reason=3)
[ 2361.019610] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2362.837674] wlan0: authenticate with <MAC C-01 CRDVD>
[ 2362.841395] wlan0: send auth to <MAC C-01 CRDVD> (try 1/3)
[ 2362.944059] wlan0: send auth to <MAC C-01 CRDVD> (try 2/3)
[ 2363.048062] wlan0: send auth to <MAC C-01 CRDVD> (try 3/3)
[ 2363.049531] wlan0: authenticated
[ 2363.052075] wlan0: associate with <MAC C-01 CRDVD> (try 1/3)
[ 2363.056344] wlan0: RX AssocResp from <MAC C-01 CRDVD> (capab=0x431 status=0 aid=1)
[ 2363.056721] wlan0: associated
[ 2363.056757] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2363.072467] wlan0: deauthenticating from <MAC C-01 CRDVD> by local choice (reason=2)
[ 2363.080373] wlan0: authenticate with <MAC C-01 CRDVD>
[ 2363.080604] wlan0: send auth to <MAC C-01 CRDVD> (try 1/3)
[ 2363.082989] wlan0: authenticated
[ 2363.092062] wlan0: associate with <MAC C-01 CRDVD> (try 1/3)
[ 2363.100959] wlan0: RX AssocResp from <MAC C-01 CRDVD> (capab=0x431 status=0 aid=1)
[ 2363.101332] wlan0: associated
[ 2591.062896] wlan0: deauthenticating from <MAC C-01 CRDVD> by local choice (reason=3)
[ 2592.018823] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2594.241951] wlan0: authenticate with <MAC C-01 CRDVD>
[ 2594.251597] wlan0: send auth to <MAC C-01 CRDVD> (try 1/3)
[ 2594.253439] wlan0: authenticated
[ 2594.256250] wlan0: associate with <MAC C-01 CRDVD> (try 1/3)
[ 2594.260457] wlan0: RX AssocResp from <MAC C-01 CRDVD> (capab=0x431 status=0 aid=1)
[ 2594.260902] wlan0: associated
[ 2594.260938] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2594.270887] wlan0: deauthenticating from <MAC C-01 CRDVD> by local choice (reason=2)
[ 2594.276907] wlan0: authenticate with <MAC C-01 CRDVD>
[ 2594.277135] wlan0: send auth to <MAC C-01 CRDVD> (try 1/3)
[ 2594.278522] wlan0: authenticated
[ 2594.284296] wlan0: associate with <MAC C-01 CRDVD> (try 1/3)
[ 2594.288804] wlan0: RX AssocResp from <MAC C-01 CRDVD> (capab=0x431 status=0 aid=1)
[ 2594.289175] wlan0: associated
[ 2886.077222] wlan0: deauthenticating from <MAC C-01 CRDVD> by local choice (reason=3)
[ 2887.018836] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2889.081760] wlan0: authenticate with <MAC C-01 CRDVD>
[ 2889.090147] wlan0: send auth to <MAC C-01 CRDVD> (try 1/3)
[ 2889.093966] wlan0: authenticated
[ 2889.096209] wlan0: associate with <MAC C-01 CRDVD> (try 1/3)
[ 2889.101326] wlan0: RX AssocResp from <MAC C-01 CRDVD> (capab=0x431 status=0 aid=1)
[ 2889.101714] wlan0: associated
[ 2889.101836] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2889.107044] wlan0: deauthenticating from <MAC C-01 CRDVD> by local choice (reason=2)
[ 2889.115613] wlan0: authenticate with <MAC C-01 CRDVD>
[ 2889.115842] wlan0: send auth to <MAC C-01 CRDVD> (try 1/3)
[ 2889.117253] wlan0: authenticated
[ 2889.124109] wlan0: associate with <MAC C-01 CRDVD> (try 1/3)
[ 2889.135097] wlan0: RX AssocResp from <MAC C-01 CRDVD> (capab=0x431 status=0 aid=1)
[ 2889.135559] wlan0: associated
[ 3077.212555] wlan0: deauthenticating from <MAC C-01 CRDVD> by local choice (reason=3)
[ 3108.827222] ath5k 0000:0a:03.0: registered as 'phy0'
[ 3109.566353] ath: EEPROM regdomain: 0x63
[ 3109.566359] ath: EEPROM indicates we should expect a direct regpair map
[ 3109.566364] ath: Country alpha2 being used: 00
[ 3109.566366] ath: Regpair used: 0x63
[ 3109.570213] ath5k: phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
[ 3109.868318] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3109.874010] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3120.204997] wlan0: authenticate with <MAC C-01 CRDVD>
[ 3120.209667] wlan0: send auth to <MAC C-01 CRDVD> (try 1/3)
[ 3120.211204] wlan0: authenticated
[ 3125.212026] wlan0: deauthenticating from <MAC C-01 CRDVD> by local choice (reason=3)
[ 3135.324150] wlan0: authenticate with <MAC C-01 CRDVD>
[ 3135.324383] wlan0: send auth to <MAC C-01 CRDVD> (try 1/3)
[ 3135.326382] wlan0: authenticated
[ 3140.325017] wlan0: deauthenticating from <MAC C-01 CRDVD> by local choice (reason=3)
[ 3150.832166] wlan0: authenticate with <MAC C-01 CRDVD>
[ 3150.832398] wlan0: send auth to <MAC C-01 CRDVD> (try 1/3)
[ 3150.936057] wlan0: send auth to <MAC C-01 CRDVD> (try 2/3)
[ 3150.937452] wlan0: authenticated
[ 3155.837644] wlan0: deauthenticating from <MAC C-01 CRDVD> by local choice (reason=3)
[ 3166.847219] wlan0: authenticate with <MAC C-01 CRDVD>
[ 3166.847452] wlan0: send auth to <MAC C-01 CRDVD> (try 1/3)
[ 3166.849563] wlan0: authenticated
[ 3171.849611] wlan0: deauthenticating from <MAC C-01 CRDVD> by local choice (reason=3)
[ 3183.018738] wlan0: authenticate with <MAC C-01 CRDVD>
[ 3183.018968] wlan0: send auth to <MAC C-01 CRDVD> (try 1/3)
[ 3183.124059] wlan0: send auth to <MAC C-01 CRDVD> (try 2/3)
[ 3183.126268] wlan0: authenticated
[ 3188.024138] wlan0: deauthenticating from <MAC C-01 CRDVD> by local choice (reason=3)
[ 3208.034914] wlan0: authenticate with <MAC C-01 CRDVD>
[ 3208.035142] wlan0: send auth to <MAC C-01 CRDVD> (try 1/3)
[ 3208.038935] wlan0: authenticated
[ 3213.036151] wlan0: deauthenticating from <MAC C-01 CRDVD> by local choice (reason=3)
[ 3246.018522] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3534.006974] wlan0: authenticate with <MAC C-01 CRDVD>
[ 3534.007209] wlan0: send auth to <MAC C-01 CRDVD> (try 1/3)
[ 3534.009608] wlan0: authenticated
[ 3539.010282] wlan0: deauthenticating from <MAC C-01 CRDVD> by local choice (reason=3)
[ 3549.119622] wlan0: authenticate with <MAC C-01 CRDVD>
[ 3549.119857] wlan0: send auth to <MAC C-01 CRDVD> (try 1/3)
[ 3549.224059] wlan0: send auth to <MAC C-01 CRDVD> (try 2/3)
[ 3549.225464] wlan0: authenticated
[ 3554.006838] wlan0: deauthenticating from <MAC C-01 CRDVD> by local choice (reason=3)
[ 3564.027457] wlan0: authenticate with <MAC C-01 CRDVD>
[ 3564.027688] wlan0: send auth to <MAC C-01 CRDVD> (try 1/3)
[ 3564.029872] wlan0: authenticated
[ 3569.030763] wlan0: deauthenticating from <MAC C-01 CRDVD> by local choice (reason=3)
[ 3579.538773] wlan0: authenticate with <MAC C-01 CRDVD>
[ 3579.539011] wlan0: send auth to <MAC C-01 CRDVD> (try 1/3)
[ 3579.640057] wlan0: send auth to <MAC C-01 CRDVD> (try 2/3)
[ 3579.641447] wlan0: authenticated
[ 3582.007302] wlan0: deauthenticating from <MAC C-01 CRDVD> by local choice (reason=3)
[ 3592.018767] wlan0: authenticate with <MAC C-01 CRDVD>
[ 3592.018996] wlan0: send auth to <MAC C-01 CRDVD> (try 1/3)
[ 3592.022599] wlan0: authenticated
[ 3597.020063] wlan0: deauthenticating from <MAC C-01 CRDVD> by local choice (reason=3)
[ 3608.024120] wlan0: authenticate with <MAC C-01 CRDVD>
[ 3608.024349] wlan0: send auth to <MAC C-01 CRDVD> (try 1/3)
[ 3608.128058] wlan0: send auth to <MAC C-01 CRDVD> (try 2/3)
[ 3608.129473] wlan0: authenticated
[ 3610.006800] wlan0: deauthenticating from <MAC C-01 CRDVD> by local choice (reason=3)
[ 3620.033960] wlan0: authenticate with <MAC C-01 CRDVD>
[ 3620.034193] wlan0: send auth to <MAC C-01 CRDVD> (try 1/3)
[ 3620.035595] wlan0: authenticated
[ 3625.039434] wlan0: deauthenticating from <MAC C-01 CRDVD> by local choice (reason=3)
[ 3726.017518] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3732.028932] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3803.018418] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3948.146562] wlan0: authenticate with <MAC C-01 CRDVD>
[ 3948.146806] wlan0: send auth to <MAC C-01 CRDVD> (try 1/3)
[ 3948.148286] wlan0: authenticated
[ 3953.147093] wlan0: deauthenticating from <MAC C-01 CRDVD> by local choice (reason=3)
[ 3966.134600] wlan0: authenticate with <MAC C-01 CRDVD>
[ 3966.134832] wlan0: send auth to <MAC C-01 CRDVD> (try 1/3)
[ 3966.136245] wlan0: authenticated
[ 3971.139870] wlan0: deauthenticating from <MAC C-01 CRDVD> by local choice (reason=3)
[ 3981.646790] wlan0: authenticate with <MAC C-01 CRDVD>
[ 3981.647018] wlan0: send auth to <MAC C-01 CRDVD> (try 1/3)
[ 3981.650815] wlan0: authenticated
[ 3986.650746] wlan0: deauthenticating from <MAC C-01 CRDVD> by local choice (reason=3)
[ 3997.659209] wlan0: authenticate with <MAC C-01 CRDVD>
[ 3997.659441] wlan0: send auth to <MAC C-01 CRDVD> (try 1/3)
[ 3997.660823] wlan0: authenticated
[ 4002.664677] wlan0: deauthenticating from <MAC C-01 CRDVD> by local choice (reason=3)
[ 4017.675710] wlan0: authenticate with <MAC C-01 CRDVD>
[ 4017.675939] wlan0: send auth to <MAC C-01 CRDVD> (try 1/3)
[ 4017.679898] wlan0: authenticated
[ 4019.007381] wlan0: deauthenticating from <MAC C-01 CRDVD> by local choice (reason=3)
[ 4029.020287] wlan0: authenticate with <MAC C-01 CRDVD>
[ 4029.020516] wlan0: send auth to <MAC C-01 CRDVD> (try 1/3)
[ 4029.124058] wlan0: send auth to <MAC C-01 CRDVD> (try 2/3)
[ 4029.125461] wlan0: authenticated
[ 4034.021658] wlan0: deauthenticating from <MAC C-01 CRDVD> by local choice (reason=3)
[ 4034.022178] wlan0: authenticate with <MAC C-01 CRDVD>
[ 4034.022405] wlan0: send auth to <MAC C-01 CRDVD> (try 1/3)
[ 4034.023953] wlan0: authenticated
[ 4039.024150] wlan0: deauthenticating from <MAC C-01 CRDVD> by local choice (reason=3)
[ 4357.130514] wlan0: authenticate with <MAC C-01 CRDVD>
[ 4357.130742] wlan0: send auth to <MAC C-01 CRDVD> (try 1/3)
[ 4357.132829] wlan0: authenticated
[ 4362.135977] wlan0: deauthenticating from <MAC C-01 CRDVD> by local choice (reason=3)
[ 4382.019150] wlan0: authenticate with <MAC C-01 CRDVD>
[ 4382.019380] wlan0: send auth to <MAC C-01 CRDVD> (try 1/3)
[ 4382.022555] wlan0: authenticated
[ 4387.023329] wlan0: deauthenticating from <MAC C-01 CRDVD> by local choice (reason=3)
[ 4407.032166] wlan0: authenticate with <MAC C-01 CRDVD>
[ 4407.032398] wlan0: send auth to <MAC C-01 CRDVD> (try 1/3)
[ 4407.034288] wlan0: authenticated
[ 4412.037023] wlan0: deauthenticating from <MAC C-01 CRDVD> by local choice (reason=3)
[ 4432.054604] wlan0: authenticate with <MAC C-01 CRDVD>
[ 4432.054837] wlan0: send auth to <MAC C-01 CRDVD> (try 1/3)
[ 4432.056348] wlan0: authenticated
[ 4437.058848] wlan0: deauthenticating from <MAC C-01 CRDVD> by local choice (reason=3)
[ 4766.150765] wlan0: authenticate with <MAC C-01 CRDVD>
[ 4766.150995] wlan0: send auth to <MAC C-01 CRDVD> (try 1/3)
[ 4766.153603] wlan0: authenticated
[ 4771.156217] wlan0: deauthenticating from <MAC C-01 CRDVD> by local choice (reason=3)
[ 4791.021739] wlan0: authenticate with <MAC C-01 CRDVD>
[ 4791.021971] wlan0: send auth to <MAC C-01 CRDVD> (try 1/3)
[ 4791.124057] wlan0: send auth to <MAC C-01 CRDVD> (try 2/3)
[ 4791.126335] wlan0: authenticated
[ 4796.024144] wlan0: deauthenticating from <MAC C-01 CRDVD> by local choice (reason=3)
[ 4816.029278] wlan0: authenticate with <MAC C-01 CRDVD>
[ 4816.029509] wlan0: send auth to <MAC C-01 CRDVD> (try 1/3)
[ 4816.032991] wlan0: authenticated
[ 4821.034743] wlan0: deauthenticating from <MAC C-01 CRDVD> by local choice (reason=3)
[ 4841.048165] wlan0: authenticate with <MAC C-01 CRDVD>
[ 4841.048395] wlan0: send auth to <MAC C-01 CRDVD> (try 1/3)
[ 4841.152067] wlan0: send auth to <MAC C-01 CRDVD> (try 2/3)
[ 4841.153624] wlan0: authenticated
[ 4846.051138] wlan0: deauthenticating from <MAC C-01 CRDVD> by local choice (reason=3)
[ 5175.167722] wlan0: authenticate with <MAC C-01 CRDVD>
[ 5175.167957] wlan0: send auth to <MAC C-01 CRDVD> (try 1/3)
[ 5175.169407] wlan0: authenticated
[ 5180.173491] wlan0: deauthenticating from <MAC C-01 CRDVD> by local choice (reason=3)
[ 5200.023893] wlan0: authenticate with <MAC C-01 CRDVD>
[ 5200.024763] wlan0: send auth to <MAC C-01 CRDVD> (try 1/3)
[ 5200.026267] wlan0: authenticated
[ 5205.026335] wlan0: deauthenticating from <MAC C-01 CRDVD> by local choice (reason=3)
[ 5215.018545] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5235.054139] wlan0: authenticate with <MAC C-01 CRDVD>
[ 5235.054375] wlan0: send auth to <MAC C-01 CRDVD> (try 1/3)
[ 5235.060932] wlan0: authenticated
[ 5240.058361] wlan0: deauthenticating from <MAC C-01 CRDVD> by local choice (reason=3)
[ 5240.058879] wlan0: authenticate with <MAC C-01 CRDVD>
[ 5240.059101] wlan0: send auth to <MAC C-01 CRDVD> (try 1/3)
[ 5240.061503] wlan0: authenticated
[ 5245.059309] wlan0: deauthenticating from <MAC C-01 CRDVD> by local choice (reason=3)
[ 5245.059759] wlan0: authenticate with <MAC C-01 CRDVD>
[ 5245.059980] wlan0: send auth to <MAC C-01 CRDVD> (try 1/3)
[ 5245.062706] wlan0: authenticated
[ 5250.064162] wlan0: deauthenticating from <MAC C-01 CRDVD> by local choice (reason=3)
[ 5261.067619] wlan0: authenticate with <MAC C-01 CRDVD>
[ 5261.067853] wlan0: send auth to <MAC C-01 CRDVD> (try 1/3)
[ 5261.070896] wlan0: authenticated
[ 5266.069119] wlan0: deauthenticating from <MAC C-01 CRDVD> by local choice (reason=3)
[ 5281.081728] wlan0: authenticate with <MAC C-01 CRDVD>
[ 5281.081962] wlan0: send auth to <MAC C-01 CRDVD> (try 1/3)
[ 5281.188058] wlan0: send auth to <MAC C-01 CRDVD> (try 2/3)
[ 5281.189446] wlan0: authenticated
[ 5282.007639] wlan0: deauthenticating from <MAC C-01 CRDVD> by local choice (reason=3)
[ 5292.024849] wlan0: authenticate with <MAC C-01 CRDVD>
[ 5292.025081] wlan0: send auth to <MAC C-01 CRDVD> (try 1/3)
[ 5292.028223] wlan0: authenticated
[ 5297.027254] wlan0: deauthenticating from <MAC C-01 CRDVD> by local choice (reason=3)
[ 5297.027588] wlan0: authenticate with <MAC C-01 CRDVD>
[ 5297.027819] wlan0: send auth to <MAC C-01 CRDVD> (try 1/3)
[ 5297.132031] wlan0: send auth to <MAC C-01 CRDVD> (try 2/3)
[ 5297.133508] wlan0: authenticated
[ 5302.033064] wlan0: deauthenticating from <MAC C-01 CRDVD> by local choice (reason=3)


    ======== Done ========



```

I'll do the dump on my "A" router tomorrow after I get back.

---

### Post by varunendra on 2014-08-17
> **Pidge66 said:**
> How is hiding SSID not "a bit" more secure?  I could not field that question.

Hiding SSID only prevents 'Accidental' access. It is the security key that prevents the intended attempt from unauthorized people.

If someone has the security key, 'Hiding' is meaningless (they will already have a saved profile with security key, or can create one).

If someone doesn't have it, they will be stopped at authentication stage when making an attempt to connect.

If someone is an attacker (knowledgeable about techniques, or a stupid with tools meant for that purpose), they don't rely on SSID at all. Even the most basic tools (not even meant for an attack) can detect the existence of your network and its other settings required to uniquely identify it (for example the "iwlist scan" command we used in the script). Rest of the process to attempt a connection/attack remains the same whether you are advertising your SSID or not.

So hiding it is fundamentally pointless. If an authorized person wants to connect to it, they can and will whenever they want.
If an unauthorized person want's to 'attack', they can and will whenever they want. It won't take them more than two seconds to see how many networks are active near them, and not more than half a minute to figure out how many of them are really accessible/vulnerable.

In order to connect to a network, a system MUST advertise its ARP (Address Resolution Protocol) packets - it is the fundamental requirement for a networking to work. But I'm afraid I don't have enough knowledge about ARP packets to explain clearly how it works and why it is necessary, and any attempt to do so may result in wrong and confusing information. If you are interested, search and you'll find plenty of information on it.

---

### Post by Pidge66 on 2014-08-17
Thanks for the detailed answer regarding hiding SSID !!

So, I'm back to my weekday router "A".  Again, sitting next to the router (level ~82%) my Lubuntu has no problem accessing the internet; however, in my room (level ~48%), internet requests would time out.

Here's the wireless-script dump while subjecting to the latter condition.  Any suggestions would be greatly appreciated.  Thanks!

```


    ======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


henry-TravelMate-2480 3.13.0-33-generic i686,  Ubuntu 14.04.1 LTS, trusty


CPU    : Intel(R) Celeron(R) M CPU        420  @ 1.60GHz
Memory : 992 MB
Uptime : 21:27:25 up 4 min,  2 users,  load average: 1.65, 2.49, 1.22




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller [11ab:4352] (rev 14)
    Subsystem: Acer Incorporated [ALI] Device [1025:0110]
    Kernel driver in use: sky2
0a:03.0 Ethernet controller [0200]: Qualcomm Atheros AR2413/AR2414 Wireless Network Adapter [AR5005G(S) 802.11bg] [168c:001a] (rev 01)
    Subsystem: AMBIT Microsystem Corp. Device [1468:0418]
    Kernel driver in use: ath5k




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     IEEE 802.11bg  ESSID:"MSHOME"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC C-01 MSHOME>   
          Bit Rate=36 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=41/70  Signal level=-69 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:20  Invalid misc:2   Missed beacon:0






rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


      Interface                 Soft blocked  Hard blocked
0: acer-wireless: Wireless LAN      no            no
1: phy0: Wireless LAN               no            no




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


acer_wmi               31735  0 
sparse_keymap          13708  1 acer_wmi
ath5k                 134977  0 
ath                    23922  1 ath5k
mac80211              546051  1 ath5k
cfg80211              409394  3 ath,ath5k,mac80211
wmi                    18673  1 acer_wmi
video                  18903  2 i915,acer_wmi




module parameters ~~~~~~~~~~~~~~~~~~


acer_wmi      (5): brightness=-1 | ec_raw_mode=N | force_series=0 | mailled=-1 | threeg=-1
ath5k         (3): fastchanswitch=N | nohwcrypt=N | no_hw_rfkill_switch=N
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=-1
wmi           (2): debug_dump_wdg=N | debug_event=N




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: connected (global)
=================o=============o========o=========  ====o=========o===========o==============o========  ===
 Interface & ID  | Type        | Driver | State       | Default | Speed     | Support      | HW Addr   
=================o=============o========o=========  ====o=========o===========o==============o========  ===
 wlan0  [MSHOME] | 802.11 WiFi | ath5k  | connected   | yes     | 1 Mb/s    | WEP/WPA/WPA2 | <MAC wlan0>


    DIRECT-roku-527: Infra, <MAC C-03 DIRECT-roku-527>, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WPA2
    5DH67:           Infra, <MAC C-02 5DH67>, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WPA2
    Linares:         Infra, <MAC C-NA Linares 1>, Freq 2427 MHz, Rate 54 Mb/s, Strength 9 WPA2
    *MSHOME:         Infra, <MAC C-01 MSHOME>, Freq 2412 MHz, Rate 54 Mb/s, Strength 51 WPA2
    DIRECT-roku-752: Infra, <MAC C-NA DIRECT-roku-752 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 15 WPA2


    Address:         192.168.1.188
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             192.168.1.1
-----------------+-------------+--------+-------------+---------+-----------+--------------+-----------
 eth0            | Wired       | sky2   | unavailable | no      |           |              | <MAC eth0>
-----------------+-------------+--------+-------------+---------+-----------+--------------+-----------




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


CRDVD                : ssid=CRDVD | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
MSHOME               : ssid=MSHOME | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Palumbo Pizza        : ssid=Palumbo Pizza | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Palumbo Pizza-guest  : ssid=Palumbo Pizza-guest | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 




interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~


nameserver 127.0.1.1




Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


--- 192.168.1.1 ping statistics ---
3 packets transmitted, 2 received, 33% packet loss, time 2008ms
rtt min/avg/max/mdev = 170.095/210.094/250.094/40.002 ms


--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1000ms
rtt min/avg/max/mdev = 0.043/0.047/0.051/0.004 ms




iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~


(Region : en_US.UTF-8)




iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)


          Current Frequency=2.412 GHz (Channel 1)




iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 MSHOME>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"MSHOME"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001187951774b
                    Extra: Last beacon: 124ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 5DH67>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"5DH67"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000003249b682180
                    Extra: Last beacon: 188ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 DIRECT-roku-527>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"DIRECT-roku-527"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000758fba4000
                    Extra: Last beacon: 132ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK




blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/libpisock9.conf]
blacklist visor




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[acer_wmi]
filename:       /lib/modules/3.13.0-33-generic/kernel/drivers/platform/x86/acer-wmi.ko
srcversion:     15371DC0E403E93954B38E5
depends:        wmi,sparse-keymap,video
parm:           mailled:Set initial state of Mail LED (int)
parm:           brightness:Set initial LCD backlight brightness (int)
parm:           threeg:Set initial state of 3G hardware (int)
parm:           force_series:Force a different laptop series (int)
parm:           ec_raw_mode:Enable EC raw mode (bool)


[ath5k]
filename:       /lib/modules/3.13.0-33-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
srcversion:     F36818A2F0BCB2B0CC9BB8C
depends:        mac80211,cfg80211,ath
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)


[ath]
filename:       /lib/modules/3.13.0-33-generic/kernel/drivers/net/wireless/ath/ath.ko
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211


[mac80211]
filename:       /lib/modules/3.13.0-33-generic/kernel/net/mac80211/mac80211.ko
srcversion:     8ADA881D348148A3358334C
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.13.0-33-generic/kernel/net/wireless/cfg80211.ko
srcversion:     E786D076B61F97809B04B64
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[wmi]
filename:       /lib/modules/3.13.0-33-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


[video]
filename:       /lib/modules/3.13.0-33-generic/kernel/drivers/acpi/video.ko
srcversion:     274A2250DEAB415D412A67C
depends:        
parm:           brightness_switch_enabled:bool
parm:           allow_duplicates:bool
parm:           use_native_backlight:int




udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~


# PCI device 0x11ab:0x4352 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x168c:0x001a (ath5k)
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


BOOT_IMAGE=/vmlinuz-3.13.0-33-generic root=/dev/mapper/lubuntu--vg-root ro quiet splash vt.handoff=7




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    1.399608] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.400123] audit: initializing netlink socket (disabled)
[   17.434284] wmi: Mapper loaded
[   18.215991] ath5k 0000:0a:03.0: registered as 'phy0'
[   18.773654] acer_wmi: Acer Laptop ACPI-WMI Extras
[   18.775625] acer_wmi: Function bitmap for Communication Device: 0x27
[   18.775640] acer_wmi: Disabling ACPI video driver
[   19.663382] ath: EEPROM regdomain: 0x63
[   19.663387] ath: EEPROM indicates we should expect a direct regpair map
[   19.663391] ath: Country alpha2 being used: 00
[   19.663394] ath: Regpair used: 0x63
[   19.677052] ath5k: phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
[   81.204835] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   84.271773] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   84.272949] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   86.677385] wlan0: authenticate with <MAC C-01 MSHOME>
[   86.682147] wlan0: send auth to <MAC C-01 MSHOME> (try 1/3)
[   86.756847] wlan0: send auth to <MAC C-01 MSHOME> (try 2/3)
[   86.769723] wlan0: authenticated
[   86.772060] wlan0: associate with <MAC C-01 MSHOME> (try 1/3)
[   86.774834] wlan0: RX AssocResp from <MAC C-01 MSHOME> (capab=0x411 status=0 aid=5)
[   86.775215] wlan0: associated
[   86.775249] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  126.858053] wlan0: deauthenticating from <MAC C-01 MSHOME> by local choice (reason=3)
[  127.833194] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  129.172472] wlan0: authenticate with <MAC C-01 MSHOME>
[  129.172720] wlan0: send auth to <MAC C-01 MSHOME> (try 1/3)
[  129.174226] wlan0: authenticated
[  129.176264] wlan0: associate with <MAC C-01 MSHOME> (try 1/3)
[  129.179382] wlan0: RX AssocResp from <MAC C-01 MSHOME> (capab=0x411 status=0 aid=5)
[  129.179759] wlan0: associated
[  129.179801] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  170.825436] wlan0: authenticate with <MAC C-01 MSHOME>
[  170.830802] wlan0: send auth to <MAC C-01 MSHOME> (try 1/3)
[  170.899764] wlan0: authenticated
[  170.904053] wlan0: associate with <MAC C-01 MSHOME> (try 1/3)
[  170.906637] wlan0: RX AssocResp from <MAC C-01 MSHOME> (capab=0x411 status=0 aid=5)
[  170.907019] wlan0: associated
[  212.761458] wlan0: authenticate with <MAC C-01 MSHOME>
[  212.766728] wlan0: send auth to <MAC C-01 MSHOME> (try 1/3)
[  212.838203] wlan0: authenticated
[  212.840214] wlan0: associate with <MAC C-01 MSHOME> (try 1/3)
[  212.842787] wlan0: RX AssocResp from <MAC C-01 MSHOME> (capab=0x411 status=0 aid=5)
[  212.843177] wlan0: associated


    ======== Done ========



```

---

### Post by varunendra on 2014-08-19
Sorry for a late reply, deadlines are killing me. Anyway..

The only thing we can do about signal strength at the OS side is to try increasing the Tx Power, but that is already 20 dBm which is quite sufficient (and max for most regions). So I don't think we can do anything about it in your case.

However, the 'iwconfig' part shows the connection speed to be 36 Mbps, while 'nm-tool' part shows it to be 1 Mbps. So it seems the speed is badly fluctuating depending on the signal strength. See if setting it to a fixed value can help -

```
sudo iwconfig wlan0 rate 24M
```
Other acceptable values (between 1 to 54 Mbps) are - 5.5M, 11M, 18M, 36M. The usual routine is to try the lowest "workable" speed (5.5M) to see if it can at least bring some stability to the connection, then try higher values that seem stable.

To reset it to auto, just run -
```
sudo iwconfig wlan0 rate auto
```
..or it will reset automatically on next boot. If fixing the speed helps, we can make it permanent by adding the command to /etc/rc.local file.

Please also try the module parameter (along with the above if required) -
```
sudo modprobe -rv ath5k
sudo modprobe -v ath5k nohwcrypt=Y
```

**PS:**
Seeing how old the system/card is, you may also try WPA(1) with TKIP in the router, assuming it may not be able to do well with WPA2/AES. But if it doesn't make any difference, WPA2/AES is recommended for higher security/performance (performance on other devices that can handle it nicely).

---

### Post by Pidge66 on 2014-08-19
Thanks. I guess this was the last straw.  I changed the rate to 5.5M and 11M but neither case made a difference.  We've tried enough and should close the case.  At least it is still usable near a wifi router.

A few things bug me a little, however:

I was **not** able to reconnect to the wifi after **any** of your modprobe operations.  And a couple of times, the command had an error output "sudo: unable to resolve host henry-TravelMate-2480", even though it proceeded to install/uninstall the driver.

---

### Post by Pidge66 on 2014-08-20
Good news to report.  All the interactions with this thread somehow brought my attention to one of the wireless-script output, channel.  My output indicated channel 1 was used.  I then reconfigured my wifi router and changed channel setting from **AUTO** to **6**.  And it actually made a difference!!!   Now my room gets like 59% of signal strength and I can actually surf the net!

Thanks Varun for sticking with me!

---

### Post by varunendra on 2014-08-21
> **Pidge66 said:**
> ..changed channel setting from **AUTO** to **6**..

Oww..! Why didn't I think of that? :p

So pleased you got it sorted, thanks for the feedback (..and the heads up! I'll never take the channel setting for granted now I guess.. :p).

---

### Post by Polaka on 2015-07-30
> **varunendra said:**
> However, if it doesn't seem to help, try another parameter that is common for all athxx drivers -
```
sudo modprobe -rv ath5k
sudo modprobe -v ath5k nohwcrypt=Y
```

Thank you so much!! You saved my life! I had the same problem, and this solution worked for me. Thanks again!

---

