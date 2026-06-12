---
title: "Netgear WNDA 3100 wireless adapter"
date: 2014-10-22
forum: Networking &amp; Wireless
---

### Post by djrauland on 2014-10-22
I've followed various threads and still cant seem to get this to work, mainly [http://ubuntuforums.org/showthread.php?t=1964173](http://ubuntuforums.org/showthread.php?t=1964173). 

Here's some relevent information:

```
lsusb
```
Result: Bus 003 Device 004: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]

I have installed the driver,
```
ndiswrapper -l
```
Result: bcmn43xx32 : driver installed
    device (0846:9011) present
bcmn43xx64 : driver installed
    device (0846:9011) present

It looks like things are going wrong here,
```
sudo modprobe ndiswrapper
```
No result
```
dmesg | grep ndis
```
Result:[  286.921666] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel
[  286.922390] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[  287.143032] ndiswrapper (check_nt_hdr:141): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[  287.143035] ndiswrapper (load_sys_files:200): couldn't prepare driver 'bcmn43xx32'
[  287.143240] ndiswrapper (load_wrap_driver:103): couldn't load driver bcmn43xx32; check system log for messages from 'loadndisdriver'
[  287.143260] usbcore: registered new interface driver ndiswrapper
```
iwconfig
```
Result:eth0      no wireless extensions.

lo        no wireless extensions.

---

### Post by chili555 on 2014-10-22
You don't need both the 32- and the 64-bit driver. Let's remove the 32-bit:```
sudo ndiswrapper -e bcmn43xx32
```Reboot and let us see the diagnostics again.

---

### Post by djrauland on 2014-10-22
Removed the 32 and robooted. Voila, we have wifi thank you very much!

---

### Post by djrauland on 2014-10-22
Update: the connections became available but Im still unable to connect to a network. I rebooted again and the connections disappeared. After this section of commands, the connections became available again, but still unable to connect.```
sudo modprobe ndiswrapper
dmesg | grep ndis
```

---

### Post by chili555 on 2014-10-23
After you reload ndiswrapper, what is the result of:```
dmesg | grep ndis
```Thanks.

---

### Post by djrauland on 2014-10-23
Result:[ 5929.529393] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel
[ 5929.533530] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[ 5929.711957] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[ 5929.964919] usbcore: registered new interface driver ndiswrapper

---

### Post by chili555 on 2014-10-23
Looks perfect! We wonder what Network Manager is doing:```
cat /var/log/syslog | grep etwork | tail -n20
sudo iwlist wlan0 scan

```

---

### Post by djrauland on 2014-10-23
Upon reboot, the connections disappeared again. I followed the procedure that made them appear before but got a different result this time with no wireless available. 
```
sudo modprobe ndiswrapper
dmesg | grep ndis
```
Result: [   50.929572] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel
[   50.930187] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[   51.170814] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[   52.184001] ndiswrapper (mp_init:211): couldn't initialize device: C0000001
[   52.184004] ndiswrapper (pnp_start_device:395): Windows driver couldn't initialize the device (C0000001)
[   52.184007] ndiswrapper (mp_halt:254): device ffff880211e61880 is not initialized - not halting
[   52.184008] ndiswrapper: device eth%d removed
[   52.184044] ndiswrapper: probe of 3-13:1.0 failed with error -22
[   52.184059] usbcore: registered new interface driver ndiswrapper

---

### Post by chili555 on 2014-10-24
I am surprised that you are getting different results in *dmesg*. I wonder if things improve if the driver is available on boot rather than being manually inserted later. Let's get it to load on boot:```
sudo -i
echo ndiswrapper  >>  /etc/modules
exit
```Reboot and let's check again:```
dmesg | grep ndis
sudo iwlist wlan0 scan
cat /var/log/syslog | grep etwork | tail -n20
```

---

### Post by joe134 on 2014-11-07
I am having an issue with this wireless adapter as well - although I am currently online and using it, the connection rate is horrible at best and I seem to be having frequent drops/reconnects. I am not sure but the drops could have been the onboard wireless which has no antenna connected, and I finally got it to stop trying to connect earlier today - leading me to being certain it was something wrong with usb adapter. I have scoured the forums for a couple hours (this time) to try and fix the speed issue but I can't come up with anything to fix it. I would like to mention that Chili555's prior post's on this adapter and the link to the drivers proved invaluable in getting this adapter working in the first place, also I used varunendra's script to get the following info:

```


    ======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


