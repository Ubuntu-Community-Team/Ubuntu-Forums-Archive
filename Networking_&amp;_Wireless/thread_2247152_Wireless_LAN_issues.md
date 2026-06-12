---
title: "Wireless LAN issues"
date: 2014-10-06
forum: Networking &amp; Wireless
---

### Post by lamogo on 2014-10-06
Let me just start by saying I love Ubuntu, and have been using all flavors for more than 5 years, and don't visit this site much since I can solve most issues, but not sure what to do with this one...

I'm aware that what I am doing is a little unorthodoxed.

I just installed Ubuntu [Server] on to an older laptop, and have it connected via wifi. One issue that I am having is that one I close the lid, it cuts the wifi. I changed the line in cd /etc/systemd/logind to read HandleLidSwitch=ignore which I beleive is keeping the laptop from suspending, however, my wifi is shutting off, keeping me disconnected from my server. Is it possible to keep wifi running when my lid is closed?

Acer Aspire 5050
```

lspci
08:04.0 Ethernet controller: Qualcomm Atheros AR2413/AR2414 Wireless Network Adapter [AR5005G(S) 802.11bg] (rev 01)

```

Any help would be appreciated.

---

### Post by varunendra on 2014-10-06
Please follow the instructions in this post to download and run 'wireless_script' (alternative version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

### Post by lamogo on 2014-10-06
```
        ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

server 3.13.0-32-generic i686,  Ubuntu 14.04.1 LTS, trusty

CPU    : AMD Turion(tm) 64 X2 Mobile Technology TL-50
Memory : 2267 MB
Uptime : 01:54:21 up 1 min,  1 user,  load average: 0.45, 0.34, 0.13


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

08:02.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [10ec:8139] (rev 10)
        Subsystem: Acer Incorporated [ALI] Device [1025:010f]
        Kernel driver in use: 8139too
08:04.0 Ethernet controller [0200]: Qualcomm Atheros AR2413/AR2414 Wireless Network Adapter [AR5005G(S) 802.11bg] [168c:001a] (rev 01)
        Subsystem: AMBIT Microsystem Corp. Device [1468:0418]
        Kernel driver in use: ath5k


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 002: ID 0c45:6260 Microdia PC Camera (SN9C201 + OV7670ISP)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bg  ESSID:"Secure"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC C-01 Secure>   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=50/70  Signal level=-60 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:38   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

acer_wmi               31735  0 
sparse_keymap          13708  1 acer_wmi
video                  18903  1 acer_wmi
ath5k                 134977  0 
ath                    23922  1 ath5k
mac80211              546051  1 ath5k
cfg80211              409394  3 ath,ath5k,mac80211
wmi                    18673  1 acer_wmi


module parameters ~~~~~~~~~~~~~~~~~~

acer_wmi      (5): brightness=-1 | ec_raw_mode=N | force_series=0 | mailled=-1 | threeg=-1
ath5k         (3): fastchanswitch=N | nohwcrypt=N | no_hw_rfkill_switch=N
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=-1
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


================o======o========o========o========  =o===========o==============o===========
 Interface & ID | Type | Driver | State  | Default | Speed     | Support      | HW Addr   
================o======o========o========o========  =o===========o==============o===========
                |      |        |        |         |           |              |           
----------------+------+--------+--------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~


NetworkManager.conf ~~~~~~~~~~~~~~~~



NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~
 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 192.168.254.254
search netgear.com


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.254.254 0.0.0.0         UG    0      0        0 wlan0
192.168.254.0   0.0.0.0         255.255.255.0   U     0      0        0 wlan0

--- 192.168.254.254 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 1.011/1.034/1.057/0.023 ms

--- 192.168.254.254 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 0.917/0.967/1.018/0.059 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : en_US.UTF-8)
country US:
        (2402 - 2472 @ 40), (3, 27)
        (5170 - 5250 @ 40), (3, 17)
        (5250 - 5330 @ 40), (3, 20), DFS
        (5490 - 5600 @ 40), (3, 20), DFS
        (5650 - 5710 @ 40), (3, 20), DFS
        (5735 - 5835 @ 40), (3, 30)
        (57240 - 63720 @ 2160), (N/A, 40)


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     11 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 11 (2.462 GHz)

          Current Frequency=2.412 GHz (Channel 1)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 Secure>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"Secure"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000045493323c
                    Extra: Last beacon: 56ms ago
          Cell 02 - Address: <MAC C-02 linksys>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"linksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000082fd28a9c
                    Extra: Last beacon: 56ms ago
          Cell 03 - Address: <MAC C-03 linksys>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:off
                    ESSID:"linksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000fd4f126cb4
                    Extra: Last beacon: 56ms ago


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[acer_wmi]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/platform/x86/acer-wmi.ko
srcversion:     15371DC0E403E93954B38E5
depends:        wmi,sparse-keymap,video
parm:           mailled:Set initial state of Mail LED (int)
parm:           brightness:Set initial LCD backlight brightness (int)
parm:           threeg:Set initial state of 3G hardware (int)
parm:           force_series:Force a different laptop series (int)
parm:           ec_raw_mode:Enable EC raw mode (bool)

[video]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/acpi/video.ko
srcversion:     274A2250DEAB415D412A67C
depends:        
parm:           brightness_switch_enabled:bool
parm:           allow_duplicates:bool
parm:           use_native_backlight:int

[ath5k]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
srcversion:     F36818A2F0BCB2B0CC9BB8C
depends:        mac80211,cfg80211,ath
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)

[ath]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath.ko
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211

[mac80211]
filename:       /lib/modules/3.13.0-32-generic/kernel/net/mac80211/mac80211.ko
srcversion:     8ADA881D348148A3358334C
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

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

# PCI device 0x10ec:0x8139 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:0x001a (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Not Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/rc.local]
ifconfig eth0 down
ifconfig wlan0 down
dhclient -r wlan0
iwconfig wlan0 essid "Secure"
iwconfig wlan0 key 39DFF836A6
iwconfig wlan0 key open
iwconfig wlan0 mode Managed
ifconfig wlan0 up
dhclient wlan0
exit 0

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-32-generic root=UUID=57706d8e-a612-4b25-90b6-b6f72cbc2895 ro


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.982619] audit: initializing netlink socket (disabled)
[    6.436518] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    6.583940] 8139too: 8139too Fast Ethernet driver 0.9.28
[   19.065995] wmi: Mapper loaded
[   19.761704] ath5k 0000:08:04.0: registered as 'phy0'
[   20.083516] acer_wmi: Acer Laptop ACPI-WMI Extras
[   20.083898] acer_wmi: Function bitmap for Communication Device: 0x21
[   20.083974] acer_wmi: Disabling ACPI video driver
[   20.871144] ath: EEPROM regdomain: 0x63
[   20.871150] ath: EEPROM indicates we should expect a direct regpair map
[   20.871155] ath: Country alpha2 being used: 00
[   20.871157] ath: Regpair used: 0x63
[   20.882804] ath5k: phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
[   29.482552] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   30.364126] wlan0: authenticate with <MAC C-01 Secure>
[   30.368978] wlan0: send auth to <MAC C-01 Secure> (try 1/3)
[   30.371038] wlan0: authenticated
[   30.371072] ath5k 0000:08:04.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   30.372073] wlan0: associate with <MAC C-01 Secure> (try 1/3)
[   30.374055] wlan0: RX AssocResp from <MAC C-01 Secure> (capab=0x431 status=0 aid=2)
[   30.374442] wlan0: associated
[   30.374456] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   30.411120] ath: EEPROM regdomain: 0x8348
[   30.411128] ath: EEPROM indicates we should expect a country code
[   30.411132] ath: doing EEPROM country->regdmn map search
[   30.411134] ath: country maps to regdmn code: 0x3a
[   30.411136] ath: Country alpha2 being used: US
[   30.411139] ath: Regpair used: 0x3a
[   30.411141] ath: regdomain 0x8348 dynamically updated by country IE

        ======== Done ========


```

---

### Post by slickymaster on 2014-10-06
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by Hadaka on 2014-10-06
Hi, I use 12.04 but im sure 14.04 has a like setting.

Click-  System Settings.......Power..

[ATTACH=CONFIG]256978[/ATTACH]

---

### Post by varunendra on 2014-10-06
Sorry, I didn't read the first post correctly it seems. I guess I just read the title, the card in the code box, and jumped the gun thinking you are having some kind of disconnection problem (or maybe I got confused with multiple tabs open in my browser).

Anyway, assuming you don't have a GUI to do what Hadaka suggested (besides, that doesn't work sometimes as expected), have you already tried all that is suggested as answer to this question on askubuntu ? - [http://askubuntu.com/questions/15520/how-can-i-tell-ubuntu-to-do-nothing-when-i-close-my-laptop-lid](http://askubuntu.com/questions/15520/how-can-i-tell-ubuntu-to-do-nothing-when-i-close-my-laptop-lid)

It contains multiple suggestions, many of which can be applicable to your case. Please try the others and let us know if any of them worked for you.

One of the many suggestions, for special emphasis on it : [http://askubuntu.com/questions/360615/ubuntu-server-13-10-now-goes-to-sleep-when-closing-laptop-lid](http://askubuntu.com/questions/360615/ubuntu-server-13-10-now-goes-to-sleep-when-closing-laptop-lid)

---

### Post by lamogo on 2014-10-06
Thank you for the help.

As stated above in my original post I had already made the change in the systemd.conf and it is keeping my computer from suspending, however the wifi is turning off.

I can turn the server on and close the lid while it boots and the wifi stays on, as per one of your posts. 

so I'll mark this solved. Thank you again.

---

### Post by varunendra on 2014-10-06
> **lamogo said:**
> I can turn the server on and close the lid while it boots and the wifi stays on, **as per one of your posts**.

Err... my post? I don't remember having ever written such a 'trick' :p

But have you also tried the other suggestions from the first link? Maybe one of them could give you a more decent solution.

It may also help if we can get some clues from the system logs, especially - syslog, pm-powersave.log, pm-suspend.log in /var/log directory. But no clues=no more ideas :|

---

