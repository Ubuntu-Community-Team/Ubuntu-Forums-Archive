---
title: "Wired and Wireless not working after Clean install. [14.04.1]."
date: 2014-07-30
forum: Networking &amp; Wireless
---

### Post by s-l-425434 on 2014-07-30
Hello, this is my first post in the forums, so please don´t shoot me, if I´ve placed anything in the wrong section.

I´ve been fondling around with this for a couple of days, and I´m starting to get slightly frustrated, so figured it was time to look for some help.
I have a problem with my Acer Aspire E15 511 laptop. 
I installed Xubuntu 14.04.1 on it. The wired and wireless  worked in the bootable usb "Try" edition, but not in the final installation. (Though the various wireless networks do show up, just not able to connect), (The laptop has no optical drive).
I´ve tried another fresh install, installing ubuntu 14.04.1 and mint 17. Same issue persists across these distros. 
Now I´m back to xubuntu 14.04.1 

I´ve tried various methods of resolving, and found some fixes, messed around with firmware, deb files offline installs, the nonfree package, tried installing without updates and third party software,
 etc. etc. But clearly I´m a spass at this. 
(Just before posting this thread I made another clean install so the following information haven´t been messed up by my messing around).

Here´s a little info: 
[B]
Firstly:[/B]

```
 lspci

```

Gave me this: 
```
 00:00.0 Host bridge: Intel Corporation ValleyView SSA-CUnit (rev 0e)
00:02.0 VGA compatible controller: Intel Corporation ValleyView Gen7 (rev 0e)
00:13.0 SATA controller: Intel Corporation ValleyView 6-Port SATA AHCI Controller (rev 0e)
00:14.0 USB controller: Intel Corporation ValleyView USB xHCI Host Controller (rev 0e)
00:1a.0 Encryption controller: Intel Corporation ValleyView SEC (rev 0e)
00:1b.0 Audio device: Intel Corporation ValleyView High Definition Audio Controller (rev 0e)
00:1c.0 PCI bridge: Intel Corporation ValleyView PCI Express Root Port (rev 0e)
00:1c.1 PCI bridge: Intel Corporation ValleyView PCI Express Root Port (rev 0e)
00:1f.0 ISA bridge: Intel Corporation ValleyView Power Control Unit (rev 0e)
00:1f.3 SMBus: Intel Corporation ValleyView SMBus Controller (rev 0e)
01:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5287 (rev 01)
01:00.1 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 12)
02:00.0 Network controller: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01)

```

I´ve read something about that Realtek 8168 driver being somewhat of a culprit in theses issues but I´m not a native English speaker, and I´ve had a bit of trouble understanding those threads. 
[B]
Secondly: 
[/B]
```
ifconfig

```

Gave me this:

```
 eth0      Link encap:Ethernet  HWaddr f8:a9:63:75:bb:8a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:71 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4780 (4.7 KB)  TX bytes:13445 (13.4 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:52 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4016 (4.0 KB)  TX bytes:4016 (4.0 KB)

wlan0     Link encap:Ethernet  HWaddr b8:ee:65:bd:6e:da  
          inet6 addr: fe80::baee:65ff:febd:6eda/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3789 (3.7 KB)  TX bytes:6884 (6.8 KB) 
```

**Nextly:**

```
 iwconfig 
```

Gave me this:

```
 wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

eth0      no wireless extensions.

 
```



**Last:**

```
 sudo lshw -C network 
```

Gave me this:

```
[sudo] password for simon: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.1
       bus info: pci@0000:01:00.1
       logical name: eth0
       version: 12
       serial: f8:a9:63:75:bb:8a
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8411-2_0.0.1 07/08/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:106 ioport:1000(size=256) memory:90504000-90504fff memory:90500000-90503fff
  *-network
       description: Wireless interface
       product: QCA9565 / AR9565 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: b8:ee:65:bd:6e:da
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.13.0-32-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:90400000-9047ffff memory:90480000-9048ffff
```



Sorry if I´ve posted irrellevant information, I´m new to this.

I hope some kind soul out there knows what I need to do, to get this to work. 

Best Regards
-Simon.

---

### Post by varunendra on 2014-07-31
Welcome to the forums Simon!

Please disconnect your Ethernet network cable, wait for a couple of minutes (or just reboot while keeping the cable unplugged) and try to connect with Wireless again.

Network Manager prefers the cable connection when it is available, and in that case, it may not attempt to connect via wireless at all. So make sure to keep the Ethernet cable unplugged while trying to connect wirelessly. It is not necessary, but it is good to remove it for now to avoid system confusion.

As for the Ethernet (wired) connection, we may need to install a tiny program 'ethtool' to fix it. That would be easy if you can connect to internet via the wireless connection, which should be fine after disconnecting the ethernet cable.

If you can't connect wirelessly even after disconnecting the ethernet cable, please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

### Post by s-l-425434 on 2014-07-31
Hey and thanks for the welcome! 

I have tried unplugging the cable and rebooting multiple times, and disabling bluetooth on boot to avoid interference. No luck there. 

Ran the script, wouldn´t execute it, so just dragndropped in terminal and ran without problems. 

```

 ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

simon-Aspire-E5-511 3.13.0-32-generic i686,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Pentium(R) CPU  N3530  @ 2.16GHz
Memory : 7966 MB
Uptime : 16:42:49 up 8 min,  2 users,  load average: 0.09, 0.09, 0.05


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

01:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
    Subsystem: Acer Incorporated [ALI] Device [1025:0905]
    Kernel driver in use: r8169
02:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
    Subsystem: Lite-On Communications Inc Device [11ad:0642]
    Kernel driver in use: ath9k


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04f2:b455 Chicony Electronics Co., Ltd 
Bus 001 Device 005: ID 04cf:8818 Myson Century, Inc. USB2.0 to ATAPI Bridge Controller
Bus 001 Device 004: ID 04ca:300b Lite-On Technology Corp. 
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface                 Soft blocked  Hard blocked
0: acer-wireless: Wireless LAN      no            no
1: acer-bluetooth: Bluetooth        no            no
2: hci0: Bluetooth                  no            no
3: phy0: Wireless LAN               no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

ath9k                 144602  0 
ath9k_common           13359  1 ath9k
ath9k_hw              438205  2 ath9k_common,ath9k
ath                    23922  3 ath9k_common,ath9k,ath9k_hw
mac80211              546051  1 ath9k
cfg80211              409394  3 ath,ath9k,mac80211
acer_wmi               31735  0 
sparse_keymap          13708  1 acer_wmi
video                  18903  2 i915,acer_wmi
wmi                    18673  1 acer_wmi


module parameters ~~~~~~~~~~~~~~~~~~

acer_wmi      (5): brightness=-1 | ec_raw_mode=N | force_series=0 | mailled=-1 | threeg=-1
ath9k         (5): blink=0 | bt_ant_diversity=0 | btcoex_enable=0 | nohwcrypt=0 | ps_enable=0
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=-1
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: disconnected
================o=============o========o==========  ====o=========o===========o==============o========  ===
 Interface & ID | Type        | Driver | State        | Default | Speed     | Support      | HW Addr   
================o=============o========o==========  ====o=========o===========o==============o========  ===
 wlan0          | 802.11 WiFi | ath9k  | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>

    Belkin_N1_Wireless_3D076E: Infra, <MAC C-01 Belkin_N1_Wireless_3D076E>, Freq 2412 MHz, Rate 54 Mb/s, Strength 64 WPA
    TDC-B30C:        Infra, <MAC C-03 TDC-B30C>, Freq 2422 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    TDC-FB5E:        Infra, <MAC C-02 TDC-FB5E>, Freq 2457 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
----------------+-------------+--------+--------------+---------+-----------+--------------+-----------
 eth0           | Wired       | r8169  | unavailable  | no      |           |              | <MAC eth0>
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

Belkin_N1_Wireless_3D076E : ssid=Belkin_N1_Wireless_3D076E | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


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

wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 Belkin_N1_Wireless_3D076E>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"Belkin_N1_Wireless_3D076E"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000d769a64297
                    Extra: Last beacon: 8ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 TDC-FB5E>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"TDC-FB5E"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000178ffa39ece
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 TDC-B30C>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"TDC-B30C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000024f7e12180
                    Extra: Last beacon: 680ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[ath9k]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
srcversion:     7EAAD420ADF6B9354F0C8C1
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

[ath9k_common]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
srcversion:     696B00A6C59713EC0966997
depends:        ath,ath9k_hw

[ath9k_hw]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
srcversion:     4809F3842A0542CD6B556D3
depends:        ath

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

[wmi]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:0x0036 (ath9k)
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

BOOT_IMAGE=/boot/vmlinuz-3.13.0-32-generic root=UUID=faabd7d4-887b-4f5f-83de-80b1b867f2a1 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    1.302749] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.303261] audit: initializing netlink socket (disabled)
[    2.047462] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   11.731382] wmi: Mapper loaded
[   11.756341] acer_wmi: Acer Laptop ACPI-WMI Extras
[   11.756363] acer_wmi: Function bitmap for Communication Button: 0x801
[   11.756519] acer_wmi: Brightness must be controlled by acpi video driver
[   11.778794] acer_wmi: Enabling Launch Manager failed: 0xe4 - 0x0
[   12.025594] ath: phy0: WB335 2-ANT card detected
[   12.025600] ath: phy0: Set BT/WLAN RX diversity capability
[   12.032380] ath: phy0: Enable LNA combining
[   12.034927] ath: phy0: ASPM enabled: 0x42
[   12.034933] ath: EEPROM regdomain: 0x65
[   12.034935] ath: EEPROM indicates we should expect a direct regpair map
[   12.034938] ath: Country alpha2 being used: 00
[   12.034940] ath: Regpair used: 0x65
[   14.909972] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   15.425161] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.428542] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

    ======== Done ========


```

And thanks for the reply.

---

### Post by varunendra on 2014-07-31
Please try these, one at a time (may keep the previous change), try to connect, try the next if no success -

[indent]**1)** A driver parameter -
```
sudo modprobe -rv ath9k
sudo modprobe -v ath9k nohwcrypt=1
```

**2)** Try changing the encryption in the router to WPA2-PSK with AES. Make sure it is pure WPA2 and not WPA/WPA2 mixed mode, and no TKIP.