joe-Aspire-7745G 3.13.0-39-generic x86_64,  Ubuntu 14.04.1 LTS, trusty


CPU    : Intel(R) Core(TM) i7 CPU       Q 740  @ 1.73GHz
Memory : 11949 MB
Uptime : 00:38:37 up 16:02,  3 users,  load average: 1.16, 1.34, 1.15




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


09:00.0 Network controller [0280]: Qualcomm Atheros AR9287 Wireless Network Adapter (PCI-Express) [168c:002e] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e034]
    Kernel driver in use: ath9k




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 002 Device 004: ID 0bc2:5031 Seagate RSS LLC FreeAgent GoFlex USB 3.0
Bus 002 Device 003: ID 099a:2515 Zippy Technology Corp. 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 045: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]
Bus 001 Device 006: ID 192f:0916 Avago Technologies, Pte. 
Bus 001 Device 003: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~


wlan1     IEEE 802.11g  ESSID:"[MySSID]"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC C-01 [MySSID]>   
          Bit Rate=5.5 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:84/100  Signal level:-42 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:931413  Invalid misc:1696209   Missed beacon:0


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          




rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


      Interface                 Soft blocked  Hard blocked
0: phy0: Wireless LAN               no            no
1: acer-wireless: Wireless LAN      no            no




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


acer_wmi               32522  0 
sparse_keymap          13948  1 acer_wmi
ndiswrapper           283985  0 
ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              630653  1 ath9k
cfg80211              484040  3 ath,ath9k,mac80211
wmi                    19177  1 acer_wmi
video                  19476  1 acer_wmi




module parameters ~~~~~~~~~~~~~~~~~~


acer_wmi      (5): brightness=-1 | ec_raw_mode=N | force_series=0 | mailled=-1 | threeg=-1
ath9k         (5): blink=0 | bt_ant_diversity=0 | btcoex_enable=0 | nohwcrypt=0 | ps_enable=0
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
ndiswrapper   (6): 
video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=-1
wmi           (2): debug_dump_wdg=N | debug_event=N




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: connected (global)
=================o=============o=============o====  ==========o=========o===========o==============o==  =========
 Interface & ID  | Type        | Driver      | State        | Default | Speed     | Support      | HW Addr   
=================o=============o=============o====  ==========o=========o===========o==============o==  =========
 wlan1  [[MySSID]] | 802.11 WiFi | ndiswrapper | connected    | yes     | 5 Mb/s    | WEP/WPA/WPA2 | <MAC wlan1>


    *[MySSID]:         Infra, <MAC C-01 [MySSID]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 76 WPA2
    [NeighborSSID]:              Infra, <MAC C-03 [NeighborSSID]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WPA2
    [NeighborSSID]:          Infra, <MAC C-02 [NeighborSSID]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WPA


    Address:         192.168.1.xxx
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.x.x
    DNS:             192.168.x.x
-----------------+-------------+-------------+--------------+---------+-----------+--------------+-----------
 wlan0           | 802.11 WiFi | ath9k       | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>


    [MySSID]:          Infra, <MAC C-01 [MySSID]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA2
-----------------+-------------+-------------+--------------+---------+-----------+--------------+-----------




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


[MySSID]               : ssid=[MySSID] | mac-address=<MAC wlan1> | ipv4=auto | ipv6=auto 
[MySSID]               : ssid=[MySSID] | permissions=user:joe:; | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 




interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~


nameserver 127.0.1.1




Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.x.x     0.0.0.0         UG    0      0        0 wlan1
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan1


--- 192.168.x.x ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1000ms
rtt min/avg/max/mdev = 1.473/1.543/1.614/0.080 ms


--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.014/0.032/0.050/0.018 ms




iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~


(Region : "en_US.UTF-8")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS




iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan1     14 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 14 (2.484 GHz)


          Current Frequency:2.412 GHz (Channel 1)
          Channel 01 (2.412 GHz) - 14 (2.484 GHz)
wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)




iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan1     Scan completed :
          Cell 01 - Address: <MAC C-01 [MySSID]>
                    ESSID:"[MySSID]"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:84/100  Signal level:-42 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 [NeighborSSID]>
                    ESSID:"[NeighborSSID]"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:31/100  Signal level:-76 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 [NeighborSSID]>
                    ESSID:"[NeighborSSID]"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:34/100  Signal level:-74 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 [MySSID]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"[MySSID]"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000006e3cbcf3da
                    Extra: Last beacon: 760ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK




blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[acer_wmi]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/platform/x86/acer-wmi.ko
srcversion:     15371DC0E403E93954B38E5
depends:        wmi,sparse-keymap,video
parm:           mailled:Set initial state of Mail LED (int)
parm:           brightness:Set initial LCD backlight brightness (int)
parm:           threeg:Set initial state of 3G hardware (int)
parm:           force_series:Force a different laptop series (int)
parm:           ec_raw_mode:Enable EC raw mode (bool)


[ndiswrapper]
filename:       /lib/modules/3.13.0-39-generic/updates/dkms/ndiswrapper.ko
version:        1.59
srcversion:     DC1EFD919FDF2DB80D424C6
depends:        
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)


[ath9k]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
srcversion:     DF02272C2FA4678C49046E5
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)


[ath9k_common]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
srcversion:     696B00A6C59713EC0966997
depends:        ath,ath9k_hw


[ath9k_hw]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
srcversion:     4809F3842A0542CD6B556D3
depends:        ath


[ath]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/ath/ath.ko
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211


[mac80211]
filename:       /lib/modules/3.13.0-39-generic/kernel/net/mac80211/mac80211.ko
srcversion:     B822641624778B987844F6F
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.13.0-39-generic/kernel/net/wireless/cfg80211.ko
srcversion:     C2478077E22138832B71659
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[wmi]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


[video]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/acpi/video.ko
srcversion:     FBDB15F61F4F35FB6EE9AC8
depends:        
parm:           brightness_switch_enabled:bool
parm:           allow_duplicates:bool
parm:           use_native_backlight:int




udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~


# PCI device 0x168c:0x002e (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# USB device 0x:0x (ndiswrapper)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan1>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"




Custom files/entries ~~~~~~~~~~~~~~~


/etc/modules        : Not Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default


[/etc/modules]
ndiswrapper


