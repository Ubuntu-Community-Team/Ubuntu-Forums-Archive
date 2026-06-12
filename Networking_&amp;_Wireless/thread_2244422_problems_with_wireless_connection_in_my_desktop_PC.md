---
title: "problems with wireless connection in my desktop PC and wireless card"
date: 2014-09-16
forum: Networking &amp; Wireless
---

### Post by rafael18 on 2014-09-16
Hi. My problem is about the wireless connection in my desktop PC: it is unstable. When I turn on the PC, sometimes the wireless works connecting to the signal immediately, but in other occasions it does not. The network is detected, but I cannot connect, even if I try manually: I put the password, the system try to connect but after some minutes it asks for the password again. I have tried turning the PC off, but it does not make any change. The connection is randomly, sometime yes, sometime no. Sometime it connects after some minutes... When I tried to connect using the network manager I can see that stages: 
connecting > putting interface up > validating identification......... and it cannot go further. 

I have had this problem since I was using Lubuntu 13.04. Now I have Lubuntu 14.04 and the problems remains. I live in a residence for students and I am the only one that has this problem. In addition, I cannot make changes in the router.

I used the **[[COLOR=DarkRed]_Wireless Script_[/COLOR]]("http://ubuntuforums.org/showthread.php?p=13024222#post13024222") **to get a detail of the system while is working 
I will appreciate any help.
Thanks

```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

bitacovir-Precision-WorkStation-670 3.13.0-35-generic x86_64,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Xeon(TM) CPU 3.60GHz
Memory : 3887 MB
Uptime : 07:28:22 up  1:11,  2 users,  load average: 0.28, 0.20, 0.20


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

02:0c.0 Ethernet controller [0200]: Qualcomm Atheros AR2417 Wireless Network Adapter [AR5007G 802.11bg] [168c:001d] (rev 01)
    Subsystem: Qualcomm Atheros Device [168c:2055]
    Kernel driver in use: ath5k
--
03:0e.0 Ethernet controller [0200]: Intel Corporation 82545GM Gigabit Ethernet Controller [8086:1026] (rev 04)
    Subsystem: Dell Precision Workstation 670 Mainboard [1028:0168]
    Kernel driver in use: e1000


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 002: ID 1bcf:0c31 Sunplus Innovation Technology Inc. SPIF30x Serial-ATA bridge
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 003: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 005 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bg  ESSID:"Vidragon"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC C-01 Vidragon>   
          Bit Rate=36 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=38/70  Signal level=-72 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:54  Invalid misc:403   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

mxm_wmi                13021  1 nouveau
wmi                    19177  2 mxm_wmi,nouveau
ath5k                 149924  0 
ath                    28698  1 ath5k
mac80211              630653  1 ath5k
cfg80211              484040  3 ath,ath5k,mac80211


module parameters ~~~~~~~~~~~~~~~~~~

ath5k         (3): fastchanswitch=N | nohwcrypt=N | no_hw_rfkill_switch=N
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
===================o=============o========o=============o=========o===========o==============o===========
 Interface & ID    | Type        | Driver | State       | Default | Speed     | Support      | HW Addr   
===================o=============o========o=============o=========o===========o==============o===========
 eth0              | Wired       | e1000  | unavailable | no      |           |              | <MAC eth0>
-------------------+-------------+--------+-------------+---------+-----------+--------------+-----------
 wlan0  [Vidragon] | 802.11 WiFi | ath5k  | connected   | yes     | 36 Mb/s   | WEP/WPA/WPA2 | <MAC wlan0>

    Vidragon-2.4G:   Infra, <MAC C-02 Vidragon-2.4G>, Freq 2412 MHz, Rate 54 Mb/s, Strength 45 WPA
    Vidragon-2.4G_2GEXT: Infra, <MAC C-03 Vidragon-2.4G_2GEXT>, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WPA
    *Vidragon:       Infra, <MAC C-01 Vidragon>, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WPA

    Address:         192.168.0.28
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1
    DNS:             192.168.0.1
-------------------+-------------+--------+-------------+---------+-----------+--------------+-----------


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

Vidragon             : ssid=Vidragon | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

--- 192.168.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 2.998/4.057/5.116/1.059 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.038/0.040/0.043/0.006 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_AU.UTF-8")


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)

          Current Frequency:2.437 GHz (Channel 6)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 Vidragon>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"Vidragon"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000b8a7b5d3c
                    Extra: Last beacon: 8ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 Vidragon-2.4G>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"Vidragon-2.4G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000268a8a7939
                    Extra: Last beacon: 8ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 Vidragon-2.4G_2GEXT>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"Vidragon-2.4G_2GEXT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000070599c3ba
                    Extra: Last beacon: 8ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/libpisock9.conf]
blacklist visor


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

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

[ath5k]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
srcversion:     F36818A2F0BCB2B0CC9BB8C
depends:        mac80211,cfg80211,ath
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)

[ath]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/ath/ath.ko
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211

[mac80211]
filename:       /lib/modules/3.13.0-35-generic/kernel/net/mac80211/mac80211.ko
srcversion:     D491AB7C521706DA5F4BE7C
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-35-generic/kernel/net/wireless/cfg80211.ko
srcversion:     C2478077E22138832B71659
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:02.0/0000:01:00.2/0000:03:0e.0 (e1000)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:02.0/0000:01:00.0/0000:02:0c.0 (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


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

BOOT_IMAGE=/boot/vmlinuz-3.13.0-35-generic root=UUID=30c9ecf6-a26a-4b75-9b73-4376d25ea679 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.841765] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.842232] audit: initializing netlink socket (disabled)
[   12.272220] ath5k 0000:02:0c.0: PCI IRQ 26 -> rerouted to legacy IRQ 18
[   12.272286] ath5k 0000:02:0c.0: registered as 'phy0'
[   12.854065] ath: EEPROM regdomain: 0x809c
[   12.854072] ath: EEPROM indicates we should expect a country code
[   12.854075] ath: doing EEPROM country->regdmn map search
[   12.854078] ath: country maps to regdmn code: 0x52
[   12.854081] ath: Country alpha2 being used: CN
[   12.854083] ath: Regpair used: 0x52
[   12.863360] ath5k: phy0: Atheros AR2417 chip found (MAC: 0xf0, PHY: 0x70)
[   12.882672] wmi: Mapper loaded
[   14.932742] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.064982] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.065541] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.916517] wlan0: authenticate with <MAC C-01 Vidragon>
[   17.924853] wlan0: send auth to <MAC C-01 Vidragon> (try 1/3)
[   17.926350] wlan0: authenticated
[   17.926567] ath5k 0000:02:0c.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   17.928068] wlan0: associate with <MAC C-01 Vidragon> (try 1/3)
[   17.930430] wlan0: RX AssocResp from <MAC C-01 Vidragon> (capab=0x11 status=0 aid=7)
[   17.930670] wlan0: associated
[   17.930700] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   17.956493] wlan0: deauthenticating from <MAC C-01 Vidragon> by local choice (reason=2)
[   17.956787] wlan0: authenticate with <MAC C-01 Vidragon>
[   17.957001] wlan0: send auth to <MAC C-01 Vidragon> (try 1/3)
[   17.960134] wlan0: authenticated
[   17.960287] ath5k 0000:02:0c.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   17.964052] wlan0: associate with <MAC C-01 Vidragon> (try 1/3)
[   17.966573] wlan0: RX AssocResp from <MAC C-01 Vidragon> (capab=0x11 status=0 aid=7)
[   17.966812] wlan0: associated
[   20.012291] ath5k: ath5k_hw_get_isr: ISR: 0x00000400 IMR: 0x00000000

    ======== Done ========

```