**3)** Try changing the Access-Point name to something less funky. I'm not sure if it may cause a problem, but it is unusually long. Perhaps try something simple like "Belkin" (without the quotes of course).

**4)** Set "IPv6" to "Ignore" in Network Manager, if you are not using it (it is still not supported by many ISPs and old routers).

**5)** Explicitly define your country code for RegDomain settings. Assuming you are in USA (country code 'US') -
```
sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda
```
..followed by a reboot. If you are in a different country, see this table for country code : [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2#Decoding_table](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2#Decoding_table)[/indent]

If none of these help, run the script in a live session where the wifi works. Comparing both outputs, we may be able to find a solution.

---

### Post by s-l-425434 on 2014-07-31
I´ve searched around but couldn´t find how to do 2 & 3, could you specify how to do this?

Thanks.

Edit: 
I tried running the script in a live session, it tells me that the wireless-info.temp doesn´t exist.

---

### Post by varunendra on 2014-07-31
> **s-l-425434 said:**
> I´ve searched around but couldn´t find how to do 2 & 3, could you specify how to do this?

I can't. Please refer to your router's user manual for that. Usually you log into the router/AP's web interface by typing its IP address in the browser > Enter > provide the username and password for the router's admin. Then look under wireless settings for those.

**PS:**
No idea about the script error you mentioned. It can only happen if you run it on a read-only media (where no new files can be created), or for some reason, the script deletes the tmp file before applying the filter commands.

---

### Post by s-l-425434 on 2014-07-31
Alright I got 2 & 3 down now, and the script of a live session with internet access, after I downloaded the script again. Dunno what went wrong. 
But the 2 and 3 didn´t work either.

Here is the script from the live session:

```
 
    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

xubuntu 3.13.0-32-generic i686,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Pentium(R) CPU  N3530  @ 2.16GHz
Memory : 7966 MB
Uptime : 22:41:33 up  3:54,  8 users,  load average: 0.60, 0.48, 0.32


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

01:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
    Subsystem: Acer Incorporated [ALI] Device [1025:0905]
    Kernel driver in use: r8169
02:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
    Subsystem: Lite-On Communications Inc Device [11ad:0642]
    Kernel driver in use: ath9k


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04f2:b455 Chicony Electronics Co., Ltd 
Bus 001 Device 006: ID 1058:0740 Western Digital Technologies, Inc. My Passport
Bus 001 Device 005: ID 04cf:8818 Myson Century, Inc. USB2.0 to ATAPI Bridge Controller
Bus 001 Device 004: ID 04ca:300b Lite-On Technology Corp. 
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface                 Soft blocked  Hard blocked
1: acer-wireless: Wireless LAN      no            no
2: acer-bluetooth: Bluetooth        no            no
3: phy0: Wireless LAN               no            no
4: hci0: Bluetooth                  no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

ath9k                 144602  0 
ath9k_common           13359  1 ath9k
ath9k_hw              438205  2 ath9k_common,ath9k
ath                    23922  3 ath9k_common,ath9k,ath9k_hw
acer_wmi               31735  0 
mac80211              546051  1 ath9k
sparse_keymap          13708  1 acer_wmi
cfg80211              409394  3 ath,ath9k,mac80211
video                  18903  2 i915,acer_wmi
wmi                    18673  1 acer_wmi


module parameters ~~~~~~~~~~~~~~~~~~

acer_wmi      (5): brightness=-1 | ec_raw_mode=N | force_series=0 | mailled=-1 | threeg=-1
ath9k         (5): blink=0 | bt_ant_diversity=0 | btcoex_enable=0 | nohwcrypt=0 | ps_enable=0
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=-1
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: disconnected
================o=============o========o==========  ====o=========o===========o==============o========  ===
 Interface & ID | Type        | Driver | State        | Default | Speed     | Support      | HW Addr   
================o=============o========o==========  ====o=========o===========o==============o========  ===
 wlan0          | 802.11 WiFi | ath9k  | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>

    TDC-FB5E:        Infra, <MAC C-01 TDC-FB5E>, Freq 2457 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    Belkin:          Infra, <MAC C-02 Belkin>, Freq 2417 MHz, Rate 54 Mb/s, Strength 53 WPA2
    TDC-B30C:        Infra, <MAC C-03 TDC-B30C>, Freq 2422 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
----------------+-------------+--------+--------------+---------+-----------+--------------+-----------
 eth0           | Wired       | r8169  | unavailable  | no      |           |              | <MAC eth0>
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

Belkin               : ssid=Belkin | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Belkin_N1_Wireless_3D076E : ssid=Belkin_N1_Wireless_3D076E | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


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

wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 TDC-FB5E>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"TDC-FB5E"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000017e016e016c
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 Belkin>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"Belkin"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000022c239c
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 TDC-B30C>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"TDC-B30C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000029f9fbe180
                    Extra: Last beacon: 684ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[ath9k]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
srcversion:     7EAAD420ADF6B9354F0C8C1
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

[ath9k_common]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
srcversion:     696B00A6C59713EC0966997
depends:        ath,ath9k_hw

[ath9k_hw]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
srcversion:     4809F3842A0542CD6B556D3
depends:        ath

[ath]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath.ko
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211

[acer_wmi]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/platform/x86/acer-wmi.ko
srcversion:     15371DC0E403E93954B38E5
depends:        wmi,sparse-keymap,video
parm:           mailled:Set initial state of Mail LED (int)
parm:           brightness:Set initial LCD backlight brightness (int)
parm:           threeg:Set initial state of 3G hardware (int)
parm:           force_series:Force a different laptop series (int)
parm:           ec_raw_mode:Enable EC raw mode (bool)

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

[video]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/acpi/video.ko
srcversion:     274A2250DEAB415D412A67C
depends:        
parm:           brightness_switch_enabled:bool
parm:           allow_duplicates:bool
parm:           use_native_backlight:int

[wmi]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:0x0036 (ath9k)
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

noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/xubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash -- maybe-ubiquity


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    7.518089] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    7.518612] audit: initializing netlink socket (disabled)
[    8.102767] wmi: Mapper loaded
[    8.271294] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   33.047462] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   33.619733] acer_wmi: Acer Laptop ACPI-WMI Extras
[   33.619758] acer_wmi: Function bitmap for Communication Button: 0x801
[   33.619765] acer_wmi: Brightness must be controlled by acpi video driver
[   33.639468] acer_wmi: Enabling Launch Manager failed: 0xe4 - 0x0
[   34.613719] ath: phy0: WB335 2-ANT card detected
[   34.613724] ath: phy0: Set BT/WLAN RX diversity capability
[   34.620257] ath: phy0: Enable LNA combining
[   34.621358] ath: phy0: ASPM enabled: 0x42
[   34.621362] ath: EEPROM regdomain: 0x65
[   34.621364] ath: EEPROM indicates we should expect a direct regpair map
[   34.621367] ath: Country alpha2 being used: 00
[   34.621369] ath: Regpair used: 0x65
[   37.426178] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   37.429478] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   39.290788] wlan0: authenticate with <MAC C-02 Belkin>
[   39.310794] wlan0: send auth to <MAC C-02 Belkin> (try 1/3)
[   39.312700] wlan0: authenticated
[   39.313042] ath9k 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   39.314019] wlan0: associate with <MAC C-02 Belkin> (try 1/3)
[   39.316887] wlan0: RX AssocResp from <MAC C-02 Belkin> (capab=0x411 status=0 aid=2)
[   39.317524] wlan0: associated
[   39.317558] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   39.344393] wlan0: deauthenticating from <MAC C-02 Belkin> by local choice (reason=2)
[   39.354755] wlan0: authenticate with <MAC C-02 Belkin>
[   39.369070] wlan0: send auth to <MAC C-02 Belkin> (try 1/3)
[   39.377165] wlan0: authenticated
[   39.377508] ath9k 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   39.378098] wlan0: associate with <MAC C-02 Belkin> (try 1/3)
[   39.395769] wlan0: RX AssocResp from <MAC C-02 Belkin> (capab=0x411 status=0 aid=2)
[   39.396404] wlan0: associated
[  482.540432] wlan0: deauthenticating from <MAC C-02 Belkin> by local choice (reason=3)
[  485.011113] ath: phy0: ASPM enabled: 0x42
[  488.162587] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  496.565975] wlan0: authenticate with <MAC C-02 Belkin>
[  496.588308] wlan0: send auth to <MAC C-02 Belkin> (try 1/3)
[  496.590522] wlan0: authenticated
[  496.591961] wlan0: associate with <MAC C-02 Belkin> (try 1/3)
[  496.595009] wlan0: RX AssocResp from <MAC C-02 Belkin> (capab=0x411 status=0 aid=1)
[  496.595037] wlan0: AP bug: HT capability missing from AssocResp
[  496.595049] wlan0: AP bug: HT operation missing from AssocResp
[  496.595199] wlan0: associated
[  496.595241] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  506.835279] wlan0: deauthenticating from <MAC C-02 Belkin> by local choice (reason=3)

    ======== Done ========

 
```


EDIT:
After doing step two and three, and booting back into the install I get a slightly different output from the script, under iwconfig, but that might just be because I ran the script while I was trying to connect to said network? 
Still no wireless or wired though.

```
 
    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

simon-Aspire-E5-511 3.13.0-32-generic i686,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Pentium(R) CPU  N3530  @ 2.16GHz
Memory : 7966 MB
Uptime : 23:13:38 up 11 min,  2 users,  load average: 0.49, 0.22, 0.15


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

01:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
    Subsystem: Acer Incorporated [ALI] Device [1025:0905]
    Kernel driver in use: r8169
02:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
    Subsystem: Lite-On Communications Inc Device [11ad:0642]
    Kernel driver in use: ath9k


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04f2:b455 Chicony Electronics Co., Ltd 
Bus 001 Device 004: ID 04ca:300b Lite-On Technology Corp. 
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:"Belkin"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: <MAC C-01 Belkin>   
          Bit Rate=43.3 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=43/70  Signal level=-67 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:29   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface                 Soft blocked  Hard blocked
0: acer-wireless: Wireless LAN      no            no
1: acer-bluetooth: Bluetooth        yes           no
2: hci0: Bluetooth                  yes           no
3: phy0: Wireless LAN               no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

ath9k                 144602  0 
ath9k_common           13359  1 ath9k
ath9k_hw              438205  2 ath9k_common,ath9k
ath                    23922  3 ath9k_common,ath9k,ath9k_hw
mac80211              546051  1 ath9k
cfg80211              409394  3 ath,ath9k,mac80211
acer_wmi               31735  0 
sparse_keymap          13708  1 acer_wmi
wmi                    18673  1 acer_wmi
video                  18903  2 i915,acer_wmi


module parameters ~~~~~~~~~~~~~~~~~~

acer_wmi      (5): brightness=-1 | ec_raw_mode=N | force_series=0 | mailled=-1 | threeg=-1
ath9k         (5): blink=0 | bt_ant_diversity=0 | btcoex_enable=0 | nohwcrypt=0 | ps_enable=0
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=-1
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connecting
=================o=============o========o=========  ==============================o=========o=========  ==o==============o===========
 Interface & ID  | Type        | Driver | State                                 | Default | Speed     | Support      | HW Addr   
=================o=============o========o=========  ==============================o=========o=========  ==o==============o===========
 wlan0  [Belkin] | 802.11 WiFi | ath9k  | connecting (getting IP configuration) | no      |           | WEP/WPA/WPA2 | <MAC wlan0>

    TDC-FB5E:        Infra, <MAC C-02 TDC-FB5E>, Freq 2457 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    TDC-B30C:        Infra, <MAC C-03 TDC-B30C>, Freq 2422 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    Belkin:          Infra, <MAC C-01 Belkin>, Freq 2417 MHz, Rate 54 Mb/s, Strength 52 WPA2
-----------------+-------------+--------+---------------------------------------+---------+-----------+--------------+-----------
 eth0            | Wired       | r8169  | unavailable                           | no      |           |              | <MAC eth0>
-----------------+-------------+--------+---------------------------------------+---------+-----------+--------------+-----------


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

Belkin               : ssid=Belkin | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Belkin_N1_Wireless_3D076E : ssid=Belkin_N1_Wireless_3D076E | mac-address=<MAC wlan0> | ipv4=auto | ipv6=ignore 


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
country DK:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5490 - 5710 @ 40), (N/A, 27), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)

          Current Frequency=2.417 GHz (Channel 2)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 Belkin>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"Belkin"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000753934e4
                    Extra: Last beacon: 28ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 TDC-FB5E>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"TDC-FB5E"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000017e747ffbee
                    Extra: Last beacon: 28ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 TDC-B30C>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"TDC-B30C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002a6d0c2180
                    Extra: Last beacon: 1988ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[ath9k]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
srcversion:     7EAAD420ADF6B9354F0C8C1
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

[ath9k_common]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
srcversion:     696B00A6C59713EC0966997
depends:        ath,ath9k_hw

[ath9k_hw]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
srcversion:     4809F3842A0542CD6B556D3
depends:        ath

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

[acer_wmi]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/platform/x86/acer-wmi.ko
srcversion:     15371DC0E403E93954B38E5
depends:        wmi,sparse-keymap,video
parm:           mailled:Set initial state of Mail LED (int)
parm:           brightness:Set initial LCD backlight brightness (int)
parm:           threeg:Set initial state of 3G hardware (int)
parm:           force_series:Force a different laptop series (int)
parm:           ec_raw_mode:Enable EC raw mode (bool)

[wmi]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)

[video]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/acpi/video.ko
srcversion:     274A2250DEAB415D412A67C
depends:        
parm:           brightness_switch_enabled:bool
parm:           allow_duplicates:bool
parm:           use_native_backlight:int


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:0x0036 (ath9k)
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

BOOT_IMAGE=/boot/vmlinuz-3.13.0-32-generic root=UUID=faabd7d4-887b-4f5f-83de-80b1b867f2a1 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    1.302698] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.303198] audit: initializing netlink socket (disabled)
[    2.061195] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   11.669880] wmi: Mapper loaded
[   11.698879] acer_wmi: Acer Laptop ACPI-WMI Extras
[   11.698901] acer_wmi: Function bitmap for Communication Button: 0x801
[   11.699186] acer_wmi: Brightness must be controlled by acpi video driver
[   11.743036] acer_wmi: Enabling Launch Manager failed: 0xe4 - 0x0
[   12.004750] ath: phy0: WB335 2-ANT card detected
[   12.004755] ath: phy0: Set BT/WLAN RX diversity capability
[   12.011537] ath: phy0: Enable LNA combining
[   12.012648] ath: phy0: ASPM enabled: 0x42
[   12.012652] ath: EEPROM regdomain: 0x65
[   12.012654] ath: EEPROM indicates we should expect a direct regpair map
[   12.012657] ath: Country alpha2 being used: 00
[   12.012659] ath: Regpair used: 0x65
[   14.387304] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   15.397000] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.400135] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   52.258235] wlan0: authenticate with <MAC C-01 Belkin>
[   52.278176] wlan0: send auth to <MAC C-01 Belkin> (try 1/3)
[   52.280234] wlan0: authenticated
[   52.281639] wlan0: associate with <MAC C-01 Belkin> (try 1/3)
[   52.284640] wlan0: RX AssocResp from <MAC C-01 Belkin> (capab=0x411 status=0 aid=1)
[   52.284648] wlan0: AP bug: HT capability missing from AssocResp
[   52.284650] wlan0: AP bug: HT operation missing from AssocResp
[   52.284698] wlan0: associated
[   52.284733] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   98.312830] wlan0: deauthenticating from <MAC C-01 Belkin> by local choice (reason=3)
[  114.873322] wlan0: authenticate with <MAC C-01 Belkin>
[  114.893998] wlan0: send auth to <MAC C-01 Belkin> (try 1/3)
[  114.896009] wlan0: authenticated
[  114.896465] wlan0: associate with <MAC C-01 Belkin> (try 1/3)
[  114.899380] wlan0: RX AssocResp from <MAC C-01 Belkin> (capab=0x411 status=0 aid=1)
[  114.899386] wlan0: AP bug: HT capability missing from AssocResp
[  114.899389] wlan0: AP bug: HT operation missing from AssocResp
[  114.899435] wlan0: associated
[  127.328052] wlan0: deauthenticating from <MAC C-01 Belkin> by local choice (reason=3)
[  134.728482] wlan0: authenticate with <MAC C-01 Belkin>
[  134.743114] wlan0: send auth to <MAC C-01 Belkin> (try 1/3)
[  134.745014] wlan0: authenticated
[  134.748580] wlan0: associate with <MAC C-01 Belkin> (try 1/3)
[  134.751521] wlan0: RX AssocResp from <MAC C-01 Belkin> (capab=0x411 status=0 aid=1)
[  134.751530] wlan0: AP bug: HT capability missing from AssocResp
[  134.751533] wlan0: AP bug: HT operation missing from AssocResp
[  134.751583] wlan0: associated
[  180.384506] wlan0: deauthenticating from <MAC C-01 Belkin> by local choice (reason=3)
[  642.451149] wlan0: authenticate with <MAC C-01 Belkin>
[  642.471551] wlan0: send auth to <MAC C-01 Belkin> (try 1/3)
[  642.475161] wlan0: authenticated
[  642.477252] wlan0: associate with <MAC C-01 Belkin> (try 1/3)
[  642.480261] wlan0: RX AssocResp from <MAC C-01 Belkin> (capab=0x411 status=0 aid=1)
[  642.480289] wlan0: AP bug: HT capability missing from AssocResp
[  642.480301] wlan0: AP bug: HT operation missing from AssocResp
[  642.480449] wlan0: associated

    ======== Done ========

 
```

---

### Post by varunendra on 2014-07-31
The access-point was showing channel 1 earlier, now it is showing channel 2. Is it set to "auto" mode in the router/access-point? Fix it to 1 or 11 if yes.

Try the 'nohwcrypt=1' parameter in Ubuntu again with this new setting. Or rather, make it permanent -
```
[s]echo "options nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf[/s]
echo "options **ath9k** nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
```
(EDIT: Corrected the command above)
This will create a file "ath9k.conf" in /etc/modprobe.d directory, that will make the parameter permanent so it loads automatically since next boot.

The "IPv6" setting is still set to "Auto" in Network Manager. Please set it to "Ignore" permanently unless you are sure you need it. Delete the older wifi profile to avoid confusion.

Is the country setting in your router (if provided) also set to 'Denmark'? It is important that the router's country setting is same as the card's setting in the router. Different settings may sometimes cause problems.

And one more setting in the router, seeing the "AP bug" errors. Is your router set to b/g/n mode? Try disabling N channel if so. That is, set it to b/g only mode.

With these changes applied, reboot the router and the system both to make sure everything is properly reset, then post back a fresh wireless_script report if the connection is still unsuccessful.


**PS:**
For wired, what do these commands return -
```
sudo mii-tool -F 100baseTx-FD eth0
apt-get install --print-uris ethtool
```
??

---

### Post by s-l-425434 on 2014-07-31
Yes I live in Denmark, and it´s 4 AM over here and my eyes are getting sore. 
I haven´t been able to work out the wireless, but the wired seems to be the above mentioned driver in my original post.
A fix to it needs build-essentials which I have been trying to install in offline mode, but unsuccessfully due to all the dependencies, so I´ve been spending the last 4 hours trying to customize a cd image to have it in the installation. 
I will be back tomorrow and try out what you´ve written, but at the moment, I´m simply to tired and weary of this issue. Sleep tight.


Edit: Ok back for another bright day.  I made a new cdimage, using the uck tool, containing build-essential and ethtool, just in the case that it wasn´t the drivers fault. 
Installed the thing, compiled the driver, blacklisted the old one and placed the new one in the kernel, no success. 

Then I retried all the above mentioned solutions, still no success, but now we should be up to date with this thread, and here is a wireless script:

```
 
    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

simon-Aspire-E5-511 3.13.0-32-generic i686,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Pentium(R) CPU  N3530  @ 2.16GHz
Memory : 7966 MB
Uptime : 14:34:15 up  8:46,  2 users,  load average: 0.33, 0.17, 0.15


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

01:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
    Subsystem: Acer Incorporated [ALI] Device [1025:0905]
    Kernel driver in use: r8168
02:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
    Subsystem: Lite-On Communications Inc Device [11ad:0642]
    Kernel driver in use: ath9k


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 002: ID 1058:0740 Western Digital Technologies, Inc. My Passport
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04f2:b455 Chicony Electronics Co., Ltd 
Bus 001 Device 004: ID 04ca:300b Lite-On Technology Corp. 
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface                 Soft blocked  Hard blocked
0: acer-wireless: Wireless LAN      no            no
1: acer-bluetooth: Bluetooth        no            no
4: hci0: Bluetooth                  no            no
5: phy0: Wireless LAN               no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

ath9k                 144602  0 
ath9k_common           13359  1 ath9k
ath9k_hw              438205  2 ath9k_common,ath9k
ath                    23922  3 ath9k_common,ath9k,ath9k_hw
mac80211              546051  1 ath9k
cfg80211              409394  3 ath,ath9k,mac80211
acer_wmi               31735  0 
sparse_keymap          13708  1 acer_wmi
wmi                    18673  1 acer_wmi
video                  18903  2 i915,acer_wmi


module parameters ~~~~~~~~~~~~~~~~~~

acer_wmi      (5): brightness=-1 | ec_raw_mode=N | force_series=0 | mailled=-1 | threeg=-1
ath9k         (5): blink=0 | bt_ant_diversity=0 | btcoex_enable=0 | nohwcrypt=1 | ps_enable=0
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=-1
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: disconnected
================o=============o========o==========  ====o=========o===========o==============o========  ===
 Interface & ID | Type        | Driver | State        | Default | Speed     | Support      | HW Addr   
================o=============o========o==========  ====o=========o===========o==============o========  ===
 wlan0          | 802.11 WiFi | ath9k  | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>

    TDC-B30C:        Infra, <MAC C-03 TDC-B30C>, Freq 2422 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    TDC-FB5E:        Infra, <MAC C-02 TDC-FB5E>, Freq 2457 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    Belkin:          Infra, <MAC C-01 Belkin>, Freq 2417 MHz, Rate 54 Mb/s, Strength 67 WPA2
----------------+-------------+--------+--------------+---------+-----------+--------------+-----------
 eth0           | Wired       | r8168  | unavailable  | no      | 100 Mb/s  |              | <MAC eth0>
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

Belkin               : ssid=Belkin | mac-address=<MAC wlan0> | ipv4=auto | ipv6=ignore 


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

wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 Belkin>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"Belkin"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000000ca999d1
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 TDC-FB5E>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"TDC-FB5E"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000018b5012a1ca
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 TDC-B30C>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"TDC-B30C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000374976c1a5
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist r8169


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[ath9k]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
srcversion:     7EAAD420ADF6B9354F0C8C1
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

[ath9k_common]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
srcversion:     696B00A6C59713EC0966997
depends:        ath,ath9k_hw

[ath9k_hw]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
srcversion:     4809F3842A0542CD6B556D3
depends:        ath

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

[acer_wmi]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/platform/x86/acer-wmi.ko
srcversion:     15371DC0E403E93954B38E5
depends:        wmi,sparse-keymap,video
parm:           mailled:Set initial state of Mail LED (int)
parm:           brightness:Set initial LCD backlight brightness (int)
parm:           threeg:Set initial state of 3G hardware (int)
parm:           force_series:Force a different laptop series (int)
parm:           ec_raw_mode:Enable EC raw mode (bool)

[wmi]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)

[video]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/acpi/video.ko
srcversion:     274A2250DEAB415D412A67C
depends:        
parm:           brightness_switch_enabled:bool
parm:           allow_duplicates:bool
parm:           use_native_backlight:int


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:0x0036 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Not Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modules]
&#8220;r8168&#8243;

[/etc/modprobe.d]
ath9k.conf        : options nohwcrypt=1
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-32-generic root=UUID=41fd691c-955f-43f1-8da0-b9576a475c48 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    1.304949] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.305483] audit: initializing netlink socket (disabled)
[    2.036591] r8168 Gigabit Ethernet driver 8.038.00-NAPI loaded
[   12.674062] wmi: Mapper loaded
[   12.689138] acer_wmi: Acer Laptop ACPI-WMI Extras
[   12.689159] acer_wmi: Function bitmap for Communication Button: 0x801
[   12.689318] acer_wmi: Brightness must be controlled by acpi video driver
[   12.716486] acer_wmi: Enabling Launch Manager failed: 0xe4 - 0x0
[   13.132568] ath: phy0: WB335 2-ANT card detected
[   13.132573] ath: phy0: Set BT/WLAN RX diversity capability
[   13.140712] ath: phy0: Enable LNA combining
[   13.144067] ath: phy0: ASPM enabled: 0x42
[   13.144074] ath: EEPROM regdomain: 0x65
[   13.144076] ath: EEPROM indicates we should expect a direct regpair map
[   13.144079] ath: Country alpha2 being used: 00
[   13.144081] ath: Regpair used: 0x65
[   16.024756] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.508640] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.511747] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  140.599762] ath: phy0: ASPM enabled: 0x42
[  143.984878] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  286.509977] ath9k: ath9k: Driver unloaded
[  317.397273] ath: phy0: WB335 2-ANT card detected
[  317.397279] ath: phy0: Set BT/WLAN RX diversity capability
[  317.403741] ath: phy0: Enable LNA combining
[  317.404840] ath: phy0: ASPM enabled: 0x42
[  317.404844] ath: EEPROM regdomain: 0x65
[  317.404846] ath: EEPROM indicates we should expect a direct regpair map
[  317.404849] ath: Country alpha2 being used: 00
[  317.404851] ath: Regpair used: 0x65
[  317.424053] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  317.428427] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  337.499886] wlan0: authenticate with <MAC C-01 Belkin>
[  337.515118] wlan0: send auth to <MAC C-01 Belkin> (try 1/3)
[  337.517087] wlan0: authenticated
[  342.562611] wlan0: deauthenticating from <MAC C-01 Belkin> by local choice (reason=3)
[  352.703427] wlan0: authenticate with <MAC C-01 Belkin>
[  352.718799] wlan0: send auth to <MAC C-01 Belkin> (try 1/3)
[  352.720840] wlan0: authenticated
[  357.723469] wlan0: deauthenticating from <MAC C-01 Belkin> by local choice (reason=3)
[  909.637433] wlan0: authenticate with <MAC C-01 Belkin>
[  909.652349] wlan0: send auth to <MAC C-01 Belkin> (try 1/3)
[  909.654221] wlan0: authenticated
[  914.661837] wlan0: deauthenticating from <MAC C-01 Belkin> by local choice (reason=3)
[  925.693583] wlan0: authenticate with <MAC C-01 Belkin>
[  925.702940] wlan0: send auth to <MAC C-01 Belkin> (try 1/3)
[  925.704708] wlan0: authenticated
[  930.709847] wlan0: deauthenticating from <MAC C-01 Belkin> by local choice (reason=3)

    ======== Done ========

 
```

And the code of the two commands you requested, tells me that the newest version of the software is installed.
As I´d hoped since I threw it in the image. 
I don´t know exactly what to do with ethtool though? 


And really, thanks for all the help, it´s greatly appreciated.

---

### Post by s-l-425434 on 2014-08-01
After setting to b/g and 1 or 11 my wired connection on the desktop I´m posting from became unbearably slow. Tried changing those back and now the internet is fast again on this one.
So just a question because I´m curious, why can wireless settings affect wired performance?

---

### Post by chili555 on 2014-08-01
I suspect my esteemed colleague Varun, who is 127 time zones away, may be away from the computer right now (read: asleep). Let me just offer some suggestions until he jumps back in. He's one of our very best, so I doubt you'll get better advice.

First, I notice your country code is still 00; that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set DK
```Of course, substitute your country code if not Denmark. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=DK
```Proofread carefully, save and close the text editor. 

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

Next, your original post says that your wireless doesn't work but it seems, according to your log, to be trying to connect. What, exactly, are your symptoms?

---

### Post by s-l-425434 on 2014-08-01
Thanks for the reply.
I have followed the steps provided- 

As mentioned  in OP, the various wireless networks close to me show up. I press on the  desired connection, it asks for pass, then tries to connect for a  minute and then the message " Disconnected-you are now offline" shows  up.

Edit: Other wireless devices in the household, running on said WIFI do work.

---

### Post by varunendra on 2014-08-02
So did you do what dr. chili suggested above? Can we see a fresh wireless_script report please? Plus the output requested below -

> **s-l-425434 said:**
> And the code of the two commands you requested, tells me that the newest version of the software is installed.
Only the second one (sudo apt-get install) should have returned that message. The first one, if successful, would have returned no outputs, or some error message. Which was the case?

With 'ethtool', you can set the same thing that the "mii-too" command would do, if mii is supported. The 'ethtool' command is just a more promising tool for the same job. What does this show us now -
```
sudo ethtool eth0
```

And the r8168 vs r8169 issues doesn't exist anymore as far as I know. It used to exist long ago, but then the native r8169 became quite mature and better. Although I must admit that I have recently seen at least one post where the proprietary r8168 solved the issue, but not much else was tried, so I guess r8169 is still good.

> **s-l-425434 said:**
> After setting to b/g and 1 or 11 my wired connection on the desktop I´m posting from became unbearably slow. Tried changing those back and now the internet is fast again on this one.
So just a question because I´m curious, why can wireless settings affect wired performance?

[s]I suspect your connection may have picked up 'b' mode, because 'g' is comparatively slower than 'n' mode, but not really "painful". :)