[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en




Kernel boot line ~~~~~~~~~~~~~~~~~~~


BOOT_IMAGE=/boot/vmlinuz-3.13.0-39-generic root=UUID=b9c3e9dc-5f99-4934-ba30-25f639eacad2 ro quiet splash vt.handoff=7




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    1.020805] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.021221] audit: initializing netlink socket (disabled)
[    1.806713] wmi: Mapper loaded
[   18.119028] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel
[   18.120510] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[   18.185789] ath: phy0: ASPM enabled: 0x42
[   18.185795] ath: EEPROM regdomain: 0x65
[   18.185797] ath: EEPROM indicates we should expect a direct regpair map
[   18.185801] ath: Country alpha2 being used: 00
[   18.185803] ath: Regpair used: 0x65
[   18.263785] acer_wmi: Acer Laptop ACPI-WMI Extras
[   18.263880] acer_wmi: Function bitmap for Communication Button: 0x1
[   18.263887] acer_wmi: Brightness must be controlled by acpi video driver
[   18.566288] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[   19.110925] wlan1: ethernet device <MAC wlan1> using NDIS driver: bcmn43xx64, version: 0x50a4f1e, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:9011.F.conf
[   19.113559] wlan1: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[   25.111475] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   26.897004] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   26.897286] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   26.917078] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   26.920260] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   27.874306] wlan0: authenticate with <MAC C-01 [MySSID]>
[   27.894038] wlan0: send auth to <MAC C-01 [MySSID]> (try 1/3)
[   27.959885] wlan0: authenticated
[   27.962721] wlan0: associate with <MAC C-01 [MySSID]> (try 1/3)
[   27.966657] wlan0: RX AssocResp from <MAC C-01 [MySSID]> (capab=0x411 status=0 aid=3)
[   27.966725] wlan0: associated
[   27.966769] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   37.571051] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[  208.743909] wlan0: deauthenticating from <MAC C-01 [MySSID]> by local choice (reason=3)
[  316.418846] wlan0: authenticate with <MAC C-01 [MySSID]>
[  316.438458] wlan0: send auth to <MAC C-01 [MySSID]> (try 1/3)
[  316.455843] wlan0: authenticated
[  316.456270] wlan0: associate with <MAC C-01 [MySSID]> (try 1/3)
[  316.486274] wlan0: RX AssocResp from <MAC C-01 [MySSID]> (capab=0x411 status=0 aid=4)
[  316.486344] wlan0: associated
[  324.214843] ndiswrapper: device wlan1 removed
[  328.747977] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[  329.300741] wlan1: ethernet device <MAC wlan1> using NDIS driver: bcmn43xx64, version: 0x50a4f1e, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:9011.F.conf
[  329.303450] wlan1: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[  329.323497] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  329.324062] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  349.901265] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 5142.640238] wlan0: deauthenticating from <MAC C-01 [MySSID]> by local choice (reason=3)
[18309.166022] wlan0: authenticate with <MAC C-01 [MySSID]>
[18309.194323] wlan0: send auth to <MAC C-01 [MySSID]> (try 1/3)
[18309.196346] wlan0: authenticated
[18309.197302] wlan0: associate with <MAC C-01 [MySSID]> (try 1/3)
[18309.201182] wlan0: RX AssocResp from <MAC C-01 [MySSID]> (capab=0x411 status=0 aid=9)
[18309.201256] wlan0: associated
[18313.547295] wlan0: deauthenticating from <MAC C-01 [MySSID]> by local choice (reason=3)
[18407.089859] wlan0: authenticate with <MAC C-01 [MySSID]>
[18407.118088] wlan0: direct probe to <MAC C-01 [MySSID]> (try 1/3)
[18407.320898] wlan0: direct probe to <MAC C-01 [MySSID]> (try 2/3)
[18407.524776] wlan0: send auth to <MAC C-01 [MySSID]> (try 3/3)
[18407.526839] wlan0: authenticated
[18407.528601] wlan0: associate with <MAC C-01 [MySSID]> (try 1/3)
[18407.532487] wlan0: RX AssocResp from <MAC C-01 [MySSID]> (capab=0x411 status=0 aid=9)
[18407.532589] wlan0: associated
[19872.129102] wlan0: deauthenticating from <MAC C-01 [MySSID]> by local choice (reason=3)
[19926.011409] ndiswrapper: device wlan1 removed
[19946.037002] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[19946.584157] wlan1: ethernet device <MAC wlan1> using NDIS driver: bcmn43xx64, version: 0x50a4f1e, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:9011.F.conf
[19946.586989] wlan1: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[19946.609959] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[19946.610246] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[19967.214911] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[20513.292418] wlan0: authenticate with <MAC C-01 [MySSID]>
[20513.320022] wlan0: direct probe to <MAC C-01 [MySSID]> (try 1/3)
[20513.523458] wlan0: direct probe to <MAC C-01 [MySSID]> (try 2/3)
[20513.731343] wlan0: direct probe to <MAC C-01 [MySSID]> (try 3/3)
[20513.935321] wlan0: authentication with <MAC C-01 [MySSID]> timed out
[20514.939835] wlan0: authenticate with <MAC C-01 [MySSID]>
[20514.967987] wlan0: direct probe to <MAC C-01 [MySSID]> (try 1/3)
[20515.171065] wlan0: direct probe to <MAC C-01 [MySSID]> (try 2/3)
[20515.374982] wlan0: direct probe to <MAC C-01 [MySSID]> (try 3/3)
[20515.578938] wlan0: authentication with <MAC C-01 [MySSID]> timed out
[20528.724458] wlan0: authenticate with <MAC C-01 [MySSID]>
[20528.752353] wlan0: direct probe to <MAC C-01 [MySSID]> (try 1/3)
[20528.955588] wlan0: direct probe to <MAC C-01 [MySSID]> (try 2/3)
[20529.159592] wlan0: direct probe to <MAC C-01 [MySSID]> (try 3/3)
[20529.363431] wlan0: authentication with <MAC C-01 [MySSID]> timed out
[20531.267414] wlan0: authenticate with <MAC C-01 [MySSID]>
[20531.294997] wlan0: send auth to <MAC C-01 [MySSID]> (try 1/3)
[20531.325230] wlan0: authenticated
[20531.327000] wlan0: associate with <MAC C-01 [MySSID]> (try 1/3)
[20531.378760] wlan0: RX AssocResp from <MAC C-01 [MySSID]> (capab=0x411 status=0 aid=9)
[20531.378824] wlan0: associated
[20540.100214] wlan0: deauthenticating from <MAC C-01 [MySSID]> by local choice (reason=3)


    ======== Done ========