---

### Post by praseodym on 2014-09-16
Hi,

add the MAC address of your (current) AP into the field BSSID of the network-manager profile:
> 
```
wlan0     Scan completed :
          Cell 01 - Address: [COLOR="#FF0000"]<MAC C-01 Vidragon>[/COLOR]
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"[COLOR="#FF0000"]Vidragon[/COLOR]"
```
Check

```
sudo iwlist scan
```
for yourself because the script cuts it off. There are other APs with similar ESSIDs around.

---

### Post by rafael18 on 2014-09-17
Thanks for you response. I will try and publish the results here.

Regards

---

### Post by rafael18 on 2014-09-18
Hi. I tried with the suggestion, but there is not improvement. The system remains a random unstable. Please, is there another idea?

---

### Post by Hadaka on 2014-09-18
Hi, please post the output of,,
```
nm-tool
cat /etc/network/interfaces
```
then set your router to wpa2 ccmp anything but tkip
thanks.

---

### Post by rafael18 on 2014-09-19
> **Hadaka said:**
> Hi, please post the output of,,
```
nm-tool
cat /etc/network/interfaces
```
then set your router to wpa2 ccmp anything but tkip
thanks.

Hi. Thanks for the help.
Here you are the information that you ask.
Sorry, But I cannot set up the router. I live in a residence for students with many peoples. The router belongs to the landlord and we shared the router.

```
NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000
  State:             unavailable
  Default:           no
  HW Address:        00:12:3F:33:C2:08

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [Vidragon] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             connected
  Default:           yes
  HW Address:        B0:48:7A:DE:A5:A2

  Capabilities:
    Speed:           24 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Vidragon-2.4G:   Infra, 20:4E:7F:0A:ED:88, Freq 2412 MHz, Rate 54 Mb/s, Strength 54 WPA
    Vidragon-2.4G_2GEXT: Infra, E8:FC:AF:83:E1:77, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA
    *Vidragon:       Infra, 30:46:9A:34:9E:9F, Freq 2437 MHz, Rate 54 Mb/s, Strength 49 WPA

  IPv4 Settings:
    Address:         192.168.0.36
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1


```

---