Can you quantify the term "slow"? How slow? How did you observe/measure it? Stats or comparisons?

The limit of 'b' mode is 11 Mbps, while that of 'g' mode is 54 Mbps.[/s] (Edit: Misread and misunderstood the above part).

And I don't think the wireless settings are affecting the wired connection here. Both are separate issues, should be fixed with separate solutions.

---

### Post by s-l-425434 on 2014-08-02
Yes, I did as Dr. chili suggested, and still no success. 


Here is the full output of the two commands:

```
 sudo mii-tool -F 100baseTx-FD etho 
```

Gave this:

```
 SIOCGMIIPHY on 'etho' failed: No such device 
```

```
  apt-get install --print-uris ethtool 
```

Gave this: 

```
 Reading package lists... Done
Building dependency tree       
Reading state information... Done
ethtool is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded. 
```


The wireless script:

```
 ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

simon-Aspire-E5-511 3.13.0-32-generic i686,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Pentium(R) CPU  N3530  @ 2.16GHz
Memory : 7966 MB
Uptime : 16:47:47 up 19:21,  2 users,  load average: 0.06, 0.09, 0.12


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

01:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
    Subsystem: Acer Incorporated [ALI] Device [1025:0905]
    Kernel driver in use: r8168
02:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
    Subsystem: Lite-On Communications Inc Device [11ad:0642]
    Kernel driver in use: ath9k


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04f2:b455 Chicony Electronics Co., Ltd 
Bus 001 Device 004: ID 04ca:300b Lite-On Technology Corp. 
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface                 Soft blocked  Hard blocked
0: acer-wireless: Wireless LAN      no            no
1: acer-bluetooth: Bluetooth        yes           no
3: phy0: Wireless LAN               no            no
5: hci0: Bluetooth                  yes           no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

ath9k                 144602  0 
ath9k_common           13359  1 ath9k
ath9k_hw              438205  2 ath9k_common,ath9k
ath                    23922  3 ath9k_common,ath9k,ath9k_hw
mac80211              546051  1 ath9k
cfg80211              409394  3 ath,ath9k,mac80211
acer_wmi               31735  0 
sparse_keymap          13708  1 acer_wmi
video                  18903  2 i915,acer_wmi
wmi                    18673  1 acer_wmi


module parameters ~~~~~~~~~~~~~~~~~~

acer_wmi      (5): brightness=-1 | ec_raw_mode=N | force_series=0 | mailled=-1 | threeg=-1
ath9k         (5): blink=0 | bt_ant_diversity=0 | btcoex_enable=0 | nohwcrypt=0 | ps_enable=0
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=-1
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: disconnected
================o=============o========o==========  ====o=========o===========o==============o========  ===
 Interface & ID | Type        | Driver | State        | Default | Speed     | Support      | HW Addr   
================o=============o========o==========  ====o=========o===========o==============o========  ===
 wlan0          | 802.11 WiFi | ath9k  | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>

    TDC-B30C:        Infra, <MAC C-03 TDC-B30C>, Freq 2422 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    TDC-FB5E:        Infra, <MAC C-02 TDC-FB5E>, Freq 2457 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    Belkin:          Infra, <MAC C-01 Belkin>, Freq 2462 MHz, Rate 54 Mb/s, Strength 52 WPA2
----------------+-------------+--------+--------------+---------+-----------+--------------+-----------
 eth0           | Wired       | r8168  | unavailable  | no      |           |              | <MAC eth0>
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

Belkin               : ssid=Belkin | mac-address=<MAC wlan0> | ipv4=auto | ipv6=ignore 


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
country DK:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5490 - 5710 @ 40), (N/A, 27), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 Belkin>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"Belkin"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000d55903335
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 TDC-FB5E>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"TDC-FB5E"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001a14a0700f8
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 TDC-B30C>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"TDC-B30C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004d44cbdda0
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist r8169


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[ath9k]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
srcversion:     7EAAD420ADF6B9354F0C8C1
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

[ath9k_common]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
srcversion:     696B00A6C59713EC0966997
depends:        ath,ath9k_hw

[ath9k_hw]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
srcversion:     4809F3842A0542CD6B556D3
depends:        ath

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

[wmi]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:0x0036 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Not Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modules]
“r8168&#8243;

[/etc/modprobe.d]
ath9k.conf        : options nohwcrypt=1
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-32-generic root=UUID=41fd691c-955f-43f1-8da0-b9576a475c48 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    1.304714] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.305241] audit: initializing netlink socket (disabled)
[    2.036299] r8168 Gigabit Ethernet driver 8.038.00-NAPI loaded
[   13.067499] wmi: Mapper loaded
[   13.090952] acer_wmi: Acer Laptop ACPI-WMI Extras
[   13.090974] acer_wmi: Function bitmap for Communication Button: 0x801
[   13.091138] acer_wmi: Brightness must be controlled by acpi video driver
[   13.116521] acer_wmi: Enabling Launch Manager failed: 0xe4 - 0x0
[   13.458364] ath: phy0: WB335 2-ANT card detected
[   13.458369] ath: phy0: Set BT/WLAN RX diversity capability
[   13.464853] ath: phy0: Enable LNA combining
[   13.467553] ath: phy0: ASPM enabled: 0x42
[   13.467559] ath: EEPROM regdomain: 0x65
[   13.467561] ath: EEPROM indicates we should expect a direct regpair map
[   13.467565] ath: Country alpha2 being used: 00
[   13.467567] ath: Regpair used: 0x65
[   16.286455] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.936816] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.940105] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4083.628664] ath: phy0: ASPM enabled: 0x42
[ 4087.585181] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4336.599579] wlan0: authenticate with <MAC C-01 Belkin>
[ 4336.622162] wlan0: send auth to <MAC C-01 Belkin> (try 1/3)
[ 4336.624211] wlan0: authenticated
[ 4336.626461] wlan0: associate with <MAC C-01 Belkin> (try 1/3)
[ 4336.629630] wlan0: RX AssocResp from <MAC C-01 Belkin> (capab=0x411 status=0 aid=2)
[ 4336.629658] wlan0: AP bug: HT capability missing from AssocResp
[ 4336.629670] wlan0: AP bug: HT operation missing from AssocResp
[ 4336.629799] wlan0: associated
[ 4336.629815] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4339.620289] wlan0: deauthenticated from <MAC C-01 Belkin> (Reason: 15)
[ 4343.845832] wlan0: authenticate with <MAC C-01 Belkin>
[ 4343.864936] wlan0: send auth to <MAC C-01 Belkin> (try 1/3)
[ 4343.866897] wlan0: authenticated
[ 4343.867981] wlan0: associate with <MAC C-01 Belkin> (try 1/3)
[ 4343.870953] wlan0: RX AssocResp from <MAC C-01 Belkin> (capab=0x411 status=0 aid=2)
[ 4343.870960] wlan0: AP bug: HT capability missing from AssocResp
[ 4343.870962] wlan0: AP bug: HT operation missing from AssocResp
[ 4343.871007] wlan0: associated
[ 4346.867145] wlan0: deauthenticated from <MAC C-01 Belkin> (Reason: 15)
[ 4358.690256] wlan0: authenticate with <MAC C-01 Belkin>
[ 4358.712295] wlan0: send auth to <MAC C-01 Belkin> (try 1/3)
[ 4358.714252] wlan0: authenticated
[ 4358.716017] wlan0: associate with <MAC C-01 Belkin> (try 1/3)
[ 4358.718951] wlan0: RX AssocResp from <MAC C-01 Belkin> (capab=0x411 status=0 aid=2)
[ 4358.718958] wlan0: AP bug: HT capability missing from AssocResp
[ 4358.718961] wlan0: AP bug: HT operation missing from AssocResp
[ 4358.719012] wlan0: associated
[ 4361.711535] wlan0: deauthenticated from <MAC C-01 Belkin> (Reason: 15)
[ 4370.720017] wlan0: authenticate with <MAC C-01 Belkin>
[ 4370.739398] wlan0: send auth to <MAC C-01 Belkin> (try 1/3)
[ 4370.742115] wlan0: authenticated
[ 4370.746171] wlan0: associate with <MAC C-01 Belkin> (try 1/3)
[ 4370.850864] wlan0: RX AssocResp from <MAC C-01 Belkin> (capab=0x411 status=0 aid=2)
[ 4370.850874] wlan0: AP bug: HT capability missing from AssocResp
[ 4370.850876] wlan0: AP bug: HT operation missing from AssocResp
[ 4370.850926] wlan0: associated
[ 4373.741325] wlan0: deauthenticated from <MAC C-01 Belkin> (Reason: 15)
[ 4377.484500] wlan0: authenticate with <MAC C-01 Belkin>
[ 4377.504713] wlan0: send auth to <MAC C-01 Belkin> (try 1/3)
[ 4377.506672] wlan0: authenticated
[ 4377.507364] wlan0: associate with <MAC C-01 Belkin> (try 1/3)
[ 4377.510468] wlan0: RX AssocResp from <MAC C-01 Belkin> (capab=0x411 status=0 aid=2)
[ 4377.510496] wlan0: AP bug: HT capability missing from AssocResp
[ 4377.510508] wlan0: AP bug: HT operation missing from AssocResp
[ 4377.510654] wlan0: associated
[ 4380.499681] wlan0: deauthenticated from <MAC C-01 Belkin> (Reason: 15)
[ 4399.403704] wlan0: authenticate with <MAC C-01 Belkin>
[ 4399.425303] wlan0: send auth to <MAC C-01 Belkin> (try 1/3)
[ 4399.427262] wlan0: authenticated
[ 4399.429114] wlan0: associate with <MAC C-01 Belkin> (try 1/3)
[ 4399.432076] wlan0: RX AssocResp from <MAC C-01 Belkin> (capab=0x411 status=0 aid=2)
[ 4399.432083] wlan0: AP bug: HT capability missing from AssocResp
[ 4399.432085] wlan0: AP bug: HT operation missing from AssocResp
[ 4399.432130] wlan0: associated
[ 4402.419552] wlan0: deauthenticated from <MAC C-01 Belkin> (Reason: 15)
[ 4408.537532] wlan0: authenticate with <MAC C-01 Belkin>
[ 4408.552268] wlan0: send auth to <MAC C-01 Belkin> (try 1/3)
[ 4408.565440] wlan0: authenticated
[ 4408.568625] wlan0: associate with <MAC C-01 Belkin> (try 1/3)
[ 4408.577856] wlan0: RX AssocResp from <MAC C-01 Belkin> (capab=0x411 status=0 aid=2)
[ 4408.577879] wlan0: AP bug: HT capability missing from AssocResp
[ 4408.577889] wlan0: AP bug: HT operation missing from AssocResp
[ 4408.578004] wlan0: associated
[ 4411.570916] wlan0: deauthenticated from <MAC C-01 Belkin> (Reason: 15)
[ 4516.533742] wlan0: authenticate with <MAC C-01 Belkin>
[ 4516.555636] wlan0: send auth to <MAC C-01 Belkin> (try 1/3)
[ 4516.557680] wlan0: authenticated
[ 4516.560475] wlan0: associate with <MAC C-01 Belkin> (try 1/3)
[ 4516.563443] wlan0: RX AssocResp from <MAC C-01 Belkin> (capab=0x411 status=0 aid=2)
[ 4516.563449] wlan0: AP bug: HT capability missing from AssocResp
[ 4516.563452] wlan0: AP bug: HT operation missing from AssocResp
[ 4516.564523] wlan0: associated
[ 4519.555180] wlan0: deauthenticated from <MAC C-01 Belkin> (Reason: 15)
[ 4522.806466] wlan0: authenticate with <MAC C-01 Belkin>
[ 4522.829644] wlan0: send auth to <MAC C-01 Belkin> (try 1/3)
[ 4522.853580] wlan0: authenticated
[ 4522.857742] wlan0: associate with <MAC C-01 Belkin> (try 1/3)
[ 4522.860817] wlan0: RX AssocResp from <MAC C-01 Belkin> (capab=0x411 status=0 aid=2)
[ 4522.860844] wlan0: AP bug: HT capability missing from AssocResp
[ 4522.860855] wlan0: AP bug: HT operation missing from AssocResp
[ 4522.861001] wlan0: associated
[ 4525.856058] wlan0: deauthenticated from <MAC C-01 Belkin> (Reason: 15)
[ 4529.929443] wlan0: authenticate with <MAC C-01 Belkin>
[ 4529.948828] wlan0: send auth to <MAC C-01 Belkin> (try 1/3)
[ 4529.950725] wlan0: authenticated
[ 4529.951240] wlan0: associate with <MAC C-01 Belkin> (try 1/3)
[ 4529.954164] wlan0: RX AssocResp from <MAC C-01 Belkin> (capab=0x411 status=0 aid=2)
[ 4529.954171] wlan0: AP bug: HT capability missing from AssocResp
[ 4529.954174] wlan0: AP bug: HT operation missing from AssocResp
[ 4529.954220] wlan0: associated
[ 4532.942511] wlan0: deauthenticated from <MAC C-01 Belkin> (Reason: 15)
[ 4594.641982] wlan0: authenticate with <MAC C-01 Belkin>
[ 4594.661149] wlan0: send auth to <MAC C-01 Belkin> (try 1/3)
[ 4594.664051] wlan0: authenticated
[ 4594.667994] wlan0: associate with <MAC C-01 Belkin> (try 1/3)
[ 4594.670905] wlan0: RX AssocResp from <MAC C-01 Belkin> (capab=0x411 status=0 aid=2)
[ 4594.672301] wlan0: associated
[ 4640.006856] wlan0: deauthenticating from <MAC C-01 Belkin> by local choice (reason=3)
[ 4816.336783] wlan0: authenticate with <MAC C-01 Belkin>
[ 4816.353922] wlan0: send auth to <MAC C-01 Belkin> (try 1/3)
[ 4816.362894] wlan0: authenticated
[ 4816.364047] wlan0: associate with <MAC C-01 Belkin> (try 1/3)
[ 4816.367112] wlan0: RX AssocResp from <MAC C-01 Belkin> (capab=0x411 status=0 aid=2)
[ 4816.368940] wlan0: associated
[ 4862.191725] wlan0: deauthenticating from <MAC C-01 Belkin> by local choice (reason=3)
[ 6246.547487] wlan0: authenticate with <MAC C-01 Belkin>
[ 6246.561644] wlan0: send auth to <MAC C-01 Belkin> (try 1/3)
[ 6246.563590] wlan0: authenticated
[ 6246.566794] wlan0: associate with <MAC C-01 Belkin> (try 1/3)
[ 6246.569634] wlan0: RX AssocResp from <MAC C-01 Belkin> (capab=0x411 status=0 aid=2)
[ 6246.571123] wlan0: associated
[ 6292.350293] wlan0: deauthenticating from <MAC C-01 Belkin> by local choice (reason=3)
[14655.875902] ath: phy0: ASPM enabled: 0x42
[14659.872638] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[14676.657416] wlan0: authenticate with <MAC C-01 Belkin>
[14676.671742] wlan0: send auth to <MAC C-01 Belkin> (try 1/3)
[14676.673685] wlan0: authenticated
[14676.676665] wlan0: associate with <MAC C-01 Belkin> (try 1/3)
[14676.679525] wlan0: RX AssocResp from <MAC C-01 Belkin> (capab=0x411 status=0 aid=1)
[14676.681523] wlan0: associated
[14676.681569] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[14722.207274] wlan0: deauthenticating from <MAC C-01 Belkin> by local choice (reason=3)

    ======== Done ======== 
```