```

and a cleaner dmesg:
```

dmesg | grep ndis
[   18.119028] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel
[   18.120510] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[   18.566288] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[   19.114255] usbcore: registered new interface driver ndiswrapper
[  324.214843] ndiswrapper: device wlan1 removed
[  328.747977] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[19926.011409] ndiswrapper: device wlan1 removed
[19946.037002] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded

```

Hope there is some insight in there other than - yeah the connections sucks :)

---

### Post by chili555 on 2014-11-07
Why are using this device when you have an apparently working internal device? I realize that ath9k is a bit tricky, but have you fully researched methods to get your Atheros working as expected?

---

### Post by joe134 on 2014-11-07
Phew... ok so here is the long explanation - a while back my laptop started overheating repeatedly even after being blown out, eventually I was forced to remove the motherboard from the laptop completely and install (I use install loosely here) it into a an old emachine desktop case, and rig a fan from another laptop to the heatsink. So the internal adapter is physically present, however I do not have any antennae hooked up to it, and honestly have been to lazy to try and find new antennae wires from another laptop to put into it, that in combination with the fact the internal wireless is only .11b/g instead of b/g/n has lead me to really do everything I can to get this one working, on my win8 partition even when it had proper antennae connected the WNDA3100 beat the snot out of my onboard for transmission rate (e.g. ubuntu iso torrent test: 8 MB/s WNDA3100 vs. 3 MB/s onboard) and stability to hold those transmission rates. Now the given i am sitting practically on top of my router (a RT AC66-R) {it's mounted next to the cieling on floor 1 of my house and this pc is on floor 2 6 ft away straight line, there is 1 electric line ran in the floor/ceiling that intersect the direct line of sight that powers 1 lightbulb} I am able to get the internal to connect however the connection is not stable and has very high packet loss even going to the router. So all in all - it's this one I want to get working (as best as possible). 

I am wondering if the "tx excessive retries" being so high is a symptom of what is causing the problem. I can't find an explanation what it is or what could be causing it, I would assume it's a figure of packet loss? Could maybe adjusting something along the lines of the MTU work? I really am not an expert *or* novice when it comes to networking and this is right outside what I fully understand how to fix.
I do appreciate your (and anyone else's) expertise on this.

---

### Post by chili555 on 2014-11-07
Yikes. Just yikes.

Usually, laptop wireless cards are attached to a PCIe or similar slot: [http://galleryplus.ebayimg.com/ws/web/200918060988_1_0_1/1000x1000.jpg](http://galleryplus.ebayimg.com/ws/web/200918060988_1_0_1/1000x1000.jpg) I think my first step would be to try to, at least temporarily, remove it altogether. It is certainly likely that its driver suite is interfering here.

If that is not a realistic option, let's blacklist its driver:```
sudo -i
echo "blacklist ath9k"  >>  /etc/modprobe.d/blacklist.conf
modprobe -r ath9k
exit
```Any improvement?

---

### Post by joe134 on 2014-11-07
Ok, so I am unable to remove the onboard nic (now permanently due to a stripped screw), I however did follow your instructions  for blacklisting the driver (that part worked fine), I then also disconnected and reconnected the dongle, rebooted, and started up a ubuntu 14.04 torrent, the torrent is capping out at 312KiB/s 23 minutes into downloading  (win8 I would likely get the 4-6 MB/s). iwconfig is returning same results with ```
iwconfigwlan1     IEEE 802.11g  ESSID:"[my ssid]"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 10:C3:7B:CE:80:08   
          Bit Rate=5.5 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:73/100  Signal level:-49 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:50713  Invalid misc:80982   Missed beacon:0


lo        no wireless extensions.