```
 sudo ethtool eth0 
```

Returned this: 

```
 
Settings for eth0:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Speed: 10Mb/s
    Duplex: Half
    Port: Twisted Pair
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: Unknown
    Supports Wake-on: pumbg
    Wake-on: d
    Current message level: 0x00000033 (51)
                   drv probe ifdown ifup
    Link detected: no 
``` 

This was without the cable inserted.
When I insert the cable, it tries to connect for a minute and then also gives me the message "Disconnected, you are now offline".

Here is the out put of 
```
 sudo ethtool eth0
```

With the cable inserted:

```
 Settings for eth0:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Advertised pause frame use: Symmetric Receive-only
    Advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: Twisted Pair
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: Unknown
    Supports Wake-on: pumbg
    Wake-on: d
    Current message level: 0x00000033 (51)
                   drv probe ifdown ifup
    Link detected: yes

 
```


As far as the speed problem after b/g mode and channel one was enabled:
I tested it with the online speed tester tool, it had the same speed as usual. However every other time I tried to go to a new page it would take a minute to load, or tell me that the server wasn´t available. Other times when refreshing it came with usual speed. After I had set the channel and mode back to original, I tried setting the wireless channel and mode back to the way you suggested once again (though this time channel 11 instead of 1), and restarting the router, and no problems at all, so might have been an issue after the router restart I made :D
(Speed here is limited generally, living in a rural area, 8 mbps down, 0.8 up, on the wired connection.  Moving on monday though). 

Nice to know the driver issue is no longer really relevent, I´m not especially tech savy but I try to find solutions before asking questions.. + you learn something that way :)

---

### Post by chili555 on 2014-08-02
> Code:
 sudo mii-tool -F 100baseTx-FD etho
Gave this:

Code:
 SIOCGMIIPHY on 'etho' failed: No such devicePlease try again; it is eth0 and not etho. In words, it is eth-zero and not eth-lower-case-O.

---

### Post by s-l-425434 on 2014-08-02
Sorry, I´m aware it should be zero, must have had a brainfart. 

```
 sudo mii-tool -F 100baseTx-FD eth0 
```

Returns nothing, but prompts me to 
```
 ~$ 
```

So no error message :)

---

### Post by praseodym on 2014-08-02
Hi,

every output showed no nameservers in your /etc/resolv.conf:
```

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee /etc/resolv.conf
sudo service network-manager restart
```

---

### Post by s-l-425434 on 2014-08-02
Hi.
```
 echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee /etc/resolv.conf 
```

gives this output: 

```
 
nameserver 8.8.8.8
nameserver 8.8.4.4

```

```
 sudo service network-manager restart 
```

Gives this: 

```
 
network-manager stop/waiting 
network-manager start/running, process 2182

```

Still no internet, but thanks for the reply.