``` I had started the torrent before rebooting so that is 50k on a fresh boot over 23 minutes.

---

### Post by chili555 on 2014-11-07
If there are no clues here, then I'd look at the settings in the router:```
dmesg | grep -e wlan -e ndis
```

WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, I have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. After making these changes, reboot the router.

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

---

### Post by joe134 on 2014-11-07
Found those instructions earlier and checked some of them already. So - router was already on WPA2-AES, channel set to explicit 20mhz from 20/40, REGDOMAIN now explicitly set (both temp and perm), IPV6 set to ignore on wlan1.
output of  [COLOR=#000000][FONT=Ubuntu Mono]dmesg | grep -e wlan -e ndis
[/FONT][/COLOR]```
Aspire-7745G:~$ dmesg | grep -e wlan -e ndis
>>>[   13.388180] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel
[   13.389245] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[   14.011829] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[   14.271498] wlan0: ethernet device 4c:60:de:82:85:5a using NDIS driver: bcmn43xx64, version: 0x50a4f1e, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:9011.F.conf
[   14.273841] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[   14.275714] usbcore: registered new interface driver ndiswrapper
[   17.253729] ndiswrapper: interface renamed to 'wlan1'
[   17.253751] systemd-udevd[474]: renamed network interface wlan0 to wlan1
[   33.519849] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   33.520101] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   65.260510] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 2667.310215] ndiswrapper: device wlan1 removed
[ 2671.078141] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[ 2671.630627] wlan0: ethernet device 4c:60:de:82:85:5a using NDIS driver: bcmn43xx64, version: 0x50a4f1e, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:9011.F.conf
[ 2671.632614] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[ 2671.657024] ndiswrapper: interface renamed to 'wlan1'
[ 2671.657065] systemd-udevd[5622]: renamed network interface wlan0 to wlan1
[ 2671.662698] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 2671.663110] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 2692.267836] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready

```

>>>[   13.388180] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel

Problem? From what I can find on google you (have read so many of your posts now...) normally attribute this to a fouled ndiswrapper installation - but then there are also a host of other errors normally after it too...

---

### Post by chili555 on 2014-11-07
> >>>[ 13.388180] ndiswrapper: module verification failed: signature and/or required key missing - tainting kernel

Problem? From what I can find on google Not really a problem; it may safely be ignored. Here is more information about the subject. [http://stackoverflow.com/questions/24975377/kvm-module-verification-failed-signature-and-or-required-key-missing-taintin](http://stackoverflow.com/questions/24975377/kvm-module-verification-failed-signature-and-or-required-key-missing-taintin)

In this case, the module is not prevented from loading, it simply loads with a harmless warning. This really shouldn't happen with an Ubuntu default install from the repositories, but it does. 

It happens most often with modules compiled from source code where the authors didn't get an Ubuntu signing key, a Mint, an Arch, a Debian, etc., etc. or, more likely, any keys at all!!

When I see it and my next post is that the install is incorrect, it is because there are many actual errors along with this warning.

So, has performance improved? At all? A little??

---

### Post by joe134 on 2014-11-07
No, performance has actually worsened. I lost access to my NAS (external freeagent goflex on my rt66), it says that there is a firewall? but to my knowledge I don't have one. Deluge is running a bunch of torrents and staying between 120 - 250kbps, and when it runs it kills all other internet access - XBMC was on 15 minutes trying to update 1 movie when I finally closed Deluge and then it snapped right to and finished. iwconfig still shows errors and that horrible connection rate.
I did notice one thing and not sure if it make a difference or give you any idea - when the desktop first loads, iwconig will show it trying to connect at 300 bit rate, then 170 (or so) bit rate, and again at 110 (or so) bit rate, before finally connecting at 5.5 - each time it attempts a new speed it pops up with a "connection lost" (sorry don't have the error in front of me I think that verbatim). :confused:

```

Aspire-7745G:~$ iwconfig
wlan1     IEEE 802.11g  ESSID:"HASSAN"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 10:C3:7B:CE:80:08   
          Bit Rate=5.5 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:89/100  Signal level:-39 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:106448  Invalid misc:163858   Missed beacon:0


lo        no wireless extensions.

```

---

### Post by chili555 on 2014-11-07
> it trying to connect at 300 bit rate, then 170 (or so) bit rate, and again at 110 (or so) bit rate, before finally connecting at 5.5 - each time it attempts a new speed it pops up with a "connection lost"I think that's the router and the Netgear negotiating a suitable rate. 

You might try a different channel in the router. You might try with 5 GHz disabled. You might try with N disabled.

We are dealing with a kludge using Win XP files. While I don't expect pristine 300 Mb/s performance, I'd certainly hope for better than:```
wlan1     IEEE 802.11g  ESSID:"HASSAN"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 10:C3:7B:CE:80:08   
          Bit Rate=[COLOR="#FF0000"]5.5 Mb/s[/COLOR]   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:89/100  Si
```Is your router set to mixed B, G and N? Or N only? I'd try mixed.

---