---

### Post by varunendra on 2014-08-02
I think the wired connection issue is very close to the solution, so let's try it again-
> **s-l-425434 said:**
> With the cable inserted:
```
 Settings for eth0:
    ....
    Speed: 100Mb/s
    Duplex: Full
    ....
    **Link detected: yes** 
```

Suggests you should have had everything all set, except maybe the DHCP pack - the thing that gives you an IP address so you get 'logically' connected as well as physically to the network.

Please connect the cable again, run -
```
sudo ethtool eth0
```
..again, and if it shows the above quoted stuff again, (Speed : 100, Duplex : Full, Link : Yes), but you don't get connected, try manually assigning an IP to the interface. For example -
```
sudo ifconfig eth0 down
sudo ifconfig eth0 192.168.1.200
```
..where the IP "192.168.1.200" is just for an example. Change it with an IP that is available (not used by any other device) and out-of-DHCP range (in the router). I am assuming here that you know the how to see/set the DHCP range in the router.

If everything is okay at physical connection and card/driver part, the above should get you connected to the network (but not Internet, unless we also manually define a gateway and DNS). If it does, we can try manually defining the network configuration in Network Manager to at least get the wired connection working.

By the way, can you confirm if DHCP is enabled in your router and is working properly with your Desktop or other devices?

**PS:**
I misread your post about the slow speed. I thought you were talking about wireless speed, totally forgetting that you never got wired or wireless connection going on it at all! So please disregard that explanation. Although the info about b/g speeds is correct. :)

---

### Post by s-l-425434 on 2014-08-02
"Change it with an IP that is available (not used by any other device)  and out-of-DHCP range (in the router). I am assuming here that you know  the how to see/set the DHCP range in the router."
Unfortunately I have no clue, googling around now. 

"By the way, can you confirm if DHCP is enabled in your router and is working properly with your Desktop or other devices?"
Could you dumb it down a bit please :) If you´re asking if I´ve got internet connection on my desktop then yes?

In lan setup I get this:
[B]- Change the Internal IP address of the Router. The default = 192.168.2.1
                                  - Change the Subnet Mask. The default = 255.255.255.0
                                  - Enable/Disable the DHCP Server Function. Default= ON (Enabled)
                                  - Specify the Starting and Ending IP Pool Address. Default = Starting: 2 / Ending: 100
                                  - Specify the IP address Lease Time. Default= Forever
                                  - Specify a local Domain Name. Default = Belkin[/B]
Edit:

Also I´ve only got one cable, and my desktop haven´t got a wireless card, so when doing this I´m switching the plug back and fourth between the computers, so I´ll have to disconnect the cable, even if success to get back on here.

---

### Post by varunendra on 2014-08-02
I had a feeling that I was being too tekky while writing that, sorry :p

Do you know your router's IP address? Since you managed to log into it and change settings, I believe you do (unless you used the USB connection + router's windows application to log into it).

If it is, say, 192.168.1.1 (most often that is it, but can be different), then your network is on IP pattern "192.168.1.xx" - where "xx" can be anything from 0 to 255. You have to choose the value of "xx" such that it is not in use by any other device on your network.

For the DHCP, if you log into your router again, look for DHCP settings (usually under LAN settings, or a separate tab/link). Let us know whether it is enabled or not. If Enabled, there must be a range of IPs defined under it. This is the range that the DHCP is supposed to pick IPs from and assign them automatically to the connected devices so they can connect to the network.

If the DHCP is not enabled, or if not configured/working properly (usually has just a couple of settings), the connected devices would not get an IP address automatically and hence won't connect to the network (unless manually configured).

So.... you have to tell us -

1) Is DHCP enabled in your router?
2) What is the range defined under DHCP (if enabled)
3) What is the IP of your router (LAN side, not WAN side)

---

### Post by s-l-425434 on 2014-08-02
After connecting and once again disconnecting the cable, I went in to my DHCP client list, and my acer E15 is listed there with the ip 192.168.2.6.

Still with the internet cable connected, the little connections sign in the top right corner kept spinning like it was trying to connect.


Hmm, an edit on my last post didn´t register, I found out how to do what you told me to do. 
Changed the IP address to 192.168.2.9 
But in lan settings after I pull out the plug of the E15 it´s still shown in there, though as earlier mentioned 192.168.2.6

For the record:
1. Yes. DHCP enabled.
2. 2-100
3. [B]The default = 192.168.2.1
[/B]
:D

---

### Post by varunendra on 2014-08-02
Which means your laptop got an IP. Which further means it should have been connected (at least to the local network if not Internet). Why did you need to disconnect it then?

Assuming your router's IP is 192.168.2.1, can you ping it? That is, in terminal -
```
ping -c4 192.168.2.1
```
..returns any ping replies? Of course change the IP with your router's if it is different.

While the cable is plugged, please post back the output of -
```
nm-tool
route -n
```

---

### Post by s-l-425434 on 2014-08-02
I disconnected it because I had to get back on here and post back from the desktop with a working wired internet :).

---

### Post by varunendra on 2014-08-02
If this one (the working one) is Windows, please open its command prompt (If newer than Windows XP, you may have to open it with Admin privilege to do this), then post back the output of -
```
ipconfig /all
``` (or /a, I don't remember exactly)

If it is also Linux, the output of -
```
nm-tool
```..from it.

By looking at this output, we can confirm the working settings.

---

### Post by s-l-425434 on 2014-08-02
On the non working one with cable plugged in I ran ethtool again to confirm it was as it should be.

Here is the out put of the ping and the two commands.

```
simon@simon-Aspire-E5-511:~$ ping -c4 192.168.2.1
connect: Network is unreachable
    
simon@simon-Aspire-E5-511:~$ nm-tool

NetworkManager Tool

State: connecting

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             disconnected
  Default:           no
  HW Address:        B8:EE:65:BD:6E:DA

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Belkin:          Infra, 00:17:3F:3D:07:6E, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA2
    TDC-B30C:        Infra, 00:19:70:66:EC:36, Freq 2422 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    TDC-FB5E:        Infra, 00:21:86:EC:C5:E8, Freq 2457 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2


- Device: eth0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            r8168
  State:             connecting (getting IP configuration)
  Default:           no
  HW Address:        F8:A9:63:75:BB:8A

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on


simon@simon-Aspire-E5-511:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
simon@simon-Aspire-E5-511:~$ 


```

**Question: **Should I also set IPv6 to ignore on the wired connection?
On the working one.

```
simon@simon-Aspire-M5100:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             connected
  Default:           yes
  HW Address:        00:1C:25:4E:D5:D5

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.2.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1


```

---

### Post by varunendra on 2014-08-02
It was still in the process of getting an IP -
> **s-l-425434 said:**
> ```
- Device: eth0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            r8168
 ** State:             [COLOR="#FF0000"]connecting (getting IP configuration)[/COLOR]**
  Default:           no
```

It got one last time (192.168.2.6), but then you disconnected without checking further. Now if it doesn't succeed, I suggest you log into your router, and give us the details about the DHCP range (from which to which IP is in that range). If required, we shall then redefine the range so that some IP addresses are left outside DHCP range, and then we'll manually assign one of these 'left-out' IPs to your Ethernet interface to get you connected.

For manual configuration in Network Manager, you'll have to select (under "IPv4 settings") :

[INDENT]Method : Manual
IP : Any chosen IP that is out of DHCP range (for example, 192.168.2.210)
Subnet : 24
Gateway : 192.168.2.1

DNS servers : 8.8.8.8, 8.8.4.4[/INDENT]

---

### Post by s-l-425434 on 2014-08-02
I already posted the range.
[B]Starting and Ending IP Pool Address. Default = Starting: 2 / Ending: 100
:)
[/B]

---

### Post by varunendra on 2014-08-02
> **s-l-425434 said:**
> I already posted the range.
..In an edit after my post. New info in new posts please. :)

So, please try what I suggested with Network Manager settings above -

IP : 192.168.2.210

(rest as suggested already). Save > close > try to connect the wired connection. Success?

**PS:**
While putting the IP, Subnet, Gateway, press 'Enter' after filling in each setting, else it may not stick.

After it is saved, confirm the setting with "nm-tool" command.

---

### Post by s-l-425434 on 2014-08-02
Ok I´ll remember to post new information in new posts :)



"So, please try what I suggested with Network Manager settings above -

IP : 192.168.2.210

(rest as suggested already). Save > close > try to connect the wired connection. Success?

**PS:**
While putting the IP, Subnet, Gateway, press 'Enter' after filling in each setting, else it may not stick."

Ok, I will go do that now, but here is some addtional info in the mean time. 

When trying to connect, the nm-tool keeps telling me "getting IP configuration" for several minutes. After a couple of minutes and I try the command again it says "Disconnected" where the "Getting IP configuration" was previously. 
However, immediately after I plug my cable back into the desktop and go to DHCP clients it is listed with an IP. 192.168.2.6. 
So it´s like my router knows that it has assigned an IP to the device, but the device doesn´t recognize that the router has done so? 

Will try you manual settings now :)

---

### Post by s-l-425434 on 2014-08-02
HAHAHA! IT´S WORKING! Posting from wired connection on the laptop :D

---

### Post by varunendra on 2014-08-02
While it is possible that the router is assigning the IP ...6 to it and it is Ubuntu/network-card that is unable to receive the offered packet, it is also normal that once a router assigns an IP to a system, it remains listed for quite sometime even if the system is not connected anymore. This 'sometime' can be more than half an hour with some routers as far as I have experienced.

---

### Post by varunendra on 2014-08-02
> **s-l-425434 said:**
> HAHAHA! IT´S WORKING! Posting from wired connection on the laptop :D

So whether it is the router that does not like Linux, or the driver/card itself, the problem is, apparently that they are having trouble negotiating a DHCP offer. Either the router's firmware is stuck on a previous configuration/connection, or it is Ubuntu/the card/driver that is having trouble getting/recognizing the offered packet. I don't know of a way to be sure, but given the problem is with both the Ethernet and WiFi, I suspect it is your router that is kinda 'Slow' with Linux.

Either way, the manual configuration will work - just proved.

Now time to focus on WiFi?

If yes, please disconnect the cable (don't worry, with manual configuration, it'll work as soon as plugged again) > wait a couple of minutes > try to connect wirelessly > let it fail > run the wireless_script again > post back the fresh report.

---

### Post by s-l-425434 on 2014-08-02
Will do :D

---

### Post by s-l-425434 on 2014-08-02
Here is the script output after following the instructions:

```
 
    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

simon-Aspire-E5-511 3.13.0-32-generic i686,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Pentium(R) CPU  N3530  @ 2.16GHz
Memory : 7966 MB
Uptime : 21:11:57 up 38 min,  3 users,  load average: 0.13, 0.14, 0.17


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

01:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
    Subsystem: Acer Incorporated [ALI] Device [1025:0905]
    Kernel driver in use: r8168
02:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
    Subsystem: Lite-On Communications Inc Device [11ad:0642]
    Kernel driver in use: ath9k


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04f2:b455 Chicony Electronics Co., Ltd 
Bus 001 Device 004: ID 04ca:300b Lite-On Technology Corp. 
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface                 Soft blocked  Hard blocked
0: acer-wireless: Wireless LAN      no            no
1: acer-bluetooth: Bluetooth        yes           no
2: hci0: Bluetooth                  yes           no
3: phy0: Wireless LAN               no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

ath9k                 144602  0 
ath9k_common           13359  1 ath9k
ath9k_hw              438205  2 ath9k_common,ath9k
ath                    23922  3 ath9k_common,ath9k,ath9k_hw
mac80211              546051  1 ath9k
cfg80211              409394  3 ath,ath9k,mac80211
acer_wmi               31735  0 
sparse_keymap          13708  1 acer_wmi
wmi                    18673  1 acer_wmi
video                  18903  2 i915,acer_wmi


module parameters ~~~~~~~~~~~~~~~~~~

acer_wmi      (5): brightness=-1 | ec_raw_mode=N | force_series=0 | mailled=-1 | threeg=-1
ath9k         (5): blink=0 | bt_ant_diversity=0 | btcoex_enable=0 | nohwcrypt=0 | ps_enable=0
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=-1
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: disconnected
================o=============o========o==========  ====o=========o===========o==============o========  ===
 Interface & ID | Type        | Driver | State        | Default | Speed     | Support      | HW Addr   
================o=============o========o==========  ====o=========o===========o==============o========  ===
 wlan0          | 802.11 WiFi | ath9k  | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>

    TDC-B30C:        Infra, <MAC C-02 TDC-B30C>, Freq 2422 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    TDC-FB5E:        Infra, <MAC C-NA TDC-FB5E 1>, Freq 2457 MHz, Rate 54 Mb/s, Strength 12 WPA WPA2
    Belkin:          Infra, <MAC C-01 Belkin>, Freq 2462 MHz, Rate 54 Mb/s, Strength 64 WPA2
----------------+-------------+--------+--------------+---------+-----------+--------------+-----------
 eth0           | Wired       | r8168  | unavailable  | no      | 100 Mb/s  |              | <MAC eth0>
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

no-auto-default=<MAC eth0>,

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~

Belkin               : ssid=Belkin | mac-address=<MAC wlan0> | ipv4=auto | ipv6=ignore 


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
country DK:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5490 - 5710 @ 40), (N/A, 27), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 Belkin>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"Belkin"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000110658844e
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 TDC-B30C>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"TDC-B30C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000050f594c2b7
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist r8169


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[ath9k]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
srcversion:     7EAAD420ADF6B9354F0C8C1
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

[ath9k_common]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
srcversion:     696B00A6C59713EC0966997
depends:        ath,ath9k_hw

[ath9k_hw]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
srcversion:     4809F3842A0542CD6B556D3
depends:        ath

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

[acer_wmi]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/platform/x86/acer-wmi.ko
srcversion:     15371DC0E403E93954B38E5
depends:        wmi,sparse-keymap,video
parm:           mailled:Set initial state of Mail LED (int)
parm:           brightness:Set initial LCD backlight brightness (int)
parm:           threeg:Set initial state of 3G hardware (int)
parm:           force_series:Force a different laptop series (int)
parm:           ec_raw_mode:Enable EC raw mode (bool)

[wmi]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)

[video]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/acpi/video.ko
srcversion:     274A2250DEAB415D412A67C
depends:        
parm:           brightness_switch_enabled:bool
parm:           allow_duplicates:bool
parm:           use_native_backlight:int


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:0x0036 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Not Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modules]
“r8168&#8243;

[/etc/modprobe.d]
ath9k.conf        : options nohwcrypt=1
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-32-generic root=UUID=41fd691c-955f-43f1-8da0-b9576a475c48 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    1.303230] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.303765] audit: initializing netlink socket (disabled)
[    2.099668] r8168 Gigabit Ethernet driver 8.038.00-NAPI loaded
[   12.520729] wmi: Mapper loaded
[   12.538932] acer_wmi: Acer Laptop ACPI-WMI Extras
[   12.538954] acer_wmi: Function bitmap for Communication Button: 0x801
[   12.539115] acer_wmi: Brightness must be controlled by acpi video driver
[   12.562013] acer_wmi: Enabling Launch Manager failed: 0xe4 - 0x0
[   12.849861] ath: phy0: WB335 2-ANT card detected
[   12.849866] ath: phy0: Set BT/WLAN RX diversity capability
[   12.924739] ath: phy0: Enable LNA combining
[   12.930806] ath: phy0: ASPM enabled: 0x42
[   12.930808] ath: EEPROM regdomain: 0x65
[   12.930809] ath: EEPROM indicates we should expect a direct regpair map
[   12.930811] ath: Country alpha2 being used: 00
[   12.930812] ath: Regpair used: 0x65
[   15.680516] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.802533] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.802972] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2157.151687] wlan0: authenticate with <MAC C-01 Belkin>
[ 2157.170658] wlan0: send auth to <MAC C-01 Belkin> (try 1/3)
[ 2157.172656] wlan0: authenticated
[ 2157.173274] wlan0: associate with <MAC C-01 Belkin> (try 1/3)
[ 2157.176345] wlan0: RX AssocResp from <MAC C-01 Belkin> (capab=0x411 status=0 aid=2)
[ 2157.177034] wlan0: associated
[ 2157.177048] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2202.594413] wlan0: deauthenticating from <MAC C-01 Belkin> by local choice (reason=3)

    ======== Done ========


```

---

### Post by varunendra on 2014-08-02
A mistake I made earlier and overlooked since then. Please try the corrected command to create the ath9k.conf file again, with correct contents this time -
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
```

Followed by a reboot or -
```
sudo modprobe -rv ath9k
sudo modprobe -v ath9k
```
Can you connect wirelessly now? If not, please post back the outputs of -
```
grep -R [[:alnum:]] /sys/module/ath9k/parameters
dmesg | tail -20
```
..immediately after the connection attempt fails.

**PS:**
1:12 am (past midnight) now, time to fall dead, not sure when I can be back. Sunday is going to be ultra busy, perhaps. So.. Good Luck in advance, you have my masters on your thread :)

---

### Post by s-l-425434 on 2014-08-02
Thank you so insanely much, I could kiss you for getting the wired to work :D Sleep tight! 

Here is the output of the commands in question :)
```

simon@simon-Aspire-E5-511:~$ echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
[sudo] password for simon: 
options ath9k nohwcrypt=1
simon@simon-Aspire-E5-511:~$ sudo modprobe -rv ath9k
rmmod ath9k
rmmod mac80211
rmmod ath9k_common
rmmod ath9k_hw
rmmod ath
rmmod cfg80211
simon@simon-Aspire-E5-511:~$ sudo modprobe -v ath9k
insmod /lib/modules/3.13.0-32-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.13.0-32-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath.ko 
insmod /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko 
insmod /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko 
insmod /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko nohwcrypt=1 
simon@simon-Aspire-E5-511:~$ grep -R [[:alnum:]] /sys/module/ath9k/parameters
/sys/module/ath9k/parameters/blink:0
/sys/module/ath9k/parameters/bt_ant_diversity:0
/sys/module/ath9k/parameters/nohwcrypt:1
/sys/module/ath9k/parameters/btcoex_enable:0
/sys/module/ath9k/parameters/ps_enable:0
simon@simon-Aspire-E5-511:~$ dmesg | tail -20
[ 4849.295375] ath: Regpair used: 0x65
[ 4849.296234] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[ 4849.296749] ieee80211 phy0: Atheros AR9565 Rev:1 mem=0xf9380000, irq=17
[ 4849.319794] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4849.320432] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4849.320907] cfg80211: Calling CRDA for country: DK
[ 4849.335427] cfg80211: Regulatory domain changed to country: DK
[ 4849.335433] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 4849.335437] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 4849.335439] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 4849.335442] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 4849.335444] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[ 4849.335447] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm)
[ 4869.398714] wlan0: authenticate with 00:17:3f:3d:07:6e
[ 4869.414182] wlan0: direct probe to 00:17:3f:3d:07:6e (try 1/3)
[ 4869.615791] wlan0: send auth to 00:17:3f:3d:07:6e (try 2/3)
[ 4869.756057] wlan0: send auth to 00:17:3f:3d:07:6e (try 3/3)
[ 4869.904118] wlan0: authentication with 00:17:3f:3d:07:6e timed out
[ 4874.423644] wlan0: deauthenticating from 00:17:3f:3d:07:6e by local choice (reason=3)
[ 4879.438646] wlan0: deauthenticating from 00:17:3f:3d:07:6e by local choice (reason=3)
simon@simon-Aspire-E5-511:~$ 


```

---

### Post by praseodym on 2014-08-02
```
[ 4874.423644] wlan0: deauthenticating from 00:17:3f:3d:07:6e by local choice (reason=3)
```
Reason 3 is a network-manager issue. Try Wicd:
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
Chose **wlan0** as interface name and **wext** as driver.

---

### Post by s-l-425434 on 2014-08-02
could you please expand on: 

"Chose **wlan0** as interface name and **wext** as driver" :)?

---

### Post by s-l-425434 on 2014-08-02
After running: 

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

my nm-tool report went from saying:

```
  configuring 
```

To 

```
 Getting IP configuration 
```

As I got earlier on the wired.
I tried then manually configuring the wireless connection using the above instructions I did for the wireless, and now it works!

Thanks everyone! I don´t know if this is a permanent fix for other wireless networks, I.e. if I wanna connect to a public network? 
But so far I guess this is solved :)

---

### Post by praseodym on 2014-08-02
Deactivate the network manager from the autostart! Otherwise both the NM and Wicd are started.

P.S.: Glad it worked

---

### Post by svenoh on 2015-03-23
I the same problem with an Asus laptop and after installing 14.04 recommended updates I have no network connection at all.

I did run a wireless info scrip and got this: 


    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

sven-Q400A 3.13.0-46-generic x86_64,  Ubuntu 14.04.2 LTS, trusty

CPU    : Intel(R) Core(TM) i7-3632QM CPU @ 2.20GHz
Memory : 7870 MB
Uptime : 11:28:05 up 40 min,  1 user,  load average: 0.52, 0.38, 0.32


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 2230 [8086:0887] (rev c4)
    Subsystem: Intel Corporation Centrino Wireless-N 2230 BGN [8086:4062]
03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1467]


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04f2:b33e Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 8087:07da Intel Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 058f:6387 Alcor Micro Corp. Flash Drive
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~




module parameters ~~~~~~~~~~~~~~~~~~


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: disconnected
================o======o========o========o========  =o===========o==============o===========
 Interface & ID | Type | Driver | State  | Default | Speed     | Support      | HW Addr   
================o======o========o========o========  =o===========o==============o===========
                |      |        |        |         |           |              |           
----------------+------+--------+--------+---------+-----------+--------------+-----------


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



Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : es_DO.UTF-8)


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

           - 


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~



blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x1969:/sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC  eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*",  NAME="eth0"

# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC  wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*",  NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Not Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modules]
loop

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-46-generic root=UUID=c97d1231-8f0c-4b08-8ed1-000bf10ccff2 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.419390] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.419683] audit: initializing netlink socket (disabled)
[    1.601661] psmouse serio4: elantech: assuming hardware version 4 (with firmware version 0x361f01)

    ======== Done ========

Any recommendations?

---

### Post by praseodym on 2015-03-24
Yes, load the drivers:
```

sudo modprobe -v iwlwifi
sudo modprobe -v atl1c
```

---

### Post by svenoh on 2015-03-24
Thanks:

But i get this error:

ERROR: could not insert 'iwlwifi': Function not implemented
modprobe: FATAL: Module atl1c not found.

Any other suggestions are very much appreciated?

---

### Post by praseodym on 2015-03-24
Obviously, the driver file is missing:

[http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-extra-3.13.0-46-generic_3.13.0-46.79_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-extra-3.13.0-46-generic_3.13.0-46.79_amd64.deb)

Save it in "Downloads" and install via
```

sudo dpkg -i ~/Downloads/*.deb
```
Reboot.

---

### Post by svenoh on 2015-03-24
Success, thank you so much!!!!!

---

